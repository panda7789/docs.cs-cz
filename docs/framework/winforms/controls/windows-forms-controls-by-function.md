---
title: Ovládací prvky Windows Forms podle funkce
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: 366b7412a61cac9d3706500adaee34fa8659fba2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922721"
---
# <a name="windows-forms-controls-by-function"></a>Ovládací prvky Windows Forms podle funkce
Model Windows Forms nabízí ovládací prvky a komponenty, které provádějí řadu funkcí. Následující tabulka uvádí ovládací prvky a součásti model Windows Forms podle obecné funkce. Kromě toho, kde existuje více ovládacích prvků, které obsluhují stejnou funkci, je doporučený ovládací prvek uveden s poznámkami, které se týkají ovládacího prvku, který nahradil. V samostatné následné tabulce jsou nahrazené ovládací prvky označeny doporučenými nahrazeními.  
  
> [!NOTE]
> V následujících tabulkách nejsou uvedeny všechny ovládací prvky nebo součásti, které můžete použít v model Windows Forms. komplexnější seznam najdete v tématu [ovládací prvky pro použití v model Windows Forms](controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Doporučené ovládací prvky a komponenty podle funkcí  
  
|Funkce|Control|Popis|  
|--------------|-------------|-----------------|  
|Zobrazení dat|<xref:System.Windows.Forms.DataGridView>nad|<xref:System.Windows.Forms.DataGridView> Ovládací prvek poskytuje přizpůsobitelnou tabulku pro zobrazení dat. <xref:System.Windows.Forms.DataGridView> Třída umožňuje přizpůsobit buňky, řádky, sloupce a ohraničení. **Poznámka:**  Ovládací prvek poskytuje řadu základních a rozšířených funkcí, které <xref:System.Windows.Forms.DataGrid> v ovládacím prvku chybí. <xref:System.Windows.Forms.DataGridView> Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md) .|  
|Datová vazba a navigace|<xref:System.Windows.Forms.BindingSource>část|Zjednodušuje ovládací prvky vazby na formuláři na data tím, že poskytuje správu měn, oznamování změn a další služby.|  
||<xref:System.Windows.Forms.BindingNavigator>nad|Poskytuje rozhraní typu panel nástrojů pro navigaci a manipulaci s daty ve formuláři.|  
|Úpravy textu|<xref:System.Windows.Forms.TextBox>nad|Zobrazuje text zadaný v době návrhu, který je možné upravovat uživateli v době běhu, nebo se programově změnil.|  
||<xref:System.Windows.Forms.RichTextBox>nad|Umožňuje zobrazit text s formátováním v prostém textu nebo ve formátu RTF (Rich Text Format).|  
||<xref:System.Windows.Forms.MaskedTextBox>nad|Omezuje formát vstupu uživatele.|  
|Zobrazení informací (jen pro čtení)|<xref:System.Windows.Forms.Label>nad|Zobrazí text, který uživatelé nemohou přímo upravovat.|  
||<xref:System.Windows.Forms.LinkLabel>nad|Zobrazí text jako odkaz na webový styl a aktivuje událost, když uživatel klikne na speciální text. Obvykle je text odkazem na jiné okno nebo Web.|  
||<xref:System.Windows.Forms.StatusStrip>nad|Zobrazí informace o aktuálním stavu aplikace pomocí rámečkované oblasti, obvykle v dolní části nadřazeného formuláře.|  
||<xref:System.Windows.Forms.ProgressBar>nad|Zobrazí aktuální průběh operace s uživatelem.|  
|Zobrazení webové stránky|<xref:System.Windows.Forms.WebBrowser>nad|Umožňuje uživateli procházet webové stránky uvnitř formuláře.|  
|Výběr ze seznamu|<xref:System.Windows.Forms.CheckedListBox>nad|Zobrazí posuvný seznam položek, přičemž každý z nich bude obsahovat zaškrtávací políčko.|  
||<xref:System.Windows.Forms.ComboBox>nad|Zobrazí rozevírací seznam položek.|  
||<xref:System.Windows.Forms.DomainUpDown>nad|Zobrazí seznam textových položek, které mohou uživatelé procházet pomocí tlačítek nahoru a dolů.|  
||<xref:System.Windows.Forms.ListBox>nad|Zobrazí seznam textových a grafických položek (ikony).|  
||<xref:System.Windows.Forms.ListView>nad|Zobrazí položky v jednom ze čtyř různých zobrazení. Zobrazení zahrnují pouze text, text s malými ikonami, text s velkými ikonami a zobrazení podrobností.|  
||<xref:System.Windows.Forms.NumericUpDown>nad|Zobrazí seznam číslic, které mohou uživatelé procházet pomocí tlačítek nahoru a dolů.|  
||<xref:System.Windows.Forms.TreeView>nad|Zobrazuje hierarchickou kolekci objektů uzlů, které se mohou skládat z textu s volitelnými políčky nebo ikonami.|  
|Grafické zobrazení|<xref:System.Windows.Forms.PictureBox>nad|Zobrazí v rámečku grafické soubory, jako jsou rastrové obrázky a ikony.|  
|Grafické úložiště|<xref:System.Windows.Forms.ImageList>nad|Slouží jako úložiště pro image. <xref:System.Windows.Forms.ImageList>ovládací prvky a obrázky, které obsahují, lze znovu použít z jedné aplikace na další.|  
|Nastavení hodnoty|<xref:System.Windows.Forms.CheckBox>nad|Zobrazí zaškrtávací políčko a popisek pro text. Obecně se používá k nastavení možností.|  
||<xref:System.Windows.Forms.CheckedListBox>nad|Zobrazí posuvný seznam položek, přičemž každý z nich bude obsahovat zaškrtávací políčko.|  
||<xref:System.Windows.Forms.RadioButton>nad|Zobrazí tlačítko, které lze zapnout nebo vypnout.|  
||<xref:System.Windows.Forms.TrackBar>nad|Umožňuje uživatelům nastavit hodnoty na stupnici přesunutím "palec" podél škály.|  
|Nastavení data|<xref:System.Windows.Forms.DateTimePicker>nad|Zobrazí grafický kalendář, který uživatelům umožní vybrat datum nebo čas.|  
||<xref:System.Windows.Forms.MonthCalendar>nad|Zobrazí grafický kalendář, který uživatelům umožní vybrat rozsah kalendářních dat.|  
|Dialogová okna|<xref:System.Windows.Forms.ColorDialog>nad|Zobrazí dialogové okno pro výběr barvy, které umožňuje uživatelům nastavit barvu prvku rozhraní.|  
||<xref:System.Windows.Forms.FontDialog>nad|Zobrazí dialogové okno, které umožňuje uživatelům nastavit písmo a jeho atributy.|  
||<xref:System.Windows.Forms.OpenFileDialog>nad|Zobrazí dialogové okno, které umožňuje uživatelům přejít na soubor a vybrat ho.|  
||<xref:System.Windows.Forms.PrintDialog>nad|Zobrazí dialogové okno, které umožňuje uživatelům vybrat tiskárnu a nastavit její atributy.|  
||<xref:System.Windows.Forms.PrintPreviewDialog>nad|Zobrazí dialogové okno, které ukazuje, jak se <xref:System.Drawing.Printing.PrintDocument> při tisku zobrazí komponenta ovládacího prvku.|  
||<xref:System.Windows.Forms.FolderBrowserDialog>nad|Zobrazí dialogové okno, které uživatelům umožňuje procházet, vytvářet a nakonec vybrat složku.|  
||<xref:System.Windows.Forms.SaveFileDialog>nad|Zobrazí dialogové okno, které umožňuje uživatelům uložit soubor.|  
|Ovládací prvky nabídky|<xref:System.Windows.Forms.MenuStrip>nad|Vytvoří vlastní nabídky. **Poznámka:**  Je navržen pro <xref:System.Windows.Forms.MainMenu> nahrazení ovládacího prvku. <xref:System.Windows.Forms.MenuStrip>|  
||<xref:System.Windows.Forms.ContextMenuStrip>nad|Vytvoří vlastní kontextové nabídky. **Poznámka:**  Je navržen pro <xref:System.Windows.Forms.ContextMenu> nahrazení ovládacího prvku. <xref:System.Windows.Forms.ContextMenuStrip>|  
|Příkazy|<xref:System.Windows.Forms.Button>nad|Spustí, zastaví nebo přerušuje proces.|  
||<xref:System.Windows.Forms.LinkLabel>nad|Zobrazí text jako odkaz na webový styl a aktivuje událost, když uživatel klikne na speciální text. Obvykle je text odkazem na jiné okno nebo Web.|  
||<xref:System.Windows.Forms.NotifyIcon>nad|Zobrazí ikonu v oznamovací oblasti pro stav hlavního panelu, která představuje aplikaci spuštěnou na pozadí.|  
||<xref:System.Windows.Forms.ToolStrip>nad|Vytvoří panely nástrojů, které mohou mít Microsoft Windows XP, systém Microsoft Office, Microsoft Internet Explorer nebo vlastní vzhled a chování, s motivy nebo bez motivů, a s podporou přeřazení položek při přetečení a za běhu. **Poznámka:**  Ovládací prvek je navržen pro <xref:System.Windows.Forms.ToolBar> nahrazení ovládacího prvku. <xref:System.Windows.Forms.ToolStrip>|  
|Uživatelská informace|<xref:System.Windows.Forms.HelpProvider>část|Poskytuje místní nebo online nápovědu k ovládacím prvkům.|  
||<xref:System.Windows.Forms.ToolTip>část|Poskytuje automaticky otevírané okno, které zobrazuje stručný popis účelu ovládacího prvku, když uživatel umístí ukazatel na ovládací prvek.|  
|Seskupení dalších ovládacích prvků|<xref:System.Windows.Forms.Panel>nad|Seskupí sadu ovládacích prvků na neoznačený, posuvný rámeček.|  
||<xref:System.Windows.Forms.GroupBox>nad|Seskupí sadu ovládacích prvků (například přepínačů) na označený, neposuvný rámeček.|  
||<xref:System.Windows.Forms.TabControl>nad|Poskytuje stránku s kartami pro efektivní organizování a přístup k seskupeným objektům.|  
||<xref:System.Windows.Forms.SplitContainer>nad|Poskytuje dva panely oddělené pohyblivým pruhem. **Poznámka:**  Ovládací prvek je navržen pro <xref:System.Windows.Forms.Splitter> nahrazení ovládacího prvku. <xref:System.Windows.Forms.SplitContainer>|  
||<xref:System.Windows.Forms.TableLayoutPanel>nad|Představuje panel, který dynamicky rozloží svůj obsah v mřížce skládající se z řádků a sloupců.|  
||<xref:System.Windows.Forms.FlowLayoutPanel>nad|Představuje panel, který dynamicky rozloží svůj obsah vodorovně nebo svisle.|  
|Zvuk|<xref:System.Media.SoundPlayer>nad|Přehrává zvukové soubory ve formátu. wav. Zvuky lze načíst nebo přehrát asynchronně.|  
  
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
