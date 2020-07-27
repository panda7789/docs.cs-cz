---
title: DataGrid
description: Přečtěte si, jak ovládací prvek DataGrid umožňuje zobrazit a upravit data z různých zdrojů, jako je databáze, dotaz LINQ nebo jakýkoli jiný zdroj dat s možností vazby.
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
ms.openlocfilehash: 3db49c12fcb363ef7f99e5c69beae09ab05addcf
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168323"
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid>Ovládací prvek umožňuje zobrazit a upravit data z mnoha různých zdrojů, například z databáze SQL, dotazu LINQ nebo jakéhokoli jiného zdroje dat s možností vazby. Další informace najdete v tématu [Přehled zdrojů vazby](../data/binding-sources-overview.md).  
  
 Sloupce mohou zobrazovat text, ovládací prvky, jako například <xref:System.Windows.Controls.ComboBox> , nebo jakýkoli jiný obsah WPF, například obrázky, tlačítka nebo jakýkoli obsah obsažený v šabloně. Můžete použít <xref:System.Windows.Controls.DataGridTemplateColumn> k zobrazení dat definovaných v šabloně. V následující tabulce jsou uvedeny typy sloupců, které jsou ve výchozím nastavení k dispozici.  
  
|Typ generovaného sloupce|Typ dat|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>lze přizpůsobit vzhled, jako je písmo buňky, barva a velikost. <xref:System.Windows.Controls.DataGrid>podporuje všechny styly a funkce šablonování jiných ovládacích prvků WPF. <xref:System.Windows.Controls.DataGrid>zahrnuje také výchozí a přizpůsobitelné chování pro úpravy, řazení a ověřování.  
  
 V následující tabulce jsou uvedeny některé běžné úlohy pro <xref:System.Windows.Controls.DataGrid> a jejich provádění. Zobrazením souvisejících rozhraní API můžete najít další informace a ukázkový kód.  
  
|Scénář|Přístup|  
|--------------|--------------|  
|Střídavé barvy pozadí|Nastavte <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> vlastnost na 2 nebo více a potom přiřaďte <xref:System.Windows.Media.Brush> <xref:System.Windows.Controls.DataGrid.RowBackground%2A> <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> vlastnosti a.|  
|Definování chování při výběru buněk a řádků|Nastavte <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> vlastnosti a <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> .|  
|Přizpůsobení vizuálního vzhledu záhlaví, buněk a řádků|Použijte nový <xref:System.Windows.Style> pro <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A> <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A> vlastnosti,, <xref:System.Windows.Controls.DataGrid.CellStyle%2A> nebo <xref:System.Windows.Controls.DataGrid.RowStyle%2A> .|  
|Nastavení možností změny velikosti|Nastavte <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti, <xref:System.Windows.FrameworkElement.MaxHeight%2A> , <xref:System.Windows.FrameworkElement.MinHeight%2A> , <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.FrameworkElement.MaxWidth%2A> nebo <xref:System.Windows.FrameworkElement.MinWidth%2A> . Další informace najdete v tématu [Možnosti změny velikosti v ovládacím prvku DataGrid](sizing-options-in-the-datagrid-control.md).|  
|Přístup k vybraným položkám|Ověřte <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> vlastnost a získejte vybrané buňky a <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> vlastnost pro získání vybraných řádků. Další informace naleznete v tématu <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Přizpůsobení interakcí koncových uživatelů|Nastavte <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A> vlastnosti, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A> , <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A> , <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A> , <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A> a <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> .|  
|Zrušení nebo změna automaticky generovaných sloupců|Zpracujte <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> událost.|  
|Ukotvit sloupec|Nastavte <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> vlastnost na 1 a sloupec přesuňte na nejvyšší pozici tak, že nastavíte <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> vlastnost na hodnotu 0.|  
|Použít data XML jako zdroj dat|Vytvořte vazby na <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.DataGrid> k dotazu XPath, který představuje kolekci položek. Vytvořte jednotlivé sloupce v <xref:System.Windows.Controls.DataGrid> . Svázat jednotlivé sloupce nastavením XPath u vazby na dotaz, který získá vlastnost u zdroje položky. Příklad naleznete v tématu <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Návod: Zobrazení dat z databáze SQL Serveru v ovládacím prvku DataGrid](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Popisuje, jak nastavit nový projekt WPF, přidat prvek Entity Framework, nastavit zdroj a zobrazit data v <xref:System.Windows.Controls.DataGrid> .|  
|[Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid](how-to-add-row-details-to-a-datagrid-control.md)|Popisuje, jak vytvořit podrobnosti řádku pro <xref:System.Windows.Controls.DataGrid> .|  
|[Postupy: Implementace ověření pomocí ovládacího prvku DataGrid](how-to-implement-validation-with-the-datagrid-control.md)|Popisuje ověření hodnot v <xref:System.Windows.Controls.DataGrid> buňkách a řádcích a zobrazení zpětné vazby k ověření.|  
|[Výchozí chování klávesnice a myši v ovládacím prvku DataGrid](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Popisuje, jak pracovat s <xref:System.Windows.Controls.DataGrid> ovládacím prvkem pomocí klávesnice a myši.|  
|[Postupy: Seskupení, řazení a filtrování dat v ovládacím prvku DataGrid](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Popisuje, jak zobrazit data <xref:System.Windows.Controls.DataGrid> různými způsoby seskupením, řazením a filtrováním dat.|  
|[Možnosti změny velikosti v ovládacím prvku DataGrid](sizing-options-in-the-datagrid-control.md)|V této části najdete popis postupu při řízení absolutních a automatických velikostí v <xref:System.Windows.Controls.DataGrid> .|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.DataGrid>
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled datových šablon](../data/data-templating-overview.md)
- [Ovládací prvky](index.md)
- [Model obsahu WPF](wpf-content-model.md)
