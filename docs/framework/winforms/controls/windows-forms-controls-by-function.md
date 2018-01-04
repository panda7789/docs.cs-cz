---
title: "Ovládací prvky Windows Forms podle funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a48e1e728e3ded58b0045554a81588933027074c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-controls-by-function"></a>Ovládací prvky Windows Forms podle funkce
Windows Forms nabízí ovládací prvky a součásti, které provádět spoustu funkcí. Následující tabulka uvádí Windows Forms – ovládací prvky a součásti podle obecné funkce. Kromě toho kde více ovládacích prvků existují, které slouží stejnou funkci, je uvedena doporučené ovládacího prvku se poznámky týkající se ovládací prvek, který je nahrazena. V samostatné následné tabulce jsou uvedeny nahrazené ovládací prvky s jejich doporučené nahrazení.  
  
> [!NOTE]
>  Následující tabulky, neuvádějte každý ovládací prvek nebo součást, kterou můžete použít v systému Windows Forms; komplexnější seznam najdete v tématu [ovládací prvky používané ve formulářích Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Doporučené ovládací prvky a součásti podle funkce  
  
|Funkce|Ovládací prvek|Popis|  
|--------------|-------------|-----------------|  
|Zobrazení dat|<xref:System.Windows.Forms.DataGridView>ovládací prvek|<xref:System.Windows.Forms.DataGridView> Řízení poskytuje přizpůsobitelné tabulku pro zobrazení dat. <xref:System.Windows.Forms.DataGridView> Třída umožňuje přizpůsobení buněk, řádků, sloupců a ohraničení. **Poznámka:** <xref:System.Windows.Forms.DataGridView> řízení poskytuje mnoho základních a pokročilých funkcí, které chybí v <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|Datová vazba a navigace|<xref:System.Windows.Forms.BindingSource>součást|Vazba ovládacích prvků ve formuláři na data zjednodušuje tím, že poskytuje správu měny, oznámení o změně a dalším službám.|  
||<xref:System.Windows.Forms.BindingNavigator>ovládací prvek|Poskytuje rozhraní typ panelu nástrojů navigace a manipulace dat ve formuláři.|  
|Úpravy textu|<xref:System.Windows.Forms.TextBox>ovládací prvek|Zobrazí text zadaný v době návrhu, který lze upravovat uživatelé v době běhu, nebo změnit prostřednictvím kódu programu.|  
||<xref:System.Windows.Forms.RichTextBox>ovládací prvek|Umožňuje text, který se zobrazí, formátování v prostém textu nebo RTF (rich text format).|  
||<xref:System.Windows.Forms.MaskedTextBox>ovládací prvek|Omezí formát vstupu uživatele|  
|Zobrazení informací (jen pro čtení)|<xref:System.Windows.Forms.Label>ovládací prvek|Zobrazí text, který uživatelé nemohou upravovat přímo.|  
||<xref:System.Windows.Forms.LinkLabel>ovládací prvek|Zobrazí text jako odkaz webové style a aktivuje událost, když uživatel klikne speciální text. Text je obvykle odkaz na další okno nebo na web.|  
||<xref:System.Windows.Forms.StatusStrip>ovládací prvek|Zobrazí informace o aktuálním stavu aplikace pomocí rámcová oblasti, obvykle v dolní části formuláře nadřazené.|  
||<xref:System.Windows.Forms.ProgressBar>ovládací prvek|Zobrazuje aktuální průběh operace uživateli.|  
|Zobrazení webové stránky|<xref:System.Windows.Forms.WebBrowser>ovládací prvek|Umožňuje uživatelům přejděte webové stránky uvnitř formuláře.|  
|Výběr ze seznamu|<xref:System.Windows.Forms.CheckedListBox>ovládací prvek|Zobrazí posuvný seznam položek, každý připojí zaškrtávací políčko.|  
||<xref:System.Windows.Forms.ComboBox>ovládací prvek|Zobrazí rozevírací seznam položek.|  
||<xref:System.Windows.Forms.DomainUpDown>ovládací prvek|Zobrazí seznam textu položek, které uživatelé mohou posouvat pomocí tlačítka nahoru a dolů.|  
||<xref:System.Windows.Forms.ListBox>ovládací prvek|Zobrazí seznam textu a grafické položky (ikon).|  
||<xref:System.Windows.Forms.ListView>ovládací prvek|Zobrazí položky v jedné ze čtyř různých zobrazení. Zobrazení zahrnují jenom text, textu pomocí ikony. Malé ikony, textu pomocí ikony. velké ikony a zobrazení podrobností.|  
||<xref:System.Windows.Forms.NumericUpDown>ovládací prvek|Zobrazí seznam číslic, které uživatelé mohou posouvat pomocí tlačítka nahoru a dolů.|  
||<xref:System.Windows.Forms.TreeView>ovládací prvek|Zobrazí hierarchické kolekci uzlu objekty, které se může skládat z textu pomocí volitelné zaškrtávací políčka nebo ikon.|  
|Zobrazení grafiky|<xref:System.Windows.Forms.PictureBox>ovládací prvek|Zobrazí grafický soubory, třeba rastrové obrázky a ikony v rámci.|  
|Úložiště grafiky|<xref:System.Windows.Forms.ImageList>ovládací prvek|Slouží jako úložiště pro bitové kopie. <xref:System.Windows.Forms.ImageList>ovládací prvky a bitových kopií, které obsahují lze znovu použít, z jedné aplikace na další.|  
|Nastavení hodnoty|<xref:System.Windows.Forms.CheckBox>ovládací prvek|Zobrazuje zaškrtávací políčko a štítek pro text. Obvykle se používá k nastavení možností.|  
||<xref:System.Windows.Forms.CheckedListBox>ovládací prvek|Zobrazí posuvný seznam položek, každý připojí zaškrtávací políčko.|  
||<xref:System.Windows.Forms.RadioButton>ovládací prvek|Zobrazí tlačítko, které můžete zapnout nebo vypnout.|  
||<xref:System.Windows.Forms.TrackBar>ovládací prvek|Umožňuje uživatelům nastavit hodnoty na škále přesunutím "jezdec" podél škálování.|  
|Nastavení data|<xref:System.Windows.Forms.DateTimePicker>ovládací prvek|Zobrazí grafický kalendář, aby uživatelé mohli vybrat datum nebo čas.|  
||<xref:System.Windows.Forms.MonthCalendar>ovládací prvek|Zobrazí grafický kalendář, aby uživatelé mohli vybrat rozsah kalendářních dat.|  
|Dialogová okna|<xref:System.Windows.Forms.ColorDialog>ovládací prvek|Zobrazí dialogové okno pro výběr barev, který umožňuje uživatelům nastavit barvu elementu rozhraní.|  
||<xref:System.Windows.Forms.FontDialog>ovládací prvek|Zobrazí dialogové okno, které umožňuje uživatelům nastavit písmo a jeho atributy.|  
||<xref:System.Windows.Forms.OpenFileDialog>ovládací prvek|Zobrazí dialogové okno, které umožňuje uživatelům najděte a vyberte soubor.|  
||<xref:System.Windows.Forms.PrintDialog>ovládací prvek|Zobrazí dialogové okno, které umožňuje uživatelům vybrat tiskárnu a nastavit jeho atributy.|  
||<xref:System.Windows.Forms.PrintPreviewDialog>ovládací prvek|Zobrazí dialogové okno se zobrazí jak ovládacího prvku <xref:System.Drawing.Printing.PrintDocument> součást se zobrazí při tisku.|  
||<xref:System.Windows.Forms.FolderBrowserDialog>ovládací prvek|Zobrazí dialogové okno, které umožňuje uživatelům procházet, vytvoření a nakonec vyberte složku|  
||<xref:System.Windows.Forms.SaveFileDialog>ovládací prvek|Zobrazí dialogové okno, které umožňuje uživatelům uložení souboru.|  
|Ovládací prvky nabídky|<xref:System.Windows.Forms.MenuStrip>ovládací prvek|Vytvoří vlastní nabídky. **Poznámka:** <xref:System.Windows.Forms.MenuStrip> nahrazuje <xref:System.Windows.Forms.MainMenu> ovládacího prvku.|  
||<xref:System.Windows.Forms.ContextMenuStrip>ovládací prvek|Vytvoří vlastní kontextové nabídky. **Poznámka:** <xref:System.Windows.Forms.ContextMenuStrip> nahrazuje <xref:System.Windows.Forms.ContextMenu> ovládacího prvku.|  
|Příkazy|<xref:System.Windows.Forms.Button>ovládací prvek|Spustí, zastaví nebo přerušení proces.|  
||<xref:System.Windows.Forms.LinkLabel>ovládací prvek|Zobrazí text jako odkaz webové style a aktivuje událost, když uživatel klikne speciální text. Text je obvykle odkaz na další okno nebo na web.|  
||<xref:System.Windows.Forms.NotifyIcon>ovládací prvek|Zobrazí ikonu v oznamovací oblasti stav na hlavním panelu, který představuje aplikace běžící na pozadí.|  
||<xref:System.Windows.Forms.ToolStrip>ovládací prvek|Panely nástrojů, které je možné Microsoft Windows XP, Microsoft Office, aplikace Microsoft Internet Explorer nebo vlastní vzhled a chování, s nebo bez motivy a s podporou přetečení a změna pořadí položek spuštění vytvoří. **Poznámka:** <xref:System.Windows.Forms.ToolStrip> ovládací prvek je určen k nahrazení <xref:System.Windows.Forms.ToolBar> ovládacího prvku.|  
|Uživatelské nápovědy|<xref:System.Windows.Forms.HelpProvider>součást|Obsahuje místní nebo online nápovědu pro ovládací prvky.|  
||<xref:System.Windows.Forms.ToolTip>součást|Poskytuje místní okno, který se zobrazí stručný popis účelu ovládacího prvku, když uživatel ponechá ukazatel myši na ovládací prvek.|  
|Seskupování dalších ovládacích prvků|<xref:System.Windows.Forms.Panel>ovládací prvek|Skupiny sadu ovládacích prvků na bez popisku posouvatelného rámečku.|  
||<xref:System.Windows.Forms.GroupBox>ovládací prvek|Skupiny sadu ovládacích prvků (například přepínačů) na snímek s popisem, nonscrollable.|  
||<xref:System.Windows.Forms.TabControl>ovládací prvek|Poskytuje stránce s kartami k uspořádání a přístup k efektivní seskupené objekty.|  
||<xref:System.Windows.Forms.SplitContainer>ovládací prvek|Poskytuje dvě panely oddělených mobilní panelu. **Poznámka:** <xref:System.Windows.Forms.SplitContainer> ovládací prvek je určen k nahrazení <xref:System.Windows.Forms.Splitter> ovládacího prvku.|  
||<xref:System.Windows.Forms.TableLayoutPanel>ovládací prvek|Představuje panel, který dynamicky rozložen jeho obsah v mřížce skládá z řádků a sloupců.|  
||<xref:System.Windows.Forms.FlowLayoutPanel>ovládací prvek|Představuje panel, který dynamicky obsah rozložen vodorovně nebo svisle.|  
|zvuk|<xref:System.Media.SoundPlayer>ovládací prvek|Plní zvukové soubory ve formátu WAV. Zvuků můžete načíst nebo asynchronně přehrána.|  
  
## <a name="superseded-controls-and-components-by-function"></a>Nahrazené ovládací prvky a součásti podle funkce  
  
|Funkce|Nahrazené ovládací prvek|Doporučené nahrazení|  
|--------------|------------------------|-----------------------------|  
|Zobrazení dat|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|Zobrazení informací (ovládací prvky určené jen pro čtení)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Ovládací prvky nabídky|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|Příkazy|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Rozložení formuláře|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
