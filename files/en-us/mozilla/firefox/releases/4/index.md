---
title: Firefox 4 for developers
slug: Mozilla/Firefox/Releases/4
tags:
  - CSS
  - Firefox
  - Firefox 4
  - Gecko
  - Gecko 2.0
  - HTML
  - JavaScript
  - XPCOM
  - XUL
---
<div>{{FirefoxSidebar}}</div>

<p>Firefox 4, which shipped on March 22, 2011, enhances performance, adds more support for HTML5 and other evolving Web technologies, and further improves security. This article provides information about this release and what features are available for Web developers, add-on developers, and Gecko platform developers alike.</p>

<h2 id="Features_for_web_developers">Features for web developers</h2>

<p>Gecko now uses the <a href="/en-US/docs/Web/Guide/HTML/HTML5">HTML5</a> parser, which fixes bugs, improves interoperability, and improves performance. It also lets content embed <a href="/en-US/docs/Web/SVG">SVG</a> and <a href="/en-US/docs/Web/MathML">MathML</a> directly in the HTML markup.</p>

<h3 id="HTML">HTML</h3>

<dl>
 <dt><a href="/en-US/docs/Web/Guide/HTML/HTML5/HTML5_Parser">Meet the HTML5 parser</a></dt>
 <dd>A look at what the HTML5 parser means to you, and how to embed SVG and MathML into your content inline.</dd>
 <dt><a href="/en-US/docs/Learn/Forms">Forms in HTML5</a></dt>
 <dd>A look at improvements to web forms in HTML5. Among these changes are added input types in the {{HTMLElement("input")}} element, data validation, and more.</dd>
 <dt><a href="/en-US/docs/Web/HTML/Element/Heading_Elements">HTML5 Sections</a></dt>
 <dd>Gecko now supports the new HTML5 elements related to sections in a document: {{HTMLElement("article")}}, {{HTMLElement("section")}}, {{HTMLElement("nav")}}, {{HTMLElement("aside")}}, {{HTMLElement("hgroup")}}, {{HTMLElement("header")}} and {{HTMLElement("footer")}}.</dd>
 <dt><a href="/en-US/docs/Web/HTML/Global_attributes#attr-hidden">HTML5 hidden attribute</a></dt>
 <dd>This attribute, common to all elements, is used to hide content in a webpage that is not currently relevant to the user.</dd>
 <dt>Other HTML5 elements</dt>
 <dd>Gecko now also supports the following new HTML5 elements: {{HTMLElement("mark")}}, {{HTMLElement("figure")}}, and {{HTMLElement("figcaption")}}.</dd>
 <dt><a href="/en-US/docs/Web/API/WebSockets_API">WebSockets</a></dt>
 <dd>A guide to using the new WebSockets API for real-time communication between a web application and a server. Note that WebSockets as implemented in Firefox 4 is not compatible with the final standard, and should not generally be used.</dd>
</dl>

<h4 id="Canvas_improvements">Canvas improvements</h4>

<p>The following changes were made to the {{domxref("CanvasRenderingContext2D")}} interface to bring our {{HTMLElement("canvas")}} implementation closer to being in line with the specification:</p>

<ul>
 <li>Specifying a negative radius when calling <code>arc()</code> now correctly throws an <code>INDEX_SIZE_ERR</code> exception.</li>
 <li>Specifying non-finite values when calling <code>createLinearGradient()</code> and <code>createRadialGradient()</code> now throws <code>NOT_SUPPORTED_ERR</code> instead of <code>SYNTAX_ERR</code>.</li>
 <li>Setting <code>miterLimit</code> to a negative value no longer throws an exception; instead, it properly ignores non-positive values.</li>
 <li>Setting <code>lineWidth</code> to a negative value no longer throws an exception; instead, it properly ignores non-positive values.</li>
 <li>The <code>putImageData()</code> method now supports the optional parameters <code>dirtyX</code>, <code>dirtyY</code>, <code>dirtyWidth</code>, and <code>dirtyHeight</code>.</li>
</ul>

<h4 id="Miscellaneous_HTML_changes">Miscellaneous HTML changes</h4>

<ul>
 <li>{{HTMLElement("textarea")}} elements are now resizable by default; you can use the {{cssxref("resize")}} CSS property to disable this.</li>
 <li><code>canvas.getContext</code> and <code>canvas.toDataURL</code> no longer throw an exception when called with unrecognized arguments.</li>
 <li>The {{HTMLElement("canvas")}} element now supports the Mozilla-specific <code>mozGetAsFile()</code> method, which lets you obtain a memory-based file containing an image of the canvas's contents. See {{domxref("HTMLCanvasElement")}} for details.</li>
 <li><code>canvas2dcontext.lineCap</code> and <code>canvas2dcontext.lineJoin</code> no longer throw an exception when set to an unrecognized value.</li>
 <li><code>canvas2dcontext.globalCompositeOperation</code> no longer throws an exception when set to an unrecognized value, and no longer supports the non-standard <code>darker</code> value.</li>
 <li>Support for the obsolete {{HTMLElement("spacer")}} element, which was absent in all other browsers, has been removed.</li>
 <li>The {{HTMLElement("isindex")}} element, when created by calling {{domxref("document.createElement()")}}, is now created as a simple element with no properties or methods.</li>
 <li>Gecko now supports calling <code>click()</code> on {{HTMLElement("input")}} elements to open the file picker. See the <a href="/en-US/docs/Web/API/File/Using_files_from_web_applications#using_hidden_file_input_elements_using_the_click()_method">example</a> in the article <a href="/en-US/docs/Web/API/File/Using_files_from_web_applications">Using files from web applications</a>.</li>
 <li>The {{HTMLElement("input")}} element supports a new <a href="/en-US/docs/Web/HTML/Element/input#attr-mozactionhint"><code>mozactionhint</code></a> attribute, which lets you specify the label for the enter key on virtual keyboards.</li>
 <li>{{HTMLElement("script")}} elements inside {{HTMLElement("iframe")}}, {{HTMLElement("noembed")}}, and {{HTMLElement("noframes")}} elements now get executed, which they weren't in previous versions of Firefox. This is in compliance with the specification, and matches the behavior of other browsers.</li>
</ul>

<h3 id="CSS">CSS</h3>

<dl>
 <dt><a href="/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions">CSS transitions</a></dt>
 <dd>New CSS transitions support is available in Firefox 4.</dd>
 <dt>Computed values in CSS</dt>
 <dd>Support for <code>-moz-calc</code> has been added. This lets you specify <code>{{cssxref("&lt;length&gt;")}}</code> values as mathematical expressions.</dd>
 <dt>Selector grouping</dt>
 <dd>Support for <code>:-moz-any</code> to group selectors and factorize combinators.</dd>
 <dt>Background image subrectangle support</dt>
 <dd>The {{cssxref("-moz-image-rect")}} function makes it possible to use subrectangles of images as a {{cssxref("background-image")}}.</dd>
 <dt>CSS touch properties</dt>
 <dd>Support for touch properties is added. Details, and real article names, to come later.</dd>
 <dt><a href="/en-US/docs/Web/CSS/element()">Using arbitrary elements as CSS backgrounds</a></dt>
 <dd>You can use the <code>-moz-element</code> CSS function and the {{domxref("document.mozSetImageElement()")}} DOM function to use arbitrary HTML elements as backgrounds.</dd>
 <dt><a href="/en-US/docs/Web/CSS/Privacy_and_the_:visited_selector">Privacy and the :visited selector</a></dt>
 <dd>Changes have been made to what information can be obtained about the style of visited links using CSS selectors. This may affect some web applications.</dd>
