Download Link: https://assignmentchef.com/product/solved-csc3002f-assignment2-sniffing-with-wireshark
<br>
This assignment focuses on the network’s ‘packets’ being sent around on a computer network. You will take a look at what is actually sent around on the transmission medium and what those packets ‘look like’. You may have heard of IP packets, but what exactly is ‘inside’ it? Or sending HTTP request to open a web page: how is that put across the transmission medium? The Wireshark tool, a packet ‘sniffer’, will be used to obtain answers to such questions.

<strong>What</strong> <strong>you</strong> <strong>have</strong> <strong>to</strong> <strong>submit</strong> <em>in</em> <em>one</em> <em>compressed</em> <em>file</em> <strong>where</strong> <em>no</em> <em>file</em> <em>is</em> <em>in</em> <em>a</em> <em>directory</em> <strong>(as</strong> <strong>you should</strong> <strong>recall</strong> <strong>from</strong> <strong>prior</strong> <strong>exposure</strong> <strong>to</strong> <strong>the</strong> <strong>automated</strong> <strong>marker</strong> <strong>in</strong> <strong>previous</strong> <strong>courses):</strong>

<ol>

 <li>A trace file called ‘tcptrace.pcap’ containing your trace for the first half of the aassignment (questions 1-9) ;</li>

 <li>A trace file called ‘iptrace.pcap’ containing your trace for the second half of the aassignment (questions 10-18) ;</li>

 <li>The answers to the automarker-marked questions in a structured text file called ‘automark.txt’; these questions are indicated with “[AM]”; details of the file structure and a sample file are on the Vula page for the assignment;</li>

 <li>The answers (optionally including annotated screenshots) to the remaining questions of the<sup>                              </sup>Wireshark section, as indicated.</li>

</ol>

<strong>NOTE</strong>

You can submit only FIVE times, so be careful and think and check twice, or even thrice,  before submitting

Your traces must be saved as ‘pcap’ files, not ‘pcapng’ files.

<strong>NOTE</strong>

The Automarker is uniquely configured for the Wireshark section, in that it processes your trace to pull out the answers, and compares it to what you have written in the txt file. As we have a list who gets assigned which file to upload, we immediately know who’s been copying in case you submit someone else’s trace and answer file. So don’t even try, unless you want a 0 for the assignment and be added onto the departmental plagiarism list, or if you are already on there, go through the full UCT disciplinary procedures for plagiarism (see departmental plagiarism policy for details). <em>The</em> <em>format</em> <em>of the</em> <em>answer</em> <em>file</em> <em>and</em> <em>an</em> <em>example</em> <em>are</em> <em>available</em> <em>on</em> <em>Vula</em> <em>and</em> <em>shown</em> <em>in</em> <em>Appendix</em> <em>A</em> <em>of</em> <em>this</em> <em>file;</em> <em>check</em> <em>these before</em> <em>submitting</em> <em>it.</em>

<h1><a name="_Toc12327"></a>2           Sniffing with Wireshark</h1>

⇒ There’s a lengthy explanation of steps, but the trace capturing tasks are fairly short. You may wish to read through the TCP and IP section first, then capture the required traces before proceeding to answer the questions. ⇐

Note: when the description says you’re better off closing all other networked apps before starting the capture, do yourself a favour, and do so. Then answer the questions with that ‘clean’ trace.(It is most fascinating to see how busy your networked apps are even when you think nothing is happening, but that’s a different topic.)

<h2><a name="_Toc12328"></a>2.1         TCP Wireshark lab</h2>

In this part of the practical assignment, you’ll investigate the behaviour of the TCP protocol. You’ll do so by analysing a trace of the TCP segments sent and received in transferring a file from your computer to a remote server. That file is allocated to you and is old enough to have had their copyright expired, such as Lewis Carrol’s Alice’s Adventures in Wonderland (many of those books are digitised and available from Project Gutenberg<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>). You’ll study TCP’s use of sequence and acknowledgement numbers for providing reliable data transfer. TCP’s congestion control algorithm is nice, but your data will look ‘hectic’ and therefore is an optional exercise, and likewise on TCP’s receiver-advertised flow control mechanism. You will also briefly consider TCP connection setup and investigate the performance (throughput and round-trip time) of the TCP connection between your computer and the server.

