# cmp-nvim-insert-text-lsp

nvim-cmp source for neovim's built-in language server client. This source is a fork from [cmp-nvim-lsp](https://github.com/hrsh7th/cmp-nvim-lsp)
but instead of using label as the completion item text in cmp, it uses the insert text as the completion item text. 
In other words, what you see in the cmp completion menu is what will be inserted as text.

This is useful for language server such as `clangd`, where even when you disable the snippet support, 
the completion item text still shows parenthesis and typed arguments, which I found quite distracting.
With this plugin, the completion menu items are more aligned with the vscode completion menu items.

## Using nvim-lsp on c++ file

![image](https://user-images.githubusercontent.com/38927155/154865731-634f40ab-1781-4280-aeca-ec6ed8506cca.png)

## Using nvim-insert-text-lsp on c++ file

<img width="808" alt="image" src="https://user-images.githubusercontent.com/38927155/154865868-5f185233-b8db-499b-a318-1402699e0482.png">

## Using vscode on c++ file

<img width="755" alt="image" src="https://user-images.githubusercontent.com/38927155/154865896-d7df83d0-d88a-4c09-9b75-4c16580d6613.png">

# Setup

```lua
-- This setup the source only for c++
require'cmp'.setup.filetype({ "cpp" }, {
  sources = {
    { name = 'nvim_insert_text_lsp' }
  }
})

-- The nvim-cmp almost supports LSP's capabilities so You should advertise it to LSP servers..
local capabilities = require('cmp_insert_text_lsp').default_capabilities()

-- The following example advertise capabilities to `clangd`.
require'lspconfig'.clangd.setup {
  capabilities = capabilities,
}
```
