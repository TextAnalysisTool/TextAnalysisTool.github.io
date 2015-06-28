=================================
== TextAnalysisTool.NET ReadMe ==
=================================


------------------
-- Requirements --
------------------

Microsoft .NET Framework 4.0 (or later versions)

Note: TextAnalysisTool.NET is compiled for .NET 4.0. Later .NET Framework
versions are supported through a .config that needs to be configured for
the corresponding version. For more information, please refer to the
following MSDN article: "How to: Configure an App to Support .NET Framework 4
or 4.5"
http://msdn.microsoft.com/en-us/library/jj152935.aspx


-------------------------------
-- Installation Instructions --
-------------------------------
1) Copy TextAnalysisTool.NET.exe and TextAnalysisTool.NET.exe.config to a
   local folder
2) Run TextAnalysisTool.NET.exe


---------------
-- File List --
---------------
TextAnalysisTool.NET.exe - Application
TextAnalysisTool.NET.exe.config - Application configuration file
TextAnalysisTool.NET.txt - Documentation file
ReadMe.txt - Requirements, Installation Instructions, File List, Known Issues,
  Notes, History


------------------
-- Known Issues --
------------------
* GDI+ occasionally throws a System.Runtime.InteropServices.ExternalException
  with the message "A generic error occurred in GDI+.". This exceptional
  condition causes TextAnalysisTool.NET to exit after notifying the user.
* The .NET Framework's improper handling of vertical and horizontal scrollbar
  messages for ListBoxes can cause rendering problems for files with very many
  or very long lines.
* Checkboxes don't always repaint properly due to a .NET Framework bug.
* There is extra flicker when resizing the window. This is due to a workaround
  for an even worse .NET Framework repainting bug.
* ListBox limitations on 16-bit OSes (Windows 95/98/Me) prevent files with
  more than 32,767 lines from displaying properly.


-----------
-- Notes --
-----------
One of TextAnalysisTool.NET's core principles is that data should be read one
time as soon as it is available and kept in memory after that. This principle
allows the source data to be amended, changed, or even become unavailable
without affecting the user. Though this principle is an optional convenience
when the data source is a file, it is a strict requirement for data sources
that offer only one chance to read their data (such as the clipboard and plug-
ins). Accordingly, TextAnalysisTool.NET keeps the entire data set in memory at
all times which means that particularly large data sets can tax systems with
comparatively few available resources. The prototypical example is loading a
file that is larger than the amount of memory in the system: performance
suffers. TextAnalysisTool.NET strives to be as responsive as possible under
all circumstances, but is ultimately bound by the resources available to it.


-------------
-- History --
-------------

2015-06-23 by Uriel Cohen
----------
* Fixed some bugs caused by the introduction of the new menus look & feel

2015-05-18 by Uriel Cohen
----------
* Gave a more modern look to all menus
* Improved behavior of the "More..." button in Options dialog

2015-05-07 by Mike Morante
----------
* Fixed a bug where the context menu for filters would remain enabled even if
  no filter was selected

2015-04-14 by Mike Morante
----------
* Fixed a bug that would cause loading filters from the command line to fail

2015-03-27 by Mike Morante
----------
* Added columns to the filters list, use only the matching pattern for
  previewing the filter
* Added drag&drop support for the filters list
* Double-click or press Enter on a filter to edit it
* Double-click a line to create a new filter from it
* Added menu item to enable all filters at once
* Renamed "Filter" menu to "Filters"

2015-02-26 by Uriel Cohen
----------
* Added support for loading a configuration file from the command line
* Added support for multiple filter files on the command line

2015-02-24 by Uriel Cohen
----------
* Fixed a bug with handling of some defaults through registry settings

2015-01-28 by Uriel Cohen
----------
* Added support for setting configuration parameters from a preferences dialog
* Added the capability to Export and Import configuration files

2015-01-07 by Uriel Cohen
----------
* Added a tooltip to the loaded file indicator in the status bar
* Fixed a bug where setting a marker used in an active filter causes the
  current selection of lines to be changed

2015-01-07 by David Anson
----------
* Improve HTML representation of clipboard text when copying for more
  consistent paste behavior
 
2015-01-01 by Uriel Cohen
----------
* Fixed a bug where TAB characters are omitted in the display
* Fixed a bug where lines saved to file include an extra white space at the
  start

2014-12-21 by Uriel Cohen
----------
* Changed compilation to target .NET Framework 4.0

2014-12-11 by Uriel Cohen
----------
* Redesigned the status bar indications to be consistent with Visual Studio and
  added the number of currently selected lines

2014-12-04 by Uriel Cohen
----------
* Added the ability to append an existing filters file to the current filters
  list

2014-12-01 by Uriel Cohen
----------
* Added recent file/filter menus for easy access to commonly-used files
* Added a new settings registry key to set the
  maximum number of recent files or filter files allowed in the
  corresponding file menus
* Fixed bug where pressing SPACE with no matching lines from filters
  crashed the application
* Fixed a bug where copy-pasting lines from the application to Lync
  resulted in one long line without carriage returns

2014-11-11 by Uriel Cohen
----------
* Added support for selection of background color in the filters 
  (different selection of colors than the foreground colors)
* The background color can be saved and loaded with the filters
* Filters from previous versions that lack a background color will have the 
  default background color
* Saving foreground color field in filters to 'foreColor' attribute. 
  Old 'color' attribute is still being loaded for backward compatibility 
  purposes.
* Changed control alignment in Find dialog and Filter dialog

