---
title: Ovládací prvky podle funkce
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: f2341d49513b418c244ee7ab93c0858899502487
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741587"
---
# <a name="windows-forms-controls-by-function"></a>Ovládací prvky Windows Forms podle funkce
Model Windows Forms nabízí ovládací prvky a komponenty, které provádějí řadu funkcí. Následující tabulka uvádí ovládací prvky a součásti model Windows Forms podle obecné funkce. Kromě toho, kde existuje více ovládacích prvků, které obsluhují stejnou funkci, je doporučený ovládací prvek uveden s poznámkami, které se týkají ovládacího prvku, který nahradil. V samostatné následné tabulce jsou nahrazené ovládací prvky označeny doporučenými nahrazeními.  
  
> [!NOTE]
> V následujících tabulkách nejsou uvedeny všechny ovládací prvky nebo součásti, které můžete použít v model Windows Forms. komplexnější seznam najdete v tématu [ovládací prvky pro použití v model Windows Forms](controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Doporučené ovládací prvky a komponenty podle funkcí  
  
|Funkce|Control|Popis|  
|--------------|-------------|-----------------|  
|Zobrazení dat|ovládací prvek <xref:System.Windows.Forms.DataGridView>|Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje přizpůsobitelnou tabulku pro zobrazení dat. Třída <xref:System.Windows.Forms.DataGridView> umožňuje přizpůsobit buňky, řádky, sloupce a ohraničení. **Poznámka:**  Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje mnoho základních a rozšířených funkcí, které v ovládacím prvku <xref:System.Windows.Forms.DataGrid> chybí. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md) .|  
|Datová vazba a navigace|komponenta <xref:System.Windows.Forms.BindingSource>|Zjednodušuje ovládací prvky vazby na formuláři na data tím, že poskytuje správu měn, oznamování změn a další služby.|  
||ovládací prvek <xref:System.Windows.Forms.BindingNavigator>|Poskytuje rozhraní typu panel nástrojů pro navigaci a manipulaci s daty ve formuláři.|  
|Úpravy textu|ovládací prvek <xref:System.Windows.Forms.TextBox>|Zobrazuje text zadaný v době návrhu, který je možné upravovat uživateli v době běhu, nebo se programově změnil.|  
||ovládací prvek <xref:System.Windows.Forms.RichTextBox>|Umožňuje zobrazit text s formátováním v prostém textu nebo ve formátu RTF (Rich Text Format).|  
||ovládací prvek <xref:System.Windows.Forms.MaskedTextBox>|Omezuje formát vstupu uživatele.|  
|Zobrazení informací (jen pro čtení)|ovládací prvek <xref:System.Windows.Forms.Label>|Zobrazí text, který uživatelé nemohou přímo upravovat.|  
||ovládací prvek <xref:System.Windows.Forms.LinkLabel>|Zobrazí text jako odkaz na webový styl a aktivuje událost, když uživatel klikne na speciální text. Obvykle je text odkazem na jiné okno nebo Web.|  
||ovládací prvek <xref:System.Windows.Forms.StatusStrip>|Zobrazí informace o aktuálním stavu aplikace pomocí rámečkované oblasti, obvykle v dolní části nadřazeného formuláře.|  
||ovládací prvek <xref:System.Windows.Forms.ProgressBar>|Zobrazí aktuální průběh operace s uživatelem.|  
|Zobrazení webové stránky|ovládací prvek <xref:System.Windows.Forms.WebBrowser>|Umožňuje uživateli procházet webové stránky uvnitř formuláře.|  
|Výběr ze seznamu|ovládací prvek <xref:System.Windows.Forms.CheckedListBox>|Zobrazí posuvný seznam položek, přičemž každý z nich bude obsahovat zaškrtávací políčko.|  
||ovládací prvek <xref:System.Windows.Forms.ComboBox>|Zobrazí rozevírací seznam položek.|  
||ovládací prvek <xref:System.Windows.Forms.DomainUpDown>|Zobrazí seznam textových položek, které mohou uživatelé procházet pomocí tlačítek nahoru a dolů.|  
||ovládací prvek <xref:System.Windows.Forms.ListBox>|Zobrazí seznam textových a grafických položek (ikony).|  
||ovládací prvek <xref:System.Windows.Forms.ListView>|Zobrazí položky v jednom ze čtyř různých zobrazení. Zobrazení zahrnují pouze text, text s malými ikonami, text s velkými ikonami a zobrazení podrobností.|  
||ovládací prvek <xref:System.Windows.Forms.NumericUpDown>|Zobrazí seznam číslic, které mohou uživatelé procházet pomocí tlačítek nahoru a dolů.|  
||ovládací prvek <xref:System.Windows.Forms.TreeView>|Zobrazuje hierarchickou kolekci objektů uzlů, které se mohou skládat z textu s volitelnými políčky nebo ikonami.|  
|Grafické zobrazení|ovládací prvek <xref:System.Windows.Forms.PictureBox>|Zobrazí v rámečku grafické soubory, jako jsou rastrové obrázky a ikony.|  
|Grafické úložiště|ovládací prvek <xref:System.Windows.Forms.ImageList>|Slouží jako úložiště pro image. ovládací prvky <xref:System.Windows.Forms.ImageList> a obrázky, které obsahují, lze znovu použít z jedné aplikace na další.|  
|Nastavení hodnoty|ovládací prvek <xref:System.Windows.Forms.CheckBox>|Zobrazí zaškrtávací políčko a popisek pro text. Obecně se používá k nastavení možností.|  
||ovládací prvek <xref:System.Windows.Forms.CheckedListBox>|Zobrazí posuvný seznam položek, přičemž každý z nich bude obsahovat zaškrtávací políčko.|  
||ovládací prvek <xref:System.Windows.Forms.RadioButton>|Zobrazí tlačítko, které lze zapnout nebo vypnout.|  
||ovládací prvek <xref:System.Windows.Forms.TrackBar>|Umožňuje uživatelům nastavit hodnoty na stupnici přesunutím "palec" podél škály.|  
|Nastavení data|ovládací prvek <xref:System.Windows.Forms.DateTimePicker>|Zobrazí grafický kalendář, který uživatelům umožní vybrat datum nebo čas.|  
||ovládací prvek <xref:System.Windows.Forms.MonthCalendar>|Zobrazí grafický kalendář, který uživatelům umožní vybrat rozsah kalendářních dat.|  
|Dialogová okna|ovládací prvek <xref:System.Windows.Forms.ColorDialog>|Zobrazí dialogové okno pro výběr barvy, které umožňuje uživatelům nastavit barvu prvku rozhraní.|  
||ovládací prvek <xref:System.Windows.Forms.FontDialog>|Zobrazí dialogové okno, které umožňuje uživatelům nastavit písmo a jeho atributy.|  
||ovládací prvek <xref:System.Windows.Forms.OpenFileDialog>|Zobrazí dialogové okno, které umožňuje uživatelům přejít na soubor a vybrat ho.|  
||ovládací prvek <xref:System.Windows.Forms.PrintDialog>|Zobrazí dialogové okno, které umožňuje uživatelům vybrat tiskárnu a nastavit její atributy.|  
||ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog>|Zobrazí dialogové okno, které ukazuje, jak se při tisku zobrazí ovládací prvek <xref:System.Drawing.Printing.PrintDocument> komponenta.|  
||ovládací prvek <xref:System.Windows.Forms.FolderBrowserDialog>|Zobrazí dialogové okno, které uživatelům umožňuje procházet, vytvářet a nakonec vybrat složku.|  
||ovládací prvek <xref:System.Windows.Forms.SaveFileDialog>|Zobrazí dialogové okno, které umožňuje uživatelům uložit soubor.|  
|Ovládací prvky nabídky|ovládací prvek <xref:System.Windows.Forms.MenuStrip>|Vytvoří vlastní nabídky. **Poznámka:**  <xref:System.Windows.Forms.MenuStrip> je navržena tak, aby nahradila <xref:System.Windows.Forms.MainMenu> ovládací prvek.|  
||ovládací prvek <xref:System.Windows.Forms.ContextMenuStrip>|Vytvoří vlastní kontextové nabídky. **Poznámka:**  <xref:System.Windows.Forms.ContextMenuStrip> je navržena tak, aby nahradila <xref:System.Windows.Forms.ContextMenu> ovládací prvek.|  
|Příkazy|ovládací prvek <xref:System.Windows.Forms.Button>|Spustí, zastaví nebo přerušuje proces.|  
||ovládací prvek <xref:System.Windows.Forms.LinkLabel>|Zobrazí text jako odkaz na webový styl a aktivuje událost, když uživatel klikne na speciální text. Obvykle je text odkazem na jiné okno nebo Web.|  
||ovládací prvek <xref:System.Windows.Forms.NotifyIcon>|Zobrazí ikonu v oznamovací oblasti pro stav hlavního panelu, která představuje aplikaci spuštěnou na pozadí.|  
||ovládací prvek <xref:System.Windows.Forms.ToolStrip>|Vytvoří panely nástrojů, které mohou mít Microsoft Windows XP, systém Microsoft Office, Microsoft Internet Explorer nebo vlastní vzhled a chování, s motivy nebo bez motivů, a s podporou přeřazení položek při přetečení a za běhu. **Poznámka:**  <xref:System.Windows.Forms.ToolStrip> ovládací prvek je navržen tak, aby nahradil ovládací prvek <xref:System.Windows.Forms.ToolBar>.|  
|Uživatelská informace|komponenta <xref:System.Windows.Forms.HelpProvider>|Poskytuje místní nebo online nápovědu k ovládacím prvkům.|  
||komponenta <xref:System.Windows.Forms.ToolTip>|Poskytuje automaticky otevírané okno, které zobrazuje stručný popis účelu ovládacího prvku, když uživatel umístí ukazatel na ovládací prvek.|  
|Seskupení dalších ovládacích prvků|ovládací prvek <xref:System.Windows.Forms.Panel>|Seskupí sadu ovládacích prvků na neoznačený, posuvný rámeček.|  
||ovládací prvek <xref:System.Windows.Forms.GroupBox>|Seskupí sadu ovládacích prvků (například přepínačů) na označený, neposuvný rámeček.|  
||ovládací prvek <xref:System.Windows.Forms.TabControl>|Poskytuje stránku s kartami pro efektivní organizování a přístup k seskupeným objektům.|  
||ovládací prvek <xref:System.Windows.Forms.SplitContainer>|Poskytuje dva panely oddělené pohyblivým pruhem. **Poznámka:**  <xref:System.Windows.Forms.SplitContainer> ovládací prvek je navržen tak, aby nahradil ovládací prvek <xref:System.Windows.Forms.Splitter>.|  
||ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel>|Představuje panel, který dynamicky rozloží svůj obsah v mřížce skládající se z řádků a sloupců.|  
||ovládací prvek <xref:System.Windows.Forms.FlowLayoutPanel>|Představuje panel, který dynamicky rozloží svůj obsah vodorovně nebo svisle.|  
|Zvuk|ovládací prvek <xref:System.Media.SoundPlayer>|Přehrává zvukové soubory ve formátu. wav. Zvuky lze načíst nebo přehrát asynchronně.|  
  
## <a name="superseded-controls-and-components-by-function"></a>Nahrazené ovládací prvky a komponenty podle funkce  
  
|Funkce|Nahrazený ovládací prvek|Doporučená náhrada|  
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
