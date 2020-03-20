---
title: Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 36028d589e98177f6a0e83092edd656860b1a8d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179854"
---
# <a name="ui-automation-support-for-standard-controls"></a>Podpora automatizace uživatelského rozhraní pro standardní ovládací prvky
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsahuje informace o podpoře standardních [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]ovládacích prvků v aplikacích vyvinutých pro rozhraní , Win32 a Windows Forms.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a>Ovládací prvky Nadace prezentace systému Windows  
 Všechny [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky, které poskytují informace nebo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]podporu pro interakci s uživatelem mají plnou nativní podporu pro . Ostatní prvky, například panely, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nejsou viditelné .  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a>Ovládací prvky win32  
 Většina ovládacích prvků [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Win32 jsou vystaveny prostřednictvím zprostředkovatelů na straně klienta v UIAutomationClientsideProviders.dll. Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi UI Automation.  
  
 Plná podpora je poskytována pouze pro ovládací prvky z verze 6 *souboru ComCtrl32.dll*.  
  
 Následující ovládací prvky jsou podporovány.  
  
|Název třídy|Typ ovládacího prvku|  
|----------------|------------------|  
|Tlačítko|Tlačítko|  
|Tlačítko|RadioButton|  
|Tlačítko|Skupina|  
|Tlačítko|CheckBox|  
|Tlačítko|Hypertextový odkaz|  
|Tlačítko|SplitButton|  
|Tlačítko|CheckBox|  
|SeznamKrabičkaEx32|ComboBox|  
|ComboBox|ComboBox|  
|Upravit|Dokument|  
|Upravit|Upravit|  
|SysLink|Hypertextový odkaz|  
|Statická|Text|  
|Statická|Image|  
|SysIPAdresa32|Vlastní|  
|SysHeader32|Položka záhlaví nebo záhlaví|  
|SysListView32|DataGrid|  
|SysListView32|Seznam|  
|ListBox|Seznam|  
|ListBox|Listitem|  
|#32768|Nabídka|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|Richedit|Dokumentu. Viz poznámka.|  
|Richedit20A|Dokument|  
|RichEdit20W|Dokument|  
|RichEdit50W|Dokument|  
|ScrollBar|Posuvník|  
|msctls_trackbar32|Posuvník|  
|msctls_updown32|Číselník|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|Karta|  
|SysTabControl32|Tabitem|  
|Panel nástrojůOkno32|ToolBar|  
|Panel nástrojůOkno32|MenuItem|  
|Panel nástrojůOkno32|Tlačítko|  
|Panel nástrojůOkno32|CheckBox|  
|Panel nástrojůOkno32|RadioButton|  
|Panel nástrojůOkno32|Oddělovač|  
|tooltips_class32|Popisy tlačítek|  
|#32774|Popisy tlačítek|  
|Okno výztuže32|Panel nástrojů|  
|SysTreeView32|Strom|  
|SysTreeView32|Treeitem|  
  
 **Poznámka:** Ovládací prvek RichEdit je podporován pouze pro verze dodávané se systémem Windows Vista (v souboru RichEd20.dll verze 3.1 a novější a MsftEdit.dll verze 4.1 a novější).  
  
 Následující ovládací prvky nejsou podporovány.  
  
|Název třídy|Typ ovládacího prvku|  
|----------------|------------------|  
|SysAnimate32|Image|  
|SysPager|Číselník|  
|SysDateTimePick32|Vlastní|  
|SysMěsícCal32|Kalendář|  
|MS_WINNOTE|Popis|  
|VBBubble|Popis|  
|ScrollBar (při použití jako samostatný ovládací prvek)|Posuvník|  
|SuperGrid|Vlastní|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a>Ovládací prvky Windows Forms  
 Ovládací prvky Windows [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Forms jsou vystaveny prostřednictvím zprostředkovatelů na straně klienta v uIAutomationClientsideProviders.dll. Toto sestavení je automaticky registrováno pro použití s klientskými aplikacemi UI Automation.  
  
 Ovládací prvky windows forms, které jsou spravované obálky pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]běžné ovládací prvky Win32 jsou podporovány . Následující ovládací prvky jsou podporovány.  
  
|Název třídy|  
|----------------|  
|Tlačítko|  
|CheckBox|  
|Checkedlistbox|  
|Colordialog|  
|ComboBox|  
|Prohlížeč složek|  
|Fontdialog|  
|GroupBox|  
|Hscrollbar|  
|Imagelist|  
|Popisek|  
|ListBox|  
|ListView|  
|Hlavní nabídka/kontextová nabídka|  
|MonthCalendar|  
|Notifyicon|  
|Openfiledialog|  
|Pagesetupdialog|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|Savefiledialog|  
|Scrollablecontrol|  
|Soundplayer|  
|StatusBar|  
|TabControl/TabPage|  
|TextBox|  
|Časovač|  
|Panel nástrojů|  
|Popisy tlačítek|  
|Trackbar|  
|TreeView|  
|Vscrollbar|  
|Webbrowser|  
  
 Následující ovládací prvky [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jsou vystaveny pouze prostřednictvím jejich podpory pro microsoft active accessibility. Některé funkce nemusí být k dispozici.  
  
|Název ovládacího prvku|  
|------------------|  
|BindingSource|  
|DataGrid|  
|Datagridview|  
|Datový navigační panel|  
|Domainupdown|  
|ErrorProvider|  
|Flowlayoutpanel|  
|Formulář|  
|Linklabel|  
|Helpprovider|  
|Maskedtextbox|  
|Panel Proužka/Kontextový panel MenuStrip|  
|NumericUpDown|  
|Panel|  
|Picturebox|  
|Printdocument|  
|PrintPreview-Control|  
|Dialogové okno PrintPreview|  
|Propertygrid|  
|Usercontrol|  
|ToolStrip|  
|Tablelayoutpanel|  
|SplitContainer/SplitterPanel|  
|Rozdělovač|  
|RaftingKontejner|  
|StatusStrip|  
  
## <a name="see-also"></a>Viz také

- [Typy ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types.md)
