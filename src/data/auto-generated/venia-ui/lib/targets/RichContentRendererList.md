
Implementation of our 'richContentRenderers' target. This will gather
RichContentRenderer declarations { importPath, componentName } from all
interceptors, and then tap `builtins.transformModules` to inject a module
transform into the build which is configured to generate an array of modules
to be imported and then exported.

An instance of this class is made available when you use VeniaUI's
`richContentRenderers` target.

Add a rendering strategy to the RichContent component.

**Parameters**

| Name | Type | Description |
| --- | --- | --- |
| strategy | `Object` | Describes the rich content renderer to include |
| strategy.importPath | `string` | Import path to the RichContentRenderer module. Should be package-absolute. |
| strategy.componentName | `string` | Name that will be given to the imported renderer in generated code. This is used for debugging purposes. |

**Source Code**: [pwa-studio/packages/venia-ui/lib/targets/RichContentRendererList.js](https://github.com/magento/pwa-studio/blob/develop/packages/venia-ui/lib/targets/RichContentRendererList.js)
