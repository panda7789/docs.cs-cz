---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
description: Získejte informace o podpoře automatizace uživatelského rozhraní pro standardní ovládací prvky v aplikacích vyvinutých pro Windows Presentation Foundation (WPF), Win32 a model Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 17916a6978008439e91caae00d8b6f26045f9018
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166124"
---
# <a name="ui-automation-support-for-standard-controls"></a>Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podpoře standardních ovládacích prvků v aplikacích vyvinutých pro rozhraní [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] , Win32 a model Windows Forms.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a>Ovládací prvky Windows Presentation Foundation  
 Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] prvky ovládacích prvků, které poskytují informace nebo podporu pro interakci s uživatelem, mají úplnou nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Jiné prvky, například panely, nejsou viditelné pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a>Ovládací prvky Win32  
 Většina ovládacích prvků Win32 se zveřejňuje [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím poskytovatelů na straně klienta v UIAutomationClientsideProviders.dll. Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.  
  
 Plná podpora je k dispozici pouze pro ovládací prvky z verze 6 *ComCtrl32.dll*.  
  
 Podporovány jsou následující ovládací prvky.  
  
|Název třídy|Typ ovládacího prvku|  
|----------------|------------------|  
|Tlačítko|Tlačítko|  
|Tlačítko|RadioButton|  
|Tlačítko|Skupina|  
|Tlačítko|Zaškrtávací políčko|  
|Tlačítko|Hypertextový odkaz|  
|Tlačítko|SplitButton|  
|Tlačítko|Zaškrtávací políčko|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Upravit|Dokument|  
|Upravit|Upravit|  
|SysLink|Hypertextový odkaz|  
|Statická|Text|  
|Statická|Image|  
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
|ToolbarWindow32|Zaškrtávací políčko|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|Oddělovač|  
|tooltips_class32|Popisy tlačítek|  
|#32774|Popisy tlačítek|  
|ReBarWindow32|Panel nástrojů|  
|SysTreeView32|Strom|  
|SysTreeView32|TreeItem|  
  
 **Poznámka:** Ovládací prvek RichEdit je podporován pouze pro verze dodávané se systémem Windows Vista (v RichEd20.dll verze 3,1 a novější a MsftEdit.dll verze 4,1 a novější).  
  
 Následující ovládací prvky nejsou podporovány.  
  
|Název třídy|Typ ovládacího prvku|  
|----------------|------------------|  
|SysAnimate32|Image|  
|SysPager|Číselník|  
|SysDateTimePick32|Vlastní|  
|SysMonthCal32|Kalendář|  
|MS_WINNOTE|Popis tlačítka|  
|VBBubble|Popis tlačítka|  
|ScrollBar (při použití jako samostatného ovládacího prvku)|Posuvník|  
|Mřížka|Vlastní|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a>Ovládací prvky Windows Forms  
 Ovládací prvky model Windows Forms jsou zpřístupněny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím poskytovatelů na straně klienta v UIAutomationClientsideProviders.dll. Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi automatizace uživatelského rozhraní.  
  
 Obvykle jsou model Windows Forms ovládací prvky, které jsou spravované obálky pro běžné ovládací prvky Win32, podporovány nástrojem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Podporovány jsou následující ovládací prvky.  
  
|Název třídy|  
|----------------|  
|Tlačítko|  
|Zaškrtávací políčko|  
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
|Ovládací prvek ScrollableControl|  
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
  
 Následující ovládací prvky jsou k dispozici [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pouze prostřednictvím jejich podpory pro Microsoft Active Accessibility. Některé funkce nemusí být k dispozici.  
  
|Název ovládacího prvku|  
|------------------|  
|BindingSource|  
|DataGrid|  
|DataGridView|  
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
|PrintPreview – ovládací prvek|  
|PrintPreview – dialogové okno|  
|Mřížky|  
|Type|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|Rozdělovač|  
|Ovládacím RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Viz také

- [Typy ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types.md)
