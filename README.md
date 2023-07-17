# Eleventy sass example doesn't work

The elventy sass example doesn't update the resulting css if a dependency changed.

https://www.11ty.dev/docs/languages/custom/#example-add-sass-support-to-eleventy

## Steps to reproduce

1. Start eleventy: `npx @11ty/eleventy --watch`
2. Open `_site/index.css`
3. Change the content of `src/_shared.scss` (e.g. the background color)
4. `_site/index.css` is *not* updated :/

## Terminal output

```
> npx @11ty/eleventy --watch

[11ty] Writing _site/index.css from ./src/index.scss
[11ty] Wrote 1 file in 0.04 seconds (v2.0.1)
[11ty] Watching…
[11ty] File changed: src/_shared.scss
[11ty] Writing _site/index.css from ./src/index.scss
[11ty] Wrote 1 file in 0.00 seconds (v2.0.1)
[11ty] Watching…
```

## Debug Terminal output

```
> DEBUG=*Eleventy* npx @11ty/eleventy --watch

  Eleventy:cmd command: eleventy { _: [], quiet: null, version: false, watch: true, dryrun: false, help: false, serve: false, incremental: false, 'ignore-initial': false } +0ms
  Eleventy:EventBus Setting up global EventBus. +0ms
  Eleventy:UserConfig Resetting EleventyConfig to initial values. +0ms
  Eleventy:UserConfig Adding universal filter 'slug' +4ms
  Eleventy:UserConfig Adding universal filter 'slugify' +0ms
  Eleventy:UserConfig Adding universal filter 'url' +0ms
  Eleventy:UserConfig Adding universal filter 'log' +1ms
  Eleventy:UserConfig Adding universal filter 'serverlessUrl' +0ms
  Eleventy:UserConfig Adding universal filter 'getCollectionItemIndex' +0ms
  Eleventy:UserConfig Adding universal filter 'getCollectionItem' +0ms
  Eleventy:UserConfig Adding universal filter 'getPreviousCollectionItem' +0ms
  Eleventy:UserConfig Adding universal filter 'getNextCollectionItem' +0ms
  Eleventy:TemplateConfig rootConfig { templateFormats: [ 'liquid',   'ejs', 'md',       'hbs', 'mustache', 'haml', 'pug',      'njk', 'html',     '11ty.js' ], pathPrefix: '/', markdownTemplateEngine: 'liquid', htmlTemplateEngine: 'liquid', htmlOutputSuffix: '-o', dataFileSuffixes: [ '.11tydata', '' ], dataFileDirBaseNameOverride: false, keys: { package: 'pkg', layout: 'layout', permalink: 'permalink', permalinkRoot: 'permalinkBypassOutputDir', engineOverride: 'templateEngineOverride', computed: 'eleventyComputed' }, dir: { input: '.', includes: '_includes', data: '_data', output: '_site' }, handlebarsHelpers: {}, nunjucksFilters: {} } +0ms
  Eleventy Setting process.env.ELEVENTY_ROOT: '/Users/lmestel/…/tmp/eleventy-dependency-bug' +0ms
  Dev:Eleventy:TemplateConfig Merging via getConfig (first time) +0ms
  Eleventy:TemplateConfig Merging config with .eleventy.js +1ms
  Eleventy:TemplateConfig overrides: {} +80ms
  Eleventy:TemplateConfig Current configuration: { pathPrefix: '/', markdownTemplateEngine: 'liquid', htmlTemplateEngine: 'liquid', htmlOutputSuffix: '-o', dataFileSuffixes: [ '.11tydata', '' ], dataFileDirBaseNameOverride: false, keys: { package: 'pkg', layout: 'layout', permalink: 'permalink', permalinkRoot: 'permalinkBypassOutputDir', engineOverride: 'templateEngineOverride', computed: 'eleventyComputed' }, dir: { input: 'src', includes: '_includes', data: '_data', output: '_site' }, handlebarsHelpers: { slug: [Function (anonymous)], slugify: [Function (anonymous)], url: [Function (anonymous)], log: [Function (anonymous)], serverlessUrl: [Function (anonymous)], getCollectionItemIndex: [Function (anonymous)], getCollectionItem: [Function (anonymous)], getPreviousCollectionItem: [Function (anonymous)], getNextCollectionItem: [Function (anonymous)] }, nunjucksFilters: { slug: [Function (anonymous)], slugify: [Function (anonymous)], url: [Function (anonymous)], log: [Function (anonymous)], serverlessUrl: [Function (anonymous)], getCollectionItemIndex: [Function (anonymous)], getCollectionItem: [Function (anonymous)], getPreviousCollectionItem: [Function (anonymous)], getNextCollectionItem: [Function (anonymous)] }, templateFormats: [ 'liquid',   'ejs', 'md',       'hbs', 'mustache', 'haml', 'pug',      'njk', 'html',     '11ty.js', 'scss' ], transforms: {}, linters: {}, globalData: {}, layoutAliases: {}, layoutResolution: true, passthroughCopies: {}, liquidOptions: {}, liquidTags: {}, liquidFilters: { slug: [Function (anonymous)], slugify: [Function (anonymous)], url: [Function (anonymous)], log: [Function (anonymous)], serverlessUrl: [Function (anonymous)], getCollectionItemIndex: [Function (anonymous)], getCollectionItem: [Function (anonymous)], getPreviousCollectionItem: [Function (anonymous)], getNextCollectionItem: [Function (anonymous)] }, liquidShortcodes: {}, liquidPairedShortcodes: {}, nunjucksEnvironmentOptions: {}, nunjucksPrecompiledTemplates: {}, nunjucksAsyncFilters: {}, nunjucksTags: {}, nunjucksGlobals: {}, nunjucksAsyncShortcodes: {}, nunjucksShortcodes: {}, nunjucksAsyncPairedShortcodes: {}, nunjucksPairedShortcodes: {}, handlebarsShortcodes: {}, handlebarsPairedShortcodes: {}, javascriptFunctions: { slug: [Function (anonymous)], slugify: [Function (anonymous)], url: [Function (anonymous)], log: [Function (anonymous)], serverlessUrl: [Function (anonymous)], getCollectionItemIndex: [Function (anonymous)], getCollectionItem: [Function (anonymous)], getPreviousCollectionItem: [Function (anonymous)], getNextCollectionItem: [Function (anonymous)] }, pugOptions: {}, ejsOptions: {}, markdownHighlighter: null, libraryOverrides: {}, dynamicPermalinks: true, useGitIgnore: true, ignores: Set(2) { '**/node_modules/**', '.git/**' }, watchIgnores: Set(2) { '**/node_modules/**', '.git/**' }, dataDeepMerge: true, watchJavaScriptDependencies: true, additionalWatchTargets: [], serverOptions: {}, chokidarConfig: {}, watchThrottleWaitTime: 0, frontMatterParsingOptions: undefined, dataExtensions: Map(0) {}, extensionMap: Set(1) { { key: 'scss', extension: 'scss', outputFileExtension: 'css', compile: [Function: compile] } }, quietMode: false, events: AsyncEventEmitter { _events: [Object: null prototype] {}, _eventsCount: 0, _maxListeners: undefined, [Symbol(kCapture)]: false }, benchmarkManager: BenchmarkManager { benchmarkGroups: { Configuration: [BenchmarkGroup], Aggregate: [BenchmarkGroup] }, isVerbose: true, start: 158.00537490844727 }, plugins: [], useTemplateCache: true, precompiledCollections: {}, dataFilterSelectors: Set(0) {}, libraryAmendments: {}, serverPassthroughCopyBehavior: 'copy', urlTransforms: [] } +1ms
  Eleventy Eleventy warm up time (in ms) 245.6894998550415 +82ms
  Eleventy:TemplatePassthroughManager Resetting counts to 0 +0ms
  Eleventy:EleventyFiles .gitignore,.eleventyignore,src/.eleventyignore ignoring: ./node_modules/** +0ms
  Eleventy:EleventyFiles .gitignore,.eleventyignore,src/.eleventyignore ignoring: ./_site/** +0ms
  Eleventy Directories:
  Eleventy Input (Dir): src
  Eleventy Input (File): undefined
  Eleventy Data: src/_data
  Eleventy Includes: src/_includes
  Eleventy Layouts: undefined
  Eleventy Output: _site
  Eleventy Template Formats: liquid,ejs,md,hbs,mustache,haml,pug,njk,html,11ty.js,scss
  Eleventy Verbose Output: false +2ms
  Eleventy:EleventyFiles Searching for: [ './src/**/*.{liquid,ejs,md,hbs,mustache,haml,pug,njk,html,11ty.js,11ty.cjs,scss}' ] +6ms
  Eleventy:FastGlobManager Glob search ('templates') searching for: [ './src/**/*.{liquid,ejs,md,hbs,mustache,haml,pug,njk,html,11ty.js,11ty.cjs,scss}' ] +0ms
  Eleventy:FastGlobManager Glob search ('templates') ignoring: [ 'node_modules/**', '_site/**', 'src/_includes/**', 'src/_data/**', '**/node_modules/**', '.git/**' ] +0ms
  Eleventy:TemplatePassthroughManager TemplatePassthrough copy started. +15ms
  Eleventy:TemplatePassthroughManager `addPassthroughCopy` config API paths: {} +1ms
  Eleventy:TemplatePassthroughManager `addPassthroughCopy` config API normalized paths: [] +0ms
  Dev:Eleventy:Template new Template('./src/_shared.scss') +0ms
  Dev:Eleventy:Template './src/_shared.scss' getData +0ms
  Dev:Eleventy:TemplateData getLocalDataPaths('./src/_shared.scss') +0ms
  Dev:Eleventy:TemplateData parsed.dir: './src' +0ms
  Eleventy:TemplateData Using [ '.11tydata', '' ] suffixes to find data files. +0ms
  Dev:Eleventy:TemplateData allDirs: [ './src' ] +0ms
  Dev:Eleventy:TemplateData dirStr: './src'; inputDir: './src' +0ms
  Eleventy:TemplateData getLocalDataPaths('./src/_shared.scss'): [ './src/_shared.11tydata.js', './src/_shared.11tydata.cjs', './src/_shared.11tydata.json', './src/_shared.json', './src/src.11tydata.js', './src/src.11tydata.cjs', './src/src.11tydata.json', './src/src.json' ] +0ms
  Eleventy:TemplateWriter ./src/_shared.scss adding to template map. +0ms
  Dev:Eleventy:Template new Template('./src/index.scss') +1ms
  Dev:Eleventy:Template './src/index.scss' getData +0ms
  Dev:Eleventy:TemplateData getLocalDataPaths('./src/index.scss') +1ms
  Dev:Eleventy:TemplateData parsed.dir: './src' +0ms
  Eleventy:TemplateData Using [ '.11tydata', '' ] suffixes to find data files. +1ms
  Dev:Eleventy:TemplateData allDirs: [ './src' ] +0ms
  Dev:Eleventy:TemplateData dirStr: './src'; inputDir: './src' +0ms
  Eleventy:TemplateData getLocalDataPaths('./src/index.scss'): [ './src/index.11tydata.js', './src/index.11tydata.cjs', './src/index.11tydata.json', './src/index.json', './src/src.11tydata.js', './src/src.11tydata.cjs', './src/src.11tydata.json', './src/src.json' ] +0ms
  Eleventy:TemplateWriter ./src/index.scss adding to template map. +0ms
  Eleventy:TemplatePassthroughManager TemplatePassthrough copy finished. Current count: 0 +2ms
  Eleventy:FastGlobManager Glob search ('global-data') searching for: [ './src/_data/**/*.{json,cjs,js}' ] +11ms
  Dev:Eleventy:Template './src/_shared.scss' getData getTemplateDirectoryData and getGlobalData +2ms
  Dev:Eleventy:Template './src/index.scss' getData getTemplateDirectoryData and getGlobalData +0ms
  Eleventy:Template Template date: using file’s 'birthtimeMs' for './src/_shared.scss' of 2023-07-17T10:14:19.132Z (from 1689588859132.8088) +0ms
  Dev:Eleventy:Template './src/_shared.scss' getData mergedData +2ms
  Dev:Eleventy:Template './src/_shared.scss' getMapped() +0ms
  Eleventy:Template Template date: using file’s 'birthtimeMs' for './src/index.scss' of 2023-07-17T10:14:06.408Z (from 1689588846408.829) +1ms
  Dev:Eleventy:Template './src/index.scss' getData mergedData +0ms
  Dev:Eleventy:Template './src/index.scss' getMapped() +0ms
  Eleventy:TemplateMap Caching collections objects. +0ms
  Eleventy:TemplateMap Collection: collections.all size: 2 +1ms
  Eleventy:TemplateMap Collection: collections.all size: 2 +0ms
  Dev:Eleventy:TemplateContent './src/_shared.scss' compile() using engine: 'scss' +0ms
  Dev:Eleventy:TemplateContent './src/_shared.scss' getCompiledTemplate function created +0ms
  Dev:Eleventy:TemplateMap Added this.map[...].templateContent, outputPath, et al for one map entry +0ms
  Dev:Eleventy:TemplateContent './src/index.scss' compile() using engine: 'scss' +0ms
  Dev:Eleventy:TemplateContent './src/index.scss' getCompiledTemplate function created +22ms
  Dev:Eleventy:TemplateContent './src/index.scss' getCompiledTemplate called, rendered content created +1ms
  Dev:Eleventy:TemplateMap Added this.map[...].templateContent, outputPath, et al for one map entry +23ms
  Dev:Eleventy:TemplateWriter TemplateMap cache complete. +0ms
  Eleventy:TemplateWriter Template map created. +28ms
  Eleventy:Logger Writing _site/index.css from ./src/index.scss +0ms
  Eleventy:Template _site/index.css written.. +25ms
  Eleventy:Benchmark Benchmark      8ms   6%     1× (Aggregate) Searching the file system (templates) +0ms
  Eleventy:Logger Benchmark     22ms  17%     2× (Aggregate) Template Compile +1ms
  Eleventy:Benchmark Benchmark     22ms  17%     2× (Aggregate) Template Compile +0ms
  Eleventy:Logger Benchmark     22ms  16%     1× (Aggregate) > Compile > ./src/index.scss +0ms
  Eleventy:Benchmark Benchmark     22ms  16%     1× (Aggregate) > Compile > ./src/index.scss +0ms
[11ty] Wrote 1 file in 0.05 seconds (v2.0.1)
  Eleventy Finished writing templates. +45ms
  Eleventy
  Eleventy       Getting frustrated? Have a suggestion/feature request/feedback?
  Eleventy       I want to hear it! Open an issue: https://github.com/11ty/eleventy/issues/new +0ms
  Eleventy:TemplatePassthroughManager `addPassthroughCopy` config API paths: {} +29ms
  Eleventy:TemplatePassthroughManager `addPassthroughCopy` config API normalized paths: [] +0ms
  Eleventy:FastGlobManager Glob search ('js-dependencies') searching for: [ './src/**/*.11tydata.js' ] +29ms
  Eleventy:FastGlobManager Glob search ('js-dependencies') ignoring: [ '**/node_modules/**' ] +0ms
  Eleventy Watching for changes to: [ './package.json', './src/**/*.{liquid,ejs,md,hbs,mustache,haml,pug,njk,html,11ty.js,11ty.cjs,scss}', './src/_includes/**', './src/_data/**', './.gitignore', './.eleventyignore', './src/.eleventyignore', './.eleventy.js', './eleventy.config.js', './eleventy.config.cjs', './src/**/*.{json,11tydata.cjs,11tydata.js}' ] +2ms
  Eleventy Ignoring watcher changes to: [ 'node_modules/**', '_site/**', './**/node_modules/**', './.git/**' ] +0ms
  Eleventy:Benchmark Benchmark      3ms NaN%     1× (Watch) Start up --watch +3ms
[11ty] Watching…

[11ty] File changed: src/_shared.scss
  Eleventy:DeleteRequireCache Deleting '/Users/lmestel/…/tmp/eleventy-dependency-bug/src/_shared.scss' from `require` cache. +0ms
  Eleventy Restarting +22s
  Eleventy:TemplatePassthroughManager Resetting counts to 0 +22s
  Eleventy:EleventyFiles .gitignore,.eleventyignore,src/.eleventyignore ignoring: ./node_modules/** +22s
  Eleventy:EleventyFiles .gitignore,.eleventyignore,src/.eleventyignore ignoring: ./_site/** +0ms
  Eleventy:TemplatePassthroughManager Resetting counts to 0 +4ms
  Eleventy:EleventyFiles .gitignore,.eleventyignore,src/.eleventyignore ignoring: ./node_modules/** +3ms
  Eleventy:EleventyFiles .gitignore,.eleventyignore,src/.eleventyignore ignoring: ./_site/** +0ms
  Eleventy Directories:
  Eleventy Input (Dir): src
  Eleventy Input (File): undefined
  Eleventy Data: src/_data
  Eleventy Includes: src/_includes
  Eleventy Layouts: undefined
  Eleventy Output: _site
  Eleventy Template Formats: liquid,ejs,md,hbs,mustache,haml,pug,njk,html,11ty.js,scss
  Eleventy Verbose Output: false +5ms
  Eleventy:EleventyFiles Searching for: [ './src/**/*.{liquid,ejs,md,hbs,mustache,haml,pug,njk,html,11ty.js,11ty.cjs,scss}' ] +1ms
  Eleventy:FastGlobManager Glob search ('templates') searching for: [ './src/**/*.{liquid,ejs,md,hbs,mustache,haml,pug,njk,html,11ty.js,11ty.cjs,scss}' ] +22s
  Eleventy:FastGlobManager Glob search ('templates') ignoring: [ 'node_modules/**', '_site/**', 'src/_includes/**', 'src/_data/**', '**/node_modules/**', '.git/**' ] +0ms
  Eleventy:TemplatePassthroughManager TemplatePassthrough copy started. +1ms
  Eleventy:TemplatePassthroughManager `addPassthroughCopy` config API paths: {} +0ms
  Eleventy:TemplatePassthroughManager `addPassthroughCopy` config API normalized paths: [] +0ms
  Dev:Eleventy:Template './src/_shared.scss' getData +22s
  Dev:Eleventy:TemplateData getLocalDataPaths('./src/_shared.scss') +22s
  Dev:Eleventy:TemplateData parsed.dir: './src' +0ms
  Eleventy:TemplateData Using [ '.11tydata', '' ] suffixes to find data files. +22s
  Dev:Eleventy:TemplateData allDirs: [ './src' ] +0ms
  Dev:Eleventy:TemplateData dirStr: './src'; inputDir: './src' +0ms
  Eleventy:TemplateData getLocalDataPaths('./src/_shared.scss'): [ './src/_shared.11tydata.js', './src/_shared.11tydata.cjs', './src/_shared.11tydata.json', './src/_shared.json', './src/src.11tydata.js', './src/src.11tydata.cjs', './src/src.11tydata.json', './src/src.json' ] +0ms
  Eleventy:TemplateWriter ./src/_shared.scss adding to template map. +22s
  Dev:Eleventy:Template './src/index.scss' getData +1ms
  Dev:Eleventy:TemplateData getLocalDataPaths('./src/index.scss') +1ms
  Dev:Eleventy:TemplateData parsed.dir: './src' +0ms
  Eleventy:TemplateData Using [ '.11tydata', '' ] suffixes to find data files. +1ms
  Dev:Eleventy:TemplateData allDirs: [ './src' ] +0ms
  Dev:Eleventy:TemplateData dirStr: './src'; inputDir: './src' +0ms
  Eleventy:TemplateData getLocalDataPaths('./src/index.scss'): [ './src/index.11tydata.js', './src/index.11tydata.cjs', './src/index.11tydata.json', './src/index.json', './src/src.11tydata.js', './src/src.11tydata.cjs', './src/src.11tydata.json', './src/src.json' ] +0ms
  Eleventy:TemplateWriter ./src/index.scss adding to template map. +0ms
  Eleventy:TemplatePassthroughManager TemplatePassthrough copy finished. Current count: 0 +1ms
  Eleventy:FastGlobManager Glob search ('global-data') searching for: [ './src/_data/**/*.{json,cjs,js}' ] +1ms
  Dev:Eleventy:Template './src/_shared.scss' getData getTemplateDirectoryData and getGlobalData +0ms
  Dev:Eleventy:Template './src/index.scss' getData getTemplateDirectoryData and getGlobalData +1ms
  Eleventy:Template Template date: using file’s 'birthtimeMs' for './src/index.scss' of 2023-07-17T10:14:06.408Z (from 1689588846408.829) +22s
  Dev:Eleventy:Template './src/index.scss' getData mergedData +0ms
  Dev:Eleventy:Template './src/index.scss' getMapped() +0ms
  Eleventy:Template Template date: using file’s 'birthtimeMs' for './src/_shared.scss' of 2023-07-17T10:14:19.132Z (from 1689588859132.8088) +0ms
  Dev:Eleventy:Template './src/_shared.scss' getData mergedData +0ms
  Dev:Eleventy:Template './src/_shared.scss' getMapped() +0ms
  Eleventy:TemplateMap Caching collections objects. +22s
  Eleventy:TemplateMap Collection: collections.all size: 2 +1ms
  Eleventy:TemplateMap Collection: collections.all size: 2 +0ms
  Dev:Eleventy:TemplateContent './src/index.scss' compile() using engine: 'scss' +22s
  Dev:Eleventy:TemplateContent './src/index.scss' getCompiledTemplate called, rendered content created +0ms
  Dev:Eleventy:TemplateMap Added this.map[...].templateContent, outputPath, et al for one map entry +22s
  Dev:Eleventy:TemplateContent './src/_shared.scss' compile() using engine: 'scss' +0ms
  Dev:Eleventy:TemplateContent './src/_shared.scss' getCompiledTemplate function created +0ms
  Dev:Eleventy:TemplateMap Added this.map[...].templateContent, outputPath, et al for one map entry +0ms
  Dev:Eleventy:TemplateWriter TemplateMap cache complete. +22s
  Eleventy:TemplateWriter Template map created. +3ms
  Eleventy:Logger Writing _site/index.css from ./src/index.scss +22s
  Eleventy:Template _site/index.css written.. +2ms
  Eleventy:Benchmark Benchmark      0ms   3%     1× (Aggregate) Searching the file system (templates) +22s
  Eleventy:Benchmark Benchmark      0ms   2%     1× (Aggregate) Searching the file system (data) +1ms
  Eleventy:Benchmark Benchmark      1ms   6%     2× (Aggregate) Template Read +0ms
  Eleventy:Benchmark Benchmark      1ms   8%     1× (Aggregate) Template Write +0ms
[11ty] Wrote 1 file in 0.01 seconds (v2.0.1)
  Eleventy Finished writing templates. +6ms
  Eleventy
  Eleventy       Getting frustrated? Have a suggestion/feature request/feedback?
  Eleventy       I want to hear it! Open an issue: https://github.com/11ty/eleventy/issues/new +0ms
  Eleventy:FastGlobManager Glob search ('js-dependencies') searching for: [ './src/**/*.11tydata.js' ] +5ms
  Eleventy:FastGlobManager Glob search ('js-dependencies') ignoring: [ '**/node_modules/**' ] +0ms
  Eleventy:Logger Watching… +3ms
```