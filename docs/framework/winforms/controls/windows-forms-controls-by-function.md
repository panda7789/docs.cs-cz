---
title: Ovládací prvky Windows Forms podle funkce
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: 3a82642c985b7ec1cee885cdda7b054adbe3dfee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115476"
---
# <a name="windows-forms-controls-by-function"></a>Ovládací prvky Windows Forms podle funkce
Windows Forms nabízí ovládací prvky a součásti, které provádějí celou řadou funkcí. V následující tabulce jsou uvedeny ovládacích prvků Windows Forms a komponentami podle toho, obecné funkce. Kromě toho tam, kde více ovládacích prvků, které slouží stejnou funkci, je uvedený doporučený ovládacího prvku s poznámky týkající se ovládací prvek, který ho nahrazuje. V samostatné tabulce následujících nahrazené ovládací prvky jsou seřazeny jejich doporučená nahrazení.  
  
> [!NOTE]
>  Následující tabulky uvádějí ne každý ovládací prvek nebo součást, kterou můžete použít v modelu Windows Forms; ucelenější seznam najdete v tématu [ovládací prvky používané ve formulářích Windows](controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Doporučené ovládací prvky a součásti podle funkce  
  
|Funkce|Control|Popis|  
|--------------|-------------|-----------------|  
|Zobrazení dat|<xref:System.Windows.Forms.DataGridView> Ovládací prvek|<xref:System.Windows.Forms.DataGridView> Ovládací prvek pro zobrazení dat poskytuje přizpůsobitelné tabulky. <xref:System.Windows.Forms.DataGridView> Třída umožňuje přizpůsobení buněk, řádků, sloupců a ohraničení. **Poznámka:**  <xref:System.Windows.Forms.DataGridView> Řízení poskytuje mnoho základních a pokročilých funkcí, které nebyly nalezeny v <xref:System.Windows.Forms.DataGrid> ovládacího prvku. Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|Vytváření datových vazeb a navigace|<xref:System.Windows.Forms.BindingSource> Komponenta|Vazba ovládacích prvků na formuláři data zjednodušuje tím, že poskytuje správu měny, oznámení o změně a dalším službám.|  
||<xref:System.Windows.Forms.BindingNavigator> Ovládací prvek|Poskytuje rozhraní typ panelu nástrojů k navigaci a manipulaci s daty ve formuláři.|  
|Úpravy textu|<xref:System.Windows.Forms.TextBox> Ovládací prvek|Zobrazí text zadaný v době návrhu, který lze upravovat uživatelé v době běhu, nebo změnit prostřednictvím kódu programu.|  
||<xref:System.Windows.Forms.RichTextBox> Ovládací prvek|Umožňuje text, který se zobrazí při formátování v prostém textu nebo formátu RTF (RTF).|  
||<xref:System.Windows.Forms.MaskedTextBox> Ovládací prvek|Omezí formát vstupu uživatele|  
|Zobrazení informací (jen pro čtení)|<xref:System.Windows.Forms.Label> Ovládací prvek|Zobrazí text, který uživatelé nemohou upravovat přímo.|  
||<xref:System.Windows.Forms.LinkLabel> Ovládací prvek|Text se zobrazí jako odkaz webové – vizuální styl a aktivuje událost, když uživatel klepne na speciální text. Obvykle text je odkaz na další okno nebo webovou stránku.|  
||<xref:System.Windows.Forms.StatusStrip> Ovládací prvek|Zobrazí informace o aktuálním stavu aplikace pomocí orámované oblasti, obvykle v dolní části nadřazený formulář.|  
||<xref:System.Windows.Forms.ProgressBar> Ovládací prvek|Zobrazí aktuální průběh operace pro uživatele.|  
|Zobrazení webové stránky|<xref:System.Windows.Forms.WebBrowser> Ovládací prvek|Umožňuje uživateli procházet webové stránky uvnitř formuláře.|  
|Výběr ze seznamu|<xref:System.Windows.Forms.CheckedListBox> Ovládací prvek|Posuvný seznam položek, každý připojí zaškrtávací políčko.|  
||<xref:System.Windows.Forms.ComboBox> Ovládací prvek|Zobrazí rozevírací seznam položek.|  
||<xref:System.Windows.Forms.DomainUpDown> Ovládací prvek|Zobrazí seznam textových položek, které uživatelé můžou procházet s nahoru a dolů.|  
||<xref:System.Windows.Forms.ListBox> Ovládací prvek|Zobrazí seznam textové a grafické položky (ikon).|  
||<xref:System.Windows.Forms.ListView> Ovládací prvek|Zobrazí položky v jedné ze čtyř různých zobrazení. Zobrazení obsahovat pouze text, text pomocí malé ikony, text se velké ikony a zobrazení podrobností.|  
||<xref:System.Windows.Forms.NumericUpDown> Ovládací prvek|Zobrazí seznam číslic, které uživatelé můžou procházet s nahoru a dolů.|  
||<xref:System.Windows.Forms.TreeView> Ovládací prvek|Zobrazí hierarchickou kolekci uzlu objekty, které se může skládat z textu s volitelné zaškrtávací políčka nebo ikony.|  
|Grafické zobrazení|<xref:System.Windows.Forms.PictureBox> Ovládací prvek|Zobrazí grafický soubory, například rastrové obrázky a ikony v objektu frame.|  
|Úložiště grafiky|<xref:System.Windows.Forms.ImageList> Ovládací prvek|Slouží jako úložiště imagí. <xref:System.Windows.Forms.ImageList> ovládací prvky a obrázky, které obsahují lze znovu použít, z jedné aplikace na další.|  
|Nastavení hodnoty|<xref:System.Windows.Forms.CheckBox> Ovládací prvek|Zobrazuje zaškrtávací políčko a popisek pro text. Obecně lze nastavit možnosti.|  
||<xref:System.Windows.Forms.CheckedListBox> Ovládací prvek|Posuvný seznam položek, každý připojí zaškrtávací políčko.|  
||<xref:System.Windows.Forms.RadioButton> Ovládací prvek|Zobrazí tlačítko, které je možné zapnout nebo vypnout.|  
||<xref:System.Windows.Forms.TrackBar> Ovládací prvek|Umožňuje uživatelům nastavit hodnoty na škále přesunutím "jezdce" podél stupnice.|  
|Nastavení data|<xref:System.Windows.Forms.DateTimePicker> Ovládací prvek|Zobrazí grafické kalendář, který umožňuje uživatelům vybrat datum nebo čas.|  
||<xref:System.Windows.Forms.MonthCalendar> Ovládací prvek|Zobrazí grafické kalendář, chcete-li povolit uživatelům výběr rozsahu kalendářních dat.|  
|Dialogová okna|<xref:System.Windows.Forms.ColorDialog> Ovládací prvek|Zobrazí dialogové okno Výběr barvy, umožňující uživatelům nastavit barvu elementu rozhraní.|  
||<xref:System.Windows.Forms.FontDialog> Ovládací prvek|Zobrazí dialogové okno, které uživatelům umožňuje nastavit písmo a jeho atributy.|  
||<xref:System.Windows.Forms.OpenFileDialog> Ovládací prvek|Zobrazí dialogové okno, které umožňuje uživatelům přejděte a vyberte soubor.|  
||<xref:System.Windows.Forms.PrintDialog> Ovládací prvek|Zobrazí dialogové okno, které umožňuje uživatelům vybrat tiskárnu a nastavte jeho atributy.|  
||<xref:System.Windows.Forms.PrintPreviewDialog> Ovládací prvek|Zobrazí dialogové okno, které se zobrazí, jak ovládací prvek <xref:System.Drawing.Printing.PrintDocument> součást se zobrazí po vytištění.|  
||<xref:System.Windows.Forms.FolderBrowserDialog> Ovládací prvek|Zobrazí dialogové okno, které umožňuje uživatelům procházet, vytvářet a nakonec vyberte složku|  
||<xref:System.Windows.Forms.SaveFileDialog> Ovládací prvek|Zobrazí dialogové okno, které umožňuje uživatelům k uložení souboru.|  
|Ovládací prvky nabídky|<xref:System.Windows.Forms.MenuStrip> Ovládací prvek|Vytvoří vlastní nabídky. **Poznámka:**  <xref:System.Windows.Forms.MenuStrip> Je určena k nahrazení <xref:System.Windows.Forms.MainMenu> ovládacího prvku.|  
||<xref:System.Windows.Forms.ContextMenuStrip> Ovládací prvek|Vytvoří vlastní místní nabídky. **Poznámka:**  <xref:System.Windows.Forms.ContextMenuStrip> Je určena k nahrazení <xref:System.Windows.Forms.ContextMenu> ovládacího prvku.|  
|Příkazy|<xref:System.Windows.Forms.Button> Ovládací prvek|Spustí, zastaví nebo přeruší procesu.|  
||<xref:System.Windows.Forms.LinkLabel> Ovládací prvek|Text se zobrazí jako odkaz webové – vizuální styl a aktivuje událost, když uživatel klepne na speciální text. Obvykle text je odkaz na další okno nebo webovou stránku.|  
||<xref:System.Windows.Forms.NotifyIcon> Ovládací prvek|Zobrazuje ikonu v oznamovací oblasti stav na hlavním panelu, který představuje aplikace běžící na pozadí.|  
||<xref:System.Windows.Forms.ToolStrip> Ovládací prvek|Vytvoří panely nástrojů, které můžou mít Microsoft Windows XP, aplikace Microsoft Office, aplikace Microsoft Internet Explorer nebo vlastní vzhled a chování, s nebo bez motivy a díky podpoře pro přetečení a také přeuspořádání položek za běhu. **Poznámka:**  <xref:System.Windows.Forms.ToolStrip> Ovládací prvek je určen k nahrazení <xref:System.Windows.Forms.ToolBar> ovládacího prvku.|  
|Nápověda pro uživatele|<xref:System.Windows.Forms.HelpProvider> Komponenta|Zajišťuje místní nápovědu nebo nápovědu online pro ovládací prvky.|  
||<xref:System.Windows.Forms.ToolTip> Komponenta|Poskytuje automaticky otevírané okno zobrazující stručný popis účelu ovládacího prvku, když uživatel ponechá ukazatel na ovládací prvek.|  
|Seskupení jiných ovládacích prvků|<xref:System.Windows.Forms.Panel> Ovládací prvek|Seskupit sadu ovládacích prvků na nepopsané posuvný rámečku.|  
||<xref:System.Windows.Forms.GroupBox> Ovládací prvek|Seskupit sadu ovládacích prvků (například přepínačů) na blok s popiskem, nonscrollable.|  
||<xref:System.Windows.Forms.TabControl> Ovládací prvek|Poskytuje stránka s kartami k uspořádání a přístup k efektivní seskupení objektů.|  
||<xref:System.Windows.Forms.SplitContainer> Ovládací prvek|Poskytuje dva panely oddělené přesouvatelný panelu. **Poznámka:**  <xref:System.Windows.Forms.SplitContainer> Ovládací prvek je určen k nahrazení <xref:System.Windows.Forms.Splitter> ovládacího prvku.|  
||<xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek|Představuje panel, který dynamicky rozložen její obsah do mřížky skládá z řádků a sloupců.|  
||<xref:System.Windows.Forms.FlowLayoutPanel> Ovládací prvek|Představuje panel, který dynamicky obsah rozložen vodorovně nebo svisle.|  
|Zvuk|<xref:System.Media.SoundPlayer> Ovládací prvek|Přehrává zvukové soubory ve formátu WAV. Zvuky můžete načíst nebo přehrát asynchronně.|  
  
## <a name="superseded-controls-and-components-by-function"></a>Platnost nahrazených ovládací prvky a součásti podle funkce  
  
|Funkce|Nahrazené ovládacího prvku|Doporučená nahrazení|  
|--------------|------------------------|-----------------------------|  
|Zobrazení dat|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|Zobrazení informací (ovládací prvky jen pro čtení)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Ovládací prvky nabídky|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|Příkazy|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Rozložení formuláře|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](developing-custom-windows-forms-controls.md)
