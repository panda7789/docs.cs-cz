---
title: 'Postupy: Nastavení stylu řádku v zobrazení ListView s implementací GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 9af8d10c7db2d3bbe8b9443402cbb1cfeaa7edb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052011"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Postupy: Nastavení stylu řádku v zobrazení ListView s implementací GridView
Tento příklad ukazuje, jak nastavení stylu řádku v <xref:System.Windows.Controls.ListView> ovládací prvek, který implementuje <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> režimu.  
  
## <a name="example"></a>Příklad  
 Můžete stylu řádku v <xref:System.Windows.Controls.ListView> ovládacího prvku tak, že nastavíte <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> na <xref:System.Windows.Controls.ListView> ovládacího prvku. Nastavit styl pro jeho položky, které jsou reprezentovány ve formě <xref:System.Windows.Controls.ListViewItem> objekty. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Odkazy <xref:System.Windows.Controls.ControlTemplate> objekty, které se používají k zobrazení obsahu řádku.  
  
 Úplnou ukázku, která v následujících příkladech se extrahují z, zobrazí kolekci skladby informací uložených v [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] databáze. Skladeb v databázi obsahuje pole, hodnocení a hodnotou tohoto pole určuje způsob zobrazení řádku skladby informace.  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pro <xref:System.Windows.Controls.ListViewItem> objekty, které představují skladeb v kolekci skladby. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Odkazy <xref:System.Windows.Controls.ControlTemplate> objekty, které určují, jak zobrazit řádek skladby informace.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.ControlTemplate> , který přidá textový řetězec `"Strongly Recommended"` na řádek. Tato šablona odkazuje <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> a zobrazí, když skladby hodnocení má hodnotu 5 (pět). <xref:System.Windows.Controls.ControlTemplate> Zahrnuje <xref:System.Windows.Controls.GridViewRowPresenter> objekt, který nastaví rozložení obsahu řádku ve sloupcích podle definice <xref:System.Windows.Controls.GridView> režim zobrazení.  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 Následující příklad definuje <xref:System.Windows.Controls.GridView>.  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Témata s postupy](listview-how-to-topics.md)
- [ListView – přehled](listview-overview.md)
- [Styly a šablony](styling-and-templating.md)
