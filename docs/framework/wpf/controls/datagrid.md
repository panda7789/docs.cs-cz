---
title: DataGrid
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGrid column types [WPF]
- DataGrid scenarios [WPF]
- DataGrid control [WPF]
- controls [WPF], DataGrid
- DataGrid [WPF], common tasks for
- DataGrid [WPF], customizing the appearance of
- DataGrid columns [WPF], using
ms.assetid: bf89ea63-79b6-422b-bc9f-0485ad803216
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: daea7d382d64e768c9ec681e1c2041c4c80c255e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid> Řízení umožňuje zobrazit a upravit data z mnoha různých zdrojů, například z databáze SQL, dotaz LINQ nebo jakýkoli jiný zdroj dat pro vazbu. Další informace najdete v tématu [vazby Přehled zdrojů](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Sloupce můžete zobrazit text, ovládací prvky, jako například <xref:System.Windows.Controls.ComboBox>, nebo žádný jiný WPF obsah, například bitové kopie, tlačítka nebo žádný obsah obsažené v šabloně. Můžete použít <xref:System.Windows.Controls.DataGridTemplateColumn> k zobrazení dat definované v šabloně. Následující tabulka uvádí typy sloupců, které jsou k dispozici ve výchozím nastavení.  
  
|Typ generovaného sloupce|Datový typ|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>lze přizpůsobit vzhled, jako je například buňky písmo, barva a velikost. <xref:System.Windows.Controls.DataGrid>podporuje všechny funkce styly a ukázka a jiných ovládacích prvků WPF. <xref:System.Windows.Controls.DataGrid>zahrnuje taky výchozí a přizpůsobit chování pro úpravy, řazení a ověření.  
  
 Následující tabulka uvádí některé běžné úlohy pro <xref:System.Windows.Controls.DataGrid> a o způsobech je. Zobrazením souvisejících rozhraní API můžete najít další informace a ukázkový kód.  
  
|Scénář|Přístup|  
|--------------|--------------|  
|Střídání barvy pozadí|Nastavte <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> vlastnost, která má 2 nebo více a pak mu přiřaďte <xref:System.Windows.Media.Brush> k <xref:System.Windows.Controls.DataGrid.RowBackground%2A> a <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> vlastnosti.|  
|Zadejte chování při výběru buňky a řádek|Nastavte <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> a <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> vlastnosti.|  
|Přizpůsobit vzhled hlavičky, buněk a řádků|Použít novou <xref:System.Windows.Style> k <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.CellStyle%2A>, nebo <xref:System.Windows.Controls.DataGrid.RowStyle%2A> vlastnosti.|  
|Nastavit možnosti změny velikosti|Nastavte <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, nebo <xref:System.Windows.FrameworkElement.MinWidth%2A> vlastnosti. Další informace najdete v tématu [možnosti pro změnu velikosti v ovládacím prvku DataGrid](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md).|  
|Přístup k vybrané položky|Zkontrolujte <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> vlastnost k získání vybraných buněk a <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> vlastnost k získání vybrané řádky. Další informace naleznete v tématu <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Přizpůsobení interakce s koncovým uživatelem|Nastavte <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>, a <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> vlastnosti.|  
|Zrušit nebo změnit automaticky generovaný sloupců|Zpracování <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> událostí.|  
|Ukotvit sloupec|Nastavte <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> vlastnost na hodnotu 1 a přesunutí sloupec na pozici nejvíce vlevo nastavením <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> vlastnost na hodnotu 0.|  
|XML data použít jako zdroj dat|Vytvoření vazby <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> na <xref:System.Windows.Controls.DataGrid> pro dotaz XPath, který představuje kolekce položek. Vytvoření každý sloupec v <xref:System.Windows.Controls.DataGrid>. Každý sloupec vazbu nastavením jazyka XPath vazba na dotaz, který získá vlastnost ve zdroji položky. Příklad naleznete v tématu <xref:System.Windows.Controls.DataGridTextColumn>.|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Návod: Zobrazení dat z databáze serveru SQL Server v ovládacím prvku DataGrid](../../../../docs/framework/wpf/controls/walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Popisuje, jak nastavit nový projekt WPF, přidejte Entity Framework Element, nastavit zdroje a zobrazení dat v <xref:System.Windows.Controls.DataGrid>.|  
|[Postupy: Přidání podrobností řádku do ovládacího prvku DataGrid](../../../../docs/framework/wpf/controls/how-to-add-row-details-to-a-datagrid-control.md)|Popisuje, jak vytvořit řádek podrobnosti <xref:System.Windows.Controls.DataGrid>.|  
|[Postupy: Implementace ověření pomocí ovládacího prvku DataGrid](../../../../docs/framework/wpf/controls/how-to-implement-validation-with-the-datagrid-control.md)|Popisuje, jak ověřit hodnoty v <xref:System.Windows.Controls.DataGrid> buněk a řádků a zobrazení ověření zpětnou vazbu.|  
|[Výchozí chování klávesnice a myši v ovládacím prvku DataGrid](../../../../docs/framework/wpf/controls/default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Popisuje, jak pracovat s <xref:System.Windows.Controls.DataGrid> ovládacího prvku pomocí klávesnice a myši.|  
|[Postupy: Seskupení, řazení a filtrování dat v ovládacím prvku DataGrid](../../../../docs/framework/wpf/controls/how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Popisuje postup zobrazení dat v <xref:System.Windows.Controls.DataGrid> seskupování, řazení a filtrování dat různými způsoby.|  
|[Možnosti změny velikosti v ovládacím prvku DataGrid](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)|Popisuje, jak řídit absolutní a Automatická změna velikosti v <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.DataGrid>  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Přehled datových šablon](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Ovládací prvky](../../../../docs/framework/wpf/controls/index.md)  
 [Model obsahu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md)