Before beginning this lab, you’ll probably want to review sections 3.5 and 3.7 in the textbook. There is a separate Wireshark introduction pdf file on vula that you may want to read through, which gives a little overview of the tool, and there’s the manual online. As they keep on changing things in the interface and there are slight differences across OSs, it may be that the screenshots below in this document aren’t exactly the same as what you’ll see, but worry not, the questions can be answered.

<h3><a name="_Toc12329"></a>2.1.1         Capturing a bulk TCP transfer from your computer to a remote server</h3>

You’ll need to use Wireshark to obtain a packet trace of the TCP transfer of a file from your computer to a remote server. You’ll do so by accessing a Web page that will allow you to enter the name of a file stored on your computer (which contains the ASCII text of your assigned Gutenberg ebook), and then transfer the file to a Web server using the HTTP POST method (see section 2.2.3 in the text). The POST method is used rather than the GET method, because you’re going to transfer a large amount of data from your computer to another computer. You have to run Wireshark during this time to obtain the trace of the TCP segments sent and received from your computer. Do the following:

<ul>

 <li>Start up your web On Vula, go to CSC3002F,2017 Resources&gt;Networks&gt;Text File</li>

</ul>

Allocations, and retrieve an ASCII copy of the Gutenberg ebook assigned to you, your gutenbergfile.txt. Store this file somewhere on your computer.

<ul>

 <li>Next go to <a href="http://gaia.cs.umass.edu/wireshark-labs/TCP-wireshark-file1.html">http://gaia.cs.umass.edu/wireshark-labs/TCP-wireshark-file1.html</a><a href="http://gaia.cs.umass.edu/wireshark-labs/TCP-wireshark-file1.html">.</a> You should see a screen that looks like the screenshot in 1. Use the Browse button in this form to enter the name of the file (full path name) on your computer containing yourgutenbergfile (or do so manually). Don’t yet press the “Upload alice.txt file” button.</li>

 <li>Now start up Wireshark and begin packet capture (Capture −&gt; Start) and then press OK on theWireshark Packet Capture Options screen. Note: if it doesn’t work, go to Capture −&gt; Interfaces and select the <a href="https://www.gutenberg.org/">NIC and then click Start</a></li>

</ul>

Figure 1: Upload page for yourgutenbergfile.txt

<ul>

 <li>Return to your browser and press the “Upload txt file” button to upload the file to the gaia.cs.umass.edu server. Once the file has been uploaded, a short congratulations message will be displayed in your browser window.</li>

 <li>Stop the packet capture and save as ‘tcptrace.pcap’.</li>

</ul>

–Your Wireshark window should look similar to the screenshot in Fig. 2. (Note: it may look slightly different, which is due to either difference in operating system or yet another version of the

software.). Scroll down to the IP section and do that part of the trace capture.

<strong>NOTE</strong>: you certainly will be able to run Wireshark in the labs. It may well be the case that when you (want to) start doing this exercise only some 5 hours before the assignment deadline, some server is down or the network happens to be not working. <em>that’s your problem </em>and not an excuse or a valid reason for extension. There’s plenty of time to do these exercises, and most of the time, the network and servers are working.

<h3><a name="_Toc12330"></a>2.1.2         A first look at the captured trace</h3>

