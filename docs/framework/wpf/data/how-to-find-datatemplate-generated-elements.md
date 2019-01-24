---
title: 'Postupy: Hledání prvků generovaných šablonou DataTemplate'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- finding DataTemplate elements [WPF]
- DataTemplate [WPF]
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
ms.openlocfilehash: d271a3d53a0e102f8f969fd0751e15b470a52862
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511563"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Postupy: Hledání prvků generovaných šablonou DataTemplate
Tento příklad ukazuje, jak najít prvky, které jsou generovány <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je <xref:System.Windows.Controls.ListBox> , který je vázán k některým [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat:  
  
 [!code-xaml[FindGeneratedItems#LB](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 <xref:System.Windows.Controls.ListBox> Používá následující <xref:System.Windows.DataTemplate>:  
  
 [!code-xaml[FindGeneratedItems#DT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Pokud chcete načíst <xref:System.Windows.Controls.TextBlock> element generovaných <xref:System.Windows.DataTemplate> z určité <xref:System.Windows.Controls.ListBoxItem>, je potřeba získat <xref:System.Windows.Controls.ListBoxItem>, Najít <xref:System.Windows.Controls.ContentPresenter> , které <xref:System.Windows.Controls.ListBoxItem>a pak vyvolejte <xref:System.Windows.FrameworkTemplate.FindName%2A> na <xref:System.Windows.DataTemplate> který je nastaven na tom <xref:System.Windows.Controls.ContentPresenter>. Následující příklad ukazuje, jak provést tyto kroky. Pro demonstrační účely, tento příklad vytvoří okno se zprávou, která zobrazí text z obsahu <xref:System.Windows.DataTemplate>– vygeneruje textový blok.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 Tady je implementace `FindVisualChild`, který používá <xref:System.Windows.Media.VisualTreeHelper> metody:  
  
 [!code-csharp[FindGeneratedItems#FVC](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Vyhledávání elementů generovaných objektem ControlTemplate](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
- [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Obory názvů WPF XAML](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)
- [Stromy v subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
