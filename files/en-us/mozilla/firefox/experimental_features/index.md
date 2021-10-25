---
title: Experimental features in Firefox
slug: Mozilla/Firefox/Experimental_features
tags:
  - Experimental
  - Firefox
  - Preferences
  - features
---
<div>{{FirefoxSidebar}}</div>

<p>This page lists Firefox's experimental and partially implemented features, including those for proposed or cutting-edge web platform standards, along with information on the builds in which they are present, whether or not they are activated "by default", and which <em>preference</em> can be used to activate or deactivate them. This allows you to test the features before they are released.</p>

<p>New features appear first in the <a href="https://nightly.mozilla.org/">Firefox Nightly</a> build, where they are often enabled by default. They later propagate though to <a href="https://www.mozilla.org/en-US/firefox/developer/">Firefox Developer Edition</a> and eventually to the release build. Once a feature is enabled by default in a release build it is no longer experimental, and should be removed from the topic.</p>

<p>Experimental features can be enabled or disabled using the <a href="https://support.mozilla.org/en-US/kb/about-config-editor-firefox">Firefox Configuration Editor</a> (enter <code>about:config</code> in the Firefox address bar) by modifying the associated <em>preference</em> listed below.</p>

<div class="note">
  <p><strong>Note:</strong> For editors - when adding features to these tables, please try to include a link to the relevant bug or bugs using the <a href="https://github.com/mdn/yari/blob/main/kumascript/macros/bug.ejs"><code>bug</code></a> macro: <code>\{{bug(<em>bug-number</em>)}}</code>.</p>
</div>

<h2 id="HTML">HTML</h2>

<h3 id="Element_&lt;dialog&gt;">Element: &lt;dialog&gt;</h3>