</dl>

<h4 id="New_CSS_properties">New CSS properties</h4>

<table>
  <tr>
   <td>Property</td>
   <td>Description</td>
  </tr>
  <tr>
   <td><code>-moz-font-feature-settings</code></td>
   <td>Lets you customized advanced features of OpenType fonts.</td>
  </tr>
  <tr>
   <td><code>-moz-tab-size</code></td>
   <td>Specifies the width in space characters of a tab character (U+0009) when rendering text.</td>
  </tr>
  <tr>
   <td>{{cssxref("resize")}}</td>
   <td>Lets you control the dimensions in which an element may be resized.</td>
  </tr>
</table>

<h4 id="New_CSS_pseudo-classes">New CSS pseudo-classes</h4>

<table>
  <tr>
   <td >Pseudo-class</td>
   <td >Description</td>
  </tr>
  <tr>
   <td>{{cssxref(":-moz-handler-crashed")}}</td>
   <td>Used to style elements whose plugins have crashed.</td>
  </tr>
  <tr>
   <td><code>:-moz-placeholder</code></td>
   <td>Applied to placeholder text in form fields.</td>
  </tr>
  <tr>
   <td>{{cssxref(":-moz-submit-invalid")}}</td>
   <td>Applied to the submit button on forms when one or more of the form's fields doesn't validate.</td>
  </tr>
  <tr>
   <td>{{cssxref(":-moz-window-inactive")}}</td>
   <td>Applied to elements in inactive windows.</td>
  </tr>
  <tr>
   <td>{{cssxref(":invalid")}}</td>
   <td>Automatically applied to {{HTMLElement("input")}} fields when their contents are invalid.</td>
  </tr>
  <tr>
   <td>{{cssxref(":optional")}}</td>
   <td>Automatically applied to {{HTMLElement("input")}} fields that don't specify the <code>required</code> attribute.</td>
  </tr>
  <tr>
   <td>{{cssxref(":required")}}</td>
   <td>Automatically applied to {{HTMLElement("input")}} fields that specify the <code>required</code> attribute.</td>
  </tr>
  <tr>
   <td>{{cssxref(":valid")}}</td>
   <td>Automatically applied to {{HTMLElement("input")}} fields when their contents validate successfully.</td>
  </tr>
</table>

<h4 id="New_CSS_pseudo-selectors">New CSS pseudo-selectors</h4>

<table>
  <tr>
   <td >Pseudo-selector</td>
   <td >Description</td>
  </tr>
  <tr>
   <td>{{cssxref(":-moz-focusring")}}</td>
   <td>Lets you specify the appearance of an element when Gecko believes it should have a focus indication rendered.</td>
  </tr>
</table>

<h4 id="New_CSS_functions">New CSS functions</h4>

<table>
  <tr>
   <td >Function</td>
   <td >Description</td>
  </tr>
  <tr>
   <td><code>:-moz-any</code></td>
   <td>Lets you group selectors and factorize combinators.</td>
  </tr>
  <tr>
   <td><code>-moz-calc</code></td>
   <td>Lets you specify <code>{{cssxref("&lt;length&gt;")}}</code> values as mathematical expressions.</td>
  </tr>
  <tr>
   <td><code>-moz-element</code></td>
   <td>Lets you use an arbitrary element as a background for {{cssxref("background-image")}} and {{cssxref("background")}}.</td>
  </tr>
  <tr>
   <td><code>-moz-image-rect</code></td>
   <td>Lets you use a subrectangle of an image as a {{cssxref("background-image")}} or {{cssxref("background")}}.</td>
  </tr>
</table>

<h4 id="Renamed_CSS_properties">Renamed CSS properties</h4>

<table>
  <tr>
   <th>Old Name</th>
   <th>New Name</th>
   <th>Notes</th>
  </tr>
  <tr>
   <td><code>-moz-background-size</code></td>
   <td>{{cssxref("background-size")}}</td>
   <td>The name <code>-moz-background-size</code> is no longer supported.</td>
  </tr>
  <tr>
   <td><code>-moz-border-radius</code></td>
   <td>{{cssxref("border-radius")}}</td>
   <td>The old name is supported for a limited time to allow you time to update your sites. Rendering changes have also been made to match the latest version of the specification.</td>
  </tr>
  <tr>
   <td><code>-moz-box-shadow</code></td>
   <td>{{cssxref("box-shadow")}}</td>
   <td></td>
  </tr>
</table>

<h4 id="Miscellaneous_CSS_changes">Miscellaneous CSS changes</h4>

<ul>
 <li>The {{cssxref("text-shadow")}} property now caps the blur radius to 300px for sanity and performance reasons.</li>
 <li>The {{cssxref("overflow")}} property no longer applies to table-group elements (<code>&lt;thead&gt;</code>, <code>&lt;tbody&gt;</code>, and <code>&lt;tfoot&gt;</code>).</li>
 <li>The <code>-moz-appearance</code> property now supports the <code>-moz-win-borderless-glass</code> value, which applies a borderless Aero Glass look to an element.</li>
 <li>The <code><a href="/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#-moz-device-pixel-ratio">-moz-device-pixel-ratio</a></code> media feature has been added, allowing the use of the device pixels per CSS pixel ratio to be used in <a href="/en-US/docs/Web/CSS/Media_Queries/Using_media_queries">Media Queries</a>.</li>
 <li>Gecko's handling of <a href="/en-US/docs/Web/CSS/length">CSS units</a> has been revised to better match other browsers, and to more accurately translate absolute lengths into screen pixel counts based on the device's DPI.</li>
</ul>

<h3 id="Graphics_and_video">Graphics and video</h3>

