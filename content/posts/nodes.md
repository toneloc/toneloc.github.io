---
categories:
  - Miscellany
  - Code
<!-- tags:
  -  -->
title: "Setting up Local Bitcoin and Ethereum Nodes on a Dedicated Linux Machine"
date: 27 Mar 2018
draft: false
---
In my experience, to properly interrogate the bitcoin or ethereum blockchain, network, and all their associated programs and scripts, it is best to dedicate a standalone Linux machine. These programs require a lot of horsepower, storage, and network capacity. Often they must run uninterrupted for hours or days at a time. For these reasons, a dedicated computer is advisable. 

Also, as public blockchain projects come from the Linux open source lineage, Linux will be the easiest way to run a full node and interact with the latest and greatest features of cryptographic and networking technology, like homomorphic encryption techniques and the Lightning network. Don’t even try to run a full node with Windows, and Macs will only take you so far. In my experience, running an Ubuntu virtual machine with VirtualBox inside a Windows or Mac environment is not worth the ineivitable lack of performance and usability, especially when you can set up an Ubuntu environment for well under $1,000, as I describe below.

For my dedicated machine, I went with a cheap Dell laptop, into which I shoved a 1TB SSD (Samsung EVO), around $300 on Amazon. Do not -- I repeat -- do not try to sync with Ethereum on a typical HDD hard drive. It won’t end well; or rather, it will never end, as the Go Ethereum client is liable to hang for weeks on end as it tries to catch up with the burgeoning chain state. Here in the spring of 2018, checking the size of the bitcoin blockchain with "du -sh .bitcoin/" returns 177GB. The ethereum directories altogether cost 380GB, though running ethereum in a fastsync mode will recude that to tens of GBs. Bitcoin also has an option to reduce storage by 95% or more. Anyway, with these rough figures in mind, and to keep room on your laptop for the *Captain Phillips* BluRay you will torrent, it would be wise to plan for storage of 1TB or greater. 

I installed Artful Aardvark, Ubuntu 17.10 from a USB drive on my new laptop. I would recommend using the latest available Ubuntu version. I first tried installing Bitcoin Core on Ubuntu 16.10 (as was recommended) but had trouble accessing the PPA repositories. Reinstalling the latest Ubuntu did the trick. I had to format the Linux on thumb drive using Unetbootin. The other tricky part, depending on how old your computer is, will be changing the boot and BIOS settings to load from the USB first. Nothing, clever reader, you cannot handle through trial and error. And Google.

One I upgraded Ubuntu, I installed bitcoind and geth, the most popular bitcoin and ethereum clients, with the below commands:

<pre class="language-bash">
	<code class="language-bash">
		<span class="token operator">$</span> <span class="token function">sudo apt-add-repository ppa:bitcoin/bitcoin</span> 
		<span class="token operator">$</span> <span class="token function">sudo apt-get update</span> 
		<span class="token comment"># If you want the GUI you can append "bitcoin-qt" </span></code>
		<span class="token comment"># to the end of this command.</span></code>
		<span class="token operator">$</span> <span class="token function">sudo apt-get install bitcoind</span> 

		<span class="token comment"># Then run bitcoin daemon client.</span></code>
		<span class="token comment"># This will take a while ... a couple days or more.</span></code>
		<span class="token operator">$</span> <span class="token function">bitcoind -daemon</span> 

		<span class="token comment"># Check bitcoin client is installed okay with below</span></code>
		<span class="token operator">$</span> <span class="token function">bitcoin-cli getblockchaininfo</span> 

		<span class="token comment"># Watch the download progress with </span></code>
		<span class="token operator">$</span> <span class="token function">tail -f ~/.bitcoin/debug.log</span> 
	</code>
</pre>


And for ethereum ... much the same. I reccommend first syncing with --fastsync, unless you have the patience of a corpse. You can go back and do a full sync after.

<pre class="language-bash">
	<code class="language-bash">
		<span class="token operator">$</span> <span class="token function">sudo apt-get install software-properties-common</span> 
		<span class="token operator">$</span> <span class="token function">sudo add-apt-repository -y ppa:ethereum/ethereum</span> 
		<span class="token operator">$</span> <span class="token function">sudo apt-get update</span> 
		<span class="token comment"># You may find that you need to install this.</span></code>
		<span class="token operator">$</span> <span class="token function">sudo apt-get libsssl-dev</span> 
		<span class="token operator">$</span> <span class="token function">sudo apt-get install ethereum</span> 

		<span class="token comment"># Then run geth client.</span></code>
		<span class="token comment"># This will also take a while ... a couple days or more.</span></code>
		<span class="token operator">$</span> <span class="token function">geth --syncmode fast</span> 

		<span class="token comment"># Run a JS console </span></code>
		<span class="token operator">$</span> <span class="token function">geth attach</span> 

		<span class="token comment">// Check progress </span></code>
		<span class="token operator">></span> <span class="token function">web3.eth.isSyncing</span> 
	</code>
</pre>

On my first attempt to synch these clients with a 12GB HDD drive, I started downloading the Bitcoin and Ethereum blockchains concurrently on a Saturday evening. I was interested to see which blockchain caught up first, but there was no comparison: by the following afternoon, the bitcoin blockchain was at block around 80% downloaded. The bitcoin blockchain completed downloading after about 40 hours, much quicker than I had anticipated. The Ethereum blockchain was another story and never caught up (this was without the fast syncmode flag enabled), at which point I ordered an SSD drive and ditched my efforts with the HDD.

(As a brief sidenote: The difficulty of downloading the Ethereum full chain will be a hindrance to creating the distributed network that Ethereum hopes to achieve. Insofar as ease of node setup is a technical benefit in and of itself, bitcoind is the clear winner. Of course, that premise is questionable ... how many nodes do you really need?)

The steps above will allow you to run local scripts to analyze either blockchain's state, to assess smart contract security, to deploy transactions to either blockchain, and to interface with the rich commands that bitcoin-cli, geth, and the web3 console allow. They will not allow you, however, to accept inbound traffic, validate transactions, or mine for bitcoin or ether. There are further steps to take, such as opening up ports on your router and editing your bitcon.conf configuration file to allow this. But the above is a good start to getting going in a fast and usable Linux dev environment, without the hassle of messing with Windows, Mac, or a Linux VirtualBox.