<p>The HTML {{HTMLElement("dialog")}} element and its associated DOM APIs provide support for HTML-based modal dialog boxes. The current implementation is a little inelegant but is basically functional. (See {{bug(840640)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>53</td>
   <td>Yes</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>53</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>53</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>53</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>dom.dialog_element.enabled</code></td>
  </tr>
 </tbody>
</table>

<h3 id="Global_attribute_inputmode">Global attribute: inputmode</h3>

<p>Our implementation of the <code><a href="/en-US/docs/Web/HTML/Global_attributes/inputmode">inputmode</a></code> global attribute has been updated as per the WHATWG spec ({{bug(1509527)}}), but we still need to make other changes too, like making it available on contenteditable content. (See {{bug(1205133)}} for details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>75</td>
   <td>Yes</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>75</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>75</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>75</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>dom.forms.inputmode</code></th>
  </tr>
 </tbody>
</table>

<h3 id="inert_attribute">inert attribute</h3>

<p>The {{domxref("HTMLElement")}} property {{DOMxRef("HTMLElement.inert")}} is a {{jsxref("Boolean")}}, when present, may make the browser "ignore" the element from assistive technologies, page search and text selection. For more details on the status of this feature see {{bug(1655722)}}.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>81</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>81</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>81</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>81</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>html5.inert.enabled</code></th>
  </tr>
 </tbody>
</table>

<h3 id="Layout_for_input_typesearch">Layout for input type="search"</h3>

<p>Layout for <code>input type="search"</code> has been updated. This causes a search field to have a clear icon once someone starts typing in it, to match other browser implementations. (See {{bug(558594)}} for more details)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>81</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>81</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>81</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>81</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>layout.forms.input-type-search.enabled</code></th>
  </tr>
 </tbody>
</table>

<h2 id="CSS">CSS</h2>

<h3 id="Display_stray_control_characters_in_CSS_as_hex_boxes">Display stray control characters in CSS as hex boxes</h3>

<p>This feature renders control characters (Unicode category Cc) other than <em>tab</em> (<code>U+0009</code>), <em>line feed</em> (<code>U+000A</code>), <em>form feed</em> (<code>U+000C</code>), and <em>carriage return</em> (<code>U+000D</code>) as a hexbox when they are not expected. (See {{bug(1099557)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>43</td>
   <td>Yes</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>43</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>43</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>43</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>layout.css.control-characters.enabled</code> or <code>layout.css.control-characters.visible</code></th>
  </tr>
 </tbody>
</table>


<h3 id="Property_initial-letter">Property: initial-letter</h3>

<p>The {{cssxref("initial-letter")}} CSS property is part of the <a href="https://drafts.csswg.org/css-inline/">CSS Inline Layout</a> specification and allows you to specify how dropped, raised, and sunken initial letters are displayed. (See {{bug(1223880)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>50</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>50</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>50</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>50</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>layout.css.initial-letter.enabled</code></th>
  </tr>
 </tbody>
</table>


<h3 id="Single_numbers_as_aspect_ratio_in_media_queries">Single numbers as aspect ratio in media queries</h3>

<p>Support for using a single {{cssxref("number")}} as a {{cssxref("ratio")}} when specifying the aspect ratio for a <a href="/en-US/docs/Web/CSS/Media_Queries">media query</a>. (See {{bug(1565562)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>70</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>70</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>70</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>70</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>layout.css.aspect-ratio-number.enabled</code></th>
  </tr>
 </tbody>
</table>

<h3 id="Property_backdrop-filter">Property: backdrop-filter</h3>

<p>The {{cssxref("backdrop-filter")}} property applies filter effects to the area behind an element. (See {{bug(1178765)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>70</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>70</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>70</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>70</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>layout.css.backdrop-filter.enabled</code></th>
  </tr>
 </tbody>
</table>

<h3 id="Fit_content_function">The <code>fit-content()</code> function for <code>width</code> and other sizing properties</h3>

<p>The {{cssxref("fit-content()")}} function as it applies to {{cssxref("width")}} and other sizing properties. This function is already well-supported for CSS Grid Layout track sizing. (See {{bug(1312588)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>91</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>91</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>91</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>91</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>layout.css.fit-content-function.enabled</code></th>
  </tr>
 </tbody>
</table>

<h3 id="Grid_Masonry_layout">Grid: Masonry layout</h3>

<p>Adds support for a <a href="/en-US/docs/Web/CSS/CSS_Grid_Layout/Masonry_Layout">masonry-style layout</a> based on grid layout where one axis has a masonry layout and the other has a normal grid layout. This allows developers to easily create gallery style layouts like on Pinterest. See {{bug(1607954)}} for more details.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>77</td>
   <td>Yes</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>77</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>77</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>77</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>layout.css.grid-template-masonry-value.enabled</code></th>
  </tr>
 </tbody>
</table>

<h3 id="Media_feature_prefers-contrast">Media feature: prefers-contrast</h3>

<p>The <code><a href="/en-US/docs/Web/CSS/@media/prefers-contrast">prefers-contrast</a></code> media feature is used to detect whether the user has specified a preference for higher (or lower) contrast in the presentation of web content. Refer to {{bug("1506364")}} for more details.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>80</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>80</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>80</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>80</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2">
    <p><code>layout.css.prefers-contrast.enabled</code></p>
   </th>
  </tr>
 </tbody>
</table>

<h3 id="Property_math-style">Property: math-style</h3>

<p>The {{cssxref("math-style")}} property indicates whether MathML equations should render with normal or compact height. (See {{bug(1665975)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>83</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>83</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>83</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>83</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>layout.css.math-style.enabled</code></th>
  </tr>
 </tbody>
</table>

<h2 id="SVG">SVG</h2>

<h3 id="Presentation_attribute">Presentation attribute: d</h3>

<p>The SVG {{SVGAttr('d')}} attribute, used to define a path to be drawn, is now a <a href="/en-US/docs/Web/SVG/Attribute/Presentation">presentation attribute</a>. It can be used as a property in CSS and accepts the values <a href="/en-US/docs/Web/CSS/path()">path()</a> or <code>none</code>. (See {{bug(1340422)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>91</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>91</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>91</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>91</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>layout.css.d-property.enabled</code></th>
  </tr>
 </tbody>
</table>


<h2 id="JavaScript">JavaScript</h2>

<h2 id="APIs">APIs</h2>

<h3 id="Graphics_Canvas_WebGL_and_WebGPU">Graphics: Canvas, WebGL, and WebGPU</h3>

<h4 id="Interface_OffscreenCanvas">Interface: OffscreenCanvas</h4>

<p>The {{domxref("OffscreenCanvas")}} interface provides a canvas that can be rendered offscreen. It is available in both the window and <a href="/en-US/docs/Web/API/Web_Workers_API">worker</a> contexts. (See {{bug(1390089)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>44</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>44</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>44</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>44</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>gfx.offscreencanvas.enabled</code></th>
  </tr>
 </tbody>
</table>

<h4 id="Hit_regions">Hit regions</h4>

<p>Whether the mouse coordinates are within a particular area on the canvas is a common problem to solve. The hit region API allows you define an area of your canvas and provides another possibility to expose interactive content on a canvas to accessibility tools.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>30</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>30</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>30</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>30</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>canvas.hitregions.enabled</code></th>
  </tr>
 </tbody>
</table>

<h4 id="WebGL_Draft_extensions">WebGL: Draft extensions</h4>

<p>When this preference is enabled, any WebGL extensions currently in "draft" status which are being tested are enabled for use. Currently, there are no WebGL extensions being tested by Firefox.</p>

<h4 id="WebGPU_API">WebGPU API</h4>

<p>This new API provides low-level support for performing computation and graphics rendering using the {{interwiki("wikipedia", "Graphics Processing Unit")}} (GPU) of the user's device or computer. The <a href="https://gpuweb.github.io/gpuweb/">specification</a> is still a work-in-progress. See {{bug(1602129)}} for our progress on this API.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>73</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>73</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>73</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>73</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>dom.webgpu.enabled</code></th>
  </tr>
 </tbody>
</table>

<h3 id="javascript_dom_api">Audio Output API</h3>

<h4 id="">MediaDevices.selectAudioOutput()</h4>

<p>{{domxref("MediaDevices.selectAudioOutput()")}} displays a prompt from which users can select their desired audio output. See {{bug(1699026)}}.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>88</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>88</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>88</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>88</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>media.setsinkid.enabled</code></th>
  </tr>
 </tbody>
</table>

<h3 id="HTML_DOM_API">HTML DOM API</h3>

<h4 id="HTMLMediaElement_method_setSinkId">HTMLMediaElement method: setSinkId()</h4>

<p>{{domxref("HTMLMediaElement.setSinkId()")}} allows you to set the sink ID of an audio output device on an {{domxref("HTMLMediaElement")}}, thereby changing where the audio is being output. See {{bug(934425)}} for more details.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>64</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>64</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>64</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>64</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>media.setsinkid.enabled</code></th>
  </tr>
 </tbody>
</table>

<h4 id="HTMLMediaElement_properties_audioTracks_and_videoTracks">HTMLMediaElement properties: audioTracks and videoTracks</h4>

<p>Enabling this feature adds the {{domxref("HTMLMediaElement.audioTracks")}} and {{domxref("HTMLMediaElement.videoTracks")}} properties to all HTML media elements. However, because Firefox doesn't currently support multiple audio and video tracks, the most common use cases for these properties don't work, so they're both disabled by default. See {{bug(1057233)}} for more details.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>33</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>33</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>33</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>33</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>media.track.enabled</code></th>
  </tr>
 </tbody>
</table>

<h3 id="DOM">DOM</h3>

<h4 id="clipboarditem">ClipboardItem</h4>

<p>The {{domxref('ClipboardItem')}} interface of the {{domxref('Clipboard API')}} is now supported and {{domxref('Clipboard.write()')}} accepts a sequence of {{domxref('ClipboardItem','clipboard items')}} instead of the previously implemented {{domxref('DataTransfer','dataTransfer object')}}. It is available behind the pref <code>dom.events.asyncClipboard.clipboardItem</code> which was previously <code>dom.events.asyncClipboard.dataTransfer</code>.  See {{bug('1619947')}} for more details.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>87</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>87</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>87</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>87</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>dom.events.asyncClipboard.clipboardItem</code></th>
  </tr>
 </tbody>
</table>

<h4 id="clipboardread">ClipboardRead</h4>

<p> The <a href="/en-US/docs/Web/API/Clipboard/read">Clipboard.read()</a> method of the {{domxref('Clipboard')}} interface is also now available under the <code>dom.events.asyncClipboard.read</code> preference,  when previously it was under <code>dom.events.asyncClipboard.clipboardItem</code>. (See ({{bug(1701512)}}) for more details.) </p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>90</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>90</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>90</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>90</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>dom.events.asyncClipboard.read</code> </th>
  </tr>
 </tbody>
</table>

<h4 id="HTML_Sanitizer_API">HTML Sanitizer API</h4>

<p>The {{domxref('HTML Sanitizer API')}} allow developers to take untrusted strings of HTML and sanitize them for safe insertion into a document’s DOM. Default elements within each configuration property (those to be sanitized) are still under consideration. Due to this the config parameter has not been implemented (see {{domxref('Sanitizer.sanitizer()', 'the constructor')}}) for more information. See {{bug('1673309')}} for more details.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>84</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>84</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>84</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>84</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>dom.security.sanitizer.enabled</code></th>
  </tr>
 </tbody>
</table>

<h4 id="Document_property_autoplayPolicy">Document property: autoplayPolicy</h4>

<p>The {{domxref("document")}} property {{domxref("Document.autoplayPolicy", "autoplayPolicy")}} returns a string indicating how the browser handles requests to automatically play media (either using the {{domxref("HTMLMediaElement.autoplay", "autoplay")}} property on a media element or by attempting to trigger playback from JavaScript code. The spec for this API is still being written. The value changes over time depending on what the user is doing, their preferences, and the state of the browser in general. Potential values include <code>allowed</code> (autoplay is currently permitted), <code>allowed-muted</code> (autoplay is allowed but only with no—or muted—audio), and <code>disallowed</code> (autoplay is not allowed at this time). See {{bug(1506289)}} for more details.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>66</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>66</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>66</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>66</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>dom.media.autoplay.autoplay-policy-api</code></th>
  </tr>
 </tbody>
</table>

<h4 id="GeometryUtils_methods_convertPointFromNode_convertRectFromNode_and_convertQuadFromNode">GeometryUtils methods: convertPointFromNode(), convertRectFromNode(), and convertQuadFromNode()</h4>

<p>The <code>GeometryUtils</code> methods <code>convertPointFromNode()</code>, <code>convertRectFromNode()</code>, and <code></code>convertQuadFromNode()</code> map the given point, rectangle, or quadruple from the {{domxref("Node")}} on which they're called to another node. (See {{bug(918189)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>31</td>
   <td>Yes</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>31</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>31</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>31</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>layout.css.getBoxQuads.enabled</code></th>
  </tr>
 </tbody>
</table>

<h4 id="GeometryUtils_method_getBoxQuads">GeometryUtils method: getBoxQuads()</h4>

<p>The <code>GeometryUtils</code> method <code>getBoxQuads()</code> returns the CSS boxes for a {{domxref("Node")}} relative to any other node or viewport. (See {{bug(917755)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>31</td>
   <td>Yes</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>31</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>31</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>31</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>layout.css.convertFromNode.enable</code></th>
  </tr>
 </tbody>
</table>

<h3 id="Payment_Request_API">Payment Request API</h3>

<h4 id="Primary_payment_handling">Primary payment handling</h4>

<p>The <a href="/en-US/docs/Web/API/Payment_Request_API">Payment Request API</a> provides support for handling web-based payments within web content or apps. Due to a bug that came up during testing of the user interface, we have decided to postpone shipping this API while discussions over potential changes to the API are held. Work is ongoing. (See {{bug(1318984)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>55</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>55</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>55</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>55</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>dom.payments.request.enabled</code> and<br>
    <code>dom.payments.request.supportedRegions</code></th>
  </tr>
 </tbody>
</table>

<h3 id="Constructable_stylesheets">Constructable stylesheets</h3>

<p>The addition of a constructor to the {{domxref("CSSStyleSheet")}} interface as well as a variety of related changes makes it possible to directly create new stylesheets without having to add the sheet to the HTML. This makes it much easier to create reusable stylesheets for use with <a href="/en-US/docs/Web/Web_Components/Using_shadow_DOM">Shadow DOM</a>. Our implementation is not yet complete; see {{bug(1520690)}} for more details.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>73</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>73</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>73</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>73</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>layout.css.constructable-stylesheets.enabled</code></th>
  </tr>
 </tbody>
</table>

<h3 id="webshare_api">WebShare API</h3>

<p>The <a href="/en-US/docs/Web/API/Web_Share_API">Web Share API</a> allows sharing of files, URLs and other data from a site.
  Note that Firefox implements {{domxref("Navigator.share()")}} but not {{domxref("Navigator.canShare()")}} ({{bug(1666203)}}).</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version changed</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>71</td>
   <td>No (default). Yes (Windows from version 92)</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>71</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>71</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>71</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>dom.webshare.enabled</code></th>
  </tr>
 </tbody>
</table>



<h3 id="WebRTC_and_media">WebRTC and media</h3>

<p>The following experimental features include those found in the <a href="/en-US/docs/Web/API/WebRTC_API">WebRTC API</a>, the <a href="/en-US/docs/Web/API/Web_Audio_API">Web Audio API</a>, the <a href="/en-US/docs/Web/API/Media_Source_Extensions_API">Media Source Extensions API</a>, the <a href="/en-US/docs/Web/API/Encrypted_Media_Extensions_API">Encrypted Media Extensions API</a>, and the <a href="/en-US/docs/Web/API/Media_Streams_API">Media Capture and Streams API</a>.</p>

<h4 id="Asynchronous_SourceBuffer_add_and_remove">Asynchronous SourceBuffer add and remove</h4>

<p>This adds the promise-based methods {{domxref("SourceBuffer.appendBufferAsync", "appendBufferAsync()")}} and {{domxref("SourceBuffer.removeAsync", "removeAsync()")}} for adding and removing media source buffers to the {{domxref("SourceBuffer")}} interface. See {{bug(1280613)}} and {{bug(778617)}} for more information.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>62</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>62</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>62</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>62</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>media.mediasource.experimental.enabled</code></th>
  </tr>
 </tbody>
</table>


<h4 id="AVIF_compliance_strictness">AVIF compliance strictness</h4>

<p>The <code>image.avif.compliance_strictness</code> preference can be used to control the <em>strictness</em> applied when processing <a href="/en-US/docs/Web/Media/Formats/Image_types#avif_image">AVIF</a> images.
  This allows Firefox users to display images that render on some other browsers, even if they are not strictly compliant.</p>

<p>Permitted values are:</p>
<ul>
  <li><code>0</code>: Accept images with specification violations in both recommendations ("should" language) and requirements ("shall" language), provided they can be safely or unambigiously intepretted.</li>
  <li><code>1</code> (default): Reject violations of requirements, but allow violations of recommendations.</li>
  <li><code>2</code>: Strict. Reject any violations in requirements or recommendations.</li>
</ul>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Default value</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>92</td>
   <td>1</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>92</td>
   <td>1</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>92</td>
   <td>1</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>92</td>
   <td>1</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>image.avif.compliance_strictness</code></th>
  </tr>
 </tbody>
</table>

<h4 id="AV1_support_for_Firefox_on_Android">AV1 support for Firefox on Android</h4>

<p>This feature allows Firefox on Android to use <a href="/en-US/docs/Web/Media/Formats/Video_codecs#av1">AV1 format media</a>. This feature is available in nightly builds effective in Firefox for Android 81 or later. It is enabled by default.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>81</td>
   <td>Yes</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>—</td>
   <td>—</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>—</td>
   <td>—</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>—</td>
   <td>—</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2">—</th>
  </tr>
 </tbody>
</table>

<h4 id="JPEG_XL_support">JPEG XL support</h4>

<p>With this feature enabled, Firefox supports <a href="https://jpeg.org/jpegxl/">JPEG XL</a> images, see {{bug(1539075)}} for more details. This feature is available in nightly builds effective in Firefox 90 or later.</p>

<table>
  <thead>
   <tr>
    <th>Release channel</th>
    <th>Version added</th>
    <th>Enabled by default?</th>
   </tr>
  </thead>
  <tbody>
   <tr>
    <th>Nightly</th>
    <td>90</td>
    <td>No</td>
   </tr>
   <tr>
    <th>Developer Edition</th>
    <td>90</td>
    <td>No</td>
   </tr>
   <tr>
    <th>Beta</th>
    <td>90</td>
    <td>No</td>
   </tr>
   <tr>
    <th>Release</th>
    <td>—</td>
    <td>—</td>
   </tr>
   <tr>
    <th>Preference name</th>
    <td colspan="2">image.jxl.enabled</th>
   </tr>
  </tbody>
 </table>

<h2 id="Security_and_privacy">Security and privacy</h2>

<h4 id="Block_plain_text_requests_from_Flash_on_encrypted_pages">Block plain text requests from Flash on encrypted pages</h4>

<p>In order to help mitigate man-in-the-middle (MitM) attacks caused by Flash content on encrypted pages, a preference has been added to treat <code>OBJECT_SUBREQUEST</code>s as active content. See {{bug(1190623)}} for more details.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>59</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>59</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>59</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>59</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>security.mixed_content.block_object_subrequest</code></th>
  </tr>
 </tbody>
</table>

<h4 id="Insecure_page_labeling">Insecure page labeling</h4>

<p>These two preferences add a "Not secure" text label in the address bar next to the traditional lock icon when a page is loaded insecurely (that is, using {{Glossary("HTTP")}} rather than {{Glossary("HTTPS")}}). See {{bug(1335970)}} for more details.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>60</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>60</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>60</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>60</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>security.insecure_connection_text.enabled</code> for normal browsing mode; <code>security.insecure_connection_text.pbmode.enabled</code> for private browsing mode</th>
  </tr>
 </tbody>
</table>

<h4 id="Upgrading_mixed_display_content">Upgrading mixed display content</h4>

<p>When enabled, this preference causes Firefox to automatically upgrade requests for media content from HTTP to HTTPS on secure pages. The intent is to prevent mixed-content conditions in which some content is loaded securely while other content is insecure. If the upgrade fails (because the media's host doesn't support HTTPS), the media is not loaded. (See {{bug(1435733)}} for more details.)</p>

<p>This also changes the console warning; if the upgrade succeeds, the message indicates that the request was upgraded, instead of showing a warning.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>84</td>
   <td>Yes</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>60</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>60</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>60</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>security.mixed_content.upgrade_display_content</code></th>
  </tr>
 </tbody>
</table>


<h4 id="Feature_policy">Feature policy</h4>

<p><a href="/en-US/docs/Web/HTTP/Feature_Policy">Feature Policy</a> allows web developers to selectively enable, disable, and modify the behavior of certain features and APIs in the browser. It is similar to CSP but controls features instead of security behavior.</p>

<div class="note">
  <p><strong>Note:</strong> The <code>Feature-Policy</code> header has now been renamed to <code>Permissions-Policy</code> in the spec, and this article will eventually be updated to reflect that change.</p>
</div>

<table>
  <thead>
   <tr>
    <th>Release channel</th>
    <th>Version added</th>
    <th>Enabled by default?</th>
   </tr>
  </thead>
  <tbody>
   <tr>
    <th>Nightly</th>
    <td>65</td>
    <td>No</td>
   </tr>
   <tr>
    <th>Developer Edition</th>
    <td>65</td>
    <td>No</td>
   </tr>
   <tr>
    <th>Beta</th>
    <td>65</td>
    <td>No</td>
   </tr>
   <tr>
    <th>Release</th>
    <td>65</td>
    <td>No</td>
   </tr>
   <tr>
    <th>Preference name</th>
    <td colspan="2"><code>dom.security.featurePolicy.header.enabled</code></th>
   </tr>
  </tbody>
 </table>

<h2 id="Developer_tools">Developer tools</h2>

<p>Mozilla's developer tools are constantly evolving. We experiment with new ideas, add new features, and test them on the Nightly and Developer Edition channels before letting them go through to beta and release. The features below are the current crop of experimental developer tool features.</p>

<h4 id="Execution_context_selector">Execution context selector</h4>

<p>This feature displays a button on the console's command line that lets you change the context in which the expression you enter will be executed. (See {{bug(1605154)}} and {{bug(1605153)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>75</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>75</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>75</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>75</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>devtools.webconsole.input.context</code></th>
  </tr>
 </tbody>
</table>

<h4 id="Mobile_gesture_support_in_Responsive_Design_Mode">Mobile gesture support in Responsive Design Mode</h4>

<p>Mouse gestures are used to simulate mobile gestures like swiping/scrolling, double-tap and pinch-zooming and long-press to select/open the context menu. (See {{bug(1621781)}}, {{bug(1245183)}}, and {{bug(1401304)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>76<sup>[1]</sup></td>
   <td>Yes</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>76<sup>[1]</sup></td>
   <td>Yes</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>76<sup>[1]</sup></td>
   <td>Yes</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>76<sup>[1]</sup></td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2">n/a</th>
  </tr>
 </tbody>
</table>

<p>[1] Support for zooming using the double-tap gesture was added in Firefox 76. The other gestures were added for Firefox 79.</p>

<h4 id="Server-sent_events_in_Network_Monitor">Server-sent events in Network Monitor</h4>

<p>The Network Monitor displays information for <a href="/en-US/docs/Web/API/Server-sent_events">server-sent</a> events. (See {{bug(1405706)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>80</td>
   <td>Yes</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>80</td>
   <td>Yes</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>80</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>80</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>devtools.netmonitor.features.serverSentEvents</code></th>
  </tr>
 </tbody>
</table>

<h4 id="CSS_browser_compatibility_tooltips">CSS browser compatibility tooltips</h4>

<p>The CSS Rules View can display browser compatibility tooltips next to any CSS properties that have known issues. For more information see: <a href="/en-US/docs/Tools/Page_Inspector/How_to/Examine_and_edit_HTML#browser_compat_warnings">Examine and edit HTML &gt; Browser Compat Warnings</a>.</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>81</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>81</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>81</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>81</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>devtools.inspector.ruleview.inline-compatibility-warning.enabled</code></th>
  </tr>
 </tbody>
</table>

<h2 id="UI">UI</h2>

<h4 id="Desktop_zooming">Desktop zooming</h4>

<p>This feature lets you enable smooth pinch zooming on desktop computers without requiring layout reflows, just like mobile devices do. (See {{bug(1245183)}} and {{bug(1620055)}} for more details.)</p>

<table>
 <thead>
  <tr>
   <th>Release channel</th>
   <th>Version added</th>
   <th>Enabled by default?</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <th>Nightly</th>
   <td>42</td>
   <td>Yes</td>
  </tr>
  <tr>
   <th>Developer Edition</th>
   <td>42</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Beta</th>
   <td>42</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Release</th>
   <td>42</td>
   <td>No</td>
  </tr>
  <tr>
   <th>Preference name</th>
   <td colspan="2"><code>apz.allow_zooming</code> and (on Windows) <code>apz.windows.use_direct_manipulation</code></th>
  </tr>
 </tbody>
</table>

<h2 id="See_also">See also</h2>

<ul>
 <li><a href="/en-US/docs/Mozilla/Firefox/Releases">Firefox developer release notes</a></li>
 <li><a href="https://nightly.mozilla.org/">Firefox Nightly</a></li>
 <li><a href="https://www.mozilla.org/en-US/firefox/developer/">Firefox Developer Edition</a></li>
</ul>