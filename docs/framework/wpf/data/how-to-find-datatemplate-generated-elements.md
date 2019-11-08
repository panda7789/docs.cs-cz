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
ms.openlocfilehash: 2cb3d73574cd207c0e06abe15f6a953a67cd5c78
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733424"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Postupy: Vyhledávání elementů generovaných objektem DataTemplate
Tento příklad ukazuje, jak najít prvky, které jsou generovány <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je <xref:System.Windows.Controls.ListBox>, která je svázána s některými daty XML:  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 <xref:System.Windows.Controls.ListBox> používá následující <xref:System.Windows.DataTemplate>:  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Chcete-li načíst prvek <xref:System.Windows.Controls.TextBlock> generovaný <xref:System.Windows.DataTemplate> určitého <xref:System.Windows.Controls.ListBoxItem>, je třeba získat <xref:System.Windows.Controls.ListBoxItem>, najít <xref:System.Windows.Controls.ContentPresenter> v rámci tohoto <xref:System.Windows.Controls.ListBoxItem>a pak zavolat <xref:System.Windows.FrameworkTemplate.FindName%2A> na <xref:System.Windows.DataTemplate>, který je nastaven na <xref:System.Windows.Controls.ContentPresenter>. Následující příklad ukazuje, jak provést tyto kroky. Pro demonstrační účely tento příklad vytvoří okno se zprávou, které zobrazuje textový obsah textového bloku generovaného <xref:System.Windows.DataTemplate>.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 Následuje implementace `FindVisualChild`, která používá <xref:System.Windows.Media.VisualTreeHelper> metody:  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vyhledávání elementů generovaných objektem ControlTemplate](../controls/how-to-find-controltemplate-generated-elements.md)
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Obory názvů WPF XAML](../advanced/wpf-xaml-namescopes.md)
- [Stromy v subsystému WPF](../advanced/trees-in-wpf.md)