<dl>
 <dt><a href="/en-US/docs/Web/API/WebGL_API">WebGL</a></dt>
 <dd>The developing WebGL standard is now supported by Firefox.</dd>
 <dt><a href="/en-US/docs/Optimizing_graphics_performance">Optimizing graphics performance</a></dt>
 <dd>Tips and tricks for getting the most out of graphics and video performance in Firefox 4.</dd>
 <dt><a href="/en-US/docs/Web/Media/Formats#webm">Support for WebM video</a></dt>
 <dd>The new open <a href="https://www.webmproject.org/">WebM</a> video format is supported by Gecko 2.0.</dd>
 <dt><a href="/en-US/docs/Web/SVG/SVG_animation_with_SMIL">SVG animation with SMIL</a></dt>
 <dd>Support for SMIL animation of SVG is now available.</dd>
 <dt>Using SVG as images and as CSS backgrounds</dt>
 <dd>You can now use SVG with the {{htmlelement("img")}} element, as well as a CSS {{cssxref("background-image")}}.</dd>
 <dt>Media <code>buffered</code> attribute support</dt>
 <dd>The <code>buffered</code> attribute on {{HTMLElement("video")}} and {{HTMLElement("audio")}} elements is now supported, letting you determine which ranges of a media file have been buffered. The {{domxref("TimeRanges")}} DOM interface has been implemented to support this.</dd>
 <dt>Media <code>preload</code> attribute</dt>
 <dd>The <code>preload</code> attribute from the HTML5 specification has been implemented, replacing the previously-implemented (and no longer supported) <code>autobuffer</code> attribute. This affects the {{HTMLElement("video")}} and {{HTMLElement("audio")}} elements, as well as the {{interface("nsIDOMHTMLMediaElement")}} interface.</dd>
 <dt>SVG text positioning improvements</dt>
 <dd>You can now specify lists for the values of the <code>x</code>, <code>y</code>, <code>dx</code>, and <code>dy</code> properties on SVG {{SVGElement("text")}} and {{SVGElement("tspan")}} elements. This lets you control the positioning of each character in a string individually.</dd>
</dl>

<h3 id="DOM">DOM</h3>

<dl>
 <dt><a href="/en-US/docs/Web/JavaScript/Typed_arrays">JavaScript typed arrays</a></dt>
 <dd>Support has been added for JavaScript typed arrays; this allows you to manipulate buffers containing raw data using native data types. Several APIs make use of this, including the <a href="/en-US/docs/Web/API/File">File API</a>, <a href="/en-US/docs/Web/API/WebGL_API">WebGL</a>, and <a href="/en-US/docs/Web/API/WebSockets_API">WebSockets</a>.</dd>
 <dt>Obtaining boundary rectangles for ranges</dt>
 <dd>The {{domxref("Range")}} object now has {{domxref("range.getClientRects()")}} and {{domxref("range.getBoundingClientRect()")}} methods.</dd>
 <dt>Capturing mouse events on arbitrary elements</dt>
 <dd>Support for the Internet Explorer-originated <code>setCapture()</code> and <code>releaseCapture()</code> APIs has been added. See {{bug(503943)}}.</dd>
 <dt><a href="/en-US/docs/Web/API/History_API">Manipulating the browser history</a></dt>
 <dd>The existing document history object, available through the {{domxref("window.history")}} object, now supports the new HTML5 <code>pushState()</code> and <code>replaceState()</code> methods.</dd>
 <dt><a href="/en-US/docs/DOM/Animations_using_MozBeforePaint">Animations using MozBeforePaint</a></dt>
 <dd>A new event has been added which, in concert with the <code>window.mozRequestAnimationFrame()</code> method and <code>window.mozAnimationStartTime</code> property, provides a way to create animations that are synchronized with one another.</dd>
 <dt>Touch and multi-touch events</dt>
 <dd>Support has been added for touch and multi-touch events.</dd>
</dl>

<h4 id="HTML_elements'_DOM_interfaces_have_changed">HTML elements' DOM interfaces have changed</h4>

<p>Several HTML elements have had their DOM interfaces changed to the ones required by the HTML5 specification, as shown below.</p>

<table>
  <tr>
   <th>Interface in Firefox 3.6</th>
   <th>Interface in Firefox 4</th>
   <th>HTML Element</th>
  </tr>
  <tr>
   <td><code><a href="/en-US/docs/Web/API/HTMLSpanElement">HTMLSpanElement</a></code></td>
   <td><code><a href="/en-US/docs/Web/API/HTMLElement">HTMLElement</a></code></td>
   <td>{{HTMLElement("abbr")}}, {{HTMLElement("acronym")}}, {{HTMLElement("address")}}, {{HTMLElement("b")}}, {{HTMLElement("bdo")}}, {{HTMLElement("big")}}, {{HTMLElement("blink")}}, {{HTMLElement("center")}}, {{HTMLElement("cite")}}, {{HTMLElement("code")}}, {{HTMLElement("dd")}}, {{HTMLElement("dfn")}}, {{HTMLElement("dt")}}, {{HTMLElement("em")}}, {{HTMLElement("i")}}, {{HTMLElement("kbd")}}, {{HTMLElement("listing")}}, {{HTMLElement("nobr")}}, {{HTMLElement("plaintext")}}, {{HTMLElement("s")}}, {{HTMLElement("samp")}}, {{HTMLElement("small")}}, {{HTMLElement("strike")}}, {{HTMLElement("strong")}}, {{HTMLElement("sub")}}, {{HTMLElement("sup")}}, , {{HTMLElement("tt")}}, {{HTMLElement("u")}}, {{HTMLElement("var")}}, {{HTMLElement("xmp")}}</td>
  </tr>
  <tr>
   <td><code><a href="/en-US/docs/Web/API/HTMLDivElement">HTMLDivElement</a></code></td>
   <td><code><a href="/en-US/docs/Web/API/HTMLElement">HTMLElement</a></code></td>
   <td>{{HTMLElement("noembed")}}, {{HTMLElement("noframes")}}, {{HTMLElement("noscript")}}</td>
  </tr>
  <tr>
   <td><code><a href="/en-US/docs/DOM/HTMLWBRElement">HTMLWBRElement</a></code></td>
   <td><code><a href="/en-US/docs/Web/API/HTMLElement">HTMLElement</a></code></td>
   <td>{{HTMLElement("wbr")}}</td>
  </tr>
</table>

<h4 id="Miscellaneous_DOM_changes">Miscellaneous DOM changes</h4>

