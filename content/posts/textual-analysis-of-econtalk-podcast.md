---
categories:
  - Miscellany
<!-- tags:
  -  -->
title: "Textual Analysis of 672 EconTalk Podcasts"
date: 17 Mar 2019
draft: false
---
I'm a big fan of EconTalk, a podcast hosted for over a dozen years by the great spoken word champion of classical liberal ideas, Russ Roberts. Russ is a scholar formerly of George Mason University, now at the Hoover Institution at Stanford. I appreciate Russ' candor, his good-naturedness with all types of guests, and the general subject matter of the show: serious--but not too serious--applied microeconomics. 

Since I've invested several weeks of my life (!) to listening to the show, I thought it would be fun to analyze the available transcripts of 672 of the shows to see what we can find. I got the idea when I heard Patrick Collision of Stripe talk about an analysis he did of Nobel Prize winners to gauge whether innovation in the hard sciences has slowed. I got to thinking: "Were there Nobel Prize Winners in Economics which EconTalk had never even mentioned on the show?" And if so, what could that mean? Theoretically, it might indicate a few things. Maybe a) the winner's work wasn't really that great after all; or b) that the English-Language or US-centric nature of the show has made us forget about foreign contributions to economics; or c) Russ' formal education simply didn't cover a certain topic; or maybe even that d) Russ' interests or biases don't extend to the topics covered by the Prize winner. 

