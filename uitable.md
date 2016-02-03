# **uitable**
## Uitable Properties

Control appearance and behavior of tableexpand all in page
Uitables are tables that list data in a figure. The uitable function creates a table and sets any required properties before displaying it. By changing uitable property values, you can modify certain aspects of its appearance and behavior.

Starting in R2014b, you can use dot notation to query and set properties.
~~~matlab
t = uitable;
fgcolor = t.ForegroundColor;
t.ForegroundColor = [0 0 1];
~~~
If you are using an earlier release, use the get and set functions instead.


##Appearance
###Visible — Uitable visibility
'on' (default) | 'off'
Uitable visibility, specified as 'on' or 'off'. When Visible is 'off', the uitable is not visible, but you can query and set its properties.

To make your program start faster, set the Visible property of all uitables that are not initially displayed to 'off'.

###BackgroundColor — Uitable cell background color
RGB triplet | m-by-3 matrix of RGB triplets
Uitable cell background color, specified as an RGB triplet or an m-by-3 matrix of RGB triplets. An RGB triplet is a row vector that specifies the intensities of the red, green, and blue components of the color. The intensities must be in the range, [0,1]. Color names are not valid.

Specify an m-by-3 matrix when you want the shading of the table rows to follow a repeating pattern of m different colors. Each row of the matrix must be an RGB triplet. MATLAB® uses the rows of the matrix when the RowStriping property is 'on'. The table background is not striped unless both RowStriping is 'on' and the background color is an m-by-3 matrix.

The following table lists the RGB triplets for commonly used colors.
~~~matlab

Color	RGB Triplet
Yellow	[1 1 0]
Magenta	[1 0 1]
Cyan	[0 1 1]
Red	[1 0 0]
Green	[0 1 0]
Blue	[0 0 1]
White	[1 1 1]
Black	[0 0 0]
Example: [1 1 1]

Example: [1 1 1; .9 .9 .9]
~~~

###ForegroundColor — Cell text color
[0 0 0] (default) | RGB triplet | short name | long name

##Location and Size
###Position — Location and size of uitable
[left bottom width height]
###Units — Units of measurement
'pixels' (default) | 'normalized' | 'inches' | 'centimeters' | 'points' | 'characters'
###Extent — Size of uitable rectangle
four-element row vector

##Font Style
####FontName — Font for displaying cell content
string
####FontSize — Font size for uitable cell content
positive number
####FontUnits — Units of font size for uitable cell contents
'points' (default) | 'normalized' | 'inches' | 'centimeters' | 'pixels'
####FontWeight — Font weight for uitable cell contents
'normal' (default) | 'bold'
####FontAngle — Character slant of uitable cell contents
'normal' (default) | 'italic'

##Interactive Control
CellEditCallback — Cell edit callback function
function handle | cell array | string
CellSelectionCallback — Cell selection callback function
function handle | cell array | string
ColumnEditable — Ability to edit column cells
empty matrix ([]) (default) | logical 1-by-n array | scalar logical value
RearrangeableColumns — Ability to rearrange table columns
'off' (default) | 'on'
ButtonDownFcn — Button-press callback function
'' (default) | function handle | cell array | string
KeyPressFcn — Key press callback function
'' (default) | function handle | cell array | string
KeyReleaseFcn — Key-release callback function
'' (default) | function handle | cell array | string
Enable — Operational state of uitable
'on' (default) | 'inactive' | 'off'
TooltipString — Tooltip text
string
UIContextMenu — Uitable context menu
empty GraphicsPlaceholder array (default) | uicontextmenu object
Selected — Selection status of uitable
'off' (default) | 'on'
SelectionHighlight — Ability to highlight selection handles
'on' (default) | 'off'
Callback Execution Control

expand all
Interruptible — Callback interruption
'on' (default) | 'off'
BusyAction — Callback queuing
'queue' (default) | 'cancel'
HitTest — Ability to become current object
'on' (default) | 'off'
Creation and Deletion Control

expand all
BeingDeleted — Deletion status of uitable
'off' (default) | 'on'
CreateFcn — Uitable creation function
function handle | cell array | string
DeleteFcn — Uitable deletion function
function handle | cell array | string
Identifiers

expand all
Type — Type of graphics object
'uitable'
Tag — Uitable identifier
'' (default) | string
UserData — Data to associate with the uitable object
empty array (default) | array
Parent/Child

expand all
Parent — Uitable parent
figure | uipanel | uibuttongroup | uitab
Children — Children of uitable
empty array
HandleVisibility — Visibility of Uitable handle
'on' (default) | 'callback' | 'off'
Table Data

expand all
Data — Table content
numeric array | cell array
Table Layout

expand all
RowName — Row heading names
'numbered' (default) | n-by-1 cell array of strings | empty cell array ({} ) | empty matrix ([])
ColumnName — Column heading names
'numbered' (default) | n-by-1 cell array of strings | empty cell array ({} ) | empty matrix ([])
ColumnWidth — Width of table columns
'auto' (default) | 1-by-n cell array
ColumnFormat — Cell display format
empty cell array ({}) (default) | 1-by-n cell array of strings
RowStriping — Alternate row shading
'on' (default) | 'off'