Before analysing the behaviour of the TCP connection in detail, let’s take a high level view of the trace. First, filter the packets displayed in the Wireshark window by entering “tcp” (lowercase, no quotes, and don’t forget to press return after entering!) into the display filter specification window towards the top of the Wireshark window. What you should see is series of TCP and HTTP messages between your computer and gaia.cs.umass.edu. You should see the initial three-way handshake containing a SYN message. You should see an HTTP POST message. Depending on the version of Wireshark you are using, you might see a series of “HTTP Continuation” messages being sent from your computer to gaia.cs.umass.edu. There is no such thing as an HTTP Continuation message; this is Wireshark’s way of indicating that there are multiple TCP segments being used to carry a single HTTP message. In more recent versions of Wireshark, you’ll see “[TCP segment of a reassembled PDU]” in the Info column of the Wireshark display to indicate that this TCP segment contained data that belonged to an upper layer protocol message (in our case here, HTTP). You should also see TCP ACK segments being returned from gaia.cs.umass.edu to your computer.

Figure 2: A screenshot of Wireshark after packet capture.

Answer the following questions, by using your own trace. See Appendix A for the format of the txt file for the questions that will be marked by the automatic marker (indicated with “[AM]”). For the other manually marked questions, write the answer in a separate file (e.g., MS Word. Open Office, L<sup>A</sup>TEX) and, where applicable, include a screenshot of the packet(s) within the trace that you used to answer the question asked, or annotate the packet to explain your answers. (To print a packet, use File −<em>&gt; </em>Print, choose Selected packet only, choose Packet summary line, and select the minimum amount of packet detail that you need to answer the question.)

<h4>Exercises</h4>

<ol>

 <li>What is the IP address and TCP port number used by the client computer (source) that is transferring the file to gaia.cs.umass.edu? To answer this question, it’s probably easiest to select an HTTP message and explore the details of the TCP packet used to carry this HTTP message, using the “details of the selected packet header window” (refer to Figure 2 in the</li>

</ol>

‘Getting Started with Wireshark’ Lab if you’re uncertain about the Wireshark windows. [AM]

<ol start="2">

 <li>What is the IP address of gaia.cs.umass.edu? On what port number is it sending and receiving TCP segments for this connection? [AM]</li>

</ol>

<h3><a name="_Toc12331"></a>2.1.3         TCP Basics</h3>

Since this lab is about TCP rather than HTTP, let’s change Wireshark’s “listing of captured packets” window so that it shows information about the TCP segments containing the HTTP messages, rather than about the HTTP messages. To have Wireshark do this, select Analyze −<em>&gt; </em>Enabled Protocols.

Then uncheck the HTTP box and select OK. You should now see a Wireshark window that looks like the one in Fig. 3.

Figure 3: Another screenshot of Wireshark after packet capture.

This is what we’re looking for—a series of TCP segments sent between your computer and gaia.cs.umass.edu. We will use the packet trace that you have captured to study TCP behaviour in the rest of this lab.

<h4>Exercises</h4>

<ol start="3">

 <li>What is the sequence number of the TCP SYN segment that is used to initiate the TCP connection between the client computer and gaia.cs.umass.edu? What is it in the segment that identifies the segment as a SYN segment? [AM]</li>

 <li>What is the sequence number of the SYNACK segment sent by gaia.cs.umass.edu to the client computer in reply to the SYN? What is the value of the Acknowledgement field in the SYNACK segment? How did gaia.cs.umass.edu determine that value? What is it in the segment that identifies the segment as a SYNACK segment? [AM]</li>

 <li>What is the sequence number of the TCP segment containing the HTTP POST command? Note that in order to find the POST command, you’ll need to dig into the packet content field at the bottom of the Wireshark window, looking for a segment with a “POST” within its DATA field. [AM]</li>

 <li>Consider the TCP segment containing the HTTP POST as the first segment in the TCP connection. What are the sequence numbers of the first six segments in the TCP connection (including the segment containing the HTTP POST)? At what time was each segment sent? When was the ACK for each segment received? Given the difference between when each TCP segment was sent, and when its acknowledgement was received, what is the RTT value for each of the six segments? What is the EstimatedRTT value (see Section 3.5.3, page 239 in text) after the receipt of each ACK? Assume that the value of the EstimatedRTT is equal to the measured RTT for the first segment, and then is computed using the EstimatedRTT equation on page 239 for all subsequent segments. (Note: Wireshark has a nice feature that allows you to plot the RTT for each of the TCP segments sent. Select a TCP segment in the “listing of captured packets” window that is being sent from the client to the gaia.cs.umass.edu server. Then select: Statistics −<em>&gt; </em>TCP Stream Graph −<em>&gt; </em>Round Trip Time Graph.) [AM]</li>

 <li>What is the length of each of the first six TCP segments? [AM]</li>

 <li>a) What is the minimum amount of available buffer space advertised at the received for the entire trace? [AM]</li>

 <li>b) Does the lack of receiver buffer space ever throttle the sender? note: Answer this in the document that will not be marked automatically</li>

 <li>Are there any retransmitted segments in the trace file? What did you check for (in the trace) in order to answer this question? NOTE: Answer this in the document that will not be marked automatically.</li>

