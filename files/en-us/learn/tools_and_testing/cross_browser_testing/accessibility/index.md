---
title: Handling common accessibility problems
slug: Learn/Tools_and_testing/Cross_browser_testing/Accessibility
tags:
  - Accessibility
  - Article
  - Beginner
  - CSS
  - CodingScripting
  - HTML
  - JavaScript
  - Learn
  - Testing
  - Tools
  - cross browser
  - keyboard
---
<div>{{LearnSidebar}}</div>

<div>{{PreviousMenuNext("Learn/Tools_and_testing/Cross_browser_testing/JavaScript","Learn/Tools_and_testing/Cross_browser_testing/Feature_detection", "Learn/Tools_and_testing/Cross_browser_testing")}}</div>

<p>Next we turn our attention to accessibility, providing information on common problems, how to do simple testing, and how to make use of auditing/automation tools for finding accessibility issues.</p>

<table>
 <tbody>
  <tr>
   <th scope="row">Prerequisites:</th>
   <td>Familiarity with the core <a href="/en-US/docs/Learn/HTML">HTML</a>, <a href="/en-US/docs/Learn/CSS">CSS</a>, and <a href="/en-US/docs/Learn/JavaScript">JavaScript</a> languages; an idea of the high level <a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Introduction">principles of cross browser testing</a>.</td>
  </tr>
  <tr>
   <th scope="row">Objective:</th>
   <td>To be able to diagnose common Accessibility problems, and use appropriate tools and techniques to fix them.</td>
  </tr>
 </tbody>
</table>

<h2 id="What_is_accessibility">What is accessibility?</h2>

<p>When we say accessibility in the context of web technology, most people immediately think of making sure websites/apps are usable by people with disabilities, for example:</p>

<ul>
 <li>Visually impaired people using screen readers or magnification/zoom to access text</li>
 <li>People with motor function impairments using the keyboard (or other non-mouse features) to activate website functionality.</li>
 <li>People with hearing impairments relying on captions/subtitles or other text alternatives for audio/video content.</li>
</ul>

<p>However, it is wrong to say that accessibility is just about disabilities. Really, the aim of accessibility is to make your websites/apps usable by as many people in as many contexts as possible, not just those users using high-powered desktop computers. Some examples might include:</p>

<ul>
 <li>Users on mobile devices.</li>
 <li>Users on alternative browsing devices such as TVs, watches, etc.</li>
 <li>Users of older devices that might not have the latest browsers.</li>
 <li>Users of lower spec devices that might have slow processors.</li>
</ul>

<p>In a way, this whole module is about accessibility — cross browser testing makes sure that your sites can be used by as many people as possible. <a href="/en-US/docs/Learn/Accessibility/What_is_accessibility">What is accessibility?</a> defines accessibility more completely and thoroughly than this article does.</p>

<p>That said, this article will cover cross browser and testing issues surrounding people with disabilities, and how they use the Web. We've already talked about other spheres such as <a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/HTML_and_CSS#responsive_design_problems">responsive design</a> and <a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/JavaScript#performance_issues">performance</a> in other places in the module.</p>

<div class="note">
<p><strong>Note:</strong> Like many things in web development, accessibility isn't about 100% success or not; 100% accessibility is pretty much impossible to achieve for all content, especially as sites get more complex. Instead, it is more about making a reasonable effort to make as much of your content accessible to as many people as possible via defensive coding and sticking to best practices.</p>
</div>

<h2 id="Common_accessibility_issues">Common accessibility issues</h2>

<p>In this section we'll detail some of the main issues that arise around web accessibility, connected with specific technologies, along with best practices to follow, and some quick tests you can do to see if your sites are going in the right direction.</p>

<div class="note">
<p><strong>Note:</strong> Accessibility is morally the right thing to do, and good for business (numbers of disabled users, users on mobile devices, etc. present significant market segments), but it is also a legal requirement in many parts of the world to make web content accessible to people with disabilities. Read <a href="/en-US/docs/Learn/Accessibility/What_is_accessibility#accessibility_guidelines_and_the_law">Accessibility guidelines and the law</a> for more information.</p>
</div>

<h3 id="HTML">HTML</h3>

