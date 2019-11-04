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
ms.openlocfilehash: f0887f36990de483139a9fde1472a78737cb7b72
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460384"
---
# <a name="datagrid"></a>DataGrid
Ovládací prvek <xref:System.Windows.Controls.DataGrid> umožňuje zobrazit a upravit data z mnoha různých zdrojů, například z databáze SQL, dotazu LINQ nebo jakéhokoli jiného zdroje dat s možností vazby. Další informace najdete v tématu [Přehled zdrojů vazby](../data/binding-sources-overview.md).  
  
 Sloupce mohou zobrazovat text, ovládací prvky, například <xref:System.Windows.Controls.ComboBox>nebo jakýkoli jiný obsah WPF, například obrázky, tlačítka nebo jakýkoli obsah obsažený v šabloně. Pomocí <xref:System.Windows.Controls.DataGridTemplateColumn> můžete zobrazit data definovaná v šabloně. V následující tabulce jsou uvedeny typy sloupců, které jsou ve výchozím nastavení k dispozici.  
  
|Typ generovaného sloupce|Datový typ|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid> lze přizpůsobit vzhled, jako je například písmo buňky, barva a velikost. <xref:System.Windows.Controls.DataGrid> podporuje všechny funkce stylů a šablonování jiných ovládacích prvků WPF. <xref:System.Windows.Controls.DataGrid> také obsahuje výchozí a přizpůsobitelné chování pro úpravy, řazení a ověřování.  
  
 V následující tabulce jsou uvedeny některé běžné úlohy <xref:System.Windows.Controls.DataGrid> a jejich provádění. Zobrazením souvisejících rozhraní API můžete najít další informace a ukázkový kód.  
  
|Scénář|Přístup|  
|--------------|--------------|  
|Střídavé barvy pozadí|Nastavte vlastnost <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> na 2 nebo více a potom přiřaďte <xref:System.Windows.Media.Brush> vlastností <xref:System.Windows.Controls.DataGrid.RowBackground%2A> a <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A>.|  
|Definování chování při výběru buněk a řádků|Nastavte vlastnosti <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> a <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A>.|  
|Přizpůsobení vizuálního vzhledu záhlaví, buněk a řádků|Použijte nový <xref:System.Windows.Style> vlastností <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.CellStyle%2A>nebo <xref:System.Windows.Controls.DataGrid.RowStyle%2A>.|  
|Nastavení možností změny velikosti|Set the <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, or <xref:System.Windows.FrameworkElement.MinWidth%2A> properties. For more information, see [Sizing Options in the DataGrid Control](sizing-options-in-the-datagrid-control.md).|  
|Access selected items|Check the <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> property to get the selected cells and the <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> property to get the selected rows. Další informace najdete v tématu <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Customize end-user interactions|Set the <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>, and <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> properties.|  
|Cancel or change auto-generated columns|Handle the <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> event.|  
|Freeze a column|Set the <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> property to 1 and move the column to the left-most position by setting the <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> property to 0.|  
|Use XML data as the data source|Bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> on the <xref:System.Windows.Controls.DataGrid> to the XPath query that represents the collection of items. Create each column in the <xref:System.Windows.Controls.DataGrid>. Bind each column by setting the XPath on the binding to the query that gets the property on the item source. Příklad naleznete v tématu <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Návod: Zobrazení dat z databáze serveru SQL Server v ovládacím prvku DataGrid](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Describes how to set up a new WPF project, add an Entity Framework Element, set the source, and display the data in a <xref:System.Windows.Controls.DataGrid>.|  
|[Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid](how-to-add-row-details-to-a-datagrid-control.md)|Describes how to create row details for a <xref:System.Windows.Controls.DataGrid>.|  
|[Postupy: Implementace ověření pomocí ovládacího prvku DataGrid](how-to-implement-validation-with-the-datagrid-control.md)|Describes how to validate values in <xref:System.Windows.Controls.DataGrid> cells and rows, and display validation feedback.|  
|[Výchozí chování klávesnice a myši v ovládacím prvku DataGrid](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Describes how to interact with the <xref:System.Windows.Controls.DataGrid> control by using the keyboard and mouse.|  
|[Postupy: Seskupení, řazení a filtrování dat v ovládacím prvku DataGrid](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Describes how to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.|  
|[Možnosti změny velikosti v ovládacím prvku DataGrid](sizing-options-in-the-datagrid-control.md)|Describes how to control absolute and automatic sizing in the <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.DataGrid>
- [Styly a šablony](styling-and-templating.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled datových šablon](../data/data-templating-overview.md)
- [Ovládací prvky](index.md)
- [Model obsahu WPF](wpf-content-model.md)