<ul>
 <li>The wrapping of a {{HTMLElement("textarea")}} element can now be controlled via the DOM, via the <code>wrap</code> DOM attribute. {{bug(41464)}}</li>
 <li>{{HTMLElement("script")}} elements created using {{domxref("document.createElement()")}} and inserted into a document now behave according to the HTML5 specification by default. Scripts with the <code>src</code> attribute execute as soon as available (without maintaining ordering) and scripts without the <code>src</code> attribute execute synchronously. To make script-inserted scripts that have the <code>src</code> attribute execute in the insertion order, set <code>.async=false</code> on them.</li>
 <li>DOM {{domxref("file")}} objects now offer a <code>url</code> property.</li>
 <li><a href="/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest#using_formdata_objects">FormData</a> support for XMLHttpRequest.</li>
 <li>The {{domxref("element.isContentEditable")}} property has been implemented.</li>
 <li>The {{domxref("document.currentScript")}} property lets you determine which {{HTMLElement("script")}} element's script is currently executing. The new {{domxref("element.onbeforescriptexecute")}} and {{domxref("element.onafterscriptexecute")}} events are fired before and after a script element executes.</li>
 <li>Added the <a href="/en-US/docs/Web/API/DataTransfer#mozsourcenode"><code>mozSourceNode</code></a> property to the <a href="/en-US/docs/Web/API/DataTransfer"><code>DragTransfer</code></a> object.</li>
 <li>Added the <a href="/en-US/docs/Web/API/Selection/modify"><code>selection.modify()</code></a> method to the {{domxref("Selection")}} object; this lets you easily alter the current text selection or cursor position in a browser window.</li>
 <li>Support for the <code>window.directories</code> object and the <code>directories</code> feature for {{domxref("window.open")}}, which are not supported in any other browser, has been removed. Use <code>personalbar</code> instead. {{Bug(474058)}}</li>
 <li>The {{domxref("event.mozInputSource")}} property has been added to DOM user interface events; this non-standard property lets you determine the type of device that generated an event.</li>
 <li>The {{domxref("document.onreadystatechange")}} event has been implemented.</li>
 <li>The {{domxref("document.createElement")}} method no longer accepts <code>&lt;</code> and <code>&gt;</code> around the tag name in quirks mode.</li>
 <li>The {{domxref("element.setCapture()")}} and {{domxref("document.releaseCapture()")}} methods have been added, allowing elements to continue tracking mouse events even while the mouse is outside their normal tracking area after a <code>mousedown</code> event has occurred.</li>
 <li>The {{domxref("window.mozPaintCount")}} property has been added; it lets you determine how many times a document has been painted. This can be useful when testing performance of your web application.</li>
 <li>The language token has been removed from {{domxref("window.navigator.appVersion")}} and {{domxref("window.navigator.userAgent")}}. Use {{domxref("window.navigator.language")}} or the <a href="/en-US/docs/Web/HTTP/Content_negotiation">Accept-Language header</a> instead. {{Bug(572656)}}</li>
 <li>The <a href="/en-US/docs/Web/API/XMLHttpRequest">XMLHttpRequest</a> object now exposes the response as a JavaScript typed array as well as a string, using the Gecko-specific <code>mozResponseArrayBuffer</code> property.</li>
 <li><a href="/en-US/docs/Web/API/MouseEvent">Mouse events</a> now include a <code>mozPressure</code> property indicating the amount of pressure on supported pressure-sensitive input devices.</li>
 <li>The {{domxref("URL/createObjectURL", "window.URL.createObjectURL()")}} and {{domxref("URL/revokeObjectURL", "window.URL.revokeObjectURL()")}} methods let you create object URLs which reference local files.</li>
 <li>The {{domxref("DOMImplementation.createHTMLDocument()")}} method lets you create a new HTML document.</li>
 <li>{{domxref("Node.mozMatchesSelector()")}} now throws a <code>SYNTAX_ERR</code> exception if the specified selector string is invalid, instead of incorrectly returning <code>false</code>.</li>
 <li>You can now set an element's SVG properties' values using the same shorthand syntax as with CSS. For example: <code>element.style.fill = 'lime'</code>. See {{domxref("element.style")}} for details.</li>
 <li>The document root now has <a href="/en-US/docs/Supporting_private_browsing_mode#Detecting_whether_private_browsing_mode_is_permanent">a <code>privatebrowsingmode</code> attribute</a> that describes the state of private browsing mode, including an indication of whether private browsing is temporary or permanent for the session.</li>
 <li>The second parameter of the {{domxref("window.getComputedStyle()")}} method is now optional, as it is in every other major browser.</li>
 <li>The DOM <a href="/en-US/docs/DOM/event/StorageEvent"><code>StorageEvent</code></a> object now matches the latest version of the specification.</li>
 <li>The minimum allowed delay for the {{domxref("setTimeout()")}} method is now a preference, <code>dom.min_timeout_value</code>.</li>
 <li>The <a href="/en-US/docs/Gecko-Specific_DOM_Events#MozAfterPaint"><code>MozAfterPaint</code></a> event is no longer sent by default, due to a potential security issue. It can be re-enabled by setting a preference.</li>
</ul>

<h3 id="Security">Security</h3>

<dl>
 <dt><a href="/en-US/docs/Web/HTTP/CSP">Content Security Policy (CSP)</a></dt>
 <dd>Content Security Policy (CSP) is a Mozilla proposal designed to help web designers and server administrators specify how content on their web sites interacts. The goal is to help detect and mitigate attacks including cross-site scripting and data injection attacks.</dd>
 <dt><a href="/en-US/docs/Web/HTTP/Headers/Strict-Transport-Security">HTTP Strict Transport Security</a></dt>
 <dd>HTTP Strict Transport Security is a security feature that lets a web site tell browsers that it should only be communicated with using HTTPS, instead of using HTTP.</dd>
 <dt><a href="/en-US/docs/Web/HTTP/Headers/X-Frame-Options">The X-FRAME-OPTIONS response header</a></dt>
 <dd>The X-FRAME-OPTIONS HTTP response header introduced in Internet Explorer 8 is now supported by Firefox. This allows sites to indicate whether or not their pages can be used in frames, and if so, whether or not to restrict that to the same origin.</dd>
 <dt><a href="/en-US/docs/Web/HTTP/Headers/User-Agent/Firefox">User Agent string</a> changes</dt>
 <dd>As a means to reduce the amount of data and entropy sent out in HTTP requests (see {{bug("572650")}}), the crypto strength and language tokens have been removed from the user agent string.</dd>
</dl>

<h3 id="JavaScript">JavaScript</h3>

<p>For an overview of the changes implemented in JavaScript 1.8.5, see <a href="/en-US/docs/JavaScript/New_in_JavaScript/1.8.5">New in JavaScript 1.8.5</a>. JavaScript in Firefox 4 will have additional adherence to the ECMAScript 5 standard.</p>

<h3 id="Developer_tools">Developer tools</h3>

<dl>
 <dt><a href="/en-US/docs/Tools/Web_Console">Using the Web Console</a></dt>
 <dd>The Web Console tool is a useful debugging aid for web developers and extension developers alike.</dd>
</dl>

<div class="note">
  <p><strong>Note:</strong>The Error Console is disabled by default starting in {{Gecko("2.0")}}. You can re-enable it by changing the <code>devtools.errorconsole.enabled</code> preference to <code>true</code> and restarting the browser.</p>
</div>

<h2 id="Changes_for_Mozilla_and_add-on_developers">Changes for Mozilla and add-on developers</h2>

<p>For helpful tips on updating existing extensions for Firefox 4, see <a href="/en-US/docs/Extensions/Updating_extensions_for_Firefox_4">Updating extensions for Firefox 4</a>. There are several key changes that break compatibility with existing add-ons, so be sure to read that article.</p>

<p>If you're a theme developer, you should read <a href="/en-US/docs/Theme_changes_in_Firefox_4">Theme changes in Firefox 4</a> to understand some critical changes you'll need to be aware of.</p>

<h3 id="JavaScript_code_modules">JavaScript code modules</h3>

