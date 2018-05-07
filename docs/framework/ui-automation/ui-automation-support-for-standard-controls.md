---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3ccd6e1348125f5d901e0f093d2b5483b818719f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-support-for-standard-controls"></a>Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podpora pro standardní ovládací prvky v aplikacích vytvořených pro [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] architektury.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Ovládací prvky Windows Presentation Foundation  
 Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] mít úplná nativní podpora pro ovládací prvky, které poskytují informace ani podporu pro interakci s uživatelem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Další prvky, jako jsou například panelů, nejsou viditelné pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Ovládací prvky Win32  
 Většina [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky jsou viditelné na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll. Toto sestavení se automaticky registruje pro použití s automatizace uživatelského rozhraní klientské aplikace.  
  
 Úplná podpora je k dispozici pouze pro ovládací prvky z verze 6 ComCtrl32.dll (k dispozici [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] a novější).  
  
 Jsou podporovány následující ovládací prvky.  
  
|Název třídy|– Typ ovládacího prvku|  
|----------------|------------------|  
|Tlačítko|Tlačítko|  
|Tlačítko|RadioButton|  
|Tlačítko|Skupina|  
|Tlačítko|CheckBox|  
|Tlačítko|Hypertextový odkaz|  
|Tlačítko|Tlačítko rozdělení|  
|Tlačítko|CheckBox|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Upravit|Dokument|  
|Upravit|Upravit|  
|SysLink|Hypertextový odkaz|  
|Static|Text|  
|Static|Image|  
|SysIPAddress32|Vlastní|  
|SysHeader32|Hlavička/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|Seznam|  
|ListBox|Seznam|  
|ListBox|ListItem|  
|#32768|Nabídka|  
|#32768|Položka nabídky|  
|msctls_progress32|ProgressBar|  
|RichEdit|dokument. Další informace v poznámce.|  
|RichEdit20A|Dokument|  
|RichEdit20W|Dokument|  
|RichEdit50W|Dokument|  
|ScrollBar|Posuvník|  
|msctls_trackbar32|Posuvník|  
|msctls_updown32|Číselník|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|Tabulátor|  
|SysTabControl32|TabItem|  
|ToolbarWindow32|ToolBar|  
|ToolbarWindow32|Položka nabídky|  
|ToolbarWindow32|Tlačítko|  
|ToolbarWindow32|CheckBox|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|Oddělovač|  
|tooltips_class32|Popisy tlačítek|  
|#32774|Popisy tlačítek|  
|ReBarWindow32|Panel nástrojů|  
|SysTreeView32|Strom|  
|SysTreeView32|TreeItem|  
  
 **Poznámka:** ovládacího prvku RichEdit je podporována pouze pro verze součástí [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (v knihovny RichEd20.dll verze 3.1 nebo novější a MsftEdit.dll verze 4.1 a novější).  
  
 Ovládací prvky nejsou podporovány.  
  
|Název třídy|– Typ ovládacího prvku|  
|----------------|------------------|  
|SysAnimate32|Image|  
|SysPager|Číselník|  
|SysDateTimePick32|Vlastní|  
|SysMonthCal32|Kalendář|  
|MS_WINNOTE|Popisek|  
|VBBubble|Popisek|  
|ScrollBar (když se použije jako samostatný ovládací prvek)|Posuvník|  
|SuperGrid|Vlastní|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a>Ovládací prvky Windows Forms  
 Windows Forms – ovládací prvky jsou viditelné na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll. Toto sestavení se automaticky registruje pro použití s automatizace uživatelského rozhraní klientské aplikace.  
  
 Obvykle ovládací prvky Windows Forms, které jsou spravované obálky pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] běžné ovládací prvky jsou podporovány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Jsou podporovány následující ovládací prvky.  
  
|Název třídy|  
|----------------|  
|Tlačítko|  
|CheckBox|  
|CheckedListBox|  
|ColorDialog|  
|ComboBox|  
|FolderBrowser|  
|FontDialog|  
|GroupBox|  
|HscrollBar|  
|ImageList|  
|Popisek|  
|ListBox|  
|ListView|  
|MainMenu/ContextMenu|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog –|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|Ovládací prvek ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|TabControl/TabPage –|  
|TextBox|  
|Časovač|  
|Panel nástrojů|  
|Popisy tlačítek|  
|TrackBar –|  
|TreeView|  
|VscrollBar|  
|WebBrowser|  
  
 Ovládací prvky jsou viditelné na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pouze prostřednictvím jejich podpora [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]. Některé funkce nemusí být k dispozici.  
  
|Název ovládacího prvku|  
|------------------|  
|BindingSource|  
|DataGrid|  
|DataGridView|  
|DataNavigator|  
|DomainUpDown|  
|ErrorProvider|  
|FlowLayoutPanel|  
|Formulář|  
|Linklabel –|  
|HelpProvider –|  
|MaskedTextBox|  
|MenuStrip/ContextMenuStrip|  
|NumericUpDown|  
|Panel|  
|PictureBox|  
|PrintDocument|  
|Printpreview – ovládací prvek|  
|Printpreview – – dialogové okno|  
|PropertyGrid|  
|UserControl|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|Rozdělovače|  
|Prvku RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Viz také  
 [Typy ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types.md)
