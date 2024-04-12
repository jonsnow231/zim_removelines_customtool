# zim_removelines_customtool
Removes lines and adds a space at the end of each line from text pasted from documents such as .pdf that include manual line breaks. Posted on: https://github.com/jaap-karssenberg/zim-wiki/wiki/Remove-line-breaks-custom-tool


This is how to set up this custom tool on Zim Wiki: https://github.com/zim-desktop-wiki/zim-desktop-wiki 
* Exclusively tested on Windows with a portable install.


There are two options. The first is to change highlighted text to remove line breaks. The second is to paste whatever is in your clipboard modified to remove the line breaks. 

=== HIGHLIGHT REMOVE LINE BREAKS ===

1. Download the newest Python if you don't have it already: https://www.python.org/downloads/
2. Open a text document and paste the following code:

```
import sys

args = ' '.join(sys.argv[1:]).replace('\n',' ')

formatted = args.replace('  ','\n') 

print(formatted)
```
3. Save it as removelinebreaks.py anywhere in your ZIM folder. I chose Zim\share\zim\custom tools  (I created the custom tools folder)
4. Open Zim Wiki and go to Tools > Custom Tools
5. A pop up will appear where you will click the "+" button.
6. Input the following:
Name: Remove Line Breaks

Description: Removes line breaks on highlight

Command: "C:\Program Files\Python37\python.exe" "C:\Users\USERNAME\Documents\PORTABLE apps\Zim\share\zim\custom tools\removelinebreaks.py" %T 

The first quotation specifies the location of python, the second location specifies wherever you place your removelinebreaks.py. 

Icon: leave or click it to change to whatever you want

Command line does not modify data: unchecked

Output should replace current selection: checked

Show in toolbar: checked (optional)

(Under command, the first part is wherever your python.exe was installed onto in step one. The second is wherever you saved your .py python script. 

![image](https://github.com/jonsnow231/zim_removelines_customtool/assets/83853289/afcd7804-1bae-4dc4-9b1a-4f433c9ef0c2)

7. Finished. Now paste text in there, highlight it, and click the button (or go to Tools > Remove Line Breaks).


---

=== PASTE REMOVE LINE BREAKS ===

1. Exactly the same as above, but also install Pyperclip module for Python: https://pypi.org/project/pyperclip/  For windows: open CMD in administrator mode, and type: pip install pyperclip3.
2. Open a text document and paste the following code:

```
import sys
import pyperclip

args = pyperclip.paste().splitlines()
args = ' '.join(args) 

formatted = args.replace('  ','\n')

print(formatted)
```
3. Save it as pasteremoveline.py anywhere in your ZIM folder. I chose Zim\share\zim\custom tools  (I created the custom tools folder)

Everything else is the same as the highlight remove line breaks, but using this python script instead of the other. 