<dl>
 <dt><a href="/en-US/docs/JavaScript_code_modules/Services.jsm">Services.jsm</a></dt>
 <dd>The <code>Services.jsm</code> code module provides getters that make it easy to obtain references to commonly-used services, such as the preferences service or the window mediator, among others.</dd>
 <dt><a href="/en-US/docs/JavaScript_code_modules/ctypes.jsm">JS-ctypes API</a></dt>
 <dd>The JS-ctypes API makes it possible to call C-compatible foreign library functions without using XPCOM.</dd>
 <dt><a href="/en-US/docs/Addons/Add-on_Manager">Add-ons Manager</a></dt>
 <dd>The new Add-ons Manager provides information about installed add-ons, support for managing them, and provides ways to install and remove add-ons.</dd>
 <dt><a href="/en-US/docs/JavaScript_code_modules/PopupNotifications.jsm">PopupNotifications.jsm</a></dt>
 <dd>The new popup notifications module makes it easy to present attractive, non-modal notifications to the user. You can see how to use this API in <a href="/en-US/docs/Using_popup_notifications">Using popup notifications</a>.</dd>
 <dt><a href="/en-US/docs/JavaScript_code_modules/Using#Locating_the_code_module">Loading code modules from chrome: URLs</a></dt>
 <dd>You can now load JavaScript code modules using <strong>chrome:</strong> URLs, even inside JAR files.</dd>
 <dt>DownloadLastDir.jsm</dt>
 <dd>The <a href="/en-US/docs/JavaScript_code_modules/DownloadLastDir.jsm"><code>DownloadLastDir.jsm</code></a> code module provides the <code>gDownloadLastDir</code> global variable, which contains a string you can use to learn the path of the directory into which the last download occurred. This module handles issues related to private browsing for you.</dd>
 <dt><a href="/en-US/docs/Performance/Measuring_performance_using_the_PerfMeasurement.jsm_code_module">Measuring performance using the PerfMeasurement.jsm code module</a></dt>
 <dd>The <a href="/en-US/docs/JavaScript_code_modules/PerfMeasurement.jsm"><code>PerfMeasurement.jsm</code></a> code module provides an API to measure CPU-level performance data in JavaScript code.</dd>
</dl>

<h4 id="Miscellaneous_changes_to_code_modules">Miscellaneous changes to code modules</h4>

<ul>
 <li>The <code>NetUtil.jsm</code> code module now offers the <a href="/en-US/docs/JavaScript_code_modules/NetUtil.jsm#readInputStreamToString()"><code>readInputStreamToString()</code></a> method, which lets you read arbitrary bytes from a stream into a string, even if the stream includes zeroes.</li>
 <li>The XPCOMUtils.jsm code module now offers <a href="/en-US/docs/Mozilla/JavaScript_code_modules/XPCOMUtils.jsm#IterSimpleEnumerator()">IterSimpleEnumerator()</a> and <a href="/en-US/docs/Mozilla/JavaScript_code_modules/XPCOMUtils.jsm#IterStringEnumerator()">IterStringEnumerator()</a> helpers to iterate over XPCOM enumerators.</li>
 <li>You can now <a href="/en-US/docs/JavaScript_code_modules/Using_workers_in_JavaScript_code_modules">use workers in JavaScript code modules</a>.</li>
</ul>

<h3 id="DOM_changes">DOM changes</h3>

<dl>
 <dt>{{domxref("ChromeWorker")}}</dt>
 <dd>A new type of worker for privileged code; this lets you use things like <a href="/en-US/docs/js-ctypes">js-ctypes</a> from workers in extensions and application code.</dd>
 <dt><a href="/en-US/docs/Web/API/Touch_events">Touch events</a></dt>
 <dd>Support for (non-standard) touch events has been added; these let you track multiple fingers moving on a touch screen at the same time.</dd>
</dl>

<h4 id="Other_DOM_changes">Other DOM changes</h4>

<ul>
 <li>The <a href="/en-US/docs/Observer_Notifications#Documents">new "document-element-inserted" notification</a> is sent when a document's root element is created, but before any scripts are executed on it.</li>
</ul>

<h3 id="XUL">XUL</h3>

<h4 id="Changes_to_the_tabbrowser_element">Changes to the tabbrowser element</h4>

<p>Several changes were made to the <code><a href="/en-US/docs/Mozilla/Tech/XUL/tabbrowser">&lt;xul:tabbrowser&gt;</a></code> element that impact extensions that interact with tabs. In addition to supporting app tabs, these changes also change the tab bar into a standard toolbar, which lets the user drag toolbar buttons into it.</p>

<ul>
 <li>The <code>TabClose</code>, <code>TabSelect</code>, and <code>TabOpen</code> events no longer bubble up to the <code><a href="/en-US/docs/Mozilla/Tech/XUL/tabbrowser">&lt;xul:tabbrowser&gt;</a></code> element (<code>gBrowser</code>). Event listeners for those events should be added to <code>gBrowser.tabContainer</code> rather than to <code>gBrowser</code> directly.</li>
 <li>The tab context menu is no longer an anonymous child of the <code><a href="/en-US/docs/Mozilla/Tech/XUL/tabbrowser">&lt;xul:tabbrowser&gt;</a></code>. It can therefore be overlaid directly with <a href="/en-US/docs/XUL_Overlays">XUL overlays</a>. It can also be accessed more directly in JavaScript via <code>gBrowser.tabContextMenu</code>. See <a href="https://www.gavinsharp.com/blog/2010/03/31/accessingmodifying-the-firefox-tab-context-menu-from-extensions/">this blog post</a> for more details.</li>
 <li>The new <code><a href="/en-US/docs/XUL/Property/visibleTabs">visibleTabs</a></code> property was added to let you get an array of the currently visible tabs; this lets you determine which tabs are visible in the current tab set. This is used by Firefox Panorama, for example.</li>
 <li>Added the new <code><a href="/en-US/docs/Mozilla/Tech/XUL/Method/showOnlyTheseTabs">showOnlyTheseTabs</a></code> method; this is used by Firefox Panorama.</li>
 <li>Added the new <code><a href="/en-US/docs/Mozilla/Tech/XUL/Method/getIcon">getIcon</a></code> method, which lets you get a tab's favicon without having to pull up the <code><a href="/en-US/docs/Mozilla/Tech/XUL/browser">&lt;xul:browser&gt;</a></code> element.</li>
 <li>Added the new <code><a href="/en-US/docs/XUL/Property/tabbrowser.tabs">tabbrowser.tabs</a></code> property, which lets you easily get a list of the tabs in a <code><a href="/en-US/docs/Mozilla/Tech/XUL/tabbrowser">&lt;xul:tabbrowser&gt;</a></code> element.</li>
 <li>The new <code><a href="/en-US/docs/Mozilla/Tech/XUL/Method/pinTab">pinTab</a></code> and <code><a href="/en-US/docs/Mozilla/Tech/XUL/Method/unpinTab">unpinTab</a></code> methods let you pin and unpin tabs (that is, switch them between being app tabs and regular tabs).</li>
 <li>Added the <code><a href="/en-US/docs/Mozilla/Tech/XUL/Method/getTabModalPromptBox">getTabModalPromptBox</a></code> method and <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/tabmodalPromptShowing">tabmodalPromptShowing</a></code> attribute to the <code><a href="/en-US/docs/Mozilla/Tech/XUL/tabbrowser">&lt;xul:tabbrowser&gt;</a></code> to support tab-modal alerts.</li>
