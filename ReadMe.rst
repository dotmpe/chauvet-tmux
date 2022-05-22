To use Chauvet with tmux, the easiest currently is to use the Airline and Tmuxline Vim addons. See below.

Alternatively a customized Tmuxline snapshot is included in this repository.
To use it in ``tmux.conf``::

  source chauvet-powerline-statusbar.conf

Vim setup
---------
Create a ``vimrc`` section like::

  let g:tmuxline_preset = {
        \'a'    : '#S',
        \'b'    : [ ' #(whoami)' ],
        \'c'    : [ ' #(string.sh append-if-len "$(system-status charge-left-unconnected)" " ")#(string.sh prepend-if-len "$(system-status short)" " ")' ],
        \'win'  : [ '#I#W' ],
        \'cwin' : [ ' #I', '#W#F' ],
        \'x'    : [ '#(tmux-uptime p) #(user-tools weather)' ],
        \'y'    : [ '%R', "%a%V'%y " ],
        \'z'    : [ '#h' ] }

  let g:tmuxline_separators = {
                \ 'left' : '',
                \ 'left_alt': '',
                \ 'right' : '',
                \ 'right_alt' : '',
                \ 'space' : ''}

You have to provide your own scripts, above sections are my vimrc.
When Vim starts in a Tmux session, the Tmux status is updated automatically.

Alternatively you can disable Tmuxline auto-update::

  let g:airline#extensions#tmuxline#enabled = 0

and generate a snapshot to include in your tmux.conf::

  :TmuxlineSnapshot ~/.config/tmux/color.conf

And then further edit the generated file.

..