2014-10-21 by Mike Morante
----------
* Fix localization issue with the build string generation

2014-04-22 by Mike Morante
----------
* Line metadata is now visually separate from line text contents
* Markers can be shown always/never/when in use to have more room for line text
  and the chosen setting persists across sessions
* Added statusbar panel funnel icon to reflect the current status of the Show
  Only Filtered Lines setting

2014-02-27 by Mike Morante
----------
* Added zoom controls to quickly increase/decrease the font size
* Zoom level persists across sessions
* Added status bar panel to show current zoom level

2013-05-07
----------
* Compiled using the .NET 2.0 "Any CPU" configuration to enable access to more
  memory when run on 64-bit operating systems
* Superficial string changes for copyright date, etc.

2006-12-04
----------
* Copy to clipboard includes HTML formatting that preserves the font/ coloring
  of the copied text when pasting (user request)
* Enhanced New Filter and Find dialogs to pre-populate with the text of the
  currently selected line (user request)
* Added saving/loading of Show Only Filtered Lines setting in .TAT filter
  files (user request)
* Added "[x / y]" to enabled filter descriptions to show how many lines are
  currently matching each filter
* Added support for legacy keyboard shortcuts Ctrl+Insert (copy) and Shift+
  Insert (paste) (user request)
* Added black and white to list of filter color options (user request)
* Disabled glyph-mapping to work around a GDI+ bug that causes abrupt
  application termination
* Fixed bug where Help | Documentation didn't clear the Show Only Filtered
  Lines setting

2006-01-11
----------
* Significantly improved performance with large files (load time reduced by
  ~40%, memory use reduced by ~25%, filter time reduced by ~10%)
* Fixed potential null dereference in LineCollectionDisplay.OnDrawItem that is
  extremely rare on all operating systems before Windows Vista (user report)
* Fixed filter display coloration bug when running under .NET 2.0 by working
  around the problem so that the correct behavior is present under both .NET
  1.1 and .NET 2.0 (user report)
* Fixed bug where Ctrl-Alt-[A-Z] didn't work if filtered lines were hidden and
  no lines were displayed
* Fixed bug where the body of the '_' character couldn't be seen with some
  font sizes (including the default)
* Fixed bug where copying text containing '\0' to the clipboard truncated that
  text prematurely
* Fixed premature line truncation bug due to use of default encoding when
  reading files
* Fixed premature line truncation when drawing lines containing '\u0084'
* Improved performance of toggling markers on high line numbers
* Improved performance of drawing extremely long lines
* Set IMAGE_FILE_LARGE_ADDRESS_AWARE flag in PE header to enable access to a
  larger virtual memory area when it is available (ex: on 64-bit machines or
  on machines with the /3GB boot option set)
* Added formatting to the XML content of *.tat filter files for improved human
  readability and better revision control (user request)
* Added support for applying Shift modifier key to Ctrl+F to begin a reverse
  find (this shortcut overrides the shortcut for toggling filter f)
* Added display of plug-in file version to "Installed plug-ins" dialog
* Add About dialog note about protection under United States patent 6,963,878

2003-09-02
----------
* Fixed bug whereby refreshing 0-line file caused an unhandled exception
* Added short version of file name to window title, makes it easier to switch
  among different windows in the taskbar (user request)
* Last directory used for successful file and filter access (via a dialog) is
  remembered, makes it easier to keep files and filters in different locations
  (user request)
* Addressed minor focus issues related to filter display

2003-07-24
----------
* Switched to building on top of .NET Framework 1.1
* Switched to using Windows XP visual styles for dialog controls
* Improved performance during startup, reduced memory requirements
* Fixed horizontal scroll bar bug for long lines with embedded tabs
* Added keyboard shortcuts for toggling and cycling filters (user request)

2003-04-07
----------
* Added support for plug-ins that extend TextAnalysisTool.NET by allowing it
  to read custom file types! (see the "Plug-ins" section of the documentation
  for more details)

2003-03-24
----------
* Added support for coloring lines according to the filter(s) they match (see
  documentation for details) (user request)
* Right-clicking "Regular expression" checkbox opens MSDN online documentation
  for regular expression syntax (user request)
* Require confirmation when Help | Documentation is chosen to avoid
  inadvertently discarding the current lines and filters (user request)
* File sharing modes tweaked for maximum versatility (specifically, to allow
  opening a file that's actively being written to)
* File | Reload tries to preserve the selected line and current view of the
  file
* File open/save dialog boxes remember the last file type they were used with
* Focus rectangle now drawn in line display
* Other minor user interface fixes/improvements

2003-02-28
----------
Initial release of TextAnalysisTool.NET!
Highlights:
* Status bar with file name and filtered/unfiltered line count! (user request)
* Support for copying multi-line selections! (user request)
* Line display colors can be customized! (user request)
* Multiple lines can be marked at the same time! (via multi-line selections)
* Support for drag-and-drop to import text!
* Support for reading UTF-8, Unicode, and Unicode big endian files!
* User efficiency improvements to the Add Filter dialog box!
* Real-time validation for Add Filter/Find input! (great for reg-ex's)
* Filter pane is usable without a mouse!
* Checkboxes in filter pane show which filters are active!

2003-02-21, 2003-02-11, 2003-02-06
----------------------------------
Preview releases to a handful of volunteers


------------
-- People --
------------

Project owner
-------------
* David Anson - http://dlaa.me/

Contributors
------------
* Mike Morante - http://github.com/mike-mo
* Uriel Cohen - http://github.com/cohen-uriel
