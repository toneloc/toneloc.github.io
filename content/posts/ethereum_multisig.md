---
categories:
  - Miscellany
  - Letters
<!-- tags:
  -  -->
title: "Ethereum Multi-signature vs. Bitcoin Mlti-sigsinature, and Their Custodial Implicaitons"
date: 07 Apr 2018
draft: true
---
Multisig as implemented in Bitcoin is pretty easy. Bitcoin, a stack-based language, has special support for multsig in its language. The bitcoin script to create a mutlisignature address, for example, would look something like this: 

<pre class="language-javascript"><code class="language-javascript">
// Bitcoin multisig stack as follows:

x sig1 
sig2 
2 
pub1 
pub2 
2
OP_CHECKMULTISIG

</code></pre>

What is going on here is x: check the cryptographic signatures ...

All bitcoin transactions are like mini-computer programs. Contrary to popular opinion, bitcoin has smart contracts built into the system, it jsut happens to be a lot more diffiult to implement arbitrary logic. Multisig is 


*

In Ethereum, we have a different story. Despite offering greater diversity of scripting options (in bitcoin script, there are no loops, for example) ethereum multisig is oddly difficult to implement safely. Witness the following: that Parity's multisig wallet, the most popular Ethereum multisig implmentation, was hacked *twice* in 2017 alone. This poor performance coming from a company who's founder is Gavin Wood, the very *author* of the Ethereum yellow paper, the technical specifcation for the Ethereum protocol. 

First, Parity was hacked in July of last year when an artful hacker discovered that by passing in the first 6 bytes of the hash of a function call as message data, the hacker could call any function in a parent library. This is kind of like me mailing a check for $0.00 to your bank, with the words "Change account ownership to me" in the memo field. The automatic-teller then changes the bank ownership to the the sender of the check. In such a prosaic fashion several tens of million dollars where thus redirected. Whoops. 

To add insult and further injury to injury, in November, 2018 a Github user, a one "devops99", made another interesting discovery. By calling a certain function -- sending another blank check to the automatic-teller, with more devious instructions in the memo field -- devops99 was able to indefintely lock up hundreds of millions of dollars of value. 

In Ethereum, the best laid scripts off mice and men ...

Code complexity is a security hole, and it's difficult to follow and test compiled Ethereum virtual machine bytecode. Below I walk through a simple Ethereum multisig contract. Feel free to check out the full code here before proceeding.

What this contract I modified a version of Christian Lundvisk's simpler ethereum multisig (link) for this example. I am going to stick with a check metaphor, as it makes it easier to understand the code.


In the bitcoin example, everyone privy to the mutltisignature scheme must sign the check before mailing at to the blank.
1. Variables 

First we outline our variables. 

<pre class=" language-javascript">
	<code class=" language-javascript">
		<span class="token keyword">uint</span> public <span class="token operator">nonce</span><span class="token punctuation">;</span>
		<span class="token keyword">uint</span> public <span class="token operator">threshold</span><span class="token punctuation">;</span>
		<span class="token keyword">mapping</span> (address => bool) <span class="token operator">isOwner</span><span class="token punctuation">;</span> 
		<span class="token keyword">address[]</span> public <span class="token operator">ownersAddresses</span><span class="token punctuation">;</span> 
	</code>
</pre>



The only variable which can be changed of the four above is the nonce (a number used only once), which is incremented to prevent against replay attacks. A replay attack is when an attacker might try to take inputs of previous transactions and replay them to respend the money. For example, you and your business partners may have a 2-of-3 multisig account and authorize a payment of X ethereum from the shared acccount dto your friendly Balkans-based web designer. So far so good. But without a nonce or an orderer, the friendly Balkans-based web designer can replay the inputs of your transaction and again and again send X ether to his own account. 

The second variable, threshold, is simply the number of authorized signatures required to spend these funds. The third variable, isOwner, is used to check that a submitted cryptographic signature is indeed a member of the multisig group. The fourth variable, ownersAddresses, is an array of the public addresses (in etheruem, all addresses are 32 bytes) of the owners of the account. This address will be ____

Next up is a constructor function. 

<pre class=" language-javascript">
<code class=" language-javascript">
<span class="token keyword">
	function SimpleMultiSig(uint _threshold_, address[] _owners) {
	    require (_owners.length < 10);
	    require (_threshold < owners_.length);
	    require (_threshold != 0);

	    for (uint i=0; i< owners_.length; i++) {
	      isOwner[owners_[i]] = true;
	    }

	    ownersArr = owners_;
	    threshold = threshold_;
	  }
</span>
</code>
</pre>

This function will only run once, upon initiatialization of the contract on the Ethereum network. The first three "require" statements should be pretty self-explanatory. We have a hard cap of 10 singatories on this multisig. Next, we simply iterate through the submitted owner addresses and assign them to the ownersArray we described above. We then assign the submitted threshold.

The next function, and the only other function in this contract is the redeem function. 


<pre class=" language-javascript">
<code class=" language-javascript">
<span class="token keyword">
 // Note that address recovered from signatures must be strictly increasing
  function execute(uint8[] sigV, bytes32[] sigR, bytes32[] sigS, address destination, uint value, bytes data) {
    if (sigR.length != threshold) {throw;}
    if (sigR.length != sigS.length || sigR.length != sigV.length) {throw;}

    // Follows ERC191 signature scheme: https://github.com/ethereum/EIPs/issues/191
    bytes32 txHash = sha3(byte(0x19), byte(0), this, destination, value, data, nonce);

    address lastAdd = address(0); // cannot have address(0) as an owner
    for (uint i = 0; i < threshold; i++) {
        address recovered = ecrecover(txHash, sigV[i], sigR[i], sigS[i]);
        if (recovered <= lastAdd || !isOwner[recovered]) throw;
        lastAdd = recovered;
    }

    // If we make it here all signatures are accounted for
    nonce = nonce + 1;
    if (!destination.call.value(value)(data)) {throw;}
  }

  function () payable {}
}
</span>
</code>
</pre>

This function attempts to do the following. 

<pre class=" language-javascript"><code class=" language-javascript"><span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token boolean">true</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
	<span class="token keyword">while</span> <span class="token punctuation">(</span><span class="token boolean">true</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		<span class="token function">doSomething</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span></code></pre>


http://www.soroushjp.com/2014/12/20/bitcoin-multisig-the-hard-way-understanding-raw-multisignature-bitcoin-transactions/



In addition, we need to distinguish raw multisig (a simple OP_CHECKMULTISIG based script), and P2SH multisig (where the OP_CHECKMULTISIG script is only revealed upon spending).



* Incidentally, you can create a bitcoin mutlisig address with the tool I have on an open source website I host here: https://www.multisig.it.  This website is a fork of coinbin, with some added support for Ethereum and a focus on multisig tranasctions. 

Jackson Pollocks: Piece of crap jumbles of colors - hard to forge! - that you can send to other weirdoes for millions.

Bitcoins: Piece of crap jumbles of numbers - hard to forge! - that you can send to other weirdoes for millions, instantaneosuly.

