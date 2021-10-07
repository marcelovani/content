---
title: TypeScript support in Svelte
slug: Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_TypeScript
tags:
  - Beginner
  - Frameworks
  - JavaScript
  - Learn
  - Svelte
  - Typescript
  - client-side
---
<div>{{LearnSidebar}}<br>
{{PreviousMenuNext("Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_stores","Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_deployment_next", "Learn/Tools_and_testing/Client-side_JavaScript_frameworks")}}</div>

<p>In the last article we learned about Svelte stores and even implemented our own custom store to persist the app's information to Web Storage. We also had a look at using the transition directive to implement animations on DOM elements in Svelte.</p>

<p>We will now learn how to use TypeScript in Svelte applications. First we'll learn what TypeScript is and what benefits it can bring us. Then we'll see how to configure our project to work with TypeScript files. Finally we will go over our app and see what modifications we have to make to fully take advantage of TypeScript features.</p>

<table>
	<tbody>
		<tr>
			<th scope="row">Prerequisites:</th>
			<td>
			<p>At minimum, it is recommended that you are familiar with the core <a href="/en-US/docs/Learn/HTML">HTML</a>, <a href="/en-US/docs/Learn/CSS">CSS</a>, and <a href="/en-US/docs/Learn/JavaScript">JavaScript</a> languages, and have knowledge of the <a href="/en-US/docs/Learn/Tools_and_testing/Understanding_client-side_tools/Command_line">terminal/command line</a>.</p>

			<p>You'll need a terminal with node + npm installed to compile and build your app.</p>
			</td>
		</tr>
		<tr>
			<th scope="row">Objective:</th>
			<td>Learn how to configure and use TypeScript when developing Svelte applications.</td>
		</tr>
	</tbody>
</table>

<p>Note that our application is fully functional and porting it to TypeScript is completely optional. There are different opinions about it, and in this chapter we will talk briefly about the pros and cons of using TypeScript. Even if you are not planning to adopt it, this article will be useful for allowing you to learn what it has to offer and help you make your own decision. If you are not interested at all in TypeScript, you can skip to the next chapter, where we will look at different options for deploying our Svelte applications, further resources, and more.</p>

<h2 id="Code_along_with_us">Code along with us</h2>

<h3 id="Git">Git</h3>

<p>Clone the github repo (if you haven't already done it) with:</p>

<pre class="brush: bash">git clone https://github.com/opensas/mdn-svelte-tutorial.git</pre>

<p>Then to get to the current app state, run</p>

<pre class="brush: bash">cd mdn-svelte-tutorial/07-typescript-support</pre>

<p>Or directly download the folder's content:</p>

<pre class="brush: bash">npx degit opensas/mdn-svelte-tutorial/07-typescript-support</pre>

<p>Remember to run <code>npm install &amp;&amp; npm run dev</code> to start your app in development mode.</p>

<h3 id="REPL">REPL</h3>

<p>Unfortunately, <a href="https://github.com/sveltejs/svelte-repl/issues/130">TypeScript support is not yet available in the REPL</a>.</p>

<h2 id="TypeScript_optional_static_typing_for_JavaScript">TypeScript: optional static typing for JavaScript</h2>

<p><a href="https://www.typescriptlang.org/">TypeScript</a> is a superset of JavaScript that provides features such as optional static typing, classes, interfaces, and generics. The goal of TypeScript is to help catch mistakes early through its type system and make JavaScript development more efficient. One of the big benefits is enabling IDEs to provide a richer environment for spotting common errors as you type the code.</p>

<p>Best of all, JavaScript code is valid TypeScript code; TypeScript is a superset of JavaScript. You can rename most of your <code>.js</code> files to <code>.ts</code> files and they will just work.</p>

<p>Our TypeScript code will be able to run everywhere JavaScript can run. How is that possible? TypeScript "transpiles" our code to vainilla JavaScript. That means that it parses TypeScript code and produces the equivalent vanilla JavaScript code for browsers to run.</p>

<div class="notecard note">
<p><strong>Note:</strong> If you are curious about how TypeScript transpiles our code to JavaScript you can have a look at the <a href="https://www.typescriptlang.org/play/?target=1&amp;e=4#example/hello-world">TypeScript Playground</a>.</p>
</div>

<p>First class TypeScript support has been Svelte's most requested feature for quite some time. Thanks to the hard work of the Svelte team, together with many contributors, we have an <a href="https://svelte.dev/blog/svelte-and-typescript">official solution</a> ready to be put to the test. In this section we'll show you how to setup a Svelte project With TypeScript support to give it a try.</p>

<h2 id="Why_TypeScript">Why TypeScript?</h2>

<p>TypeScript's main advantages are:</p>

<ul>
	<li>Early spotted bugs: The compiler checks types at compile time and provides error reporting.</li>
	<li>Readability: Static typing gives the code more structure, making it self-documenting and more readable.</li>
	<li>Rich IDE support: Type information allows code editors and IDEs to offer features like code navigation, autocompletion, and smarter hints.</li>
	<li>Safer refactoring: Types allows IDEs to know more about your code, and assist you while refactoring large portions of your code base.</li>
	<li>Type inference: Enables you to take advantage of many TypeScript features even without declaring variable types.</li>
	<li>Availability of new and future JavaScript features: TypeScript transpiles many recent <a href="http://es6-features.org/">ES6 features</a> to plain old-school JavaScript, allowing you to use them even on user-agents that don't support them natively yet.</li>
</ul>

<p>TypeScript also has some disadvantages:</p>

<ul>
	<li>Not true static typing: Types are only checked at compile time, and they are removed from the generated code.</li>
	<li>Steep learning curve: Even though TypeScript is a superset of JavaScript and not a completely new language, there is a considerable learning curve, especially if you have no experience at all with static languages like Java or C#.</li>
	<li>More code: You have to write and maintain more code.</li>
	<li>No replacement for automatic tests: Even though types might help you catch several bugs, TypeScript is not a true replacement for a comprehensive suite of automated tests.</li>
	<li>Boiler plate code: Working with types, classes, interfaces, and generics can lead to over-engineered code bases.</li>
</ul>

<p>There seems to be a broad consensus that TypeScript is particularly well suited for large-scale projects, with many developers working on the same code base. And it is indeed being used by several large-scale projects, like Angular 2, Vue 3, Ionic, Visual Studio Code, Jest and even the Svelte compiler. Nevertheless, some developers prefer to use it even on small projects like the one we are developing.</p>

<p>In the end, it's your decision. In the following sections we hope to give you more evidence to make up your mind about it.</p>

<h2 id="Creating_a_Svelte_TypeScript_project_from_scratch">Creating a Svelte TypeScript project from scratch</h2>

<p>You can start a new Svelte TypeScript project using the <a href="https://github.com/sveltejs/template">standard template</a>. All you have to do is run the following terminal commands (run them somewhere where you are storing your Svelte test projects — it creates a new directory):</p>

<pre class="brush: bash">npx degit sveltejs/template svelte-typescript-app

cd svelte-typescript-app

node scripts/setupTypeScript.js
</pre>

<p>This creates a starter project that includes TypeScript support, which you can then modify as you wish.</p>

<p>Then you'll have to tell npm to download dependencies and start the project in development mode, like we usually do:</p>

<pre class="brush: bash">npm install

npm run dev</pre>

<h2 id="Adding_TypeScript_support_to_an_existing_Svelte_Project">Adding TypeScript support to an existing Svelte Project</h2>

<p>To add TypeScript support to an existing Svelte project you can <a href="https://svelte.dev/blog/svelte-and-typescript#Adding_TypeScript_to_an_existing_project">follow these instructions</a>. Alternatively, you can download the <code><a href="https://github.com/sveltejs/template/blob/master/scripts/setupTypeScript.js">setupTypeScript.js</a></code> file to a <code>scripts</code> folder inside your project's root folder, and then run <code>node scripts/setupTypeScript.js</code>.</p>

<p>You can even use <code>degit</code> to download the script. That's what we will do to start porting our application to TypeScript.</p>

<div class="notecard note">
<p><strong>Note:</strong> Remember that you can run <code>npx degit opensas/mdn-svelte-tutorial/07-typescript-support svelte-todo-typescript</code> to get the complete to-do list application in JavaScript before you start porting it to TypeScript.</p>
</div>

<p>Go to the root directory of the project and enter these commands:</p>

<pre class="brush: bash">npx degit sveltejs/template/scripts scripts       # download script file to a scripts folder

node scripts/setupTypeScript.js                   # run it
Converted to TypeScript.</pre>

<p>You will need to re-run your dependency manager to get started.</p>

<pre class="brush: bash">npm install                                       # download new dependencies

npm run dev                                       # start the app in development mode</pre>

<p>These instructions apply to any Svelte project you'd like to convert to TypeScript. Just take into account that the Svelte community is constantly improving Svelte TypeScript support, so you should run <code>npm update</code> regularly to take advantage of the latest changes.</p>

<div class="notecard note">
<p><strong>Note:</strong> if you find any trouble working with TypeScript inside a Svelte application, have a look at this <a href="https://github.com/sveltejs/language-tools/blob/master/docs/preprocessors/typescript.md#troubleshooting--faq">troubleshooting/FAQ section about TypeScript support</a>.</p>
</div>

<p>As we said before, TypeScript is a superset of JavaScript, so your application will run without modifications. Currently you will be running a regular JavaScript application with TypeScript support enabled, without taking advantage of any of the features that TypeScript provides. You can now start adding types progressively.</p>

<p>Once you have TypeScript configured, you can start using it from a Svelte component by just adding a <code>&lt;script lang='ts'&gt;</code> at the beginning of the script section. To use it from regular JavaScript files, just change the file extension from <code>.js</code> to <code>.ts</code>. You'll also have to update any corresponding import statements (don't include the <code>.ts</code> in your <code>import</code> statements; TypeScript chose to omit the extensions).</p>

