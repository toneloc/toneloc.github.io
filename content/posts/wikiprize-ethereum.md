---
categories:
  - Miscellany
<!-- tags:
  -  -->
title: "WikiPrize: Crowdfunded Prize Contracts Implemented on Ethereum Blockchain"
date: 30 Oct 2017
draft: true
---
This post attempts to make a material contribution to the study and implementation of crowdfunded prizes. The post describes a system called WikiPrize, whereby Ethereum users may create prize contracts controlled by customizable multisignature schemes.

The post is broken down into three parts:

(1) describes the process flow and overall functionality;
(2) documents the code implementing this system;
(3) suggests potential applications and areas for improvement;

(1) System overview

There are many things we want in the world, but don't exist yet. WikiPrize attempts to 

Assuming the contract has been deployed to the Ethereum network, the process for the user may be as follows:

(1) Someone describes something to be accomplished. This could be , for example, a mathematical problem to be solved or a desired political candidate to run for office. The user will offer an reward for anyone who solves the problem or achieves the desired result, based upon user-specified criteria. The user supplies an array of account addresses *[a]* who will serve as judges. The user specifies the threshold number *t* of judges who must agree that the desired outcome has been achieved. Finally, the user specifies a sunset block number, whereby, if the outcome is not achieved, the prize rewards shall be refunded to users. 
(2) The user publicizes the prize reward and securely distributes keys to the judges. Other users may also contribute to the prize reward fo the 
(3) Either of two results occurs: 
	(1) Nobody achieves the desired outcome. Upon reaching the sunset block number, Ether is refunded to the contributing users. 
	(2) Somebody achieves the desired outcome. Actual adjudication is handled offline. The judges submit a signed transaction with *t* or greater signatories, specifying the winning account number. 


(2) Technical implementation

Technical implementaiton makes use of the Truffle framework, testRPC, and the Open Zeppelin PullPayment, Bounty, Destructible smart contracting templates. The full code for the system can be found on GitHub. 

The system comprises one contract, WikiPrize, with five methods:

	1 - init method creating an instance of a WikiPrize, taking the following parameters:
	2 - create prize method, accepting the following parameters
	3 - fundPrize() accepting the following parameters and returning
	3 - claim prize method, accepting a text description of how the problem was solved, and specifying an account addres 
	4 - fundPrize
	5- refund money

These mutisig addresses may be themselves


(3) Possible applications

The multisignature scheme is customizable to accept 