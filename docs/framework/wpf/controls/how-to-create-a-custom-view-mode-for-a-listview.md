---
title: 'Postupy: Vytvoření vlastního režimu zobrazení pro ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 3b9ca17bddcecb1895205fca76f0a489ecf25c4f
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243216"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>Postup: Vytvoření vlastního režimu zobrazení pro listview

Tento příklad ukazuje, jak <xref:System.Windows.Controls.ListView.View%2A> vytvořit <xref:System.Windows.Controls.ListView> vlastní režim pro ovládací prvek.  
  
## <a name="example"></a>Příklad  
 Třídu je <xref:System.Windows.Controls.ViewBase> nutné použít při vytváření <xref:System.Windows.Controls.ListView> vlastního zobrazení ovládacího prvku. Následující příklad ukazuje režim `PlainView` zobrazení s názvem je <xref:System.Windows.Controls.ViewBase> odvozen od třídy.  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 Chcete-li použít styl na vlastní <xref:System.Windows.Style> zobrazení, použijte třídu. Následující příklad definuje <xref:System.Windows.Style> pro `PlainView` režim zobrazení. V předchozím příkladu je tento styl nastaven <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> jako hodnota vlastnosti, která je definována pro `PlainView`.  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 Chcete-li definovat rozložení dat ve vlastním <xref:System.Windows.DataTemplate> režimu zobrazení, definujte objekt. Následující příklad definuje <xref:System.Windows.DataTemplate> a, který lze použít `PlainView` k zobrazení dat v režimu zobrazení.  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 Následující příklad ukazuje, jak <xref:System.Windows.ResourceKey> definovat `PlainView` pro režim <xref:System.Windows.DataTemplate> zobrazení, který používá, který je definován v předchozím příkladu.  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 Ovládací <xref:System.Windows.Controls.ListView> prvek můžete použít vlastní zobrazení, pokud nastavíte <xref:System.Windows.Controls.ListView.View%2A> vlastnost na klíč prostředku. Následující příklad ukazuje, `PlainView` jak určit jako <xref:System.Windows.Controls.ListView>režim zobrazení pro .  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 Úplnou ukázku naleznete v [tématu ListView s více zobrazeními (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) nebo [ListView s více zobrazeními (Visual Basic).](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic)  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [– postupy](listview-how-to-topics.md)
- [ListView – přehled](listview-overview.md)
- [GridView – přehled](gridview-overview.md)
