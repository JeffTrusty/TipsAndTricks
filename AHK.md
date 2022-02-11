# AutoHotKey Info

## AutoHotkey Special characters
```AutoHotKey
# = Windows Key
^ = Ctrl
! = Alt
< = Left-Alt
> = Right-Alt
+ = Shift
& combines mouse and keyboard
; Inline Comment
/* Block Comment */
```

## MsgBox
```AutoHotKey
<!-- MsgBox calls the Windows MessageBox dialog and pauses until the MessageBox is closed -->
MsgBox, My MessageBox Text
```

## Assigning Values to Variables
```AutoHotKey
x:="Value"  ; Assign string value to a variable
x.="Appended Value" ; appends string value to an existing variable
Y:=10 ; Assign numeric value to Y variable
Y+=2 ; Adds 2 to numeric variable
Y-=2 ; Subtracts 2 from numeric variable
Y++ ; Increments numeric variable
Y-- ; Decrement numeric variable
; MultiLine variable
Name:="Bob"
Var=
(
this
is "With Quotes"
and variables: %Name%
multi line
variable
)
```

## Evaluating Conditions
```AutoHotKey
x:=10
y:=10
if (x=10) AND (y=10) {
  MsgBox X = %x% Condition is True
  MsgBox Another Message
}
; = ; Equal
; != ; Not Equal
; > ; Greater than
; < ; Less than
; >= ; Greater than or Equal to
; <= ; Less than or Equal to
; AND ; Both Conditions are True
; OR ; Any of the conditions are True
```

## Tooltip and SplashText
```AutoHotKey
<!-- These display messages, but do not suspend the running script -->
; ToolTips will display at the mouse position
Tooltip,Message ; display Tooltip
Sleep, 2000 ; 2 second delay
Tooltip ; Remove Tooltip
; SplashTextOn allows you to define where to display your message
SplashTextOn, 200, 50, My Title, My SplashText
Sleep, 4000
SplashTextOff
```

## Subroutines / Go Subs
```AutoHotKey
Gosub, MySubRoutine

MsgBox, Hi
Return

MySubRoutine: ; define label
  MsgBox, Inside my subroutine
  Return
```

## Functions
```AutoHotKey
myFunction(1,2,3)
myFunction("A","B","C")

myFunction(a,b,c) {
  MsgBox, % a a_Tab b a_Tab c
}
```

## Scope
```AutoHotKey
; SCOPE: x is a local variable, y is global
x:="Cat" ; local variable
global y:="Mouse" ; global variable
myFunc(x) ; Note, only passing x

ListVars ;display memory variables
MsgBox, % x A_Tab functionVar

myFunc(x) { ; value of local x variable is passed
  ; Scope: Local variable x does not affect the global x variable
  MsgBox,
  x:="Dog"
  MsgBox, % x a_Tab y
  ; Scope: functionVar variable will not be lost when returning from function
  global functionVar := "Defined in myFunc"
}
```

## Function Default values
```ahk
z:=myCalc()
MsgBox % z

z:=myCalc(5,4)
MsgBox % z

myCalc(x:=1, y:=2) {
  z:= x+y
  return z
}
```

## Includes
```AutoHotKey
#Include <path\filename.ahk>
<!--
  AHK will find the file if it is in Lib sub folder
  AHK will find the file if it is in %A_MyDocuments%\Lib sub folder (C:\Users\jeff_\OneDrive\Documents)
  AHK will find the file if it is in %A_AhkPath%\Lib sub folder
  If the filename is the same filename of the function and in the same folder, you don't need to have an #Include
  You can create libraries of functions and #Include them
    Create the XL.ahk file and prefix all function names with XL_
-->
```

## Writing, Reading, and Working with Files
```AutoHotKey
Var:="File Text`n"
FileAppend, %Var%, Filename.txt,UTF-8
FileAppend, %Var%, Filename.txt,UTF-8
FileAppend, %Var%, Filename.txt,UTF-8

if (!FileExists("Filename.txt")) {
  MsgBox, File not found!
}

if (FileExists("Filename.txt")) {
  FileRead,readVar, filename.txt ; Prefix filename with *P65001 to force UTF-8 encoding
  MsgBox, % readVar
}