</ol>

<h3><a name="_Toc12332"></a>2.1.4         TCP congestion control in action (optional!)</h3>

Let’s now examine the amount of data sent per unit time from the client to the server. Rather than (tediously!) calculating this from the raw data in the Wireshark window, we’ll use one of Wireshark’s TCP graphing utilities—Time-Sequence-Graph (Stevens)—to plot out data.

Select a TCP segment in the Wireshark’s “listing of captured-packets” window. Then select the menu : Statistics −<em>&gt; </em>TCP Stream Graph −<em>&gt; </em>Time-Sequence-Graph(Stevens). In theory, you should see a plot that looks similar to the plot as shown in Figure 4, which was created from the captured packets in the packet trace tcp-ethereal-trace-1 in http://gaia.cs.umass.edu/wiresharklabs/wireshark-traces.zip. In practice, you’re unlikely to see such neat results with your own trace.

Here, each dot represents a TCP segment sent, plotting the sequence number of the segment versus the time at which it was sent. Note that a set of dots stacked above each other represents a series of packets that were sent back-to-back by the sender.

Use the Time-Sequence-Graph(Stevens) plotting tool to view the sequence number versus time plot of segments being sent from the client to the gaia.cs.umass.edu server. Can you identify where TCP’s slowstart phase begins and ends, and where congestion avoidance takes over? If not (or extremely hard to find out form the graph), why not? Comment on ways in which the measured data differs from the idealised behaviour of TCP that we’ve studied in the text.

Note: the reason why this exercise is optional is because your own trace will not nearly be as neat as this one in Fig. 4. That’s not your bad. Can you think of a reason why yours will be so different?

<h2><a name="_Toc12333"></a>2.2         IP Wireshark lab</h2>

In this part of the practical assignment, you’ll investigate the IP protocol, focusing on the IP datagram. You’ll do so by analysing a trace of IP datagrams sent and received by an execution of the traceroute program<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a>. We’ll investigate the various fields in the IP datagram, and study IP fragmentation in detail.

Figure 4: Time sequence graph with the book’s clean data.

Before beginning this lab, you’ll probably want to review sections 1.4.3 in the text and section 3.4 of RFC 2151<a href="#_ftn3" name="_ftnref3"><sup>[3]</sup></a> to update yourself on the operation of the traceroute program. You’ll also want to read Section 4.4 in the text, and probably also have RFC 791<sup>4 </sup>on hand as well, for a discussion of the IP protocol.

<h3><a name="_Toc12334"></a>2.2.1         Capturing packets from an execution of traceroute</h3>