<div class="notecard note">
<p><strong>Note:</strong> Using TypeScript in component markup sections is <a href="https://github.com/sveltejs/svelte/issues/4701">not supported yet</a>. You'll have to use JavaScript from the markup, and TypeScript in the <code>&lt;script lang='ts'&gt;</code> section.</p>
</div>

<h2 id="Improved_developer_experience_with_TypeScript">Improved developer experience with TypeScript</h2>

<p>TypeScript provides code editors and IDEs with lots of information to allow them to deliver a friendlier development experience.</p>

<p>We'll use <a href="https://code.visualstudio.com/">Visual Studio Code</a> to do a quick test and see how we can get autocompletion hints and type-checking as we're writing components.</p>

<div class="notecard note">
<p><strong>Note:</strong> If you don't wish to use VS Code, we also provide instructions for using TypeScript error checking from the terminal instead, slightly later on.</p>
</div>

<p>There is work in progress to support TypeScript in Svelte projects in several code editors; the most complete support so far is available in the <a href="https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode">Svelte for VS Code extension</a>, which is developed and maintained by the Svelte team. This extension offers type checking, inspecting, refactoring, intellisense, hover-information, auto-completion, and other features. This kind of developer assistance is another good reason to start using TypeScript in your projects.</p>

<div class="notecard note">
<p><strong>Note:</strong> Make sure you are using <a href="https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode">Svelte for VS Code</a> and NOT the old "Svelte" by James Birtles, which has been discontinued. In case you have it installed, you should uninstall it and install the official Svelte extension instead.</p>
</div>

<p>Anyway, assuming you are inside the VS Code application, from the root of your project's folder, type <code>code .</code> (the trailing dot tells VS code to open the current folder) to open the code editor. VS Code will tell you that there are recommended extensions to install.</p>

<p><img alt="dialog box saying this workspace has extension recommendations, with options to install or show a list" src="01-vscode-extension-recommendations.png"></p>

<p>Clicking <em>Install all</em> will install Svelte for VS Code.</p>

<p><img alt="svelte for vs code extension information" src="02-svelte-for-vscode.png"></p>

<p>We can also see that the <code>setupTypeScript.js</code> file made a couple of changes to our project. The <code>main.js</code> file has been renamed to <code>main.ts</code>, which means that VS Code can provide hover-information on our svelte components:</p>

<p><img alt='vs code screenshot showing that when you add type="ts" to a component, it gives you three dot alert hints' src="03-vscode-hints-in-main-ts.png"></p>

<p>We also get type-checking for free. If we pass an unknown property in the options parameter of the <code>App</code> constructor (for example a typo like <code>traget</code> instead of <code>target</code>) TypeScript will complain:</p>

<p><img alt="type checking in vs code - App object has been given an unknown property target" src="04-vscode-type-checking-in-main-ts.png"></p>

<p>In the <code>App.svelte</code> component, the <code>setupTypeScript.js</code> script has added the <code>lang="ts"</code> attribute to the <code>&lt;script&gt;</code> tag. Moreover, thanks to type inference, in many cases we won't even need to specify types to get code assistance. For example, if you start adding an <code>ms</code> property to the <code>Alert</code> component call, TypeScript will infer from the default value that the <code>ms</code> property should be a number:</p>

<p><img alt="vs code type inference and code hinting - ms variable should be a number" src="05-vscode-type-inference-and-code-assistance.png"></p>

<p>And if you pass something that is not a number it will complain about it:</p>

<p><img alt="type checking in vs code - App object has been given an unknown property target" src="06-vscode-type-checking-in-components.png"></p>

<p>The application template has a <code>validate</code> script configured that runs <code>svelte-check</code> against your code. This package allows you to detect errors and warnings normally displayed by a code editor from the command line, which makes it pretty useful for running it in a continuous integration (CI) pipeline. Just run <code>npm run validate</code> to check for unused CSS, and return A11y hints and TypeScript compile errors.</p>

