---
title: 'Postupy: Nastavení stylu řádku v zobrazení ListView s implementací GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: ce79899d5c8e825ecb39e14ae8af4e0c33f13db3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733544"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Postupy: Nastavení stylu řádku v zobrazení ListView s implementací GridView
Tento příklad ukazuje, jak styl řádku v ovládacím prvku <xref:System.Windows.Controls.ListView>, který implementuje režim <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A>.  
  
## <a name="example"></a>Příklad  
 Můžete nastavit styl řádku v ovládacím prvku <xref:System.Windows.Controls.ListView> nastavením <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> na ovládacím prvku <xref:System.Windows.Controls.ListView>. Nastavte styl pro položky, které jsou reprezentovány jako <xref:System.Windows.Controls.ListViewItem> objekty. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> odkazuje na objekty <xref:System.Windows.Controls.ControlTemplate>, které se používají k zobrazení obsahu řádku.  
  
 Kompletní ukázka, z níž jsou extrahovány následující příklady, zobrazuje kolekci informací o skladbách, které jsou uloženy v databázi XML. Každá skladba v databázi má pole hodnocení a hodnota tohoto pole určuje, jak se má zobrazit řádek informací o skladbě.  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pro objekty <xref:System.Windows.Controls.ListViewItem>, které reprezentují skladby v kolekci song. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> odkazuje na <xref:System.Windows.Controls.ControlTemplate> objektů, které určují, jak se má zobrazit řádek informací o skladbě.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.ControlTemplate>, který přidá textový řetězec `"Strongly Recommended"` na řádek. Na tuto šablonu odkazuje <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> a zobrazí se, když má hodnocení skladby hodnotu 5 (pět). <xref:System.Windows.Controls.ControlTemplate> obsahuje objekt <xref:System.Windows.Controls.GridViewRowPresenter>, který rozloží obsah řádku ve sloupcích, jak je definován režimem zobrazení <xref:System.Windows.Controls.GridView>.  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 Následující příklad definuje <xref:System.Windows.Controls.GridView>.  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Témata s postupy](listview-how-to-topics.md)
- [ListView – přehled](listview-overview.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
