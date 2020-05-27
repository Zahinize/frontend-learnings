# What is JavaScript?

[< Back to Home page](README.md)

JavaScript (often shortened as JS) is a lightweight, interpreted or [Just-In-Time compiled](https://en.wikipedia.org/wiki/Just-in-time_compilation) language with [first-class functions](https://developer.mozilla.org/en-US/docs/Glossary/First-class_Function) support. Even though it is primarily used as the scripting language for the web platform, .i.e, the browser environment, many non-browser environments such as [NodeJS](https://nodejs.org/en/), [Apache CouchDB](https://couchdb.apache.org/), [Couchbase](https://www.couchbase.com/) and [Adobe Acrobat](https://www.adobe.com/devnet/acrobat/javascript.html) use it as well. It is a prototype-based, multi-paradigm, single-threaded dynamic language that supports imperative, object-oriented and declarative (functional programming) styles.

> ### Just-In-Time Compilation
>
> A Just-In-Time (JIT) or run-time compilation is a process where the code is compiled when executed, i.e., at run time, rather than at build time. It consist of the two traditional approaches to execute the code, i.e., an Interpreter and a Compiler. It typically involves the translation of Source code to Byte code or more commonly used Machine code which is directly executed by the system. It provides the flexibility of an interpreter, continous code analysis, performance optimization and speedy execution of an AOT (Ahead-Of-Time Compiler) while bearing the integration overhead of both of them. Thus, it can yield faster code execution as compared to a traditional Compiler.

> ### First-Class Functions
>
> Any language can be said to support first-class functions if the functions are treated like any other variable. In such a language, a function can be passed as a argument to another function, returned from another function or assigned to a variable.

<pre>
	<code class="lang-js">
	const firstClassFunctions = (function() {
		// A function is assigned to a variable
		const sayHello = function() {
			return "Hello, I am ";
		}
		sayHello();

		// A function is passed as an argument to another function
		const greeting = function(sayHello, fullName) {
			console.log(`${sayHello()}${fullName}`);
		}
		greeting(sayHello, "Zahin Omar Alwa");

		// A function is returned from another function
		const adder = function(x) {
			return function(y) {
				return x + y;
			}
		}
		let numberAdder = adder(5);

		numberAdder = numberAdder(7);
		console.log(numberAdder);
	});
	firstClassFunctions();
	</code>
</pre>

REPL: [https://repl.it/@zahinalwa/JavaScript-fundamentals](https://repl.it/@zahinalwa/JavaScript-fundamentals)

> ### Prototype-based programming
>
> A prototype-based programming is a part of object-oriented programming where classes are not explicitly created, rather derived by creating properties and methods on the prototype object of the constructor class which are mutually shared by all of its instance objects. All non-sharing properties and methods are created inside of the constructor class and are unique to every instance object. Thus, you can create instance objects from the constructor class function or an empty object without creating its class first. Once an object has been created, it can act as a blueprint (prototype) for creating similar objects.

<pre>
	<code class="lang-js">
	const prototypeBasedProgramming = (function() {
		// Object instances have different local properties and methods
		// but share the same prototype properties and methods
		function BulbaSaur({ name, word, rank, level}) {
			this.name = name;
			this.word = word;
			this.rank = rank;
			this.level = level;
			this.speak = function() {
				const string = `My name is ${this.name} with rank ${this.rank} and level ${this.level}. My eyes color is ${this.eyesColor} and body color is ${this.bodyColor}.`;

				console.log(string);
			}
		}

		// Properties and Methods set on its prototype
		BulbaSaur.prototype.eyesColor = "red";
		BulbaSaur.prototype.bodyColor = "green";
		BulbaSaur.prototype.fight = function() {
			console.log(`Get ready to fight me! My signature move is Solar Beam and it can hurt you badly. ${this.word}`);
			console.log("\n");
		}


		const bulbasaur = new BulbaSaur({name: "BulbaSaur", word: "Bulba!", rank: 1, level: 1});
		bulbasaur.speak();
		bulbasaur.fight();

		const ivySaur = new BulbaSaur({name: "IvySaur", word: "Ivy!", rank: 2, level: 2});
		ivySaur.speak();
		ivySaur.fight();

		const venuSaur = new BulbaSaur({name: "VenuSaur", word: "Venu!", rank: 3, level: 3});
		venuSaur.speak();
		venuSaur.fight();
	});
	prototypeBasedProgramming();
	</code>
</pre>

REPL: [https://repl.it/@zahinalwa/JavaScript-fundamentals](https://repl.it/@zahinalwa/JavaScript-fundamentals)

The standard for JavaScript is [ECMAScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Language_Resources). As of 2012, all modern browsers supported ECMAScript 5.1. Older browsers supported atleast ECMAScript 3. On June 17 2015, ECMAScript International released the sixth major version of ECMAScript which was initially referred as ECMAScript2015 or ES6. Since then, ECMAScript is on an yearly release cycle. The current released standard version is ECMAScript 2020 or ES11.

JavaScript runs on the client side of the web which is responsible for controlling web page behaviour on occurrence of an event. It is easy to learn and powerful enough to create interactive web applications.

Contrary to popular misconception, **JavaScript is not interpreted Java**. Apart from having the first four same characters and registered trademarks assigned to Oracle in the US, they are different programming languages with different use-cases. JavaScript is a loosely typed language that supports prototypial (object-oriented) inheritance whereas Java is a strongly typed language that supports classical inheritance. Objects can be created at run time in JavaScript as compared to the classical syntax that has to be created at build time by compiled languages such as C++ or Java.

The dynamic capabilities of JavaScript includes run-time object construction, variable-parameter lists, function variables, dynamic script creation (by `eval`), object introspection via (for..in loop) and source code recovery (JS programs can decompile their function bodies to their original source text).

### JavaScript Engines

There are six major JavaScript engines released and used by the world's biggest tech companies till date.

-   **SpiderMonkey and Rhino - Mozilla (Netscape)**

    -   SpiderMonkey was written by Brendan Eich in C/C++. Rhino was primarily written by Norris Boyd in Java. Both engines were optimized to be compliant with ECMA-262 Edition 5 and later versions. Some major engine runtime optimizations such as TracerMonkey (Firefox 3.5), JagerMonkey (Firefox 4) and IonMonkey were added to SpiderMonkey engine respectively. Code performance optimizations are constantly added to improve the engine.

-   **V8 - Google**

    -   V8 is the high-performance JS engine used in leading software and technologies such as Google Chrome, Microsoft Edge (latest version), Opera (version 15+) and NodeJS.

-   **JavaScriptCore (SquirrelFish/Nitro) - Apple**

    -   JavaScriptCore is used by some of the Webkit browsers such as Apple Safari.

-   **Carakan - Opera (version < 15)**

    -   This engine was used in the older version of the Opera browser before the company adopted Google's V8 engine and deprecated their own.

-   **Chakra - Microsoft**
    -   This engine was used in the Internet Explorer and older version of Microsoft Edge browsers before the company adopted Google's V8 engine and deprecated their own.

**Source**

-   [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/About_JavaScript)
-   [Wiki Page](https://en.wikipedia.org/wiki/List_of_ECMAScript_engines)
