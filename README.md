# cmp-nvim-insert-text-lsp

nvim-cmp source for neovim's built-in language server client. This source is a fork from [cmp-nvim-lsp](https://github.com/hrsh7th/cmp-nvim-lsp)
but instead of using label as the completion item text in cmp, it uses the insert text as the completion item text. 
In other words, what you see in the cmp completion menu is what will be inserted as text.

This is useful for language server such as `clangd`, where even when you disable the snippet support, 
the completion item text still shows parenthesis and typed arguments, which I found quite distracting.
With this plugin, the completion menu items are more aligned with the vscode completion menu items.

## Using nvim-lsp on c++ file

## Using nvim-insert-text-lsp on c++ file

## Using vscode on c++ file

# Setup

```lua
-- This setup the source only for c++
require'cmp'.setup.filetype({ "cpp" }, {
  sources = {
    { name = 'nvim_insert_text_lsp' }
  }
})

-- This enable all the capabilities except for snippet support
local capabilities = vim.lsp.protocol.make_client_capabilities()
capabilities = require('cmp_nvim_insert_text_lsp').update_capabilities(capabilities)

-- The following example advertise capabilities to `clangd`.
require'lspconfig'.clangd.setup {
  capabilities = capabilities,
}
```

