---
title: 'Postupy: Vodorovné a svislé zarovnání obsahu v objektu StackPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: a03cb1ed9b3e5bd42b28e37f5bbb3e1d0446a4ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>Postupy: Vodorovné a svislé zarovnání obsahu v objektu StackPanel
Tento příklad ukazuje, jak upravit <xref:System.Windows.Controls.StackPanel.Orientation%2A> obsahu v rámci <xref:System.Windows.Controls.StackPanel> element a také jak upravit <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> podřízené obsahu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří tři <xref:System.Windows.Controls.ListBox> elementů v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Každý <xref:System.Windows.Controls.ListBox> představuje možných hodnot <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnosti <xref:System.Windows.Controls.StackPanel>. Když uživatel vybere hodnotu v některém z <xref:System.Windows.Controls.ListBox> elementy, přidružené vlastnosti <xref:System.Windows.Controls.StackPanel> a jeho podřízené <xref:System.Windows.Controls.Button> elementy změnit.  
  
 [!code-xaml[StackPanelIntroSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 Následující soubor kódu definuje změny k událostem, které jsou přidružené <xref:System.Windows.Controls.ListBox> výběr změny. <xref:System.Windows.Controls.StackPanel> je identifikována <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.  
  
 [!code-csharp[StackPanelIntroSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)