</ul>

<h4 id="Changes_to_popups">Changes to popups</h4>

<ul>
 <li>The <code><a href="/en-US/docs/Mozilla/Tech/XUL/popup">&lt;xul:popup&gt;</a></code> element is no longer supported; you should use <code><a href="/en-US/docs/Mozilla/Tech/XUL/menupopup">&lt;xul:menupopup&gt;</a></code> instead. (If you continue using <code>popup</code>, you will encounter glitches, since the element has no special meaning anymore. For example, <code><a href="/en-US/docs/Mozilla/Tech/XUL/menuseparator">&lt;xul:menuseparator&gt;</a></code> can appear transparent when used in a <code><a href="/en-US/docs/Mozilla/Tech/XUL/popup">&lt;xul:popup&gt;</a></code>.)</li>
 <li>The <code><a href="/en-US/docs/Mozilla/Tech/XUL/menupopup">&lt;xul:menupopup&gt;</a></code> XUL element now has a <code><a href="/en-US/docs/XUL/Property/triggerNode">triggerNode</a></code> property, which indicates the node on which the event occurred that caused the popup to open. This also required the addition of a trigger event parameter to the <code><a href="/en-US/docs/Mozilla/Tech/XUL/Method/openPopup">openPopup</a></code> method. Also, the <code><a href="/en-US/docs/XUL/Property/anchorNode">anchorNode</a></code> property has been added; it returns the anchor specified when the popup was created.</li>
 <li>The <code><a href="/en-US/docs/Mozilla/Tech/XUL/panel">&lt;xul:panel&gt;</a></code> element now offers <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/fade">fade</a></code> and <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/flip">flip</a></code> attributes, which are used to configure the behavior of new "arrow" style notification panels.</li>
</ul>

<h4 id="Remote_XUL_support_removed">Remote XUL support removed</h4>

<p>Remote XUL is no longer supported; this affects XUL documents being served through HTTP; also, you can no longer load XUL documents using <code>file://</code> URLs unless you create the preference <code>dom.allow_XUL_XBL_for_file</code> and set it to <code>true</code>. There is, however, a whitelist feature that can be used to allow specific domains to load remote XUL. The <a href="https://addons.mozilla.org/en-US/firefox/addon/235281/">Remote XUL Manager extension</a> lets you manage this whitelist.</p>

<h4 id="Miscellaneous_XUL_changes">Miscellaneous XUL changes</h4>

<ul>
 <li>The <code>readonly</code> attribute now correctly works for <a href="/en-US/docs/XBL/XBL_1.0_Reference/Elements#field">XBL fields</a>.</li>
 <li>The <code><a href="/en-US/docs/Mozilla/Tech/XUL/resizer">&lt;xul:resizer&gt;</a></code> element now lets you use the <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/element">element</a></code> attribute to specify an element to resize, instead of resizing the window.</li>
 <li>The <code><a href="/en-US/docs/Mozilla/Tech/XUL/resizer">&lt;xul:resizer&gt;</a></code> element now has an <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/resizer.type">type</a></code> attribute that lets you specify that the resizer is for a window instead of an element, to prevent the window resizer from being drawn twice.</li>
 <li>The "active" attribute no longer gets set on active XUL windows. Instead, you can use the new <a href="/en-US/docs/Web/CSS/:-moz-window-inactive"><code>:-moz-window-inactive</code></a> pseudoclass in order to assign different styles to background windows.</li>
 <li>The <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/emptytext">emptytext</a></code> attribute is now deprecated; you should use <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/placeholder">placeholder</a></code> instead.</li>
 <li>The <code><a href="/en-US/docs/Mozilla/Tech/XUL/window">&lt;xul:window&gt;</a></code> element now offers a <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/accelerated">accelerated</a></code> attribute; when true, the hardware layer manager is permitted to accelerate the window.</li>
 <li>The <code><a href="/en-US/docs/Mozilla/Tech/XUL/stack">&lt;xul:stack&gt;</a></code> element now supports the <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/bottom">bottom</a></code> and <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/right">right</a></code> attributes.</li>
 <li>Events are now fired during <code><a href="/en-US/docs/Mozilla/Tech/XUL/toolbox">&lt;xul:toolbox&gt;</a></code> customization, allowing you to <a href="/en-US/docs/XUL/Toolbars/Toolbar_customization_events">detect changes to toolbars</a>.</li>
 <li>The <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/alternatingbackground">alternatingbackground</a></code> attribute for <code><a href="/en-US/docs/Mozilla/Tech/XUL/tree">&lt;xul:tree&gt;</a></code> elements is no longer supported; you can use the <a href="/en-US/docs/Web/CSS/:-moz-tree-row"><code>:-moz-tree-row</code></a> pseudo-class instead.</li>
 <li>The Bookmarks Toolbar overflow button with anonid chevronPopup is no longer anonymous; it has an ID of "PlacesChevron".</li>
 <li>The <code><a href="/en-US/docs/Mozilla/Tech/XUL/tabs">&lt;xul:tabs&gt;</a></code> element now has a <code><a href="/en-US/docs/XUL/Property/tabbox">tabbox</a></code> property, replacing the old <code>_tabbox</code> property, which has been deprecated (and was never documented).</li>
 <li>XUL <code><a href="/en-US/docs/Mozilla/Tech/XUL/window">&lt;xul:window&gt;</a></code> elements now have the <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/drawintitlebar">drawintitlebar</a></code> attribute; if this is <code>true</code>, the window's content area includes the title bar, allowing drawing into the title bar.</li>
 <li>New <code>TabPinned</code> and <code>TabUnpinned</code> events are available, allowing you to <a href="/../../../../en-US/docs/Code_snippets/Tabbed_browser#Notification_when_a_tab_is_pinned_or_unpinned">detect when tabs are pinned and unpinned</a>.</li>
 <li>The new <a href="/en-US/docs/Code_snippets/Tabbed_browser#Notification_when_a_tab%27s_attributes_change"><code>TabAttrModified</code> event</a> is sent when a tab's <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/label">label</a></code>, <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/crop">crop</a></code>, <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/busy">busy</a></code>, <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/image">image</a></code>, or <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/selected">selected</a></code> attributes change.</li>
 <li><code><a href="/en-US/docs/Mozilla/Tech/XUL/tab">&lt;xul:tab&gt;</a></code> elements now have a <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/pinned">pinned</a></code> attribute, letting you determine whether or not a tab is currently pinned.</li>
 <li>The <code>setDirectionIndicator</code> class on <code><a href="/en-US/docs/Mozilla/Tech/XUL/tree">&lt;xul:tree&gt;</a></code> elements hasn't done anything for some time now; now it's not used at all anymore.</li>
 <li>The <code><a href="/en-US/docs/Mozilla/Tech/XUL/window">&lt;xul:window&gt;</a></code> element now has a <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/chromemargin">chromemargin</a></code> attribute that lets you set the margin between chrome and content on each side of a window; you can use this to draw into the title bar, for example.</li>
 <li>The <code><a href="/en-US/docs/Mozilla/Tech/XUL/window">&lt;xul:window&gt;</a></code> element now has a <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/disablechrome">disablechrome</a></code> attribute; this is used to hide most of the chrome in a window when it's being used to display in-browser UI, such as <code>about:addons</code>.</li>
 <li>The <code><a href="/en-US/docs/Mozilla/Tech/XUL/window">&lt;xul:window&gt;</a></code> element now has a <code><a href="/en-US/docs/Mozilla/Tech/XUL/Attribute/disablefastfind">disablefastfind</a></code> attribute, which lets you disable the find bar in a window when the content doesn't support it. This is used, for example, by the add-ons panel.</li>
 <li>Toolbars can now be external to toolboxes, while still being considered a member of the <code><a href="/en-US/docs/Mozilla/Tech/XUL/toolbox">&lt;xul:toolbox&gt;</a></code>, by setting the <code><a href="/en-US/docs/XUL/Property/toolboxid">toolboxid</a></code> property of the <code><a href="/en-US/docs/Mozilla/Tech/XUL/toolbar">&lt;xul:toolbar&gt;</a></code>. Also, the <code><a href="/en-US/docs/Mozilla/Tech/XUL/toolbox">&lt;xul:toolbox&gt;</a></code> element now has a <code><a href="/en-US/docs/XUL/Property/externalToolbars">externalToolbars</a></code> property, which lists all the toolbars that are considered members of the toolbox.</li>
 <li>Support has been added for <a href="/en-US/docs/XUL/Template_Guide/Template_Logging">logging XUL templates</a> for debugging purposes.</li>
