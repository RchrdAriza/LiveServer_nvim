### requirements

- nodejs/npm
- live-server
- [notify](https://github.com/rcarriga/nvim-notify) (opcional)
- [which-key](https://github.com/folke/which-key.nvim) (opcional)

Install live-server using ```npm``` with the following command:
```bash
npm i live-server
```
Copy the following functions to your neovim configuration file:

```* to start live-server```
```lua
function live_server()

  -- In case you have the notify plugin installed uncomment the following lines
  -- local notify = require("notify")
  -- notify("Starting live server...")
  vim.cmd("silent !live-server . >/dev/null 2>&1 &")
  local message = "Starting live server"
  vim.api.nvim_echo({{message}}, true, {})
end
```
```* to stop live-server```
```lua
function stop_live_server()
  
  -- In case you have the notify plugin installed uncomment the following lines
  -- local notify = require("notify")
  -- notify("Stopping live server")
  vim.cmd("silent !pkill -f live-server")
  local message = "Stopping live server"
  vim.api.nvim_echo({{message}}, true, {})
end
```

To use the functions you can call them from the neovim command line like this:
```:lua live-server()``` to start live-server.

```:lua stop_live_server()``` to stop live-server.

## Optional configuration

You can use the <a href='https://github.com/folke/which-key.nvim' target='_blank'>which-key</a> plugin to facilitate the use of the functions by adding the following lines to your which-key configuration:
```lua
-- To create a new option group
require("which-key").register({
  ["<leader>w"] = {
    name = "Web development",
    l = { "<cmd>lua live-server()<cr>", "Start live-server" },
    s = { "<cmd>lua stop_live_server()<cr>", "Stop live-server"}
  },
})
```
You may also be interested in: [MarkdownLive](https://www.github.com/RchrdAlv/NvimOnMy_Way)

Alternatively you can use my neovim configuration, which already has this function and others. [here](https://www.github.com/RchrdAlv/NvimOnMy_Way)
