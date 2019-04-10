---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 3fde9779205ea7d0902ddd99ed192f097a159d2c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221476"
---
# <a name="ui-automation-support-for-standard-controls"></a>Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podporu pro aplikace vyvinuté pro standardní ovládací prvky [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] architektur.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Ovládací prvky Windows Presentation Foundation  
 Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků, které poskytují informace ani podporu pro interakci s uživatelem mají plně nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Další prvky, jako je například panely, nejsou viditelné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Ovládací prvky systému Win32  
 Většina [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll. Toto sestavení se automaticky registruje pomocí automatizace uživatelského rozhraní klientské aplikace.  
  
 Plná podpora se poskytuje jenom pro ovládací prvky z verze 6 ComCtrl32.dll (k dispozici [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] a novější).  
  
 Podporují se následující ovládací prvky.  
  
|Název třídy|Typ ovládacího prvku|  
|----------------|------------------|  
|Tlačítko|Tlačítko|  
|Tlačítko|RadioButton|  
|Tlačítko|Skupina|  
|Tlačítko|CheckBox|  
|Tlačítko|Hypertextový odkaz|  
|Tlačítko|SplitButton|  
|Tlačítko|CheckBox|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Upravit|Dokument|  
|Upravit|Upravit|  
|SysLink|Hypertextový odkaz|  
|Static|Text|  
|Static|Image|  
|SysIPAddress32|Vlastní|  
|SysHeader32|Záhlaví/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|Seznam|  
|ListBox|Seznam|  
|ListBox|ListItem|  
|#32768|Nabídka|  
|#32768|Položku nabídky|  
|msctls_progress32|ProgressBar|  
|RichEdit|dokument. Viz poznámka.|  
|RichEdit20A|Dokument|  
|RichEdit20W|Dokument|  
|RichEdit50W|Dokument|  
|ScrollBar|Posuvník|  
|msctls_trackbar32|Posuvník|  
|msctls_updown32|Číselník|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|Karta|  
|SysTabControl32|TabItem|  
|ToolbarWindow32|ToolBar|  
|ToolbarWindow32|Položku nabídky|  
|ToolbarWindow32|Tlačítko|  
|ToolbarWindow32|CheckBox|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|Oddělovač|  
|tooltips_class32|Popisy tlačítek|  
|#32774|Popisy tlačítek|  
|ReBarWindow32|Panel nástrojů|  
|SysTreeView32|Strom|  
|SysTreeView32|TreeItem|  
  
 **Poznámka:** ovládacího prvku The RichEdit je podporována pouze pro verze, kterou jste dostali se [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (ve verzi knihovny RichEd20.dll 3.1 nebo novější a MsftEdit.dll verze 4.1 a novější).  
  
 Následující ovládací prvky nejsou podporovány.  
  
|Název třídy|Typ ovládacího prvku|  
|----------------|------------------|  
|SysAnimate32|Image|  
|SysPager|Číselník|  
|SysDateTimePick32|Vlastní|  
|SysMonthCal32|Kalendář|  
|MS_WINNOTE|Popis tlačítka|  
|VBBubble|Popis tlačítka|  
|Posuvník (při použití jako samostatný ovládací prvek)|Posuvník|  
|SuperGrid|Vlastní|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a>Ovládací prvky Windows Forms  
 Ovládací prvky Windows Forms jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím zprostředkovatele na straně klienta v UIAutomationClientsideProviders.dll. Toto sestavení se automaticky registruje pomocí automatizace uživatelského rozhraní klientské aplikace.  
  
 Obvykle ovládacích prvků Windows Forms, které jsou spravované obálky pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] běžné ovládací prvky jsou podporovány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Podporují se následující ovládací prvky.  
  
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
|Ovládací prvek ImageList|  
|Popisek|  
|ListBox|  
|ListView|  
|MainMenu – / ContextMenu|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|TabControl – / TabPage –|  
|TextBox|  
|Časovač|  
|Panel nástrojů|  
|Popisy tlačítek|  
|TrackBar|  
|TreeView|  
|VscrollBar|  
|WebBrowser|  
  
 Následující ovládací prvky jsou vystaveny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pouze prostřednictvím jejich podporu [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]. Některé funkce nemusí být k dispozici.  
  
|Název ovládacího prvku|  
|------------------|  
|BindingSource|  
|DataGrid|  
|Ovládací prvek DataGridView|  
|DataNavigator|  
|DomainUpDown|  
|ErrorProvider|  
|FlowLayoutPanel|  
|Formulář|  
|LinkLabel|  
|HelpProvider|  
|MaskedTextBox|  
|MenuStrip – / ContextMenuStrip|  
|NumericUpDown|  
|Panel|  
|PictureBox|  
|PrintDocument|  
|PrintPreview-Control|  
|PrintPreview-Dialog|  
|PropertyGrid|  
|UserControl|  
|ToolStrip|  
|Kontejner TableLayoutPanel|  
|SplitContainer – / SplitterPanel|  
|Rozdělovač|  
|RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Viz také:

- [Typy ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types.md)