So I compiled a list of 672 shows web pages. Each show as an associated "Audio Highlights" section. For recent shows, this is essentially a transcript. For older shows, it really is more like highlights or even jotted-down notes and definitely not transcribed spoken word. I scraped the data from the "Audio Highlights" section for each of the 672 shows. The resulting text file can be found [here](https://github.com/toneloc/econtalk-scrape/blob/master/econtalk-audio-highlights.txt.zip). The file contains about 5 million words.

I searched the compiled transcripts for mentions of each of the Economics Nobel Prize winners, who were mentioned a total of around 3,000 times. Listeners won't be surprised to find that F.A. Hayek tops the list of most mentions: 1,308. In fact, if a Nobel Prize-winning economist was mentioned on the show, there was a 1 in 3 chance that it was Hayek. This is fine by me; I find Hayek to be one of the most nuanced and novel social theorists of the 20th Century. 

But who else made the top 10? Let's see:

<table>
	<tbody>
		<h5>Top 10 most-mentioned Economics Nobel Prize Winners</h5>
		<td><b>Name</b></td>
		<td><b>Mentions</b</td>
		</tr><td>Friedrich Hayek</td><td >1308</td></tr>
		<tr></th><td >Milton Friedman</td><td >616</td></tr><tr >
		</th><td >Ronald Coase</td><td >303</td></tr><tr >
		</th><td>James M. Buchanan</td><td >168</td></tr>
		<tr ></th><td>Paul Krugman</td><td >156</td></tr><tr >
		</th><td>George Stigler</td><td >101</td></tr><tr >
		</th><td >Gary Becker</td><td >92</td></tr><tr >
		</th><td>Paul Samuelson</td><td >85</td></tr><tr >
		</th><td >Robert Lucas, Jr.</td><td >55</td></tr><tr >
		</th><td>Daniel Kahneman</td><td >50</td></tr>
	</tbody>
</table>

The list is heavy on U. Chicago economists: Friedman, Becker, Coase. Russ went to U. Chicago, so this makes sense. The outlier Krugman, perhaps because of his *New York Times* megaphone, also made the list. 


This data might be misleading in some ways, but I did take basic steps to avoid miscounts. For example, the lone female winner of the Economics Nobel, Elinor Ostrom of Indiana University, had an equally erudite husband, political theorist Vincent Ostrom. I made sure to remove reference's to Vincent from Elinor's count. I made sure too that Smiths of the "Adam" type did not count for Smiths of the "Vernon" flavor and took care to separate "Julian Simon" for "Herb Simon." And when guests talk first names--as in "Merton [Miller] was incredible"--I tried to have that not confuse the count for Robert Merton. I also didn't give any special count to guests on the show. Paul Romer (not Christina Romer, mind you) was on the show a few times, but even if he spoke for hours, his mentions didn't get any special increase. I excluded speaker labels and names in the URLs of the Audio Highlights sections.  

So, anyway, getting back to my original line of inquiry, were there any Economics Nobel Prize winners who were not mentioned at all? Yes, by my count, there were 18. And were they disproportionately not American? Well, not really. 10 of the 18 were not American. The full results can found at the bottom of this post. Many of the economists who received short shrift of EconTalk attention were econometricians, a group Russ is vocal in critiquing. There are some exceptions however. Oliver Hart, for example, is an American specialist in the field of Law and Economics, which seems like an especially interesting omission. 

Incidentally, if Adam Smith had won the Nobel Prize, he would have likely been the second-most mentioned economist. The full phrase "Adam Smith" -- not even counting his other rightful "Smith" mentions -- was uttered at least 531 times. 

Let's take a look at some other notable EconTalk phrases. 

<table>
	<tbody>
		<h5>EconTalk notable phrase and mentions</h5>
		<td><b>Phrase</b></td>
		<td><b>Mentions</b></td>
		</tr><td>"the Fed"</td><td >1707</td></tr>
		<tr><td >"minimum wage"</td><td >454</td></tr>
		<tr ><td >"tax", "taxation", etc.</td><td >3671</td></tr>
		<tr><td >"regulation", "regulate", etc.</td><td >2256</td></tr><tr>
		<tr><td >"curious task"</td><td >25</td></tr><tr>
		<td >"not only to be loved"</td><td >16</td></tr><tr>
		<td >"emergent"</td><td >223</td></tr><tr>
		<td >"skin in the game"</td><td >134</td></tr><tr>
		<td >"bias"</td><td >694</td></tr><tr>
	</tbody>
</table>

I also wanted to gauge what world economies are getting less attention. I measured a country's mentions per trillion dollars of GDP (I took the average of nominal and PPP GDP). I excluded the USA out of the practical difficulty of counting all the various forms of "U.S.", "America", "U.S.A." and so on. 

<table>
	<tbody>
		<h5>Top 10 national economies and their mentions per trillion dollars of GDP</h5>
		<td><b>National Economy</b></td>
		<td><b>Mentions / trillion dollars GDP</b></td>
		<tr><td >USA</td><td ><i>n/a</i></td></tr>
		<tr><td >China</td><td >51</td></tr>
		<tr><td >Japan</td><td >59</td></tr>
		<tr><td >Germany</td><td>90</td></tr>
		<tr><td >England</td><td >214</td></tr>
		<tr><td >India</td><td >42</td></tr>
		<tr><td >France</td><td >126</td></tr>
		<tr><td >Brazil</td><td >17</td></tr>
		<tr><td >Italy</td><td >64</td></tr>
		<tr><td >Canada</td><td >124</td></tr>
	</tbody>
</table>

By this measure, England is getting outsized attention--makes sense, they speak English. India and Brazil espcially are getting notably less attention than their economic output might warrant, while the European countries get, on the whole, get around twice as many mentions as their Asian counterparts, measured against GDP. 

Some further research could potentially use a tool like the NLTK to do some sentiment analysis around certian keywords: how is "minimum wage" or "conservative" or "progressive" spoken about? 

Full results below.

<table>
	<tbody>
		<h5>Nobel Prize Winners in Economics and their number of mentions on Econtalk</h5>
		<td><b>Year</b></td>
		<td><b>Nobel Prize Winner</b></td>
		<td><b>Mentions</b></td>
		<tr><td>1969</td><td>Ragnar Frisch</td><td>0</td></tr>
		<tr><td>1969</td><td>Jan Tinbergen</td><td>2</td></tr>
		<tr><td>1970</td><td>Paul Samuelson</td><td>85</td></tr>
		<tr><td>1971</td><td>Simon Kuznets</td><td>17</td></tr>
		<tr><td>1972</td><td>John Hicks</td><td>13</td></tr>
		<tr><td>1972</td><td>Kenneth Arrow</td><td>34</td></tr>
		<tr><td>1973</td><td>Wassily Leontief</td><td>8</td></tr>
		<tr><td>1974</td><td>Gunnar Myrdal</td><td>9</td></tr>
		<tr><td>1974</td><td>Friedrich Hayek</td><td>1308</td></tr>
		<tr><td>1975</td><td>Leonid Kantorovich</td><td>0</td></tr>
		<tr><td>1975</td><td>Tjalling Koopmans</td><td>6</td></tr>
		<tr><td>1976</td><td>Milton Friedman</td><td>616</td></tr>
		<tr><td>1977</td><td>Bertil Ohlin</td><td>4</td></tr>
		<tr><td>1977</td><td>James Meade</td><td>11</td></tr>
		<tr><td>1978</td><td>Herbert A. Simon</td><td>6</td></tr>
		<tr><td>1979</td><td>Theodore Schultz</td><td>8</td></tr>
		<tr><td>1979</td><td>Arthur Lewis</td><td>2</td></tr>
		<tr><td>1980</td><td>Lawrence Klein</td><td>0</td></tr>
		<tr><td>1981</td><td>James Tobin</td><td>12</td></tr>
		<tr><td>1982</td><td>George Stigler</td><td>101</td></tr>
		<tr><td>1983</td><td>Gérard Debreu</td><td>5</td></tr>
		<tr><td>1984</td><td>Richard Stone</td><td>1</td></tr>
		<tr><td>1985</td><td>Franco Modigliani</td><td>6</td></tr>
		<tr><td>1986</td><td>James M. Buchanan</td><td>168</td></tr>
		<tr><td>1987</td><td>Robert Solow</td><td>23</td></tr>
		<tr><td>1988</td><td>Maurice Allais</td><td>0</td></tr>
		<tr><td>1989</td><td>Trygve Haavelmo</td><td>0</td></tr>
		<tr><td>1990</td><td>Harry Markowitz</td><td>9</td></tr>
		<tr><td>1990</td><td>Merton Miller</td><td>9</td></tr>
		<tr><td>1990</td><td>William F. Sharpe</td><td>19</td></tr>
		<tr><td>1991</td><td>Ronald Coas</td><td>303</td></tr>
		<tr><td>1992</td><td>Gary Becker</td><td>92</td></tr>
		<tr><td>1993</td><td>Robert Fogel</td><td>6</td></tr>
		<tr><td>1993</td><td>Douglass North</td><td>29</td></tr>
		<tr><td>1994</td><td>John Harsanyi</td><td>0</td></tr>
		<tr><td>1994</td><td>John Forbes Nash</td><td>2</td></tr>
		<tr><td>1994</td><td>Reinhard Selten</td><td>0</td></tr>
		<tr><td>1995</td><td>Robert Lucas, Jr.</td><td>55</td></tr>
		<tr><td>1996</td><td>James Mirrlees</td><td>0</td></tr>
		<tr><td>1996</td><td>William Vickrey</td><td>1</td></tr>
		<tr><td>1997</td><td>Robert C. Merton</td><td>2</td></tr>
		<tr><td>1997</td><td>Myron Scholes</td><td>23</td></tr>
		<tr><td>1998</td><td>Amartya Sen</td><td>13</td></tr>
		<tr><td>1999</td><td>Robert Mundell</td><td>2</td></tr>
		<tr><td>2000</td><td>James Heckman</td><td>9</td></tr>
		<tr><td>2000</td><td>Daniel McFadden</td><td>0</td></tr>
		<tr><td>2001</td><td>George Akerlof</td><td>22</td></tr>
		<tr><td>2001</td><td>Michael Spence</td><td>3</td></tr>
		<tr><td>2001</td><td>Joseph E. Stiglitz</td><td>33</td></tr>
		<tr><td>2002</td><td>Daniel Kahneman</td><td>50</td></tr>
		<tr><td>2002</td><td>Vernon L. Smith</td><td>38</td></tr>
		<tr><td>2003</td><td>Robert F. Engle</td><td>0</td></tr>
		<tr><td>2003</td><td>Clive Granger</td><td>0</td></tr>
		<tr><td>2004</td><td>Finn E. Kydland</td><td>7</td></tr>
		<tr><td>2004</td><td>Edward C. Prescott</td><td>22</td></tr>
		<tr><td>2005</td><td>Robert J. Aumann</td><td>0</td></tr>
		<tr><td>2005</td><td>Thomas C. Schelling</td><td>17</td></tr>
		<tr><td>2006</td><td>Edmund S. Phelps</td><td>13</td></tr>
		<tr><td>2007</td><td>Leonid Hurwicz</td><td>1</td></tr>
		<tr><td>2007</td><td>Eric S. Maskin</td><td>0</td></tr>
		<tr><td>2007</td><td>Roger B. Myerson</td><td>0</td></tr>
		<tr><td>2008</td><td>Paul Krugman</td><td>156</td></tr>
		<tr><td>2009</td><td>Elinor Ostrom</td><td>41</td></tr>
		<tr><td>2009</td><td>Oliver E. Williamson</td><td>14</td></tr>
		<tr><td>2010</td><td>Peter A. Diamond</td><td>2</td></tr>
		<tr><td>2010</td><td>Dale T. Mortensen</td><td>2</td></tr>
		<tr><td>2010</td><td>Christopher A. Pissarides</td><td>1</td></tr>
		<tr><td>2011</td><td>Thomas J. Sargent</td><td>11</td></tr>
		<tr><td>2011</td><td>Christopher A. Sims</td><td>16</td></tr>
		<tr><td>2012</td><td>Alvin E. Roth</td><td>4</td></tr>
		<tr><td>2012</td><td>Lloyd S. Shapley</td><td>0</td></tr>
		<tr><td>2013</td><td>Eugene F. Fama</td><td>19</td></tr>
		<tr><td>2013</td><td>Lars Peter Hansen</td><td>2</td></tr>
		<tr><td>2013</td><td>Robert J. Shiller</td><td>17</td></tr>
		<tr><td>2014</td><td>Jean Tirole</td><td>0</td></tr>
		<tr><td>2015</td><td>Angus Deaton</td><td>16</td></tr>
		<tr><td>2016</td><td>Oliver Hart</td><td>0</td></tr>
		<tr><td>2016</td><td>Bengt Holmström</td><td>0</td></tr>
		<tr><td>2017</td><td>Richard Thaler</td><td>17</td></tr>
		<tr><td>2018</td><td>William Nordhaus</td><td>3</td></tr>
		<tr><td>2018</td><td>Paul Romer</td><td>16</td></tr>
		</tbody>
</table>

