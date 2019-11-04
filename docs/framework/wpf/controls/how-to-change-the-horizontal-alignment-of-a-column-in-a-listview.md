---
title: 'Postupy: Změna vodorovného zarovnání sloupce v objektu ListView'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
ms.openlocfilehash: 5447f1a73b008b2ed4f345eba00f4d631e11e257
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458601"
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>Postupy: Změna vodorovného zarovnání sloupce v objektu ListView
Ve výchozím nastavení je obsah každého sloupce v <xref:System.Windows.Controls.ListViewItem> zarovnaný doleva. Můžete změnit zarovnání každého sloupce zadáním <xref:System.Windows.DataTemplate> a nastavením vlastnosti <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> elementu v rámci <xref:System.Windows.DataTemplate>. Toto téma ukazuje, jak <xref:System.Windows.Controls.ListView> zarovnává svůj obsah ve výchozím nastavení a jak změnit zarovnání jednoho sloupce v <xref:System.Windows.Controls.ListView>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou data ve sloupcích `Title` a `ISBN` zarovnána doleva.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Chcete-li změnit zarovnání sloupce `ISBN`, je nutné určit, že vlastnost <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> každého <xref:System.Windows.Controls.ListViewItem> je <xref:System.Windows.HorizontalAlignment.Stretch>, aby elementy v každém <xref:System.Windows.Controls.ListViewItem> mohly být rozloženy nebo umístěny podél celé šířky každého sloupce. Vzhledem k tomu, že <xref:System.Windows.Controls.ListView> je svázán se zdrojem dat, je třeba vytvořit styl, který nastaví <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>. Dále je nutné použít <xref:System.Windows.DataTemplate> k zobrazení obsahu místo použití vlastnosti <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>. Chcete-li zobrazit `ISBN` jednotlivých šablon, <xref:System.Windows.DataTemplate> může obsahovat pouze <xref:System.Windows.Controls.TextBlock>, která má vlastnost <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> nastavenou na hodnotu <xref:System.Windows.HorizontalAlignment.Right>.  
  
 Následující příklad definuje styl a <xref:System.Windows.DataTemplate> nutné pro `ISBN` sloupce zarovnané vpravo a změní <xref:System.Windows.Controls.GridViewColumn> na odkaz <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewHowTos#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled datových šablon](../data/data-templating-overview.md)
- [Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView – přehled](listview-overview.md)
