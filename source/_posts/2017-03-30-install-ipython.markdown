---
layout: post
title: "Install ipython"
date: 2017-03-30 18:29:14 +0800
comments: true
categories: Python MacOS
---


    sudo pip install ipython

`Error: Operation not permittaed`

Disabled SIP(System Integrity Protection)

    sudo reboot
	Command + R 
    csrutil disable 
	sudo reboot
	sudo pip install ipython
	ipython

`Error:
File "/Library/Python/2.7/site-packages/IPython/utils/terminal.py", line 22, in <module>
    from backports.shutil_get_terminal_size import get_terminal_size as _get_terminal_size`
	
	vi /Library/Python/2.7/site-packages/IPython/utils/terminal.py
	
    Line 22: from backports.shutil_get_terminal_size import get_terminal_size as _get_terminal_size
	changed:
	Line 22: #from backports.shutil_get_terminal_size import get_terminal_size as _get_terminal_size
	Line 23: from shutil_backports import get_terminal_size as _get_terminal_size

Done.
