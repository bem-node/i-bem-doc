##About

Stack of BEM technologies contains a block i-bem.

It's JavaScript implementation uses BEM data domain. The use of this library allows one to manipulate the client-side JavaScript/DOM in BEM-Style according to BEM-Principles, not only in the design of visible components, but also their behavior.2

[Details](http://bem.info/articles/bem-js-main-terms/)

##BEM (i-bem) api reference

###Static properties

####.blocks {Object}

Storage for block declarations (hash by block name)

```js
BEM.blocks['block-name'].blockMethod();
```

###Static methods

####.create(block, [params])

 * block {String|Object} Block name or description
 * params {Object} Block parameters

Factory method for creating an instance of the block named

####.del([obj])

 * obj {Object}


Helper for cleaning out properties

####.channel([id], [drop])

 * id {String} Channel ID
 * drop {Boolean} Destroy the channel

Returns/destroys a named communication channel


####.decl(decl, decl.block|decl.name, [decl.baseBlock], [decl.modName], [decl.modVal], [props], [staticProps])

Declares blocks and creates a block class

 * decl {String|Object} Block name (simple syntax) or description
 * decl.block|decl.name {String} Block name
 * decl.baseBlock {String} Name of the parent block
 * decl.modName {String} Modifier name
 * decl.modVal {String} Modifier value
 * props {Object} Methods
 * staticProps {Object} Static methods

####.getName()

Returns the name of the current block

####.#afterCurrentEvent(fn, ctx)

 * fn {Function}
 * ctx {Object}

Adds a function to the queue for executing after the "current event"

####.changeThis(fn, ctx)

 * fn {Function}
 * ctx {Object} Context

Changes the context of the function being passe


###Instance methods

####.channel([id], [drop])

 * id {String} Channel ID
 * drop {Boolean} Destroy the channel

Returns a named communication channel

####.getDefaultParams()

Returns a block's default parameters

####.del([obj])

 * obj {Object}

Helper for cleaning up block properties

####.destruct()

Deletes a block

####.changeThis(fn, [ctx])

 * fn {Function}
 * ctx {Object} Context

Changes the context of the function being passed

####.afterCurrentEvent(fn, [ctx])

 * fn {Function}
 * ctx {Object} Context

Executes the function in the context of the block, after the "current event"

####.trigger(e, [data])

 * e {String} Event name
 * data {Object} Additional information

Executes the block's event handlers and live event handlers

####.hasMod([elem], modName, [modVal])

 * elem {Object} Nested element
 * modName {String} Modifier name
 * modVal {String} Modifier value

Checks whether a block or nested element has a modifier

####.getMod([elem], modName)

 * elem {Object} Nested element
 * modName {String} Modifier name

Returns the value of the modifier of the block/nested element

####.getMods([elem], [modName1, ..., modNameN])

 * elem {Object} Nested element
 * modName1, ..., modNameN {String} Modifier names

Returns values of modifiers of the block/nested element

####.setMod([elem], modName, modVal)

 * elem {Object} Nested element
 * modName {String} Modifier name
 * modVal {String} Modifier value

Sets the modifier for a block/nested element

####.toggleMod([elem], modName, modVal1, [modVal2], [condition])

 * elem {Object} Nested element
 * modName {String} Modifier name
 * modVal1 {String} First modifier value
 * modVal2 {String} Second modifier value
 * condition {Boolean} Condition

Sets a modifier for a block/nested element, depending on conditions. If the condition parameter is passed: when true, modVal1 is set; when false, modVal2 is set. If the condition parameter is not passed: modVal1 is set if modVal2 was set, or vice versa.

####.delMod([elem], modName)

 * elem {Object} Nested element
 * modName {String} Modifier name

Removes a modifier from a block/nested element

##BEM.DOM (i-bem__dom) api reference

###Static properties

####.extractParams {Object}

Retrieves block parameters from a DOM element

####.scope {jQuery}

Scope Will be set on onDomReady to tag `body`

####.doc {jQuery}

Document shortcut

####.win {jQuery}

Window shortcut

###Static methods

####.replace(ctx, content)

 * ctx {jQuery} Root DOM node
 * content {jQuery|String} Content to be added

Changes a fragment of the DOM tree including the context and initializes blocks.

####.append(ctx, content)

 * ctx {jQuery} Root DOM node
 * content {jQuery|String} Content to be added

Adds a fragment of the DOM tree at the end of the context and initializes blocks

####.prepend(ctx, content)

 * ctx {jQuery} Root DOM node
 * content {jQuery|String} Content to be added

Adds a fragment of the DOM tree at the beginning of the context and initializes blocks

####.before(ctx, content)

 * ctx {jQuery} Contextual DOM node
 * content {jQuery|String} Content to be added

Adds a fragment of the DOM tree before the context and initializes blocks

####.after(ctx, content)

 * ctx {jQuery} Contextual DOM node
 * content {jQuery|String} Content to be added

Adds a fragment of the DOM tree after the context and initializes blocks

####.buildSelector([elem], [modName], [modVal])

 * elem {String} Element name
 * modName {String} Modifier name
 * modVal {String} Modifier value

Builds a CSS selector corresponding to the block/element and modifier

####.getBlockByUniqId([uniqId])

 * uniqId {String}
 * getWindowSize()

Returns the size of the current window

deprecated Returns a block instance by unique ID


####.init([ctx], callback, callbackCtx)

 * ctx {jQuery} Root DOM node
 * callback
 * callbackCtx

Initializes blocks on a fragment of the DOM tree

####.destruct([keepDOM], ctx, [excludeSelf])

 * keepDOM {Boolean} Whether to keep DOM nodes in the document
 * ctx {jQuery} Root DOM node
 * excludeSelf {Boolean} Exclude the context

Destroys blocks on a fragment of the DOM tree

####.update(ctx, content, [callback], [callbackCtx])

 * ctx {jQuery} Root DOM node
 * content {jQuery|String} New content
 * callback {Function} Handler to be called after initialization
 * callbackCtx {Object} Handler's context

Replaces a fragment of the DOM tree inside the context, destroying old blocks and intializing new ones

####.liveInitOnEvent([elemName], event, [callback])

 * elemName {String} Element name or names (separated by spaces)
 * event {String} Event name
 * callback {Function} Handler to call after successful initialization

Helper for live initialization for an event on DOM elements of a block or its elements

####.liveBindTo([to], event, [callback], invokeOnInit)

 * to {String|Object} Description (object with modName, modVal, elem) or name of the element or elements (space-separated)
 * event {String} Event name
 * callback {Function} Handler
 * invokeOnInit

Helper for subscribing to live events on DOM elements of a block or its elements

####.liveUnbindFrom([elem], event, [callback])

 * elem {String} Name of the element or elements (space-separated)
 * event {String} Event name
 * callback {Function} Handler

Helper for unsubscribing from live events on DOM elements of a block or its elements

####.liveInitOnBlockEvent(event, blockName, callback)

Helper for live initialization for a different block's event on the current block's DOM element

####.event {String}

Event name

####.blockName {String}

Name of the block that should trigger a reaction when initialized

####.callback {Function}

Handler to be called after successful initialization in the new block's context

####.liveInitOnBlockInsideEvent(event, blockName, [callback])

 * event {String} Event name
 * blockName {String} Name of the block that should trigger a reaction when initialized
 * callback {Function} Handler to be called after successful initialization in the new block's context

Helper for live initialization for a different block's event inside the current block

####.liveInitOnBlockInit(blockName, callback)

deprecated - use liveInitOnBlockEvent

 * blockName {String} Name of the block that should trigger a reaction when initialized
 * callback {Function} Handler to be called after successful initialization in the new block's context

Helper for live initialization when a different block is initialized on a DOM element of the current block

####.liveInitOnBlockInsideInit(blockName, [callback])

deprecated - use liveInitOnBlockInsideEvent

 * blockName {String} Name of the block that should trigger a reaction when initialized
 * callback {Function} Handler to be called after successful initialization in the new block's context

Helper for live initialization when a different block is initialized inside the current block

####.on([ctx], e, [data], fn, [fnCtx])

 * ctx {jQuery} The element in which the event will be listened for
 * e {String} Event name
 * data {Object} Additional information that the handler gets as e.data
 * fn {Function} Handler
 * fnCtx {Object} Handler's context

Adds a live event handler to a block, based on a specified element where the event will be listened for

####.un([ctx], e, [fn], [fnCtx])

 * ctx {jQuery} The element in which the event was being listened for
 * e {String} Event name
 * fn {Function} Handler
 * fnCtx {Object} Handler context

Removes the live event handler from a block, based on a specified element where the event was being listened for

####.liveCtxBind(ctx, e, [data], fn, [fnCtx])

deprecated Use on

 * ctx {jQuery} The element in which the event will be listened for
 * e {String} Event name
 * data {Object} Additional information that the handler gets as e.data
 * fn {Function} Handler
 * fnCtx {Object} Handler context

Adds a live event handler to a block, based on a specified element where the event will be listened for

####.liveCtxUnbind(ctx, e, [fn], [fnCtx])

deprecated Use on

 * ctx {jQuery} The element in which the event was being listened for
 * e {String} Event name
 * fn {Function} Handler
 * fnCtx {Object} Handler context

Removes a live event handler from a block, based on a specified element where the event was being listened for

###Instance methods


####.elemParams(elem)

 * elem {String|jQuery} Element

Retrieves parameters of a block element

####.elemify(elem, elemName)

 * elem {jQuery} Element
 * elemName {String} Name

Elemify given element

####.buildSelector([elem], [modName], [modVal])

 * elem {String} Element name
 * modName {String} Modifier name
 * modVal {String} Modifier value

Builds a CSS selector corresponding to a block/element and modifier

####.destruct([keepDOM])

 * keepDOM {Boolean} Whether to keep the block's DOM nodes in the document

Deletes a block

####.findBlocksInside([elem], block)

 * elem {String|jQuery} Block element
 * block {String|Object} Name or description (block,modName,modVal) of the block to find

Finds blocks inside the current block or its elements (including context)

####.findBlockInside([elem], block)

 * elem {String|jQuery} Block element
 * block {String|Object} Name or description (block,modName,modVal) of the block to find

Finds the first block inside the current block or its elements (including context)

####.findBlocksOutside([elem], block)

 * elem {String|jQuery} Block element
 * block {String|Object} Name or description (block,modName,modVal) of the block to find

Finds blocks outside the current block or its elements (including context)

####.findBlockOutside([elem], block)

 * elem {String|jQuery} Block element
 * block {String|Object} Name or description (block,modName,modVal) of the block to find

Finds the first block outside the current block or its elements (including context)

####.findBlocksOn([elem], block)

 * elem {String|jQuery} Block element
 * block {String|Object} Name or description (block,modName,modVal) of the block to find

Finds blocks on DOM elements of the current block or its elements

####.findBlockOn([elem], block)

Finds the first block on DOM elements of the current block or its elements

 * elem {String|jQuery} Block element
 * block {String|Object} Name or description (block,modName,modVal) of the block to find

####.bindToDomElem(domElem, event, fn)

 * domElem {jQuery} DOM element where the event will be listened for
 * event {String|Object} Event name or event object
 * fn {Function} Handler function, which will be executed in the block's context

Adds an event handler for any DOM element

####.bindToDoc(event, fn)

 * event {String} Event name
 * fn {Function} Handler function, which will be executed in the block's context

Adds an event handler to the document

####.bindToWin(event, fn)

 * event {String} Event name
 * fn {Function} Handler function, which will be executed in the block's context

Adds an event handler to the window

####.bindTo([elem], event, fn)

 * elem {jQuery|String} Element
 * event {String} Event name
 * fn {Function} Handler function, which will be executed in the block's context

Adds an event handler to the block's main DOM elements or its nested elements

####.unbindFromDomElem(domElem, event)

 * domElem {jQuery} DOM element where the event was being listened for
 * event {String} Event name

Removes event handlers from any DOM element

####.unbindFromDoc(event)

 * event {String} Event name

Removes event handler from document

####.unbindFromWin(event)

 * event {String} Event name

Removes event handler from window

####.unbindFrom([elem], event)

 * elem {jQuery|String} Nested element
 * event {String} Event name

Removes event handlers from the block's main DOM elements or its nested elements

####.trigger(e, [data])

 * e {String} Event name
 * data {Object} Additional information

Triggers block event handlers and live event handlers

####.setMod([elem], modName, modVal)

 * elem {jQuery} Nested element
 * modName {String} Modifier name
 * modVal {String} Modifier value

Sets a modifier for a block/nested element

####.findElem([ctx], names, [modName], [modVal])

 * ctx {String|jQuery} Element where search is being performed
 * names {String} Nested element name (or names separated by spaces)
 * modName {String} Modifier name
 * modVal {String} Modifier value

Finds elements nested in a block

####.elem(names, [modName], [modVal])

 * names {String} Nested element name (or names separated by spaces)
 * modName {String} Modifier name
 * modVal {String} Modifier value

Lazy search for elements nested in a block (caches results)

####.dropElemCache(names, [modName], [modVal])

 * names {String} Nested element name (or names separated by spaces)
 * modName {String} Modifier name
 * modVal {String} Modifier value

Clearing the cache for elements

####.containsDomElem(domElem)

 * domElem {jQuery} DOM element

Checks whether a DOM element is in a block