In order to generate a trace of IP datagrams for this lab, we’ll use the traceroute program to send datagrams of different sizes towards some destination, X. Recall that traceroute operates by first sending one or more datagrams with the time-to-live (TTL) field in the IP header set to 1; it then sends a series of one or more datagrams towards the same destination with a TTL value of 2; it then sends a series of datagrams towards the same destination with a TTL value of 3; and so on. Recall that a router must decrement the TTL in each received datagram by 1 (actually, RFC 791 says that the router must decrement the TTL by at least one). If the TTL reaches 0, the router returns an ICMP message (type 11 – TTL-exceeded) to the sending host. As a result of this behaviour, a datagram with a TTL of 1 (sent by the host executing traceroute) will cause the router one hop away from the sender to send an ICMP TTL-exceeded message back to the sender; the datagram sent with a TTL of 2 will cause the router two hops away to send an ICMP message back to the sender; the datagram sent with a TTL of 3 will cause the router three hops away to send an ICMP

message back to the sender; and so on. In this manner, the host executing traceroute can learn the identities of the routers between itself and destination X by looking at the source IP addresses in the datagrams containing the ICMP TTL-exceeded messages.

We’ll want to run traceroute and have it send datagrams of various lengths.

<ul>

 <li>The tracert program (used for our ICMP Wireshark lab) provided with Windows does not allow one to change the size of the ICMP echo request (ping) message sent by the tracert program<a href="#_ftn4" name="_ftnref4"><sup>[4]</sup></a>.</li>

 <li>Linux/Unix/MacOS. With the Unix/MacOS traceroute command, the size of the UDP datagram sent towards the destination can be explicitly set by indicating the number of bytes in the datagram; this value is entered in the traceroute command line immediately after the name or address of the destination. For example, to send traceroute datagrams of 2000 bytes towards gaia.cs.umass.edu, the command would be:</li>

</ul>

traceroute gaia.cs.umass.edu 2000 Do the following:

<ul>

 <li>Start up Wireshark and begin packet capture (Capture −<em>&gt; </em>Start) and then press OK on the Wireshark Packet Capture Options screen (we won’t need to select any options here), if you did not continue with the TCP capture after all.</li>

 <li>If you are using a Windows platform, use the command prompt<a href="#_ftn5" name="_ftnref5"><sup>[5]</sup></a>. If you are using a Unix or Mac platform, enter three traceroute commands, one with a length of 56 bytes, one with a length of 2000 bytes, and one with a length of 3500 bytes. You can do the same with pingplotter, but not with tracert.</li>

 <li>Next, send a set of datagrams with a longer length, by selecting Edit −<em>&gt; </em>Advanced Options −<em>&gt; </em>Packet Options and enter a value of 2000 in the Packet Size field and then press OK.</li>

</ul>

Then press the Resume button.

<ul>

 <li>Stop Wireshark tracing when it has completed the Save the trace as ‘iptrace.pcap’.</li>

</ul>

<h3><a name="_Toc12335"></a>2.2.2         A look at the captured trace</h3>

In your trace, you should be able to see the series of ICMP Echo Request (in the case of Windows machine) or the UDP segment (in the case of Unix) sent by your computer and the ICMP TTLexceeded messages returned to your computer by the intermediate routers. In the questions below, we’ll assume you are using a Windows machine; the corresponding questions for the case of a Unix machine should be clear. When answering a question below you should hand in a softcopy of the packet(s) within the trace that you used to answer the question asked. When you hand in your assignment, annotate the output so that it’s clear where in the output you’re getting the information for your answer to the manually marked questions.

<h4>Exercises</h4>

<ol start="10">

 <li>Select the first ICMP Echo Request message sent by your computer, and expand the InternetProtocol part of the packet in the packet details window (see also Fig. 7). What is the IP address of your computer? [AM]</li>

 <li>Within the IP packet header, what is the value in the upper layer protocol field? [AM]</li>

 <li>Has this IP datagram been fragmented? [AM]</li>

 <li>Explain how you determined whether or not the datagram has been fragmented.</li>

 <li>How many bytes are in the IP header? How many bytes are in the payload of the IP datagram?</li>

</ol>

Figure 5: Screenshot related to question 10.

