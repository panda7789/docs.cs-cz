---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 314526c1164f70e6b261df1a6f11ddce2b5fa240
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960079"
---
# <a name="ui-automation-support-for-standard-controls"></a>Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje informace o podpoře [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pro standardní ovládací prvky v aplikacích vyvinutých pro [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]a [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] architektury.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Ovládací prvky Windows Presentation Foundation  
 Všechny prvky ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], které poskytují informace nebo podporu pro interakci s uživatelem, mají úplnou nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Jiné prvky, například panely, nejsou viditelné [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Ovládací prvky Win32  
 Většina [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]ch ovládacích prvků je k dispozici [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím poskytovatelů na straně klienta v UIAutomationClientsideProviders. dll. Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.  
  
 Plná podpora je k dispozici pouze pro ovládací prvky z verze 6 souboru *Comctrl32. dll*.  
  
 Podporovány jsou následující ovládací prvky.  
  
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
|Statické|Text|  
|Statické|Obrázek|  
|SysIPAddress32|Vlastní|  
|SysHeader32|Záhlaví/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|Seznam|  
|ListBox|Seznam|  
|ListBox|Collection|  
|#32768|Nabídka|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|RichEdit|Dokumentů. Viz poznámka.|  
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
|ToolbarWindow32|MenuItem|  
|ToolbarWindow32|Tlačítko|  
|ToolbarWindow32|CheckBox|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|Oddělovač|  
|tooltips_class32|Popisy tlačítek|  
|#32774|Popisy tlačítek|  
|ReBarWindow32|Panel nástrojů|  
|SysTreeView32|Strom|  
|SysTreeView32|TreeItem|  
  
 **Poznámka:** Ovládací prvek RichEdit je podporován pouze pro verze dodávané se systémem Windows Vista (v knihovny Riched20. dll verze 3,1 a novější a MsftEdit. dll verze 4,1 a novější).  
  
 Následující ovládací prvky nejsou podporovány.  
  
|Název třídy|Typ ovládacího prvku|  
|----------------|------------------|  
|SysAnimate32|Obrázek|  
|SysPager|Číselník|  
|SysDateTimePick32|Vlastní|  
|SysMonthCal32|Kalendář|  
|MS_WINNOTE|Popis tlačítka|  
|VBBubble|Popis tlačítka|  
|ScrollBar (při použití jako samostatného ovládacího prvku)|Posuvník|  
|SuperGrid|Vlastní|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a>Ovládací prvky Windows Forms  
 Ovládací prvky model Windows Forms jsou zpřístupněny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím poskytovatelů na straně klienta v knihovně UIAutomationClientsideProviders. dll. Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]podporuje obvykle model Windows Forms ovládací prvky, které jsou spravované obálky pro [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] běžné ovládací prvky. Podporovány jsou následující ovládací prvky.  
  
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
|Obrázků|  
|Popisek|  
|ListBox|  
|ListView|  
|MainMenu/vynabídku|  
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
|Komponentu|  
|StatusBar|  
|TabControl/TabPage|  
|TextBox|  
|Časovač|  
|Panel nástrojů|  
|Popisy tlačítek|  
|TrackBar|  
|TreeView|  
|VscrollBar|  
|Navig|  
  
 Následující ovládací prvky jsou k dispozici pro [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jenom prostřednictvím jejich podpory pro Microsoft Active Accessibility. Některé funkce nemusí být k dispozici.  
  
|Název ovládacího prvku|  
|------------------|  
|BindingSource|  
|DataGrid|  
|Ovládací prvek DataGridView|  
|Datanavigator|  
|DomainUpDown|  
|ErrorProvider|  
|Kontejneru|  
|Formulář|  
|LinkLabel|  
|HelpProvider –|  
|Ovládacím MaskedTextBox|  
|MenuStrip/ContextMenuStrip|  
|NumericUpDown|  
|Panel|  
|PictureBox|  
|PrintDocument|  
|PrintPreview-Control|  
|PrintPreview-Dialog|  
|Mřížky|  
|Type|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|Rozdělovač|  
|Ovládacím RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Viz také:

- [Typy ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types.md)
