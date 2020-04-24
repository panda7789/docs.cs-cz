---
title: 'Postupy: Vyhledávání elementů generovaných objektem DataTemplate'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- finding DataTemplate elements [WPF]
- DataTemplate [WPF]
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
ms.openlocfilehash: 3b222880aa4eda32502e3dcece2fa5c0b57b7a51
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646438"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Postupy: Vyhledávání elementů generovaných objektem DataTemplate
Tento příklad ukazuje, jak najít prvky, které jsou generovány <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu <xref:System.Windows.Controls.ListBox> je, který je vázán na některá data XML:  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 Používá <xref:System.Windows.Controls.ListBox> se: <xref:System.Windows.DataTemplate>  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Pokud chcete načíst <xref:System.Windows.Controls.TextBlock> prvek <xref:System.Windows.DataTemplate> generovaný určitým <xref:System.Windows.Controls.ListBoxItem>, musíte získat <xref:System.Windows.Controls.ListBoxItem>, <xref:System.Windows.Controls.ContentPresenter> najít <xref:System.Windows.Controls.ListBoxItem>v rámci <xref:System.Windows.FrameworkTemplate.FindName%2A> , <xref:System.Windows.DataTemplate> a pak volat <xref:System.Windows.Controls.ContentPresenter>na, který je nastaven na to . Následující příklad ukazuje, jak provést tyto kroky. Pro demonstrační účely tento příklad vytvoří okno se <xref:System.Windows.DataTemplate>zprávou, které zobrazuje textový obsah textového bloku generovaného.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 Následuje implementace , `FindVisualChild`která používá <xref:System.Windows.Media.VisualTreeHelper> metody:  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Viz také

- [Postupy: Vyhledávání elementů generovaných objektem ControlTemplate](../controls/how-to-find-controltemplate-generated-elements.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [– postupy](data-binding-how-to-topics.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Obory názvů WPF XAML](../advanced/wpf-xaml-namescopes.md)
- [Stromy v subsystému WPF](../advanced/trees-in-wpf.md)