Next, sort the traced packets according to IP source address by clicking on the Source column header; a small downward pointing arrow should appear next to the word Source. If the arrow points up, click on the Source column header again. Select the first ICMP Echo Request message sent by your computer, and expand the Internet Protocol portion in the “details of selected packet header” window. In the “listing of captured packets” window, you should see all of the subsequent ICMP messages (perhaps with additional interspersed packets sent by other protocols running on your computer) below this first ICMP. Use the down arrow to move through the ICMP messages sent by your computer.

<ol start="15">

 <li>Which fields in the IP datagram always change from one datagram to the next within this series of ICMP messages sent by your computer?</li>

 <li>Which fields stay constant? Which of the fields <em>must </em>stay constant? Which fields must change? Why?</li>

 <li>Describe the pattern you see in the values in the Identification field of the IP datagram</li>

</ol>

Next (with the packets still sorted by source address) find the series of ICMP TTL-exceeded replies sent to your computer by the nearest router.

<ol start="17">

 <li>Describe how you found it. What is the value in the Identification field and the TTL field?</li>

 <li>Do these values remain unchanged for all of the ICMP TTL-exceeded replies sent to your computer by the nearest (first hop) router? Why?</li>

</ol>

Credits: these Wireshark exercises are heavily based on Kurose and Ross’ material for the Wireshark labs accompanying the book, but note that <em>some strategic modifications have been made </em>to prevent you from copying the answers from those online available (well, you could, but then the answers would be wrong). That said, if you’re unsure what to do, you could find that lab assignment and answers and practice with that first.

<h1><a name="_Toc12336"></a>A          Appendix: Automarker format</h1>

The questions that will be automatically marked have to be typed up in a txt file in the following format:

Figure 6: Format of the answer file for the questions that will be marked by the automatic marker.

On the next page you can see an example of how your file may look like; this is sample data, so your answers will be different.

Figure 7: Sample file with hypothetical answers (that will be marked by the automatic marker).

<a href="#_ftnref1" name="_ftn1">[1]</a> https://www.gutenberg.org/

<a href="#_ftnref2" name="_ftn2">[2]</a> The traceroute program itself is explored in more detail elsewhere in the Wireshark ICMP lab that we don’t cover in the pracs, but is available on Vula in case you’re interested

<a href="#_ftnref3" name="_ftn3">[3]</a> <a href="ftp://ftp.rfc-editor.org/in-notes/rfc2151.txt">ftp://ftp.rfc-editor.org/in-notes/rfc2151.txt </a><a href="ftp://ftp.rfc-editor.org/in-notes/rfc791.txt"><sup>4</sup></a><a href="ftp://ftp.rfc-editor.org/in-notes/rfc791.txt">ftp://ftp.rfc-editor.org/in-notes/rfc791.txt</a>

<a href="#_ftnref4" name="_ftn4">[4]</a> A nicer Windows traceroute program is pingplotter, available both in free version and shareware versions at http://www.pingplotter.com. Download and install pingplotter, and test it out by performing a few traceroutes to your favorite sites. The size of the ICMP echo request message can be explicitly set in pingplotter by selecting the menu item Edit −<em>&gt; </em>Options −<em>&gt; </em>Packet Options and then filling in the Packet Size field. The default packet size is 56 bytes. Once pingplotter has sent a series of packets with the increasing TTL values, it restarts the sending process again with a TTL of 1, after waiting Trace Interval amount of time. The value of Trace Interval and the number of intervals can be explicitly set in pingplotter.

<a href="#_ftnref5" name="_ftn5">[5]</a> If you use pingplotter, then: start up pingplotter and enter the name of a target destination in the “Address to Trace Window.” Enter 3 in the “# of times to Trace” field, so you don’t gather too much data. Select the menu item Edit −<em>&gt; </em>Advanced Options −<em>&gt; </em>Packet Options and enter a value of 56 in the Packet Size field and then press OK. Then press the Trace button.