; FileMove,fileName,DestinationFolder ; can use wildcards in fileName
; FileCopy,fileName,DestinationFolder ; can use wildcards in fileName
; FileDelete,fileName ; can use path and wildcards in fileName
```

# Working with Text
```AutoHotKey
<!--
  StrReplace(StringToSearch,"SearchFor","Replacement")
  Trim() ; Trims white space from front and back of a string
  lTrim() ; Trims white space from front of a string
  rTrim() ; Trims white space from back of a string
  InStr() ; Returns 0 if not found else position of the occurrence
  SubStr()
  StrSplit() ;Parses a string into an array
  Sort()
 -->

Txt:="    Remember, a Jedi can feel the Force flowing through him. You mean it controls your actions? Partially. But it also obeys your commands.    "
Txt:=StrReplace(Txt, "Jedi", "Moron"); StrReplace(Txt, "SearchFor", "Replacement")
MsgBox, % "***" Txt "***"

Txt:=trim(Txt)
MsgBox, % "***" Txt "***"

Txt:="00012345600"
Txt:=trim(Txt, "0")
MsgBox, % "***" Txt "***"

Txt:="    Remember, a Jedi can feel the Force flowing through him. You mean it controls your actions? Partially. But it also obeys your commands.    "
MsgBox % StrSplit(Txt," ").4 ; get the 4th word of the string
Parsed:=StrSplit(Txt," ")
MsgBox % Parsed.2 A_Tab Parsed.3

Text:="One`nTwo`nThree`nTwo`nTwo`nFour"
MsgBox % Text
Sort,Text
MsgBox % Text
Sort,Text,R ; reverse order
MsgBox % Text
Sort,Text,U ; remove duplicates
MsgBox % Text
```

# Built-in Variables
```AutoHotKey
;Use a period . for continuation of the previous line
MsgBox % "Hello, How are you?`n`n"
. "Doing well, how are you?`n`n"
. "I'm great, thank you"

A_Space
A_Tab
A_OSVersion
A_ScreenHeight
A_ScreenWidth
A_MyDocuments
A_Startup
A_Programs
A_AppData
A_ComputerName
A_UserName
A_DDD
A_MMM
A_MM
A_YYYY
A_Hour
A_Min
A_Sec
A_Now ; YYYYMMDDHHmmSS
Clipboard
A_Index
```

## Activating, Running, Moving, Resizing Applications
```AutoHotKey
; SetTitleMatchMode options:
; SetTitleMatchMode,1 ; Window's title must start with
; SetTitleMatchMode,2 ; Window's title contains
; SetTitleMatchMode,3 ; EXACT Match
; SetTitleMatchMode,Regex ; Use Regular Expressions

SetTitleMatchMode,2 ; This is what I generally use and is case sensitive
WinActivate, AFCU.xlsm - Excel

; Winwait, [applicationName] ; Pauses script until [applicationName] is running
; WinActivate [applicationName] ; Switches focus to running [applicationName]

;WinwaitActive, [applicationName] ; Pauses script until [applicationName] is active
; If (WinExist("Notepad")) ; Checks if a window running
;    MsgBox Notepad is running

;WinGetPos,X,Y,W,H,[applicationName] ; gets the position of [applicationName]

;WinMove,[applicationName],,[PosX], [PosY], [Width], [Height]

;WinHide,[applicationName] ; Hides [applicationName] NOTE: this removes the [applicationName] from the taskbar
;sleep, 1500 ; sleep 1.5 seconds
;WinShow,[applicationName] ; Restores a hidden [applicationName]

;WinClose,[applicationName] ; Closes [applicationName], but will wait if something is preventing it from closing IE: Saving

;WinKill, [applicationName] ; Force close [applicationName]
```

## Run script as admin
```AutoHotKey
if (! A_IsAdmin) {
  Run *RunAs "%AScriptFullPath%" ; requires AHK v1.0.92.01+
  ExitApp
}
```

## Context sensitivity
```AutoHotKey
SetTitleMatchMode,2
#IfWinActive, [window title]
  MsgBox In window
#IfWinActive ; end this context sensitivity
```
