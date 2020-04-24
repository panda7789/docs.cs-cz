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
ms.openlocfilehash: cdf4bfff8182b62d55f56b823c7ff129de4f9f1c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646122"
---
# <a name="datagrid"></a>DataGrid
Ovládací <xref:System.Windows.Controls.DataGrid> prvek umožňuje zobrazit a upravit data z mnoha různých zdrojů, například z databáze SQL, linq dotazu nebo jiného zdroje dat s vazbou. Další informace naleznete v [tématu Přehled zdrojů vazby](../data/binding-sources-overview.md).  
  
 Sloupce mohou zobrazovat text, <xref:System.Windows.Controls.ComboBox>ovládací prvky, například obsah WPF, například obrázky, tlačítka nebo jakýkoli obsah obsažený v šabloně. Pomocí a <xref:System.Windows.Controls.DataGridTemplateColumn> můžete zobrazit data definovaná v šabloně. V následující tabulce jsou uvedeny typy sloupců, které jsou k dispozici ve výchozím nastavení.  
  
|Typ generovaného sloupce|Typ dat|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>lze přizpůsobit vzhledu, například písma buňky, barvy a velikosti. <xref:System.Windows.Controls.DataGrid>podporuje všechny funkce stylingu a šablonování jiných ovládacích prvků WPF. <xref:System.Windows.Controls.DataGrid>obsahuje také výchozí a přizpůsobitelné chování pro úpravy, řazení a ověřování.  
  
 V následující tabulce jsou uvedeny <xref:System.Windows.Controls.DataGrid> některé běžné úkoly a způsob jejich provedení. Zobrazením související rozhraní API, můžete najít další informace a ukázkový kód.  
  
|Scénář|Přístup|  
|--------------|--------------|  
|Střídání barev pozadí|Nastavte <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> vlastnost na 2 nebo více <xref:System.Windows.Media.Brush> a <xref:System.Windows.Controls.DataGrid.RowBackground%2A> pak <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> přiřaďte vlastnosti a.|  
|Definovat chování výběru buněk a řádků|Nastavte <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> vlastnosti a. <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A>|  
|Přizpůsobení vizuálního vzhledu záhlaví, buněk a řádků|Použijte nový <xref:System.Windows.Style> pro <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A> <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>vlastnosti , <xref:System.Windows.Controls.DataGrid.CellStyle%2A>, nebo. <xref:System.Windows.Controls.DataGrid.RowStyle%2A>|  
|Nastavení voleb velikosti|Nastavte <xref:System.Windows.FrameworkElement.Height%2A>vlastnosti <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A> , , nebo. Další informace naleznete [v tématu Možnosti velikosti v ovládacím prvku DataGrid](sizing-options-in-the-datagrid-control.md).|  
|Přístup k vybraným položkám|Zkontrolujte <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> vlastnost, chcete-li <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> získat vybrané buňky a vlastnost, abyste získali vybrané řádky. Další informace naleznete v tématu <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Přizpůsobení interakcí koncových uživatelů|Nastavte <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>vlastnosti <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A> <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A> <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> , , a.|  
|Zrušení nebo změna automaticky generovaných sloupců|Zpracování <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> události.|  
|Ukotvení sloupce|Nastavte <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> vlastnost na 1 a přesuňte sloupec na pozici <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> nejvíce vlevo nastavením vlastnosti na 0.|  
|Použití dat XML jako zdroje dat|Bind <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> na <xref:System.Windows.Controls.DataGrid> na xpath dotaz, který představuje kolekci položek. Vytvořte každý <xref:System.Windows.Controls.DataGrid>sloupec v . Svázat každý sloupec nastavením XPath na vazbu na dotaz, který získá vlastnost na zdroj položky. Příklad naleznete v tématu <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Návod: Zobrazení dat z databáze serveru SQL Server v ovládacím prvku DataGrid](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Popisuje, jak nastavit nový projekt WPF, přidat prvek frameworkentity, nastavit zdroj a <xref:System.Windows.Controls.DataGrid>zobrazit data v .|  
|[Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid](how-to-add-row-details-to-a-datagrid-control.md)|Popisuje, jak vytvořit podrobnosti <xref:System.Windows.Controls.DataGrid>řádku pro .|  
|[Postupy: Implementace ověření pomocí ovládacího prvku DataGrid](how-to-implement-validation-with-the-datagrid-control.md)|Popisuje, jak ověřit <xref:System.Windows.Controls.DataGrid> hodnoty v buňkách a řádcích a zobrazit zpětnou vazbu ověření.|  
|[Výchozí chování klávesnice a myši v ovládacím prvku DataGrid](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Popisuje, jak pracovat <xref:System.Windows.Controls.DataGrid> s ovládacím prvkem pomocí klávesnice a myši.|  
|[Postupy: Seskupení, řazení a filtrování dat v ovládacím prvku DataGrid](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Popisuje, jak zobrazit data <xref:System.Windows.Controls.DataGrid> různými způsoby seskupením, řazením a filtrováním dat.|  
|[Možnosti změny velikosti v ovládacím prvku DataGrid](sizing-options-in-the-datagrid-control.md)|Popisuje, jak řídit absolutní a automatické <xref:System.Windows.Controls.DataGrid>velikosti v .|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.DataGrid>
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled datových šablon](../data/data-templating-overview.md)
- [Ovládací prvky](index.md)
- [Model obsahu WPF](wpf-content-model.md)