<p>Semantic HTML (where the elements are used for their correct purpose) is accessible right out of the box — such content is readable by sighted viewers (provided you don't do anything silly like make the text way too small or hide it using CSS), but will also be usable by assistive technologies like screen readers (apps that literally read out a web page to their user), and confer other advantages too.</p>

<h4 id="Semantic_structure">Semantic structure</h4>

<p>The most important quick win in semantic HTML is to use a structure of headings and paragraphs for your content; this is because screen reader users tend to use the headings of a document as signposts to find the content they need more quickly. If your content has no headings, all they will get is a huge wall of text with no signposts to find anything. Examples of bad and good HTML:</p>

<pre class="brush: html example-bad">&lt;font size="7"&gt;My heading&lt;/font&gt;
&lt;br&gt;&lt;br&gt;
This is the first section of my document.
&lt;br&gt;&lt;br&gt;
I'll add another paragraph here too.
&lt;br&gt;&lt;br&gt;
&lt;font size="5"&gt;My subheading&lt;/font&gt;
&lt;br&gt;&lt;br&gt;
This is the first subsection of my document. I'd love people to be able to find this content!
&lt;br&gt;&lt;br&gt;
&lt;font size="5"&gt;My 2nd subheading&lt;/font&gt;
&lt;br&gt;&lt;br&gt;
This is the second subsection of my content. I think it is more interesting than the last one.</pre>

<pre class="brush: html example-good">&lt;h1&gt;My heading&lt;/h1&gt;

&lt;p&gt;This is the first section of my document.&lt;/p&gt;

&lt;p&gt;I'll add another paragraph here too.&lt;/p&gt;

&lt;h2&gt;My subheading&lt;/h2&gt;

&lt;p&gt;This is the first subsection of my document. I'd love people to be able to find this content!&lt;/p&gt;

&lt;h2&gt;My 2nd subheading&lt;/h2&gt;

&lt;p&gt;This is the second subsection of my content. I think it is more interesting than the last one.&lt;/p&gt;</pre>

<p>In addition, your content should make logical sense in its source order — you can always place it where you want using CSS later on, but you should get the source order right to start with.</p>

<p>As a test, you can turn off a site's CSS and see how understandable it is without it. You could do this manually by just removing the CSS from your code, but the easiest way is to use browser features, for example:</p>

<ul>
 <li>Firefox: Select <em>View &gt; Page Style &gt; No Style</em> from the main menu.</li>
 <li>Safari: Select <em>Develop &gt; Disable Styles</em> from the main menu (to enable the <em>Develop</em> menu, choose <em>Safari &gt; Preferences &gt; Advanced &gt; Show Develop menu in menu bar</em>).</li>
 <li>Chrome: Install the Web Developer Toolbar extension, then restart the browser. Click the gear icon that will appear, then select <em>CSS &gt; Disable All Styles</em>.</li>
 <li>Edge: Select <em>View &gt; Style &gt; No Style</em> from the main menu.</li>
</ul>

<h4 id="Using_native_keyboard_accessibility">Using native keyboard accessibility</h4>

<p>Certain HTML features can be selected using only the keyboard — this is default behavior, available since the early days of the web. The elements that have this capability are the common ones that allow user to interact with web pages, namely links, {{htmlelement("button")}}s, and form elements like {{htmlelement("input")}}.</p>

<p>You can try this out using our <a href="https://mdn.github.io/learning-area/tools-testing/cross-browser-testing/accessibility/native-keyboard-accessibility.html">native-keyboard-accessibility.html</a> example (see the <a href="https://github.com/mdn/learning-area/blob/master/tools-testing/cross-browser-testing/accessibility/native-keyboard-accessibility.html">source code</a>) — open this in a new tab, and try pressing the tab key; after a few presses, you should see the tab focus start to move through the different focusable elements; the focused elements are given a highlighted default style in every browser (it differs slightly between different browsers) so that you can tell what element is focused.</p>

<p><img alt="" src="button-focused-unfocused.png"></p>

<div class="notecard note">
<p><strong>Note:</strong> In Firefox, you can also enable an overlay that shows the page tabbing order. For more information see: <a href="/en-US/docs/Tools/Accessibility_inspector#show_web_page_tabbing_order">Accessibility Inspector &gt; Show web page tabbing order</a>.</p>
</div>

<p>You can then press Enter/Return to follow a focused link or press a button (we've included some JavaScript to make the buttons alert a message), or start typing to enter text in a text input (other form elements have different controls, for example the {{htmlelement("select")}} element can have its options displayed and cycled between using the up and down arrow keys).</p>

<p>Note that different browsers may have different keyboard control options available. Most modern browsers follow the tab pattern described above (you can also do Shift + Tab to move backwards through the focusable elements), but some browsers have their own idiosyncrasies:</p>

<ul>
 <li>Firefox for the Mac doesn't do tabbing by default. To turn it on, you have to go to <em>Preferences &gt; Advanced &gt; General</em>, then uncheck "Always use the cursor keys to navigate within pages". Next, you have to open your Mac's System Preferences app, then go to <em>Keyboard &gt; Shortcuts</em>, then select the <em>All Controls</em> radio button.</li>
 <li>Safari doesn't allow you to tab through links by default; to enable this, you need to open Safari's <em>Preferences</em>, go to Advanced, and check the <em>Press Tab to highlight each item on a webpage</em> checkbox.</li>
</ul>

<div class="warning">
<p><strong>Warning:</strong> You should perform this kind of test/review on any new page you write — make sure that functionality can be accessed by the keyboard, and that the tab order provides a sensible navigation path through the document.</p>
</div>

<p>This example highlights the importance of using the correct semantic element for the correct job. It is possible to style <em>any</em> element to look like a link or button with CSS, and to behave like a link or button with JavaScript, but they won't actually be links or buttons, and you'll lose a lot of the accessibility these elements give you for free. So don't do it if you can avoid it.</p>

<p>Another tip — as shown in our example, you can control how your focusable elements look when focused, using the <a href="/en-US/docs/Web/CSS/:focus">:focus</a> pseudo-class. It is a good idea to double up focus and hover styles, so your users get that visual clue that a control will do something when activated, whether they are using mouse or keyboard:</p>

<pre class="brush: css">a:hover, input:hover, button:hover, select:hover,
a:focus, input:focus, button:focus, select:focus {
  font-weight: bold;
}</pre>

<div class="note">
<p><strong>Note:</strong> If you do decide to remove the default focus styling using CSS, make sure you replace it with something else that fits in with your design better — it is a very valuable accessibility tool, and should not be removed.</p>
</div>

<h4 id="Building_in_keyboard_accessibility">Building in keyboard accessibility</h4>

<p>Sometimes it is not possible to avoid losing keyboard accessibility. You might have inherited a site where the semantics are not very good (perhaps you've ended up with a horrible CMS that generates buttons made with <code>&lt;div&gt;</code>s), or you are using a complex control that does not have keyboard accessibility built in, like the HTML5 {{htmlelement("video")}} element (amazingly, Opera is the only browser that allows you to tab through the <code>&lt;video&gt;</code> element's default browser controls). You have a few options here:</p>

<ol>
 <li>Create custom controls using <code>&lt;button&gt;</code> elements (which we can tab to by default!) and JavaScript to wire up their functionality. See <a href="/en-US/docs/Web/Guide/Audio_and_video_delivery/cross_browser_video_player">Creating a cross-browser video player</a> for some good examples of this.</li>
 <li>Create keyboard shortcuts via JavaScript, so functionality is activated when you press certain keys on the keyboard. See <a href="/en-US/docs/Games/Techniques/Control_mechanisms/Desktop_with_mouse_and_keyboard">Desktop mouse and keyboard controls</a> for some game-related examples that can be adapted for any purpose.</li>
 <li>Use some interesting tactics to fake button behavior. Take for example our <a href="https://mdn.github.io/learning-area/tools-testing/cross-browser-testing/accessibility/fake-div-buttons.html">fake-div-buttons.html</a> example (see <a href="https://github.com/mdn/learning-area/blob/master/tools-testing/cross-browser-testing/accessibility/fake-div-buttons.html">source code</a>). Here we've given our fake <code>&lt;div&gt;</code> buttons the ability to be focused (including via tab) by giving each one the attribute <code>tabindex="0"</code> (see WebAIM's <a href="https://webaim.org/techniques/keyboard/tabindex">tabindex article</a> for more really useful details). This allows us to tab to the buttons, but not to activate them via the Enter/Return key. To do that, we had to add the following bit of JavaScript trickery:
  <pre class="brush: js">document.onkeydown = function(e) {
  if(e.keyCode === 13) { // The Enter/Return key
    document.activeElement.onclick(e);
  }
};</pre>
  Here we add a listener to the <code>document</code> object to detect when a button has been pressed on the keyboard. We check what button was pressed via the event object's <a href="/en-US/docs/Web/API/KeyboardEvent/keyCode">keyCode</a> property; if it is the keycode that matches Return/Enter, we run the function stored in the button's <code>onclick</code> handler using <code>document.activeElement.onclick()</code>. <code><a href="/en-US/docs/Web/API/Document/activeElement">activeElement</a></code> gives us the element that is currently focused on the page.</li>
</ol>

<div class="note">
<p><strong>Note:</strong> This technique will only work if you set your original event handlers via event handler properties (e.g. <code>onclick</code>). <code>addEventListener</code> won't work. This is a lot of extra hassle to build the functionality back in. And there's bound to be other problems with it. Better to just use the right element for the right job in the first place.</p>
</div>

<h4 id="Text_alternatives">Text alternatives</h4>

<p>Text alternatives are very important for accessibility — if a person has a visual or hearing impairment that stops them being able to see or hear some content, then this is a problem. The simplest text alternative available is the humble <code>alt</code> attribute, which we should include on all images that contain relevant content. This should contain a description of the image that successfully conveys its meaning and content on the page, to be picked up by a screenreader and read out to the user.</p>

<div class="note">
<p><strong>Note:</strong> For more information, read <a href="/en-US/docs/Learn/Accessibility/HTML#text_alternatives">Text alternatives</a>.</p>
</div>

<p>Missing alt text can be tested for in a number of ways, for example using accessibility {{anch("Auditing tools")}}.</p>

<p>Alt text is slightly more complex for video and audio content. There is a way to define text tracks (e.g. subtitles) and display them when video is being played, in the form of the {{htmlelement("track")}} element, and the <a href="/en-US/docs/Web/API/WebVTT_API">WebVTT</a> format (see <a href="/en-US/docs/Web/Guide/Audio_and_video_delivery/Adding_captions_and_subtitles_to_HTML5_video">Adding captions and subtitles to HTML5 video</a> for a detailed tutorial). <a href="/en-US/docs/Web/Guide/Audio_and_video_delivery/Adding_captions_and_subtitles_to_HTML5_video#browser_compatibility">Browser compatibility</a> for these features is fairly good, but if you want to provide text alternatives for audio or support older browsers, a simple text transcript presented somewhere on the page or on a separate page might be a good idea.</p>

<h4 id="Element_relationships_and_context">Element relationships and context</h4>

<p>There are certain features and best practices in HTML designed to provide context and relationships between elements where none otherwise exists. The three most common examples are links, form labels, and data tables.</p>

<p>The key to accessible link text is that people using screen readers will often use a common feature whereby they pull up a list of all the links on the page. In this case, the link text needs to make sense out of context. For example, a list of links labeled "click here", "click me", etc. is really bad for accessibility. It is better for link text to make sense in context and out of context.</p>

<p>Next on our list, the form {{htmlelement("label")}} element is one of the central features that allows us to make forms accessible. The trouble with forms is that you need labels to say what data should be entered into each form input. Each label needs to be included inside a {{htmlelement("label")}} to link it unambiguously to its partner form input (each <code>&lt;label&gt;</code> <code>for</code> attribute value needs to match the form element <code>id</code> value), and it will make sense even if the source order is not completely logical (which to be fair it should be).</p>

<div class="note">
<p><strong>Note:</strong> For more information about link text and form labels, read <a href="/en-US/docs/Learn/Accessibility/HTML#meaningful_text_labels">Meaningful text labels</a>.</p>
</div>

<p>Finally, a quick word about data tables. A basic data table can be written with very simple markup (see <code>bad-table.html</code> <a href="https://mdn.github.io/learning-area/accessibility/html/bad-table.html">live</a>, and <a href="https://github.com/mdn/learning-area/blob/master/accessibility/html/bad-table.html">source</a>), but this has problems — there is no way for a screen reader user to associate rows or columns together as groupings of data — to do this you need to know what the header rows are, and if they are heading up rows, columns, etc. This can only be done visually for such a table.</p>

<p>If you instead look at our <code>punk-bands-complete.html</code> example (<a href="https://mdn.github.io/learning-area/css/styling-boxes/styling-tables/punk-bands-complete.html">live</a>, <a href="https://github.com/mdn/learning-area/blob/master/css/styling-boxes/styling-tables/punk-bands-complete.html">source</a>), you can see a few accessibility aids at work here, such as table headers ({{htmlelement("th")}} and <code>scope</code> attributes), {{htmlelement("caption")}} element, etc.</p>

<div class="note">
<p><strong>Note:</strong> For more information about accessible tables, read <a href="/en-US/docs/Learn/Accessibility/HTML#accessible_data_tables">Accessible data tables</a>.</p>
</div>

<h3 id="CSS">CSS</h3>

<p>CSS tends to provide a lot fewer fundamental accessibility features than HTML, but it can still do just as much damage to accessibility if used incorrectly. We have already mentioned a couple of accessibility tips involving CSS:</p>

<ul>
 <li>Use the correct semantic elements to mark up different content in HTML; if you want to create a different visual effect, use CSS — don't abuse an HTML element to get the look you want. For example, if you want bigger text, use {{cssxref("font-size")}}, not an {{htmlelement("h1")}} element.</li>
 <li>Make sure your source order makes sense without CSS; you can always use CSS to style the page any way you want afterward.</li>
 <li>You should make sure interactive elements like buttons and links have appropriate focus/hover/active states set, to give the user visual clues as to their function. If you remove the defaults for stylistic reasons, make sure you include some replacement styles.</li>
</ul>

<p>There are a few other considerations you should take into account.</p>

<h4 id="Color_and_color_contrast">Color and color contrast</h4>

<p>When choosing a color scheme for your website, you should make sure that the text (foreground) color contrasts well with the background color. Your design might look cool, but it is no good if people with visual impairments like color blindness can't read your content. Use a tool like WebAIM's <a href="https://webaim.org/resources/contrastchecker/">Color Contrast Checker</a> to check whether your scheme is contrasting enough.</p>

<p>Another tip is to not rely on color alone for signposts/information, as this will be no good for those who can't see the color. Instead of marking required form fields in red, for example, mark them with an asterisk and in red.</p>

<div class="note">
<p><strong>Note:</strong> A high contrast ratio will also allow anyone using a smartphone or tablet with a glossy screen to better read pages when in a bright environment, such as sunlight.</p>
</div>

<h4 id="Hiding_content">Hiding content</h4>

<p>There are many instances where a visual design will require that not all content is shown at once. For example, in our <a href="https://mdn.github.io/learning-area/css/css-layout/practical-positioning-examples/info-box.html">Tabbed info box example</a> (see <a href="https://github.com/mdn/learning-area/blob/master/css/css-layout/practical-positioning-examples/info-box.html">source code</a>) we have three panels of information, but we are <a href="/en-US/docs/Learn/CSS/CSS_layout/Positioning">positioning</a> them on top of one another and providing tabs that can be clicked to show each one (it is also keyboard accessible — you can alternatively use Tab and Enter/Return to select them).</p>

<p><img alt="" src="20191022144107.png"></p>

<p>Screen reader users don't care about any of this — they are happy with the content as long as the source order makes sense, and they can get to it all. Absolute positioning (as used in this example) is generally seen as one of the best mechanisms of hiding content for visual effect, because it doesn't stop screen readers from getting to it.</p>

<p>On the other hand, you shouldn't use {{cssxref("visibility")}}<code>:hidden</code> or {{cssxref("display")}}<code>:none</code>, because they do hide content from screenreaders. Unless of course, there is a good reason why you want this content to be hidden from screenreaders.</p>

<div class="note">
<p><strong>Note:</strong> <a href="https://webaim.org/techniques/css/invisiblecontent/">Invisible Content Just for Screen Reader Users</a> has a lot more useful detail surrounding this topic.</p>
</div>

<h3 id="JavaScript">JavaScript</h3>

<p>JavaScript has the same kind of problems as CSS with respect to accessibility — it can be disastrous for accessibility if used badly, or overused. We've already hinted at some accessibility problems related to JavaScript, mainly in the area of semantic HTML — you should always use appropriate semantic HTML to implement functionality wherever it is available, for example use links and buttons as appropriate. Don't use <code>&lt;div&gt;</code> elements with JavaScript code to fake functionality if at all possible — it is error prone, and more work than using the free functionality HTML gives you.</p>

<h4 id="Simple_functionality">Simple functionality</h4>

<p>Generally simple functionality should work with just the HTML in place — JavaScript should only be used to enhance functionality, not build it in entirely. Good uses of JavaScript include:</p>

<ul>
 <li>Providing client-side form validation, which alerts users to problems with their form entries quickly, without having to wait for the server to check the data. If it isn't available, the form will still work, but validation might be slower.</li>
 <li>Providing custom controls for HTML5 <code>&lt;video&gt;</code>s that are accessible to keyboard-only users (as we said earlier, the default browser controls aren't keyboard-accessible in most browsers).</li>
</ul>

<div class="note">
<p><strong>Note:</strong> WebAIM's <a href="https://webaim.org/techniques/javascript/">Accessible JavaScript</a> provides some useful further details about considerations for accessible JavaScript.</p>
</div>

<p>More complex JavaScript implementations can create issues with accessibility — you need to do what you can. For example, it would be unreasonable to expect you to make a complex 3D game written using <a href="/en-US/docs/Learn/WebGL">WebGL</a> 100% accessible to a blind person, but you could implement <a href="/en-US/docs/Games/Techniques/Control_mechanisms/Desktop_with_mouse_and_keyboard">keyboard controls</a> so it is usable by non-mouse users, and make the color scheme contrasting enough to be usable by those with color deficiencies.</p>

<h4 id="Complex_functionality">Complex functionality</h4>

<p>One of the main areas problematic for accessibility is complex apps that involve complicated form controls (such as date pickers) and dynamic content that is updated often and incrementally.</p>

<p>Non-native complicated form controls are problematic because they tend to involve a lot of nested <code>&lt;div&gt;</code>s, and the browser does not know what to do with them by default. If you are inventing them yourself, you need to make sure that they are keyboard accessible; if you are using some kind of third-party framework, carefully review the options available to see how accessible they are before diving in. <a href="https://getbootstrap.com/">Bootstrap</a> looks to be fairly good for accessibility, for example, although <a href="https://www.sitepoint.com/making-bootstrap-accessible/">Making Bootstrap a Little More Accessible</a> by Rhiana Heath explores some of its issues (mainly related to color contrast), and looks at some solutions.</p>

<p>Regularly updated dynamic content can be a problem because screenreader users might miss it, especially if it updates unexpectedly. If you have a single-page app with a main content panel that is regularly updated using <a href="/en-US/docs/Web/API/XMLHttpRequest">XMLHttpRequest</a> or <a href="/en-US/docs/Web/API/Fetch_API">Fetch</a>, a screenreader user might miss those updates.</p>

<h4 id="WAI-ARIA">WAI-ARIA</h4>

<p>Do you need to use such complex functionality, or will plain old semantic HTML do instead? If you do need complexity, you should consider using <a href="https://www.w3.org/TR/wai-aria-1.1/">WAI-ARIA</a> (Accessible Rich Internet Applications), a specification that provides semantics (in the form of new HTML attributes) for items such as complex form controls and updating panels that can be understood by most browsers and screen readers.</p>

<p>To deal with complex form widgets, you need to use ARIA attributes like <code>roles</code> to state what role different elements have in a widget (for example, are they a tab, or a tab panel?), <code>aria-disabled</code> to say whether a control is disabled or not, etc.</p>

<p>To deal with regularly updating regions of content, you can use the <code>aria-live</code> attribute, which identifies an updating region. Its value indicates how urgently the screen reader should read it out:</p>

<ul>
 <li><code>off:</code> The default. Updates should not be announced.</li>
 <li><code>polite</code>: Updates should be announced only if the user is idle.</li>
 <li><code>assertive</code>: Updates should be announced to the user as soon as possible.</li>
 <li><code>rude</code>: Updates should be announced straight away, even if this interrupts the user.</li>
</ul>

<p>Here's an example:</p>

<pre class="brush: html">&lt;p&gt;&lt;span id="LiveRegion1" aria-live="polite" aria-atomic="false"&gt;&lt;/span&gt;&lt;/p&gt;</pre>

<p>You can see an example in action at Freedom Scientific's <a href="https://www.freedomscientific.com/Training/Surfs-up/AriaLiveRegions.htm">ARIA (Accessible Rich Internet Applications) Live Regions</a> example — the highlighted paragraph should update its content every 10 seconds, and a screenreader should read this out to the user. <a href="https://www.freedomscientific.com/Training/Surfs-up/AriaLiveRegionsAtomic.htm">ARIA Live Regions - Atomic</a> provides another useful example.</p>

<p>We don't have space to cover WAI-ARIA in detail here, you can learn a lot more about it at <a href="/en-US/docs/Learn/Accessibility/WAI-ARIA_basics">WAI-ARIA basics</a>.</p>

<h2 id="Accessibility_tools">Accessibility tools</h2>

<p>Now we've covered accessibility considerations for different web technologies, including a few testing techniques (like keyboard navigation and color contrast checkers), let's have a look at other tools you can make use of when doing accessibility testing.</p>

<h3 id="Auditing_tools">Auditing tools</h3>

<p>There are a number of auditing tools available that you can feed your web pages into. They will look over them and return a list of accessibility issues present on the page. Examples include:</p>

<ul>
 <li><a href="https://wave.webaim.org/">Wave</a>: A rather nice online accessibility testing tool that accepts a web address and returns a useful annotated view of that page with accessibility problems highlighted.</li>
 <li><a href="https://tenon.io">Tenon</a>: Another nice online tool that goes through the code at a provided URL and returns results on accessibility errors including metrics, specific errors along with the WCAG criteria they affect, and suggested fixes. It requires a free trial signup to view the results.</li>
 <li><a href="https://khan.github.io/tota11y/">tota11y</a>: An accessibility tool from the Khan Academy that takes the form of a JavaScript library that you attach to your page to provide a number of accessibility tools.</li>
</ul>

<p>Let's look at an example, using Wave.</p>

<ol>
 <li>Go to the <a href="https://wave.webaim.org/">Wave homepage</a>.</li>
 <li>Enter the URL of our <a href="https://mdn.github.io/learning-area/accessibility/html/bad-semantics.html">bad-semantics.html</a> example into the text input box near the top of the page. Then press enter or click/tap the arrow at the far right edge of the input box.</li>
 <li>The site should respond with a description of the accessibility problems. Click the icons displayed to see more information about each of the issues identified by Wave's evaluation.</li>
</ol>

<div class="note">
<p><strong>Note:</strong> Such tools aren't good enough to solve all your accessibility problems on their own. You'll need a combination of these, knowledge and experience, user testing, etc. to get a full picture.</p>
</div>

<h3 id="Automation_tools">Automation tools</h3>

<p><a href="https://www.deque.com/products/axe/">Deque's aXe tool</a> goes a bit further than the auditing tools we mentioned above. Like the others, it checks pages and returns accessibility errors. Its most immediately useful form is probably the browser extensions:</p>

<ul>
 <li><a href="https://bitly.com/aXe-Chrome">aXe for Chrome</a></li>
 <li><a href="https://bit.ly/aXe-Firefox">aXe for Firefox</a></li>
</ul>

<p>These add an accessibility tab to the browser developer tools. For example, we installed the Firefox version, then used it to audit our <a href="https://mdn.github.io/learning-area/accessibility/html/bad-table.html">bad-table.html</a> example. We got the following results:</p>

<p><img alt="" src="axe-screenshot.png"></p>

<p>aXe is also installable using <code>npm</code>, and can be integrated with task runners like <a href="https://gruntjs.com/">Grunt</a> and <a href="https://gulpjs.com/">Gulp</a>, automation frameworks like <a href="https://www.seleniumhq.org/">Selenium</a> and <a href="https://cucumber.io/">Cucumber</a>, unit testing frameworks like <a href="https://jasmine.github.io/">Jasmine</a>, and more besides (again, see the <a href="https://www.deque.com/products/axe/">main aXe page</a> for details).</p>

<h3 id="Screenreaders">Screenreaders</h3>

<p>It is definitely worth testing with a screenreader to get used to how severely visually impaired people use the Web. There are a number of screenreaders available:</p>

<ul>
 <li>Some are paid-for commercial products, like <a href="https://www.freedomscientific.com/Products/Blindness/JAWS">JAWS</a> (Windows) and <a href="http://www.gwmicro.com/window-eyes/">Window Eyes</a> (Windows).</li>
 <li>Some are free products, like <a href="https://www.nvaccess.org/">NVDA</a> (Windows), <a href="http://www.chromevox.com/">ChromeVox</a> (Chrome, Windows, and Mac OS X), and <a href="https://wiki.gnome.org/Projects/Orca">Orca</a> (Linux).</li>
 <li>Some are built into the operating system, like <a href="https://www.apple.com/accessibility/osx/voiceover/">VoiceOver</a> (Mac OS X and iOS), <a href="http://www.chromevox.com/">ChromeVox</a> (on Chromebooks), and <a href="https://play.google.com/store/apps/details?id=com.google.android.marvin.talkback">TalkBack</a> (Android).</li>
</ul>

<p>Generally, screen readers are separate apps that run on the host operating system and can read not only web pages, but text in other apps as well. This is not always the case (ChromeVox is a browser extension), but usually. Screenreaders tend to act in slightly different ways and have different controls, so you'll have to consult the documentation for your chosen screen reader to get all of the details — saying that, they all work in basically the same sort of way.</p>

<p>Let's go through some tests with a couple of different screenreaders to give you a general idea of how they work and how to test with them.</p>

<div class="note">
<p><strong>Note:</strong> WebAIM's <a href="https://webaim.org/techniques/screenreader/">Designing for Screen Reader Compatibility</a> provides some useful information about screenreader usage and what works best for screenreaders. Also see <a href="https://webaim.org/projects/screenreadersurvey6/#used">Screen Reader User Survey #6 Results</a> for some interesting screenreader usage statistics.</p>
</div>

<h4 id="VoiceOver">VoiceOver</h4>

<p>VoiceOver (VO) comes free with your Mac/iPhone/iPad, so it's useful for testing on desktop/mobile if you use Apple products. We'll be testing it on Mac OS X on a MacBook Pro.</p>

<p>To turn it on, press Cmd + F5. If you've not used VO before, you will be given a welcome screen where you can choose to start VO or not, and run through a rather useful tutorial to learn how to use it. To turn it off again, press Cmd + F5 again.</p>

<div class="note">
<p><strong>Note:</strong> You should go through the tutorial at least once — it is a really useful way to learn VO.</p>
</div>

<p>When VO is on, the display will look mostly the same, but you'll see a black box at the bottom left of the screen that contains information on what VO currently has selected. The current selection will also be highlighted, with a black border — this highlight is known as the <strong>VO cursor</strong>.</p>

<p><img alt="" src="voiceover.png"></p>

<p>To use VO, you will make a lot of use of the "VO modifier" — this is a key or key combination that you need to press in addition to the actual VO keyboard shortcuts to get them to work. Using a modifier like this is common with screenreaders, to enable them to keep their commands from clashing with other commands. In the case of VO, the modifier can either be CapsLock, or Ctrl + Option.</p>

<p>VO has many keyboard commands, and we won't list them all here. The basic ones you'll need for web page testing are in the following table. In the keyboard shortcuts, "VO" means "the VoiceOver modifier".</p>

<table class="standard-table no-markdown">
 <caption>Most common VoiceOver keyboard shortcuts</caption>
 <thead>
  <tr>
   <th scope="col">Keyboard shortcut</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>VO + Cursor keys</td>
   <td>Move the VO cursor up, right, down, left.</td>
  </tr>
  <tr>
   <td>VO + Spacebar</td>
   <td>Select/activate items highlighted by the VO cursor. This includes items selected in the Rotor (see below).</td>
  </tr>
  <tr>
   <td>VO + Shift + down cursor</td>
   <td>Move into a group of items (such as an HTML table, or a form, etc.) Once inside a group you can move around and select items inside that group using the above commands as normal.</td>
  </tr>
  <tr>
   <td>VO + Shift + up cursor</td>
   <td>Move out of a group.</td>
  </tr>
  <tr>
   <td>VO + C</td>
   <td>(when inside a table) Read the header of the current column.</td>
  </tr>
  <tr>
   <td>VO + R</td>
   <td>(when inside a table) Read the header of the current row.</td>
  </tr>
  <tr>
   <td>VO + C + C (two Cs in succession)</td>
   <td>(when inside a table) Read the entire current column, including header.</td>
  </tr>
  <tr>
   <td>VO + R + R (two Rs in succession)</td>
   <td>(when inside a table) Read the entire current row, including the headers that correspond to each cell.</td>
  </tr>
  <tr>
   <td>VO + left cursor, VO + right cursor</td>
   <td>(when inside some horizontal options, such as a date or time picker) Move between options.</td>
  </tr>
  <tr>
   <td>VO + up cursor, VO + down cursor</td>
   <td>(when inside some horizontal options, such as a date or time picker) Change the current option.</td>
  </tr>
  <tr>
   <td>VO + U</td>
   <td>Use the Rotor, which displays lists of headings, links, form controls, etc. for easy navigation.</td>
  </tr>
  <tr>
   <td>VO + left cursor, VO + right cursor</td>
   <td>(when inside Rotor) Move between different lists available in the Rotor.</td>
  </tr>
  <tr>
   <td>VO + up cursor, VO + down cursor</td>
   <td>(when inside Rotor) Move between different items in the current Rotor list.</td>
  </tr>
  <tr>
   <td>Esc</td>
   <td>(when inside Rotor) Exit Rotor.</td>
  </tr>
  <tr>
   <td>Ctrl</td>
   <td>(when VO is speaking) Pause/Resume speech.</td>
  </tr>
  <tr>
   <td>VO + Z</td>
   <td>Restart the last bit of speech.</td>
  </tr>
  <tr>
   <td>VO + D</td>
   <td>Go into the Mac's Dock, so you can select apps to run inside it.</td>
  </tr>
 </tbody>
</table>

<p>This seems like a lot of commands, but it isn't so bad when you get used to it, and VO regularly gives you reminders of what commands to use in certain places. Have a play with VO now; you can then go on to play with some of our examples in the {{anch("Screenreader testing")}} section.</p>

<h4 id="NVDA">NVDA</h4>

<p>NVDA is Windows-only, and you'll need to install it.</p>

<ol>
 <li>Download it from <a href="https://www.nvaccess.org/">nvaccess.org</a>. You can choose whether to make a donation or download it for free; you'll also need to give them your e-mail address before you can download it.</li>
 <li>Once downloaded, install it — you double click the installer, accept the license and follow the prompts.</li>
 <li>To start NVDA, double click on the program file/shortcut, or use the keyboard shortcut Ctrl + Alt + N. You'll see the NVDA welcome dialog when you start it. Here you can choose from a couple of options, then press the <em>OK</em> button to get going.</li>
</ol>

<p>NVDA will now be active on your computer.</p>

<p>To use NVDA, you will make a lot of use of the "NVDA modifier" — this is a key that you need to press in addition to the actual NVDA keyboard shortcuts to get them to work. Using a modifier like this is common with screenreaders, to enable them to keep their commands from clashing with other commands. In the case of NVDA, the modifier can either be Insert (the default), or CapsLock (can be chosen by checking the first checkbox in the NVDA welcome dialog before pressing <em>OK</em>).</p>

<div class="note">
<p><strong>Note:</strong> NVDA is more subtle than VoiceOver in terms of how it highlights where it is and what it is doing. When you are scrolling through headings, lists, etc., items you are selected on will generally be highlighted with a subtle outline, but this is not always the case for all things. If you get completely lost, you can press Ctrl + F5 to refresh the current page and begin from the top again.</p>
</div>

<p>NVDA has many keyboard commands, and we won't list them all here. The basic ones you'll need for web page testing are in the following table. In the keyboard shortcuts, "NVDA" means "the NVDA modifier".</p>

<table class="standard-table no-markdown">
 <caption>Most common NVDA keyboard shortcuts</caption>
 <thead>
  <tr>
   <th scope="col">Keyboard shortcut</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>NVDA + Q</td>
   <td>Turn NVDA off again after you've started it.</td>
  </tr>
  <tr>
   <td>NVDA + up cursor</td>
   <td>Read the current line.</td>
  </tr>
  <tr>
   <td>NVDA + down cursor</td>
   <td>Start reading at the current position.</td>
  </tr>
  <tr>
   <td>Up cursor and down cursor, or Shift + Tab and Tab</td>
   <td>Move to previous/next item on page and read it.</td>
  </tr>
  <tr>
   <td>Left cursor and right cursor</td>
   <td>Move to previous/next character in current item and read it.</td>
  </tr>
  <tr>
   <td>Shift + H and H</td>
   <td>Move to previous/next heading and read it.</td>
  </tr>
  <tr>
   <td>Shift + K and K</td>
   <td>Move to previous/next link and read it.</td>
  </tr>
  <tr>
   <td>Shift + D and D</td>
   <td>Move to previous/next document landmark (e.g. <code>&lt;nav&gt;</code>) and read it.</td>
  </tr>
  <tr>
   <td>Shift + 1–6 and 1–6</td>
   <td>Move to previous/next heading (level 1–6) and read it.</td>
  </tr>
  <tr>
   <td>Shift + F and F</td>
   <td>Move to previous/next form input and focus on it.</td>
  </tr>
  <tr>
   <td>Shift + T and T</td>
   <td>Move to previous/next data table and focus on it.</td>
  </tr>
  <tr>
   <td>Shift + B and B</td>
   <td>Move to previous/next button and read its label.</td>
  </tr>
  <tr>
   <td>Shift + L and L</td>
   <td>Move to previous/next list and read its first list item.</td>
  </tr>
  <tr>
   <td>Shift + I and I</td>
   <td>Move to previous/next list item and read it.</td>
  </tr>
  <tr>
   <td>Enter/Return</td>
   <td>(when link/button or other activatable item is selected) Activate item.</td>
  </tr>
  <tr>
   <td>NVDA + Space</td>
   <td>(when form is selected) Enter form so individual items can be selected, or leave form if you are already in it.</td>
  </tr>
  <tr>
   <td>Shift Tab and Tab</td>
   <td>(when inside form) Move between form inputs.</td>
  </tr>
  <tr>
   <td>Up cursor and down cursor</td>
   <td>(when inside form) Change form input values (in the case of things like select boxes).</td>
  </tr>
  <tr>
   <td>Spacebar</td>
   <td>(when inside form) Select chosen value.</td>
  </tr>
  <tr>
   <td>Ctrl + Alt + cursor keys</td>
   <td>(when a table is selected) Move between table cells.</td>
  </tr>
 </tbody>
</table>

<h4 id="Screenreader_testing">Screenreader testing</h4>

<p>Now you've gotten used to using a screenreader, we'd like you to use it to do some quick accessibility tests, to get an idea of how screenreaders deal with good and bad webpage features:</p>

<ul>
 <li>Look at <a href="https://mdn.github.io/learning-area/accessibility/html/good-semantics.html">good-semantics.html</a>, and note how the headers are found by the screenreader and available to use for navigation. Now look at <a href="https://mdn.github.io/learning-area/accessibility/html/bad-semantics.html">bad-semantics.html</a>, and note how the screenreader gets none of this information. Imagine how annoying this would be when trying to navigate a really long page of text.</li>
 <li>Look at <a href="https://mdn.github.io/learning-area/accessibility/html/good-links.html">good-links.html</a>, and note how they make sense when viewed out of context. This is not the case with <a href="https://mdn.github.io/learning-area/accessibility/html/bad-links.html">bad-links.html</a> — they are all just "click here".</li>
 <li>Look at <a href="https://mdn.github.io/learning-area/accessibility/html/good-form.html">good-form.html</a>, and note how the form inputs are described using their labels because we've used <code>&lt;label&gt;</code> elements properly. In <a href="https://mdn.github.io/learning-area/accessibility/html/bad-form.html">bad-form.html</a>, they get an unhelpful label along the lines of "blank".</li>
 <li>Look at our <a href="https://mdn.github.io/learning-area/css/styling-boxes/styling-tables/punk-bands-complete.html">punk-bands-complete.html</a> example, and see how the screenreader is able to associate columns and rows of content and read them out all together because we've defined headers properly. In <a href="https://mdn.github.io/learning-area/accessibility/html/bad-table.html">bad-table.html</a>, none of the cells can be associated at all. Note that NVDA seems to behave slightly strangely when you've only got a single table on a page; you could try <a href="https://webaim.org/articles/nvda/tables.htm">WebAIM's table test page</a> instead.</li>
 <li>Have a look at the <a href="https://www.freedomscientific.com/Training/Surfs-up/AriaLiveRegions.htm">WAI-ARIA live regions example</a> we saw earlier, and note how the screen reader will keep reading out the constantly updating section as it updates.</li>
</ul>

<h3 id="User_testing">User testing</h3>

<p>As mentioned above, you can't rely on automated tools alone for determining accessibility problems on your site. It is recommended that when you draw up your testing plan, you should include some accessibility user groups if at all possible (see our <a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Testing_strategies#user_testing">User Testing</a> section earlier on in the course for some more context). Try to get some screenreader users involved, some keyboard-only users, some non-hearing users, and perhaps other groups too, as suits your requirements.</p>

<h2 id="Accessibility_testing_checklist">Accessibility testing checklist</h2>

<p>The following list provides a checklist for you to follow to make sure you've carried out the recommended accessibility testing for your project:</p>

<ol>
 <li>Make sure your HTML is as semantically correct as possible. <a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/HTML_and_CSS#validation">Validating it</a> is a good start, as is using an <a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Accessibility#auditing_tools">Auditing tool</a>.</li>
 <li>Check that your content makes sense when the CSS is turned off.</li>
 <li>Make sure your functionality is <a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Accessibility#using_native_keyboard_accessibility">keyboard accessible</a>. Test using Tab, Return/Enter, etc.</li>
 <li>Make sure your non-text content has <a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Accessibility#text_alternatives">text alternatives</a>. An <a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Accessibility#auditing_tools">Auditing tool</a> is good for catching such problems.</li>
 <li>Make sure your site's <a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Accessibility#color_and_color_contrast">color contrast</a> is acceptable, using a suitable checking tool.</li>
 <li>Make sure <a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Accessibility#hiding_content">hidden content</a> is visible by screenreaders.</li>
 <li>Make sure that functionality is usable without JavaScript wherever possible.</li>
 <li>Use ARIA to improve accessibility where appropriate.</li>
 <li>Run your site through an <a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Accessibility#auditing_tools">Auditing tool</a>.</li>
 <li>Test it with a screenreader.</li>
 <li>Include an accessibility policy/statement somewhere findable on your site to say what you did.</li>
</ol>

<h2 id="Finding_help">Finding help</h2>

<p>There are many other issues you'll encounter with accessibility; the most important thing to know really is how to find answers online. Consult the HTML and CSS article's <a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/HTML_and_CSS#finding_help">Finding help section</a> for some good pointers.</p>

<h2 id="Summary">Summary</h2>

<p>Hopefully this article has given you a good grounding in the main accessibility problems you might encounter, and how to test and overcome them.</p>

<p>In the next article we'll look at feature detection in more detail.</p>

<p>{{PreviousMenuNext("Learn/Tools_and_testing/Cross_browser_testing/JavaScript","Learn/Tools_and_testing/Cross_browser_testing/Feature_detection", "Learn/Tools_and_testing/Cross_browser_testing")}}</p>

<h2 id="In_this_module">In this module</h2>

<ul>
 <li><a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Introduction">Introduction to cross browser testing</a></li>
 <li><a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Testing_strategies">Strategies for carrying out testing</a></li>
 <li><a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/HTML_and_CSS">Handling common HTML and CSS problems</a></li>
 <li><a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/JavaScript">Handling common JavaScript problems</a></li>
 <li><a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Accessibility">Handling common accessibility problems</a></li>
 <li><a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection">Implementing feature detection</a></li>
 <li><a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Automated_testing">Introduction to automated testing</a></li>
 <li><a href="/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Your_own_automation_environment">Setting up your own test automation environment</a></li>
</ul>