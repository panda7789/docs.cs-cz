---
title: 'Postupy: nastavení stylu řádku v zobrazení ListView s použitím prvku GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 4b8b8e2f1b2d7207a37205d981bf2dab3f65122e
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271942"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Postupy: Nastavení stylu řádku v zobrazení ListView s implementací GridView
Tento příklad ukazuje, jak stylovat řádek v <xref:System.Windows.Controls.ListView> ovládacím prvku, který používá <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> režim.  
  
## <a name="example"></a>Příklad  
 Můžete nastavit styl řádku v <xref:System.Windows.Controls.ListView> ovládacím prvku nastavením <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListView> ovládacího prvku. Nastavte styl pro položky, které jsou reprezentovány jako <xref:System.Windows.Controls.ListViewItem> objekty. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>Odkazuje na <xref:System.Windows.Controls.ControlTemplate> objekty, které se používají k zobrazení obsahu řádku.  
  
 Kompletní ukázka, z níž jsou extrahovány následující příklady, zobrazuje kolekci informací o skladbách, které jsou uloženy v databázi XML. Každá skladba v databázi má pole hodnocení a hodnota tohoto pole určuje, jak se má zobrazit řádek informací o skladbě.  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pro <xref:System.Windows.Controls.ListViewItem> objekty, které reprezentují skladby v kolekci song. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>Odkazuje na <xref:System.Windows.Controls.ControlTemplate> objekty, které určují, jak se má zobrazit řádek informací o skladbě.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 Následující příklad ukazuje <xref:System.Windows.Controls.ControlTemplate> , který přidá textový řetězec `"Strongly Recommended"` na řádek. Na tuto šablonu odkazuje v <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> a se zobrazí, když má hodnocení skladby hodnotu 5 (pět). <xref:System.Windows.Controls.ControlTemplate>Obsahuje <xref:System.Windows.Controls.GridViewRowPresenter> objekt, který rozloží obsah řádku ve sloupcích definovaných <xref:System.Windows.Controls.GridView> režimem zobrazení.  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 Následující příklad definuje <xref:System.Windows.Controls.GridView> .  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [– postupy](listview-how-to-topics.md)
- [ListView – přehled](listview-overview.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
