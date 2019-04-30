---
title: DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid column types [WPF]
- DataGrid scenarios [WPF]
- DataGrid control [WPF]
- controls [WPF], DataGrid
- DataGrid [WPF], common tasks for
- DataGrid [WPF], customizing the appearance of
- DataGrid columns [WPF], using
ms.assetid: bf89ea63-79b6-422b-bc9f-0485ad803216
ms.openlocfilehash: dda712d58a4ff956de074ecd416402ba0aece5f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912233"
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid> Řízení umožňuje zobrazit a upravit data z mnoha různých zdrojů, jako například z databáze SQL, dotaz LINQ nebo kterýkoli jiný zdroj dat s možností vazby. Další informace najdete v tématu [Přehled zdrojů vazby](../data/binding-sources-overview.md).  
  
 Text, ovládací prvky, můžete zobrazit jako sloupce <xref:System.Windows.Controls.ComboBox>, nebo jakýkoli jiný WPF obsah, jako jsou obrázky, tlačítek nebo veškerý obsah v šabloně. Můžete použít <xref:System.Windows.Controls.DataGridTemplateColumn> zobrazení dat, které jsou definovány v šabloně. Následující tabulka uvádí typy sloupců, které jsou k dispozici ve výchozím nastavení.  
  
|Typ generovaného sloupce|Datový typ|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid> je možné přizpůsobit vzhled, jako je například buňky písma, barvu a velikost. <xref:System.Windows.Controls.DataGrid> podporuje všechny styly a šablony funkce jiných ovládacích prvků WPF. <xref:System.Windows.Controls.DataGrid> také obsahuje výchozí a přizpůsobit chování pro úpravy, řazení a ověřování.  
  
 Následující tabulka uvádí některé běžné úlohy pro <xref:System.Windows.Controls.DataGrid> a způsobu jejich provedení. Zobrazení souvisejících rozhraní API, můžete najít další informace a ukázky kódu.  
  
|Scénář|Přístup|  
|--------------|--------------|  
|Alternující barvy pozadí|Nastavte <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> vlastnost na hodnotu 2 nebo více a pak mu přiřaďte <xref:System.Windows.Media.Brush> k <xref:System.Windows.Controls.DataGrid.RowBackground%2A> a <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> vlastnosti.|  
|Definování chování výběru řádků a buňky|Nastavte <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> a <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> vlastnosti.|  
|Přizpůsobit vzhled záhlaví buňky a řádků|Použít novou <xref:System.Windows.Style> k <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.CellStyle%2A>, nebo <xref:System.Windows.Controls.DataGrid.RowStyle%2A> vlastnosti.|  
|Nastavit možnosti změny velikosti|Nastavte <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, nebo <xref:System.Windows.FrameworkElement.MinWidth%2A> vlastnosti. Další informace najdete v tématu [možnosti nastavení velikosti v ovládacím prvku DataGrid](sizing-options-in-the-datagrid-control.md).|  
|Přístup k vybrané položky|Zkontrolujte <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> vlastnost k získání vybraných buněk a <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> vlastnost k získání vybrané řádky. Další informace naleznete v tématu <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Upravit interakce s koncovým uživatelem|Nastavte <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>, a <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> vlastnosti.|  
|Zrušit nebo změnit automaticky generovaný sloupce|Zpracování <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> událostí.|  
|Ukotvit sloupec|Nastavte <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> vlastnost na hodnotu 1 a přesunout sloupce nejvíce vlevo umístění tak, že nastavíte <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> vlastnost na hodnotu 0.|  
|Použití dat XML jako zdroj dat|Vytvoření vazby <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> na <xref:System.Windows.Controls.DataGrid> pro dotaz XPath, který představuje kolekci položek. Vytvořit jednotlivé sloupce ve <xref:System.Windows.Controls.DataGrid>. Vytvoření vazby každý sloupec tak, že nastavíte argument XPath na vazbu k dotazu, který získá vlastnost na zdroj položky. Příklad naleznete v tématu <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Návod: Zobrazení dat z databáze systému SQL Server v ovládacím prvku DataGrid](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Popisuje, jak vytvořit nový projekt WPF, přidejte Entity Framework Element, nastavit zdroje a zobrazení dat v <xref:System.Windows.Controls.DataGrid>.|  
|[Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid](how-to-add-row-details-to-a-datagrid-control.md)|Popisuje, jak vytvořit řádek podrobnosti <xref:System.Windows.Controls.DataGrid>.|  
|[Postupy: Implementace ověření pomocí ovládacího prvku DataGrid](how-to-implement-validation-with-the-datagrid-control.md)|Popisuje, jak ověřte hodnoty v <xref:System.Windows.Controls.DataGrid> buňky a řádky a ověření zobrazení zpětné vazby.|  
|[Výchozí chování klávesnice a myši v ovládacím prvku DataGrid](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Popisuje, jak pracovat <xref:System.Windows.Controls.DataGrid> ovládacího prvku pomocí klávesnice a myši.|  
|[Postupy: Seskupení, řazení a filtrování dat v ovládacím prvku DataGrid](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Popisuje postup zobrazení dat v <xref:System.Windows.Controls.DataGrid> seskupení, řazení a filtrování dat různými způsoby.|  
|[Možnosti změny velikosti v ovládacím prvku DataGrid](sizing-options-in-the-datagrid-control.md)|Popisuje, jak řídit absolutní a Automatická změna velikosti v <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.DataGrid>
- [Styly a šablony](styling-and-templating.md)
- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Přehled datových šablon](../data/data-templating-overview.md)
- [Ovládací prvky](index.md)
- [Model obsahu WPF](wpf-content-model.md)
