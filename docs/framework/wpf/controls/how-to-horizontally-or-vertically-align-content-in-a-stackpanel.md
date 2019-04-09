---
title: 'Postupy: Vodorovné a svislé zarovnání obsahu v elementu StackPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: 03348aa0eb5b6c1791c27683c1c6c6a5d4a8a9d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186040"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>Postupy: Vodorovné a svislé zarovnání obsahu v elementu StackPanel
Tento příklad ukazuje, jak upravit <xref:System.Windows.Controls.StackPanel.Orientation%2A> obsahu v rámci <xref:System.Windows.Controls.StackPanel> elementu a jak upravit <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> podřízený obsah.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří tři <xref:System.Windows.Controls.ListBox> prvky v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Každý <xref:System.Windows.Controls.ListBox> představuje možných hodnot <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> vlastnosti <xref:System.Windows.Controls.StackPanel>. Když uživatel vybere hodnotu v některém z <xref:System.Windows.Controls.ListBox> elementy, vlastnost přidružené <xref:System.Windows.Controls.StackPanel> a jeho podřízených <xref:System.Windows.Controls.Button> změnit elementy.  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 Následující soubor kódu na pozadí definuje k událostem, které jsou přidružené změny <xref:System.Windows.Controls.ListBox> změny výběru. <xref:System.Windows.Controls.StackPanel> je identifikován <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [Přehled panelů](panels-overview.md)
