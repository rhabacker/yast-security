# Makefile.am for .../doc

SUBDIRS = autodocs

htmldir = @docdir@

#%.png: %.dia
#	dia -n -e $@ $<

todo.html: Todo.txt
	@(							\
		grep -B100 '##BODY##' skel.html;		\
		echo -e "\n<pre>\n";				\
		cat Todo.txt;					\
		echo -e "\n</pre>\n";				\
		grep -A100 '##BODY##' skel.html;		\
	)							\
		| sed 's|##TITLE##|Things To Do|g'		\
		| sed 's|^#\+$$|<hr>|g'				\
		| sed 's|^#\+ \([[:alnum:],:)( -]*\)#\+$$|<h2>\1</h2>|g'	\
		| sed 's|^\([[:alnum:],:)( -]*:\)$$|<h2>\1</h2>|g'		\
		| sed 's|#\([0-9]\{4,5\}\)|<a href="http://bugzilla.suse.de/show_bug.cgi?id=\1">#\1</a>|g' \
		> todo.html

html_DATA = add.html index.html skel.html structure.html #workflow.png 

CLEANFILES = todo.html
EXTRA_DIST = Todo.txt $(html_DATA)

