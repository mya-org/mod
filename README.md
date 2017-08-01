# mod

A module loader for mya, forked from [https://github.com/fex-team/mod](https://github.com/fex-team/mod)

# 说明

原先 `fex-team/mod/mod.js` 会在全局注册 `require` 和 `define` 方法，如果项目中使用了 `require.js` 或者其他包含自定义加载器的第三方库，可能会产生冲突（第三方加载器也在全局注册了 `require` 或 `define` 方法）。为了避免这种情况发生，我们做了一点调整，把 `require` 和 `define` 方法挂载到了全局的 `__M` 变量下，即 `__M.require` 和 `__M.define`。

配合 `mya-hook-module` 插件，我们会把源码中调用 `require` 和 `define` 的地方替换为 `__M.require` 和 `__M.define`，这意味着在开发时和原来一样，直接写 `require('xxx')` 即可。

# 相关项目

构建工具：mya
替换插件：mya-hook-module