</ul>

<h3 id="UI_changes_affecting_developers">UI changes affecting developers</h3>

<dl>
 <dt><a href="/en-US/docs/Mozilla/Firefox/Releases/4/The_add-on_bar">The add-on bar</a></dt>
 <dd>The status bar has been removed in favor of the new add-on bar. You'll need to update your extension to use this if you've been adding UI to the status bar in the past.</dd>
 <dt><a href="/en-US/docs/Hiding_browser_chrome">Hiding browser chrome</a></dt>
 <dd>You can now hide the browser's chrome when it's desirable to do so; for example, <code>about:addons</code> does this.</dd>
</dl>

<h3 id="Storage">Storage</h3>

<h4 id="Miscellaneous_storage_API_changes">Miscellaneous storage API changes</h4>

<ul>
 <li>The {{interface("mozIStorageBindingParamsArray")}} interface now has a length attribute that indicates the number of {{interface("mozIStorageBindingParams")}} objects in the array.</li>
 <li>The {{ifmethod("mozIStorageStatement", "bindParameters")}} now returns an error if the specified {{interface("mozIStorageBindingParamsArray")}} is empty.</li>
 <li>Added the {{ifmethod("mozIStorageConnection", "clone")}} method, which lets you clone an existing database connection.</li>
 <li>Added the {{ifmethod("mozIStorageConnection", "asyncClose")}} method, which lets you close a database connection asynchronously; you specify a callback to be notified when the close operation is complete.</li>
 <li>Added the {{ifmethod("mozIStorageConnection", "setGrowthIncrement")}} method, which lets you specify the amount by which a database file is grown at a time, in order to help SQLite reduce fragmentation.</li>
 <li>The <code>SQLITE_CONSTRAINT</code> error is now reported as <code>NS_ERROR_STORAGE_CONSTRAINT</code> instead of as <code>NS_ERROR_FAILURE</code>.</li>
</ul>

<h3 id="XPCOM">XPCOM</h3>

<p>In addition to the specific changes referenced below, it's important to note that there are no longer any frozen interfaces. All interfaces are now unfrozen, regardless of what the documentation may say. We'll update the documentation over time.</p>

<dl>
 <dt><a href="/en-US/docs/XPCOM/XPCOM_changes_in_Gecko_2.0">XPCOM changes in Gecko 2.0</a></dt>
 <dd>Details about changes to XPCOM that impact compatibility in Firefox 4.</dd>
 <dt><a href="/en-US/docs/Components.utils.getGlobalForObject">Components.utils.getGlobalForObject()</a></dt>
 <dd>This new method returns the global object with which an object is associated; this replaces a common use case of the now-removed <code>__parent__</code>.</dd>
</dl>

<h3 id="Places">Places</h3>

<ul>
 <li>Places query results may now be observed by multiple observers, and queries may be executed asynchronously. This means there have been some changes to the {{interface("nsINavHistoryResult")}}, {{interface("nsINavHistoryQueryOptions")}}, and {{interface("nsINavHistoryContainerResultNode")}} interfaces. More significantly, the {{interface("nsINavHistoryResultViewer")}} interface has been renamed to {{interface("nsINavHistoryResultObserver")}}.</li>
 <li>Some <a href="/en-US/docs/Observer_Notifications#Places">new notifications</a> have been added to enable the browser to track the shutdown process of the Places service more reliably. Of these, most are for internal use only, but the <code>places-connection-closed</code> notification is available to know when the Places service has completed its shutdown process.</li>
 <li>The array size output parameter on several Places methods is now optional.</li>
 <li>Support for <code>&lt;menupopup type="places"&gt;</code> has been removed. Instead, you need to create and populate a menu with Places information manually, instead of having it done for you. See <a href="/en-US/docs/Displaying_Places_information_using_views#Menu_view">Displaying Places information using views: Menu view</a> for details.</li>
</ul>

<h3 id="Interface_changes">Interface changes</h3>

