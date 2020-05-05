---
layout: post
title: HiEdVBA #1: Simple Lists
date: 2019-07-01 16:20
author: jdiodato2
comments: true
categories: [Excel, Microsoft Office, VBA, Visal Basic, Visual Basic for Applications]
---
<!-- wp:paragraph -->
<p>Lately I've been finding myself toying around more with Microsoft Excel -- a piece of software that I'm sure many of us have wrangled with at some point or another. It turns out that Microsoft Excel is an exceptionally powerful piece of software.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>One of Excel's best kept secrets is <a href="https://docs.microsoft.com/en-us/office/vba/library-reference/concepts/getting-started-with-vba-in-office">Visual Basic for Applications</a><sup>1</sup>. At its core, VBA works like a programming language that can be embedded in Microsoft Office documents to certain tasks. I know, programming sounds really scary -- but bear with me! It can be quite fun and even rewarding to become familiar with this feature of Excel*</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>The purpose of #HiEdVBA is two-fold -- as always I want to document my learning as I explore new tools and technology. I also hope that as these VBA macros become more complex, folks are able to use them to enhance their workflow. </p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>This week, I want to begin by creating a simple list. Working in residence life, I often am looking at a list of the residential communities on my campus (13 at the time this post was posted). Instead of writing out the name of each residential community and formatting the sheet to make it somewhat more visually appealing, let's start by creating a VBA macro. </p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>The first thing we need is access to the Developer tab in the Excel ribbon. It's as simple as ticking a box -- you just have to know where to look! We'll go to <strong>File -&gt; Options -&gt; Customize Ribbon</strong>. You'll see a list of the default ribbon tabs that you normally see. Let's activate the Developer tab by making sure that box is ticked. Click "Ok" to exit this menu. </p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":392} -->
<figure class="wp-block-image"><img src="https://jdiodato.files.wordpress.com/2019/06/developer-tab.png" alt="" class="wp-image-392" /><figcaption>The Developer tab, once activated, will live in the ribbon along with the other features that you typically see.</figcaption></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>There are two ways to create an Excel macro: You can either use the <em>Record Macro</em> button, or you can tell Excel exactly what you want to do using the built in text-editor. I reccomend you become comfortable with writing your code directly, as (1) the record macro feature spits out some extraneous information that just clutters your script and (2) it really empowers users to tinker and try messing with new ideas or concepts<sup>2</sup>. I'll leave the reader to read further about storing macros in such a way that other Excel workbooks can access them<sup>3</sup>. </p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Under the Developer ribbon tab, select <strong>Macros -&gt; Name Accordingly (I reccomend HallNames for this example) --&gt; Create</strong>. You should end up with a minimalistic screen that looks like a text editor. Like any other text editor, be sure to save your work frequently and double check the details as you go.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Now, there are two things that we want to accomplish with this script. We want to nicely format a header for our spreadsheet and then follow that with a list of our residence halls. Let's look at each of these components seperately.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>Spreadsheet Header</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Let's start by creating a header for our spreadsheet.</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code {"language":"vb"} -->
<pre class="wp-block-syntaxhighlighter-code brush: vb; notranslate">Sub HallNames()

Sheet1.Range("A1:B1").Merge
ActiveCell.FormulaR1C1 = "Residence Centers"
ActiveCell.Font.Bold = True
ActiveCell.Font.Size = 14
ActiveCell.Interior.ColorIndex = 37</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>It looks like there's a lot going on here, but it's not so scary once we break it down.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Every VBA script begins with a Sub header -- a name that we can use to reference the script that we're about to write. After that you might be able to parse out that the 2nd line of code above is just merging two cells together. The remaining lines format the header cells in the following steps:</p>
<!-- /wp:paragraph -->

<!-- wp:list {"ordered":true} -->
<ol><li>Add the text "Residence Centers" to the newly merged cells.</li><li>Makes the newly inputted text bold</li><li>Changes the font size to 14</li><li>Changes the cell background color to a light blue color.</li></ol>
<!-- /wp:list -->

<!-- wp:paragraph -->
<p>Now we turn our attention to the last chunk of the script.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>List of Halls </h2>
<!-- /wp:heading -->

<!-- wp:syntaxhighlighter/code {"language":"vb"} -->
<pre class="wp-block-syntaxhighlighter-code brush: vb; notranslate">    Range("A2") = "Ashton"
    Range("A3") = "Collins"
    Range("A4") = "Eigenmann"
    Range("A5") = "Wright"
    Range("A6") = "USC"
    Range("A7") = "Forest"
    Range("A8") = "Read"
    Range("A9") = "Spruce"
    Range("A10") = "Wells"
    Range("A11") = "Willkie"
    Range("A12") = "Briscoe"

End Sub</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>You might find this bit of the script a bit easier to follow along with. Starting in Cell A2 we input the name of a residence hall ("Ashton") and procede down the A column until we've entered all of the items that we want to list out. <strong>End sub</strong> marks the end of the script by telling Excel that we're done adding commands to our script! </p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>Conclusion</h2>
<!-- /wp:heading -->

<!-- wp:image {"align":"right","id":387} -->
<div class="wp-block-image"><figure class="alignright"><img src="https://jdiodato.files.wordpress.com/2019/06/hallnames.png" alt="" class="wp-image-387" /><figcaption>The result of running the complete VBA script we've created on an empty Excel workbook.</figcaption></figure></div>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>So why does VBA matter? I admit that after reading through this first entry in the #HigherEdVBA blog post series, you might not be totally convinced. After all, you could have easily decided to create an Excel template for the script we've created and be done with it. I purposely began with a simple example and script to illustrate some of the principles that undergird VBA. As our needs become more complex, we might find ourselves exceeding the limits of how much time a template can realistically save us. VBA scripts are also <em>portable</em> -- they can be dropped into any Excel file and aren't limited to one document. </p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<p><sup>1</sup>Due to security concerns, some institutions may prevent users from using .xlsm files, the filetype used to run an Excel Macro-Enabled Workbook.<p>
<p><sup>2</sup>All materials for these tutorials are hosted on my GitHub profile, <a href="https://github.com/jdiodato/VBA-Scripts-"> linked here</a>. If you're not familar with GitHub, it's basically a Google Drive or DropBox for code with some pretty cool features. Also, I don't intend on getting into the nuts and bolts of how to properly create these scripts -- I'll leave that to the reader to explore further if so desired. My primary aim with each of these series is to provide helpful scripts that folks can plug into their Excel workbook and run with.</p>
<p><sup>3</sup>See the corresponding Microsoft Office documentation, <a href="https://support.office.com/en-us/article/copy-your-macros-to-a-personal-macro-workbook-aa439b90-f836-4381-97f0-6e4c3f5ee566">linked here.</a></p>
<!-- /wp:html -->
