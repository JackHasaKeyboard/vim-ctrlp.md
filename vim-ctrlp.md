|                                                   |                                                               | 
|---------------------------------------------------|---------------------------------------------------------------| 
| `CtrlP` / `CtrlP` `[starting directory]`          | Invoke CtrlP in find file mode                                | 
| `CtrlPBuffer` / `CtrlPMRU`                        | Invoke CtrlP in find buffer or find MRU file mode             | 
| `CtrlPMixed`                                      | Search in Files-comma- Buffers and MRU files at the same time | 
| `help ctrlp-commands` / `help ctrlp-extensions`   | Other commands                                                | 

#### Within CtrlP

|      |           |      |   |                                                                                                                     | 
|------|-----------|------|---|---------------------------------------------------------------------------------------------------------------------| 
| F5   |           |      |   | Purge the cache for the current directory to get new files-comma- remove deleted files and apply new ignore options | 
| Ctrl |           |      |   |                                                                                                                     | 
|      | f / b     |      |   | Cycle between modes                                                                                                 | 
|      | d         |      |   | Switch to filename only search instead of full path                                                                 | 
|      | r         |      |   | Switch to regexp mode                                                                                               | 
|      | j / ↓     |      |   | Next result                                                                                                         | 
|      | k / ↑     |      |   | Previous result                                                                                                     | 
|      | t / v / x |      |   | Open the selected entry in a new tab or in a new split                                                              | 
|      | n         | Ctrl | p | Select the next/previous string in the prompt's history                                                             | 
|      | y         |      |   | Create a new file and its parent directories                                                                        | 
|      | z         |      |   | Mark/unmark multiple files                                                                                          | 
|      |           | Ctrl | o | Open marked files                                                                                                   | 

`help ctrlp-mappings` / `submit ?` Show more mapping help

|                 |                                                                    |
|-----------------|--------------------------------------------------------------------|
| `..`            | Go up the directory tree, one parent for every additional dot      |
| `:``[command]`  | Execute on the opening file(s)                                     |
| `[no]`          | Jump to line                                                       |
| `diffthis`      | When opening multiple files to run `diffthis` on the first 4 files |

#### Basic Options
Change the default mapping and the default command to invoke CtrlP:

`let g:ctrlp_map = '<c-p>'`
`let g:ctrlp_cmd = 'CtrlP'`

When invoked, unless a starting directory is specified, CtrlP will set its local working directory according to this variable:
`let g:ctrlp_working_path_mode = 'ra'`

|                         |                                                                                                                                        | 
|-------------------------|----------------------------------------------------------------------------------------------------------------------------------------| 
| `c`                     | The directory of the current file                                                                                                      | 
| `r`                     | The nearest ancestor that contains one of these directories or files: .git .hg .svn .bzr _darcs                                        | 
| `a`                     | Like c-comma- but only if the current working directory outside of CtrlP is not a direct ancestor of the directory of the current file | 
| `0 / '' (empty string)` | Disable this feature                                                                                                                   | 

|                        |                                | 
|------------------------|--------------------------------| 
| `g:ctrlp_root_markers` | Define additional root markers | 

<style>
	#os {
		display: flex;
	}

	#os section {
		padding: 10px;
		flex-grow: 1;
	}
</style>

<section id='os'>
<section>
Exclude files and directories:

##### MacOS / Linux
`set wildignore+=*/tmp/*,*.so,*.swp,*.zip`

##### Windows
`set wildignore+=*\\tmp\\*,*.swp,*.zip,*.exe`

`let g:ctrlp_custom_ignore = '\v[\/]\.(git|hg|svn)$'`
`let g:ctrlp_custom_ignore = {
\ 'dir':	'\v[\/]\.(git|hg|svn)$',
\ 'file': '\v\.(exe|so|dll)$',
\ 'link': 'some_bad_symbolic_links',
\ 
}`
</section>
<section>
Use a custom file listing command:

##### MacOS / Linux
`let g:ctrlp_user_command = 'find %s -type f'`

##### Windows
`let g:ctrlp_user_command = 'dir %s /-n /b /s /a-d'`
`help ctrlp-options`
</section>
</section>