<ul>
 <li>The {{interface("nsIDocShell")}} and {{interface("nsIWebBrowser")}} interfaces now have a new <code>isActive</code> attribute, which is used to allow optimization of code paths for documents that aren't currently visible.</li>
 <li>The {{interface("nsIMemory")}} method {{ifmethod("nsIMemory","isLowMemory")}} has been deprecated. You should use <a href="/en-US/docs/XPCOM_Interface_Reference/nsIMemory#Low_memory_notifications">"memory-pressure" notifications</a> to watch for low memory situations instead.</li>
 <li>The API for handling redirects on HTTP channels has changed to let them be processed asynchronously. Any code that implements redirect handling using {{ifmethod("nsIChannelEventSink", "onChannelRedirect")}} needs to be updated to use {{ifmethod("nsIChannelEventSink", "asyncOnChannelRedirect")}} instead. This accepts a callback handler that must be called when a redirect is successfully completed.</li>
 <li>The {{ifmethod("nsINavHistoryResultObserver", "batching")}} method has been added, providing a way to group Places operations into batches, reducing the number of update notifications delivered, which can improve performance when observers are performing relatively involved tasks (such as refreshing views).</li>
 <li>The long-obsolete <code>nsIPref</code> interface has finally been removed. If you haven't already switched to {{interface("nsIPrefService")}}, now is the time.</li>
 <li>The {{interface("nsISessionStore")}} and {{interface("nsISessionStartup")}} interfaces received changes to support on-demand session restore. See the {{ifmethod("nsISessionStore", "restoreLastSession")}} method.</li>
 <li>The {{interface("nsIPrincipal")}} methods {{ifmethod("nsIPrincipal", "subsumes")}} and {{ifmethod("nsIPrincipal", "checkMayLoad")}}, as well as its <code>origin</code>, <code>csp</code>, and <code>URI</code> attributes, are now available from script; previously they were only available from native code.</li>
 <li>The {{interface("nsIPrompt")}} interface now supports tab-modal alerts; see <a href="/en-US/docs/Using_tab-modal_prompts">Using tab-modal prompts</a> for details.</li>
 <li>The {{ifmethod("nsIEffectiveTLDService", "getPublicSuffixFromHost")}} method now correctly rejects host name starting with a period (".").</li>
 <li>The {{ifmethod("mozIJSSubScriptLoader", "loadSubScript")}} method now has an optional argument allowing you to specify the character set of the script; if one is not provided, ASCII is assumed (as was always assumed previously).</li>
 <li>The <code>nsIAccessProxy</code> interface has been removed. It was an implementation detail that has outlived its usefulness.</li>
 <li>The {{interface("nsIContentView")}} and {{interface("nsIContentViewManager")}} interfaces have been added for Firefox Mobile. It represents a scrollable content view whose contents are actually drawn by a separate process.</li>
 <li>The {{interface("nsIDiskCacheStreamInternal")}} interface has been added.</li>
 <li>The {{interface("nsIExternalURLHandlerService")}} interface has been added.</li>
 <li>The {{interface("nsISyncJPAKE")}} interface has been added. See {{bug("601645")}}.</li>
 <li>The {{interface("nsIINIParserWriter")}} interface was added in Gecko 1.9.2.4 to support writing to INI files.</li>
</ul>

<h3 id="Memory_management">Memory management</h3>

<dl>
 <dt><a href="/en-US/docs/Infallible_memory_allocation">Infallible memory allocation</a></dt>
 <dd>Mozilla now provides infallible memory allocators that are guaranteed not to return null. You should read this article to learn how they work and how to explicitly request fallible versus infallible memory allocation.</dd>
</dl>

<h3 id="Other_changes">Other changes</h3>

<ul>
 <li>Most of the resources contained within Firefox have been combined into a single JAR archive, <code>omni.jar</code>, which improves startup performance by reducing I/O. For details, read <a href="/en-US/docs/About_omni.jar">About omni.jar</a>.</li>
 <li>The <code>accessibility.disablecache</code> preference is no longer supported; it was only exposed for debugging purposes and is no longer used.</li>
 <li>Addons whose GUID changes from one version to another can now be updated properly.</li>
 <li>As a side effect of the removal of platform-specific directories in add-on bundles, you can no longer provide different default preferences for each platform.</li>
 <li>By default, <a href="https://blog.mozilla.com/mwu/2010/09/10/extensions-now-installed-packed/">extensions are no longer unpacked when they are installed</a>, but are instead run directly from the XPI file. Extensions can use the <a href="/en-US/docs/Install_Manifests#unpack">unpack</a> property in the <a href="/en-US/docs/Install_Manifests">install manifest</a> to choose the old behavior. Extensions that use binary components, DLLs loaded using <a href="/en-US/docs/js-ctypes">js-ctypes</a>, <a href="/en-US/docs/Web/OpenSearch">search plugins</a>, dictionaries, and window icons must specify that they need to be unpacked. Extensions that <a href="/en-US/docs/XUL_School/Local_Storage#SQLite">create SQLite database</a>, or do copy things from the filesystem relatively to the extension's directory, may also need to change their code.</li>
 <li>You may now include extensions that <a href="/en-US/docs/Mozilla/Developer_guide/Customizing_Firefox#including_extensions_with_your_distribution_of_firefox">automatically get installed at application startup</a> within a customized Firefox.</li>
</ul>

<h2 id="Other_changes_2">Other changes</h2>

<dl>
 <dt>Only the root chrome.manifest file is loaded</dt>
 <dd>Only the root <code>chrome.manifest</code> file is loaded now; if you need secondary manifest files to be loaded, you can use the <a href="/en-US/docs/Chrome_Registration#manifest"><code>manifest</code></a> command in your root <code>chrome.manifest</code> to load them.</dd>
 <dt>Gopher support removed</dt>
 <dd>The Gopher protocol is no longer supported natively. Continued support is available via the <a href="https://addons.mozilla.org/addon/7685/">OverbiteFF</a> extension.</dd>
 <dt><a href="/en-US/docs/The_message_manager">Content process event handling</a></dt>
 <dd>In order to support out-of-process plugins and other multiple-process features, a new API has been introduced to support sending messages across processes.</dd>
 <dt><a href="/en-US/docs/Extensions/Bootstrapped_extensions">Bootstrapped extensions</a></dt>
 <dd>You can now create extensions that can be installed, uninstalled, and upgraded (or downgraded) without requiring a browser restart.</dd>
 <dt>Default plugin removed</dt>
 <dd>The default plugin has been removed. The application plugins folder has also been removed by default, however support for installing plugins via this folder still exists. See {{bug("533891")}}.</dd>
 <dt>Extension Manager replaced by Addon Manager</dt>
 <dd>{{interface("nsIExtensionManager")}} has been replaced by <a href="/en-US/docs/Addons/Add-on_Manager/AddonManager">AddonManager</a>.</dd>
 <dt>Child HWNDs no longer used</dt>
 <dd>Firefox no longer creates child HWNDs for its internal use on Windows. If you've written an extension that uses native code to manipulate these HWNDs, your extension will not work on Firefox 4. You'll need to either stop using HWNDs or wrap your code that relies on HWNDs in an <a href="/en-US/docs/NPAPI">NPAPI</a> plugin. That's a lot of work, so if you can avoid using HWNDs directly, you should.</dd>
 <dt>Gesture changes</dt>
 <dd>The three finger up and down swipe gestures on trackpads have been changed to, by default, open and close Firefox Panorama view (neé TabCandy). To change these back to the previous scroll-to-top and scroll-to-bottom commands, open about:config and set <code>browser.gesture.swipe.down</code> to <code>cmd_scrollBottom</code> and <code>browser.gesture.swipe.up</code> to <code>cmd_scrollTop</code>.</dd>
</dl>

<h2 id="See_also">See also</h2>

<div>{{Firefox_for_developers('3.6')}}</div>