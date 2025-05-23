
A module that third party code can modify.

When Webpack loads a module into its bundles, it processes the source code
through a set of rules generated by Buildpack. A TargetableModule is a reference
to that source file, meant to be passed to interceptors. Inside
interceptors, extensions and projects can configure the TargetableModule to
transform it in many ways.

* [TargetableModule](#TargetableModule)
    * [new TargetableModule(file, trackingOwner)](#new_TargetableModule_new)
    * [.addTransform(type, transformModule, options)](#TargetableModule+addTransform) ⇒ `this`
    * [.flush()](#TargetableModule+flush) ⇒ `Array.<TransformRequest>`
    * [.insertAfterSource(after, insert, [options])](#TargetableModule+insertAfterSource) ⇒ `this`
    * [.insertBeforeSource(before, insert, [options])](#TargetableModule+insertBeforeSource) ⇒ `this`
    * [.prependSource(insert)](#TargetableModule+prependSource) ⇒ `this`
    * [.spliceSource(instruction)](#TargetableModule+spliceSource) ⇒ `this`

Create a TargetableModule representing a file.

**Parameters**

| Name | Type | Description |
| --- | --- | --- |
| file | `string` | Path to the underlying source file. |
| trackingOwner | `Trackable` | Parent object for debugging purposes. |

Add a transform request to this module's queue. The `fileToTransform` of
the transform request is automatically set to this module's filename.

**Chainable**  
**Returns:**
**Parameters**

| Name | Type | Description |
| --- | --- | --- |
| type | `TransformType` | Transform type |
| transformModule | `string` | The Node module that runs the transform, such as a Webpack loader for type `source` or a Babel plugin for type `babel`. |
| options | `Object` | Configuration object to send to the transformModule. |

Empty this module's queue of transforms, returning them as an array.

**Returns:**
`Array.<TransformRequest>`
   — An array of Transform requests.

Insert text into the module contents, immediately following the location
of the search string if it is found.

**Chainable**  
**Returns:**
**Parameters**

| Name | Type | Description |
| --- | --- | --- |
| after | `string` | Text string in the module code to place the new content after. |
| insert | `string` | Text to insert after the search string. |
| [options] | `Object` | Additional loader options. |
| [options.remove] | `number` | Number of characters to delete forward, after the search string. |

Insert text into the module contents, immediately before the location
of the search string if it is found.

**Chainable**  
**Returns:**
**Parameters**

| Name | Type | Description |
| --- | --- | --- |
| before | `string` | Text string in the module code to place the new content before. |
| insert | `string` | Text to insert before the search string. |
| [options] | `Object` | Additional loader options. |
| [options.remove] | `number` | Number of characters to delete forward, after the search string. |

Add text to the beginning of a file.

**Chainable**  
**Returns:**
**Parameters**

| Name | Type | Description |
| --- | --- | --- |
| insert | `string` | Text to insert up top |

Do any splice operation supported by [splice-source-loader](https://github.com/magento/pwa-studio/blob/develop/packages/pwa-buildpack/lib/WebpackTools/loaders/splice-source-loader.js).

**Chainable**  
**Returns:**
**Parameters**

| Name | Type | Description |
| --- | --- | --- |
| instruction | `object` | Splice instruction. |

**Source Code**: [pwa-studio/packages/pwa-buildpack/lib/WebpackTools/targetables/TargetableModule.js](https://github.com/magento/pwa-studio/blob/develop/packages/pwa-buildpack/lib/WebpackTools/targetables/TargetableModule.js)
