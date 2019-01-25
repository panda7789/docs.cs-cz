---
title: 'Postupy: Změna vodorovného zarovnání sloupce v objektu ListView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
ms.openlocfilehash: 07d5fd0830f98032e76b963cb32b35fd18b50475
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605222"
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>Postupy: Změna vodorovného zarovnání sloupce v objektu ListView
Ve výchozím nastavení obsahu každého sloupce v <xref:System.Windows.Controls.ListViewItem> zarovnané vlevo. Zarovnání jednotlivých sloupců můžete změnit zadáním <xref:System.Windows.DataTemplate> a nastavení <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastnosti prvku v rámci <xref:System.Windows.DataTemplate>. Toto téma ukazuje, jak <xref:System.Windows.Controls.ListView> Zarovná obsah ve výchozím nastavení a změna zarovnání jeden sloupec <xref:System.Windows.Controls.ListView>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, data `Title` a `ISBN` sloupce zarovnané vlevo.  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Chcete-li změnit zarovnání `ISBN` sloupci, budete muset určit, že <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> vlastnosti každého <xref:System.Windows.Controls.ListViewItem> je <xref:System.Windows.HorizontalAlignment.Stretch>tak, aby prvky v každém <xref:System.Windows.Controls.ListViewItem> může mít rozsah nebo umístěny podél celou šířku každého sloupce. Vzhledem k tomu, <xref:System.Windows.Controls.ListView> je vázán ke zdroji dat, je potřeba vytvořit styl, který nastaví <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>. Dále je třeba použít <xref:System.Windows.DataTemplate> k zobrazení obsahu místo <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> vlastnost. Pro zobrazení `ISBN` z každé šablony <xref:System.Windows.DataTemplate> může obsahovat jenom <xref:System.Windows.Controls.TextBlock> , který má jeho <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> nastavenou na <xref:System.Windows.HorizontalAlignment.Right>.  
  
 Následující příklad definuje styl a <xref:System.Windows.DataTemplate> potřebné k zajištění `ISBN` sloupec zarovnaný doprava a změny <xref:System.Windows.Controls.GridViewColumn> na odkaz <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Přehled datových šablon](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)
