<h1><img src="resources/icon.png" /> UnUPX</h1>

UnUPX is a deep way to decode-upx compressed resources.

it is drag&amp;drop.

you can use it with any file. it does not care. but if it isn't a binary file (exe/dll/...) it not sure to be working.

first it UnUPX the file you drag&amp;drop over it.  
then it extracts all the embedded RCDATA resources from within the file, the resources are extracted raw, with a 'rc' file.
the resources are now plain files, and they all get UnUPX if ever possible.
the resources and the 'rc' file are compiled to a 'res' file,  
we're going to generate a new exe, where first all its existing RCDATA resources are deleted,  
and then the 'res' file (which contains only RCDATA) is embedded in it.  

<hr/>
Note:  
when I'm compiling the 'rc' and resources to 'res' I don't specify a language-code, 
so it will use whatever you use on your computer, on my computer it uses Windows-1255 (or 1033), 
but it does not really matter, MOSTLY the language is useful for other types of embedded resources (STRING-TABLE and such). This is the reason I've pre deleted all the RCDATA first, since when embedding same name resources with different languages (something that might happen if the original exe has one language and your computer has another) --- it keeps both resources, which is a waste of space.  
Anyway... I might be trying to make this thing more accurate by first identifying the original language and applying switches for 'rc.exe' for compiling the resource, but it is not very important.

<hr/> 

The result is the file with addition '_mod' to its original name, and with its original extension.

<hr/>

the 'temp' and 'temp_bak' (keeps one "history" for inspection/dev.) can be safely deleted. 

<hr/>

The example I give here is rufus from https://github.com/pbatard/rufus 
since the exe is both itself UPX-ed and some of its resources are UPX-ed,  
the program is safe, but the UPX is un-needed! 
https://github.com/pbatard/rufus/issues/1120 

<hr/>

You may rename the '_mod' file to the original file-name, 
and provide other patches such as manifest patch to make it compatible with win10 and high-dpi screens (for example) with https://github.com/eladkarako/manifest

<hr/>

the script only stops on errors, if you wish to pause it to read the progress, you may comment-out the @echo off on the first line (using '::' or 'rem') or add 'pause' before it has the 'exit /b ......' line at the end, 
or simply open it in CMD so it won't close down afterwards.