---
title: 'Postupy: Vytvoření vlastního režimu zobrazení pro ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 336e4ee911d18836eafa6f444c8d900c117acad3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545274"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>Postupy: Vytvoření vlastního režimu zobrazení pro ListView
Tento příklad ukazuje, jak vytvořit vlastní <xref:System.Windows.Controls.ListView.View%2A> režim <xref:System.Windows.Controls.ListView> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Je nutné použít <xref:System.Windows.Controls.ViewBase> třídy při vytvoření vlastního zobrazení pro <xref:System.Windows.Controls.ListView> ovládacího prvku. Následující příklad ukazuje režim zobrazení, která je volána `PlainView`, který je odvozen z <xref:System.Windows.Controls.ViewBase> třídy.  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 Chcete-li použít styl na vlastní zobrazení, použijte <xref:System.Windows.Style> třídy. Následující příklad definuje <xref:System.Windows.Style> pro `PlainView` režim zobrazení. V předchozím příkladu je tímto stylem nastavena jako hodnota <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> vlastnost, která je definována pro `PlainView`.  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 Chcete-li definovat rozložení dat vlastního režimu zobrazení, definujte <xref:System.Windows.DataTemplate> objektu. Následující příklad definuje <xref:System.Windows.DataTemplate> , který slouží k zobrazení dat v `PlainView` režim zobrazení.  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.ResourceKey> pro `PlainView` režim zobrazení, která používá <xref:System.Windows.DataTemplate> , která je definována v předchozím příkladu.  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 A <xref:System.Windows.Controls.ListView> ovládací prvek lze použít vlastní zobrazení, pokud jste nastavili <xref:System.Windows.Controls.ListView.View%2A> vlastnost klíč prostředku. Následující příklad ukazuje, jak určit `PlainView` jako režim zobrazení <xref:System.Windows.Controls.ListView>.  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 Úplnou ukázku najdete v tématu [ListView s více zobrazení (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) nebo [ListView s více Views(Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Témata s postupy](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)
- [GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)