<p>In this case, if you run <code>npm run validate</code> (either in the VS Code console or terminal) you will get the following error:</p>

<p><img alt="validate command being run inside vs code showing type error, ms variable should be assigned a number" src="07-vscode-svelte-check.png"></p>

<p>Even better, if you run it from the VS Code integrated terminal (you can open it with the <kbd>Ctrl</kbd> + <kbd>`</kbd> keyboard shortcut), <kbd>Cmd</kbd>/<kbd>Ctrl</kbd> + clicking on the file name will take you to the line containing the error.</p>

<p>You can also run the <code>validate</code> script in watch mode with <code>npm run validate -- --watch</code>. In this case, the script will execute whenever you change any file. If you are running this in your regular terminal, you are advised to keep it running in the background in a separate terminal window of its own so that it can keep reporting errors but won't interfere with other terminal usage.</p>

<h2 id="Creating_a_custom_type">Creating a custom type</h2>

<p>TypeScript supports structural typing. Structural typing is a way of relating types based solely on their members, even if you do not explicitly define the type.</p>

<p>We'll define a <code>TodoType</code> type to see how TypeScript enforces that anything passed to a component expecting a <code>TodoType</code> will be structurally compatible with it.</p>

<ol>
	<li>
	<p>Inside the <code>src</code> folder create a <code>types</code> folder.</p>
	</li>
	<li>
	<p>Add a <code>todo.type.ts</code> file inside it.</p>
	</li>
	<li>
	<p>Give <code>todo.type.ts</code> the following content:</p>

	<pre class="brush: js">export type TodoType = {
  id: number
  name: string
  completed: boolean
}</pre>

	<div class="notecard note">
	<p><strong>Note:</strong> The Svelte template uses <a href="https://github.com/sveltejs/svelte-preprocess">svelte-preprocess</a> 4.0.0 to support TypeScript. From that version onward you have to use <code>export</code>/<code>import</code> type syntax to import types and interfaces. Check <a href="https://github.com/sveltejs/language-tools/blob/master/docs/preprocessors/typescript.md#how-do-i-import-interfaces-into-my-svelte-components-i-get-errors-after-transpilation">this section of the troubleshooting guide</a> for more information.</p>
	</div>
	</li>
	<li>
	<p>Now we'll use <code>TodoType</code> from our <code>Todo.svelte</code> component. First add the <code>lang="ts"</code> to our <code>&lt;script&gt;</code> tag.</p>
	</li>
	<li>
	<p>Let's <code>import</code> the type and use it to declare the <code>todo</code> property. Replace the <code>export let todo</code> line with the following:</p>

	<pre class="brush: js">import type { TodoType } from '../types/todo.type'

export let todo: TodoType</pre>

	<div class="notecard note">
	<p><strong>Note:</strong> Another reminder — When importing a <code>.ts</code> file you have to omit the extension. Check the <a href="https://www.typescriptlang.org/docs/handbook/modules.html#import"><code>import</code> section</a> of the TypeScript manual for more information.</p>
	</div>
	</li>
	<li>
	<p>Now from <code>Todos.svelte</code>, we will instantiate a Todo component with a literal object as its parameter before the call to the <code>MoreActions</code> component, like this:</p>

	<pre class="brush: html">&lt;hr /&gt;

&lt;Todo todo={ { name: 'a new task with no id!', completed: false } } /&gt;

&lt;!-- MoreActions --&gt;
&lt;MoreActions {todos}</pre>
	</li>
	<li>
	<p>Add the <code>lang='ts'</code> to the <code>&lt;script&gt;</code> tag of the <code>Todos.svelte</code> component, so that it knows to use the type checking we have specified.</p>

	<p>We will get the following error:</p>

	<p><img alt="type error in vscode, Todo Type object requires an id property." src="08-vscode-structural-typing.png"></p>
	</li>
</ol>

<p>By now you should get an idea about the kind of assistance we can get from TypeScript when building Svelte projects.</p>

<p>Now we will undo these changes in order to start porting our application to TypeScript, so we won't be bothered with all the validate warnings.</p>

<ol>
	<li>Remove the flawed todo and the <code>lang='ts'</code> attribute from the <code>Todos.svelte</code> file.</li>
	<li>Also remove the import of <code>TodoType</code> and the <code>lang='ts'</code> from <code>Todo.svelte</code>.</li>
</ol>

<p>We'll take care of them properly, later on.</p>

<h2 id="Porting_our_to-do_list_app_to_TypeScript">Porting our to-do list app to TypeScript</h2>

<p>Now we are ready to start porting our to-do list application to take advantage of all the features that TypeScript offers to us.</p>

<p>Let's start by running the validate script in watch mode inside your project root:</p>

<pre class="brush: bash">npm run validate -- --watch</pre>

<p>this should output something like the following:</p>

<pre class="brush: bash">svelte-check "--watch"

Loading svelte-check in workspace: ./svelte-todo-typescript
Getting Svelte diagnostics...
====================================
svelte-check found no errors and no warnings</pre>

<p>Note that if you are using a supporting code editor like VS Code, a simple way to start porting a Svelte component is to just add the <code>&lt;script lang='ts'&gt;</code> at the top of your component and look for the three-dotted hints:</p>

<p><img alt='vs code screenshot showing that when you add type="ts" to a component, it gives you three dot alert hints' src="09-vscode-alert-hints.png"></p>

<h3 id="Alert.svelte">Alert.svelte</h3>

<p>Let's start with our <code>Alert.svelte</code> component.</p>

<ol>
	<li>
	<p>Add <code>lang="ts"</code> into your <code>Alert.svelte</code> component's <code>&lt;script&gt;</code> tag. You'll see some warnings in the output of the <code>validate</code> script:</p>

	<pre class="brush: bash">$ npm run validate -- --watch
&gt; svelte-check "--watch"

./svelte-todo-typescript
Getting Svelte diagnostics...
====================================

./svelte-todo-typescript/src/components/Alert.svelte:8:7
Warn: Variable 'visible' implicitly has an 'any' type, but a better type may be inferred from usage. (ts)
  let visible

./svelte-todo-typescript/src/components/Alert.svelte:9:7
Warn: Variable 'timeout' implicitly has an 'any' type, but a better type may be inferred from usage. (ts)
  let timeout

./svelte-todo-typescript/src/components/Alert.svelte:11:28
Warn: Parameter 'message' implicitly has an 'any' type, but a better type may be inferred from usage. (ts)
Change = (message, ms) =&gt; {

./svelte-todo-typescript/src/components/Alert.svelte:11:37
Warn: Parameter 'ms' implicitly has an 'any' type, but a better type may be inferred from usage. (ts)
(message, ms) =&gt; {</pre>
	</li>
	<li>
	<p>You can fix these by specifying the corresponding types, like so:</p>

	<pre class="brush: js">export let ms = 3000

  let visible: boolean
  let timeout: number

  const onMessageChange = (message: string, ms: number) =&gt; {
    clearTimeout(timeout)
    if (!message) {               // hide Alert if message is empty</pre>

	<div class="notecard note">
	<p><strong>Note:</strong> There's no need to specify the <code>ms</code> type with <code>export let ms:number = 3000</code> because TypeScript is already inferring it from its default value.</p>
	</div>
	</li>
</ol>

<h3 id="MoreActions.svelte">MoreActions.svelte</h3>

<p>Now we'll do the same for the <code>MoreActions.svelte</code> component.</p>

<ol>
	<li>Add the <code>lang='ts'</code> attribute, like before. TypeScript will warn us about the <code>todos</code> prop and the <code>t</code> variable in the call to <code>todos.filter(t =&gt;...)</code>.

	<pre class="brush: bash">Warn: Variable 'todos' implicitly has an 'any' type, but a better type may be inferred from usage. (ts)
  export let todos

Warn: Parameter 't' implicitly has an 'any' type, but a better type may be inferred from usage. (ts)
  $: completedTodos = todos.filter(t =&gt; t.completed).length</pre>
	</li>
	<li>
	<p>We will use the <code>TodoType</code> we already defined to tell TypeScript that <code>todos</code> is a <code>TodoType</code> array — replace your <code>export let todos</code> line with the following:</p>

	<pre class="brush: js">import type { TodoType } from '../types/todo.type'

export let todos: TodoType[]</pre>
	</li>
</ol>

<p>Notice that now TypeScript can infer that the <code>t</code> variable in <code>todos.filter(t =&gt; t.completed)</code> is of type <code>TodoType</code>. Nevertheless, if we think it makes our code easier to read, we could specify it like this:</p>

<pre class="brush: js">$: completedTodos = todos.filter((t: TodoType) =&gt; t.completed).length</pre>

<p>Most of the time TypeScript will be able to correctly infer the reactive variable type, but sometimes you might get an "implicitly has an 'any' type" error when working with reactive assignments. In those cases you can declare the typed variable in a different statement, like this:</p>

<pre class="brush: js">let completeTodos: number
$: completedTodos = todos.filter((t: TodoType) =&gt; t.completed).length</pre>

<p>You can't specify the type in the reactive assignment itself. The following statement <code>$: completedTodos: number = todos.filter[...]</code> is invalid. For more information read <a href="https://github.com/sveltejs/language-tools/blob/master/docs/preprocessors/typescript.md#how-do-i-type-reactive-assignments--i-get-an-implicitly-has-type-any-error">How do I type reactive assignments? / I get an "implicitly has type 'any' error"</a>.</p>

<h3 id="FilterButton.svelte">FilterButton.svelte</h3>

<p>Now we'll take care of the <code>FilterButton</code> component.</p>

<ol>
	<li>
	<p>Add the <code>lang='ts'</code> attribute to the <code>&lt;script&gt;</code> tag, as usual. You'll notice there are no warnings — TypeScript infers the type of the filter variable from the default value. But we know that there are only three valid values for the filter: all, active, and completed. So we can let TypeScript know about them by creating an enum Filter.</p>
	</li>
	<li>
	<p>Create a <code>filter.enum.ts</code> file in the <code>types</code> folder.</p>
	</li>
	<li>
	<p>Give it the following contents:</p>

	<pre class="brush: js">export enum Filter {
  ALL = 'all',
  ACTIVE = 'active',
  COMPLETED = 'completed',
}</pre>
	</li>
	<li>
	<p>Now we will use this from the <code>FilterButton</code> component. Replace the content of the <code>FilterButton.svelte</code> file with the following:</p>

	<pre class="brush: html">&lt;!-- components/FilterButton.svelte --&gt;
&lt;script lang='ts'&gt;
  import { Filter } from '../types/filter.enum'

  export let filter: Filter = Filter.ALL
&lt;/script&gt;

&lt;div class="filters btn-group stack-exception"&gt;
  &lt;button class="btn toggle-btn" class:btn__primary={filter === Filter.ALL} aria-pressed={filter === Filter.ALL} on:click={()=&gt; filter = Filter.ALL} &gt;
    &lt;span class="visually-hidden"&gt;Show&lt;/span&gt;
    &lt;span&gt;All&lt;/span&gt;
    &lt;span class="visually-hidden"&gt;tasks&lt;/span&gt;
  &lt;/button&gt;
  &lt;button class="btn toggle-btn" class:btn__primary={filter === Filter.ACTIVE} aria-pressed={filter === Filter.ACTIVE} on:click={()=&gt; filter = Filter.ACTIVE} &gt;
    &lt;span class="visually-hidden"&gt;Show&lt;/span&gt;
    &lt;span&gt;Active&lt;/span&gt;
    &lt;span class="visually-hidden"&gt;tasks&lt;/span&gt;
  &lt;/button&gt;
  &lt;button class="btn toggle-btn" class:btn__primary={filter === Filter.COMPLETED} aria-pressed={filter === Filter.COMPLETED} on:click={()=&gt; filter = Filter.COMPLETED} &gt;
    &lt;span class="visually-hidden"&gt;Show&lt;/span&gt;
    &lt;span&gt;Completed&lt;/span&gt;
    &lt;span class="visually-hidden"&gt;tasks&lt;/span&gt;
  &lt;/button&gt;
&lt;/div&gt;</pre>
	</li>
</ol>

<p>Here we are just importing the <code>Filter</code> enum, and using it instead of the string values we used previously.</p>

<h3 id="Todos.svelte">Todos.svelte</h3>

<p>We will also use the <code>Filter</code> enum in the <code>Todos.svelte</code> component.</p>

<ol>
	<li>
	<p>First add the <code>lang='ts'</code> attribute to it, as before.</p>
	</li>
	<li>
	<p>Next, import the <code>Filter</code> enum — add the following <code>import</code> statement below your existing ones:</p>

	<pre class="brush: js">import { Filter } from '../types/filter.enum'</pre>
	</li>
	<li>
	<p>Now we will use it whenever we reference the current filter. Replace your two filter-related blocks with the following:</p>

	<pre class="brush: js">let filter: Filter = Filter.ALL
  const filterTodos = (filter: Filter, todos) =&gt;
    filter === Filter.ACTIVE ? todos.filter(t =&gt; !t.completed) :
    filter === Filter.COMPLETED ? todos.filter(t =&gt; t.completed) :
    todos

$: {
  if (filter === Filter.ALL)               $alert = 'Browsing all todos'
  else if (filter === Filter.ACTIVE)       $alert = 'Browsing active todos'
  else if (filter === Filter.COMPLETED)    $alert = 'Browsing completed todos'
}</pre>
	</li>
	<li>
	<p><code>validate</code> will still give us some warnings from <code>Todos.svelte</code>. Let's fix them.</p>

	<p>Start by importing the <code>TodoType</code> and telling TypeScript that our <code>todos</code> variable is an array of <code>TodoType</code>. Replace <code>export let todos = []</code> with the following two lines:</p>

	<pre class="brush: js">import type { TodoType } from '../types/todo.type'

export let todos: TodoType[] = []</pre>
	</li>
	<li>
	<p>Next we'll specify all the missing types. The variable <code>todosStatus</code>, which we used to programmatically access the methods exposed by the <code>TodosStatus</code> component, is of type <code>TodosStatus</code>. And each <code>todo</code> will be of type <code>TodoType</code>.</p>

	<p>Update your <code>&lt;script&gt;</code> section to look like this:</p>

	<pre class="brush: js">&lt;script lang='ts'&gt;
  import FilterButton from './FilterButton.svelte'
  import Todo from './Todo.svelte'
  import MoreActions from './MoreActions.svelte'
  import NewTodo from './NewTodo.svelte'
  import TodosStatus from './TodosStatus.svelte'
  import { alert } from '../stores'

  import { Filter } from '../types/filter.enum'

  import type { TodoType } from '../types/todo.type'

  export let todos: TodoType[] = []

  let todosStatus: TodosStatus                   // reference to TodosStatus instance

  $: newTodoId = todos.length &gt; 0 ? Math.max(...todos.map(t =&gt; t.id)) + 1 : 1

  function addTodo(name: string) {
    todos = [...todos, { id: newTodoId, name, completed: false }]
    $alert = `Todo '${name}' has been added`
  }

  function removeTodo(todo: TodoType) {
    todos = todos.filter(t =&gt; t.id !== todo.id)
    todosStatus.focus()             // give focus to status heading
    $alert = `Todo '${todo.name}' has been deleted`
  }

  function updateTodo(todo: TodoType) {
    const i = todos.findIndex(t =&gt; t.id === todo.id)
    if (todos[i].name !== todo.name)            $alert = `todo '${todos[i].name}' has been renamed to '${todo.name}'`
    if (todos[i].completed !== todo.completed)  $alert = `todo '${todos[i].name}' marked as ${todo.completed ? 'completed' : 'active'}`
    todos[i] = { ...todos[i], ...todo }
  }

  let filter: Filter = Filter.ALL
  const filterTodos = (filter: Filter, todos: TodoType[]) =&gt;
    filter === Filter.ACTIVE ? todos.filter(t =&gt; !t.completed) :
    filter === Filter.COMPLETED ? todos.filter(t =&gt; t.completed) :
    todos

  $: {
    if (filter === Filter.ALL)               $alert = 'Browsing all todos'
    else if (filter === Filter.ACTIVE)       $alert = 'Browsing active todos'
    else if (filter === Filter.COMPLETED)    $alert = 'Browsing completed todos'
  }

  const checkAllTodos = (completed: boolean) =&gt; {
    todos = todos.map(t =&gt; ({...t, completed}))
    $alert = `${completed ? 'Checked' : 'Unchecked'} ${todos.length} todos`
  }
  const removeCompletedTodos = () =&gt; {
    $alert = `Removed ${todos.filter(t =&gt; t.completed).length} todos`
    todos = todos.filter(t =&gt; !t.completed)
  }
&lt;/script&gt;</pre>
	</li>
</ol>

<h3 id="TodosStatus.svelte">TodosStatus.svelte</h3>

<p>We are encountering the following errors related to passing <code>todos</code> to the <code>TodosStatus.svelte</code> (and <code>Todo.svelte</code>) components:</p>

<pre class="brush: bash">./src/components/Todos.svelte:70:39
Error: Type 'TodoType[]' is not assignable to type 'undefined'. (ts)
  &lt;TodosStatus bind:this={todosStatus} {todos} /&gt;

./src/components/Todos.svelte:76:12
Error: Type 'TodoType' is not assignable to type 'undefined'. (ts)
     &lt;Todo {todo}</pre>

<p>This is because the <code>todos</code> prop in the <code>TodosStatus</code> component has no default value, so TypeScript has inferred it to be of type <code>undefined</code>, which is not compatible with an array of <code>TodoType</code>. The same thing is happening with our Todo component.</p>

<p>Let's fix it.</p>

<ol>
	<li>
	<p>Open the file <code>TodosStatus.svelte</code> and add the <code>lang='ts'</code> attribute.</p>
	</li>
	<li>
	<p>Then import the <code>TodoType</code> and declare the <code>todos</code> prop as an array of <code>TodoType</code>. Replace the first line of the <code>&lt;script&gt;</code> section with the following:</p>

	<pre class="brush: js">import type { TodoType } from '../types/todo.type'

export let todos: TodoType[]</pre>
	</li>
	<li>
	<p>We will also specify the <code>headingEl</code>, which we used to bind to the heading tag, as an <code>HTMLElement</code>. Update the <code>let headingEl</code> line with the following:</p>

	<pre class="brush: js">let headingEl: HTMLElement</pre>
	</li>
	<li>
	<p>Finally, you'll notice the following error reported, related to where we set the <code>tabindex</code> attribute. That's because TypeScript is type-checking the <code>&lt;h2&gt;</code> element and expects <code>tabindex</code> to be of type <code>number</code>.</p>

	<p><img alt="tabindex hint inside vs code, tabindex expects a type of number, not string" src="10-vscode-tabindex-hint.png"></p>

	<p>To fix it, replace <code>tabindex="-1"</code> with <code>tabindex={-1}</code>, like this:</p>

	<pre class="brush: html">&lt;h2 id="list-heading" bind:this={headingEl} tabindex={-1}&gt;{completedTodos} out of {totalTodos} items completed&lt;/h2&gt;</pre>

	<p>This way TypeScript can prevent us from incorrectly assigning it to a string variable.</p>
	</li>
</ol>

<h3 id="NewTodo.svelte">NewTodo.svelte</h3>

<p>Next we will take care of <code>NewTodo.svelte</code>.</p>

<ol>
	<li>
	<p>As usual, add the <code>lang='ts'</code> attribute.</p>
	</li>
	<li>
	<p>The warning will indicate that we have to specify a type for the <code>nameEl</code> variable. Set its type to <code>HTMLElement</code> like this:</p>

	<pre class="brush: js">let nameEl: HTMLElement     // reference to the name input DOM node</pre>
	</li>
	<li>
	<p>Last for this file, we need to specify the correct type for our <code>autofocus</code> variable; update its definition like this:</p>

	<pre class="brush: js">export let autofocus: boolean = false</pre>
	</li>
</ol>

<h3 id="Todo.svelte">Todo.svelte</h3>

<p>Now the only warnings that <code>npm run validate</code> emits are triggered by calling the <code>Todo.svelte</code> component; let's fix them.</p>

<ol>
	<li>
	<p>Open the <code>Todo.svelte</code> file, and add the <code>lang='ts'</code> attribute.</p>
	</li>
	<li>
	<p>Let's import the <code>TodoType</code>, and set the type of the <code>todo</code> prop. Replace the <code>export let todo</code> line with the following:</p>

	<pre class="brush: js">import type { TodoType } from '../types/todo.type'

export let todo: TodoType</pre>
	</li>
	<li>
	<p>The first warning we get is TypeScript telling us to define the type of the <code>update()</code> function's <code>updatedTodo</code> variable. This can be a little tricky because <code>updatedTodo</code> contains only the attributes of the todo that have been updated. That means it's not a complete todo — it only has a subset of a todo's properties.</p>

	<p>For these kinds of cases, TypeScript provides several <a href="https://www.typescriptlang.org/docs/handbook/utility-types.html">utility types</a> to make it easier to apply these common transformations. What we need right now is the <code><a href="https://www.typescriptlang.org/docs/handbook/utility-types.html#partialt">Partial&lt;T&gt;</a></code> utility, which allows us to represent all subsets of a given type. The partial utility returns a new type based on the type <code>T</code>, where every property of <code>T</code> is optional.</p>

	<p>We'll use it in the <code>update()</code> function — update yours like so:</p>

	<pre class="brush: js">function update(updatedTodo: Partial&lt;TodoType&gt;) {
  todo = { ...todo, ...updatedTodo }    // applies modifications to todo
  dispatch('update', todo)              // emit update event
}</pre>

	<p>With this we are telling TypeScript that the <code>updatedTodo</code> variable will hold a subset of the <code>TodoType</code> properties.</p>
	</li>
	<li>
	<p>Now svelte-check tells us that we have to define the type of our action function parameters:</p>

	<pre class="brush: bash">./07-next-steps/src/components/Todo.svelte:45:24
Warn: Parameter 'node' implicitly has an 'any' type, but a better type may be inferred from usage. (ts)
  const focusOnInit = (node) =&gt; node &amp;&amp; typeof node.focus === 'function' &amp;&amp; node.focus()

./07-next-steps/src/components/Todo.svelte:47:28
Warn: Parameter 'node' implicitly has an 'any' type, but a better type may be inferred from usage. (ts)
  const focusEditButton = (node) =&gt; editButtonPressed &amp;&amp; node.focus()</pre>

	<p>We just have to define the node variable to be of type <code>HTMLElement</code>. In the two lines indicated above, replace the first instance of <code>node</code> with <code>node: HTMLElement</code>.</p>
	</li>
</ol>

<h3 id="actions.js">actions.js</h3>

<p>Next we'll take care of the <code>actions.js</code> file.</p>

<ol>
	<li>
	<p>Rename it to <code>actions.ts</code> and add the type of the node parameter. It should end up looking like this:</p>

	<pre class="brush: js">// actions.ts
export function selectOnFocus(node: HTMLInputElement) {
  if (node &amp;&amp; typeof node.select === 'function' ) {               // make sure node is defined and has a select() method
    const onFocus = () =&gt; node.select()                           // event handler
    node.addEventListener('focus', onFocus)                       // when node gets focus call onFocus()
    return {
      destroy: () =&gt; node.removeEventListener('focus', onFocus)   // this will be executed when the node is removed from the DOM
    }
  }
}</pre>
	</li>
	<li>
	<p>Now update <code>Todo.svelte</code> and <code>NewTodo.svelte</code> where we import the actions file. Remember that imports in TypeScript don't include the file extension. In each case it should end up like this:</p>

	<pre class="brush: js">import { selectOnFocus } from '../actions'</pre>
	</li>
</ol>

<h3 id="Migrating_the_stores_to_TypeScript">Migrating the stores to TypeScript</h3>

<p>Now we have to migrate the <code>stores.js</code> and <code>localStore.js</code> files to TypeScript.</p>

<p>Tip: the script <code>npm run validate</code>, which uses the <code><a href="https://github.com/sveltejs/language-tools/tree/master/packages/svelte-check">svelte-check</a></code> tool, will only check our application's <code>.svelte</code> files. If you want to also check the <code>.ts</code> files you can run <code>npm run validate &amp;&amp; npx tsc --noemit</code>, which tells the TypeScript compiler to check for errors without generating the <code>.js</code> output files. You could even add a script to your <code>package.json</code> file that runs that command.</p>

<p>We'll start with <code>stores.js</code>.</p>

<ol>
	<li>
	<p>Rename the file to <code>stores.ts</code>.</p>
	</li>
	<li>
	<p>Set the type of our <code>initialTodos</code> array to <code>TodoType[]</code>. This is how the contents will end up:</p>

	<pre class="brush: js">// stores.ts
import { writable } from 'svelte/store'
import { localStore } from './localStore.js'
import type { TodoType } from './types/todo.type'

export const alert = writable('Welcome to the To-Do list app!')

const initialTodos: TodoType[] = [
  { id: 1, name: 'Visit MDN web docs', completed: true },
  { id: 2, name: 'Complete the Svelte Tutorial', completed: false },
]

export const todos = localStore('mdn-svelte-todo', initialTodos)</pre>
	</li>
	<li>
	<p>Remember to update the <code>import</code> statements in <code>App.svelte</code>, <code>Alert.svelte</code>, and <code>Todos.svelte</code>. Just remove the <code>.js</code> extension, like this:</p>

	<pre class="brush: js">import { todos } from '../stores'</pre>
	</li>
</ol>

<p>Now onto <code>localStore.js</code>.</p>

<p>Update the <code>import</code> statement in <code>stores.ts</code>, like so:</p>

<pre class="brush: js">import { localStore } from './localStore'</pre>

<ol>
	<li>
	<p>Start by renaming the file to <code>localStore.ts</code>.</p>
	</li>
	<li>
	<p>TypeScript is telling us to specify the type of the <code>key</code>, <code>initial</code>, and <code>value</code> variables. The first one is easy — the key of our local web storage should be a string.</p>

	<p>But <code>initial</code> and <code>value</code> should be any object that could be converted to a valid JSON string with the <code><a href="/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify">JSON.stringify</a></code> method. So it is in fact any JavaScript object with a couple limitations, for example <code>undefined</code>, functions, and symbols are not valid JSON values.</p>

	<p>So we'll create the type <code>JsonValue</code> to specify these conditions.</p>

	<p>Create the file <code>json.type.ts</code> in the <code>types</code> folder.</p>
	</li>
	<li>
	<p>Give it the following content:</p>

	<pre class="brush: js">export type JsonValue = string | number | boolean | null | JsonValue[] | { [key: string]: JsonValue }</pre>

	<p>The <code>|</code> operator lets us declare variables that could store values of two or more types. A <code>JsonValue</code> could be a string, a number, a boolean, and so on. In this case we are also making use of recursive types, to specify that a <code>JsonValue</code> can have an array of <code>JsonValue</code>, and also an object with properties of type <code>JsonValue</code>.</p>
	</li>
	<li>
	<p>We will import our <code>JsonValue</code> type and use it accordingly. Update your <code>localStore.ts</code> file like this:</p>

	<pre class="brush: js">// localStore.ts
import { writable } from 'svelte/store'

import type { JsonValue } from './types/json.type'

export const localStore = (key: string, initial: JsonValue) =&gt; {          // receives the key of the local storage and an initial value

  const toString = (value: JsonValue) =&gt; JSON.stringify(value, null, 2)   // helper function
  const toObj = JSON.parse                                                // helper function

  if (localStorage.getItem(key) === null) {                               // item not present in local storage
    localStorage.setItem(key, toString(initial))                          // initialize local storage with initial value
  }

  const saved = toObj(localStorage.getItem(key))                          // convert to object

  const { subscribe, set, update } = writable(saved)                      // create the underlying writable store

  return {
    subscribe,
    set: (value: JsonValue) =&gt; {
      localStorage.setItem(key, toString(value))                          // save also to local storage as a string
      return set(value)
    },
    update
  }
}</pre>
	</li>
</ol>

<p>Now if we try to create a <code>localStore</code> with something that cannot be converted to JSON via <code>JSON.stringify()</code>, for example an object with a function as a property, VS Code/<code>validate</code> will complain about it:</p>

<p><img alt="vs code showing an error with using our store — it fails when trying to set a local storage value to something incompatible with json stringify" src="11-vscode-invalid-store.png"></p>

<p>And best of all, it will even work with the <a href="https://svelte.dev/docs#4_Prefix_stores_with_%24_to_access_their_values"><code>$store</code> auto-subscription syntax</a>. If we try to save an invalid value to our <code>todos</code> store using the <code>$store</code> syntax, like this:</p>

<pre class="brush: html">&lt;!-- App.svelte --&gt;
&lt;script lang="ts"&gt;
  import Todos from './components/Todos.svelte'
  import Alert from './components/Alert.svelte'

  import { todos } from './stores'

  // this is invalid, the content cannot be converted to JSON using JSON.stringify
  $todos = { handler: () =&gt; {} }

&lt;/script&gt;</pre>

<p>The validate script will report the following error:</p>

<pre class="brush: bash">&gt; npm run validate

Getting Svelte diagnostics...
====================================

./svelte-todo-typescript/src/App.svelte:8:12
Error: Argument of type '{ handler: () =&gt; void; }' is not assignable to parameter of type 'JsonValue'.
  Types of property 'handler' are incompatible.
    Type '() =&gt; void' is not assignable to type 'JsonValue'.
      Type '() =&gt; void' is not assignable to type '{ [key: string]: JsonValue; }'.
        Index signature is missing in type '() =&gt; void'. (ts)
 $todos = { handler: () =&gt; {} }</pre>

<p>This is another example of how specifying types can make our code more robust, and help us catch more bugs before they get into production.</p>

<p>And that's it. We've converted our whole application to use TypeScript.</p>

<h2 id="Bulletproofing_our_stores_with_Generics">Bulletproofing our stores with Generics</h2>

<p>Our stores have already been ported to TypeScript but we can do better. We shouldn't need to store any kind of value — we know that the alert store should contain string messages, and the todos store should contain an array of <code>TodoType</code>, etc. We can let TypeScript enforce this using <a href="https://www.typescriptlang.org/docs/handbook/generics.html">TypeScript Generics</a>; let's find out more.</p>

<h3 id="Understanding_TypeScript_generics">Understanding TypeScript generics</h3>

<p>Generics allow us to create reusable code components that work with a variety of types instead of a single type. They can be applied to interfaces, classes, and functions. Generic types are passed as parameters using a special syntax: they are specified between angle-brackets, and by convention are denoted with an upper-cased single char letter. Generic types allows us to capture the types provided by the user to be used later.</p>

<p>Let's see a quick example, a simple <code>Stack</code> class that let's us <code>push</code> and <code>pop</code> elements, like this:</p>

<pre class="brush: js">export class Stack {
  private elements = []

  push = (element) =&gt; this.elements.push(element)

  pop() {
    if (this.elements.length === 0) throw new Error('The stack is empty!')
    return this.elements.pop()
  }
}</pre>

<p>In this case <code>elements</code> is an array of type <code>any</code>, and accordingly the <code>push()</code> and <code>pop()</code> methods both receive and return a variable of type <code>any</code>. So it's perfectly valid to do something like the following:</p>

<pre class="brush: js">const anyStack = new Stack()

anyStack.push(1)
anyStack.push('hello')</pre>

<p>But what if we wanted to have a <code>Stack</code> that would only work with type <code>string</code>? We could do the following:</p>

<pre class="brush: js">export class StringStack {
  private elements: string[] = []

  push = (element: string) =&gt; this.elements.push(element)

  pop(): string {
    if (this.elements.length === 0) throw new Error('The stack is empty!')
    return this.elements.pop()
  }
}</pre>

<p>That would work. But if we wanted to work with numbers we would then have to duplicate our code and create a <code>NumberStack</code> class. And how could we handle a stack of types we don't know yet, and that should be defined by the consumer?</p>

<p>To solve all these problems we can use generics.</p>

<p>This is our <code>Stack</code> class reimplemented using generics:</p>

<pre class="brush: js">export class Stack&lt;T&gt; {
  private elements: T[] = []

  push = (element: T): number =&gt; this.elements.push(element)

  pop(): T {
    if (this.elements.length === 0) throw new Error('The stack is empty!')
    return this.elements.pop()
  }
}</pre>

<p>We define a generic type <code>T</code> and then use it like we would normally use a specific type. Now elements is an array of type <code>T</code>, and <code>push()</code> and <code>pop()</code> both receive and return a variable of type <code>T</code>.</p>

<p>This is how we would use our generic <code>Stack</code>:</p>

<pre class="brush: js">const numberStack = new Stack&lt;number&gt;()
numberStack.push(1)</pre>

<p>Now TypeScript knows that our stack can only accept numbers, and will issue an error if we try to push anything else:</p>

<p><img alt="Argument of type hello is not assignable to parameter of type number" src="12-vscode-generic-stack-error.png"></p>

<p>TypeScript can also infer generic types by its usage. Generics also support default values and constraints.</p>

<p>Generics is a powerful feature that allows our code to abstract away from the specific types being used, making it more reusable and generic without giving up on type-safety. To learn more about it check out the <a href="https://www.typescriptlang.org/docs/handbook/generics.html">TypeScript Introduction to Generics</a>.</p>

<h3 id="Using_Svelte_stores_with_generics">Using Svelte stores with generics</h3>

<p>Svelte stores support generics out of the box. And, because of generic type inference we can take advantage of it without even touching our code.</p>

<p>If you open the file <code>Todos.svelte</code> and assign a <code>number</code> type to our <code>$alert</code> store, you'll get the following error:</p>

<p><img alt="Todo Type object property complete should be completed" src="13-vscode-generic-alert-error.png"></p>

<p>That's because when we defined our alert store in the <code>stores.ts</code> file with:</p>

<pre class="brush: js">export const alert = writable('Welcome to the To-Do list app!')</pre>

<p>TypeScript inferred the generic type to be <code>string</code>. If we wanted to be explicit about it, we could do the following:</p>

<pre class="brush: js">export const alert = writable&lt;string&gt;('Welcome to the To-Do list app!')</pre>

<p>Now we'll make our <code>localStore</code> store support generics. Remember that we defined the <code>JsonValue</code> type to prevent the usage of our <code>localStore</code> store with values that cannot be persisted using <code>JSON.stringify()</code>. Now we want the consumers of <code>localStore</code> to be able to specify the type of data to persist, but instead of working with any type they should comply with the <code>JsonValue</code> type. We'll specify that with a Generic constraint, like this:</p>

<pre class="brush: js">export const localStore = &lt;T extends JsonValue&gt;(key: string, initial: T)</pre>

<p>We define a generic type <code>T</code> and specify that it must be compatible with the <code>JsonValue</code> type. Then we'll use the <code>T</code> type appropriately.</p>

<p>Our <code>localStore.ts</code> file will end up like this — try the new code now in your version:</p>

<pre class="brush: js">// localStore.ts
import { writable } from 'svelte/store'

import type { JsonValue } from './types/json.type'

export const localStore = &lt;T extends JsonValue&gt;(key: string, initial: T) =&gt; {          // receives the key of the local storage and an initial value

  const toString = (value: T) =&gt; JSON.stringify(value, null, 2)           // helper function
  const toObj = JSON.parse                                                // helper function

  if (localStorage.getItem(key) === null) {                               // item not present in local storage
    localStorage.setItem(key, toString(initial))                          // initialize local storage with initial value
  }

  const saved = toObj(localStorage.getItem(key))                          // convert to object

  const { subscribe, set, update } = writable&lt;T&gt;(saved)                   // create the underlying writable store

  return {
    subscribe,
    set: (value: T) =&gt; {
      localStorage.setItem(key, toString(value))                          // save also to local storage as a string
      return set(value)
    },
    update
  }
}</pre>

<p>And thanks to generic type inference, TypeScript already knows that our <code>$todos</code> store should contain an array of <code>TodoType</code>:</p>

<p><img alt="Todo Type object property complete should be completed" src="14-vscode-generic-localstore-error.png"></p>

<p>Once again, if we wanted to be explicit about it, we could do so in the <code>stores.ts</code> file like this:</p>

<pre class="brush: js">const initialTodos: TodoType[] = [
  { id: 1, name: 'Visit MDN web docs', completed: true },
  { id: 2, name: 'Complete the Svelte Tutorial', completed: false },
]

export const todos = localStore&lt;TodoType[]&gt;('mdn-svelte-todo', initialTodos)</pre>

<p>That will do for our brief tour of TypeScript Generics.</p>

<h2 id="The_code_so_far">The code so far</h2>

<h3 id="Git_2">Git</h3>

<p>To see the state of the code as it should be at the end of this article, access your copy of our repo like this:</p>

<pre class="brush: bash">cd mdn-svelte-tutorial/08-next-steps</pre>

<p>Or directly download the folder's content:</p>

<pre class="brush: bash">npx degit opensas/mdn-svelte-tutorial/08-next-steps</pre>

<p>Remember to run <code>npm install &amp;&amp; npm run dev</code> to start your app in development mode.</p>

<h3 id="REPL_2">REPL</h3>

<p>As we said earlier, TypeScript is not yet available in the REPL.</p>

<h2 id="Summary">Summary</h2>

<p>In this article we took our to-do list application and ported it to TypeScript.</p>

<p>We first learnt about TypeScript and what advantages it can bring us. Then we saw how to create a new Svelte project with TypeScript support. We also saw how to convert an existing Svelte project to use TypeScript — our to-do list app.</p>

<p>We saw how to work with <a href="https://code.visualstudio.com/">Visual Studio Code</a> and the <a href="https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode">Svelte extension</a> to get features like type checking and auto-completion. We also used the <code>svelte-check</code> tool to inspect TypeScript issues from the command line.</p>

<p>In the next article we will learn how to compile and deploy our app to production. We will also see which resources are available online to go further with learning Svelte.</p>

<p>{{PreviousMenuNext("Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_stores","Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_deployment_next", "Learn/Tools_and_testing/Client-side_JavaScript_frameworks")}}</p>

<h2 id="In_this_module">In this module</h2>

<ul>
 <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Introduction">Introduction to client-side frameworks</a></li>
 <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Main_features">Framework main features</a></li>
 <li>React
  <ul>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_getting_started">Getting started with React</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_todo_list_beginning">Beginning our React todo list</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_components">Componentizing our React app</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_interactivity_events_state">React interactivity: Events and state</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_interactivity_filtering_conditional_rendering">React interactivity: Editing, filtering, conditional rendering</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_accessibility">Accessibility in React</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_resources">React resources</a></li>
  </ul>
 </li>
 <li>Ember
  <ul>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Ember_getting_started">Getting started with Ember</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Ember_structure_componentization">Ember app structure and componentization</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Ember_interactivity_events_state">Ember interactivity: Events, classes and state</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Ember_conditional_footer">Ember Interactivity: Footer functionality, conditional rendering</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Ember_routing">Routing in Ember</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Ember_resources">Ember resources and troubleshooting</a></li>
  </ul>
 </li>
 <li>Vue
  <ul>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Vue_getting_started">Getting started with Vue</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Vue_first_component">Creating our first Vue component</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Vue_rendering_lists">Rendering a list of Vue components</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Vue_methods_events_models">Adding a new todo form: Vue events, methods, and models</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Vue_styling">Styling Vue components with CSS</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Vue_computed_properties">Using Vue computed properties</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Vue_conditional_rendering">Vue conditional rendering: editing existing todos</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Vue_refs_focus_management">Focus management with Vue refs</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Vue_resources">Vue resources</a></li>
  </ul>
 </li>
 <li>Svelte
  <ul>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_getting_started">Getting started with Svelte</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_Todo_list_beginning">Starting our Svelte Todo list app</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_variables_props">Dynamic behavior in Svelte: working with variables and props</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_components">Componentizing our Svelte app</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_reactivity_lifecycle_accessibility">Advanced Svelte: Reactivity, lifecycle, accessibility</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_stores">Working with Svelte stores</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_TypeScript">TypeScript support in Svelte</a></li>
   <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Svelte_deployment_next">Deployment and next steps</a></li>
  </ul>
 </li>
 <li>Angular
   <ul>
    <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Angular_getting_started">Getting started with Angular</a></li>
    <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Angular_todo_list_beginning">Beginning our Angular todo list app</a></li>
    <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Angular_styling">Styling our Angular app</a></li>
    <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Angular_item_component">Creating an item component</a></li>
    <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Angular_filtering">Filtering our to-do items</a></li>
    <li><a href="/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Angular_building">Building Angular applications and further resources</a></li>
   </ul>
 </li>
</ul>