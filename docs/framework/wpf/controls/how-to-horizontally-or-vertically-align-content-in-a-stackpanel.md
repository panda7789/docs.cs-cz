---
title: 'Postupy: Vodorovné a svislé zarovnání obsahu v objektu StackPanel'
description: Naučte se upravovat orientaci obsahu v Windows Presentation Foundation StackPanel a HorizontalAlignment a VerticalAlignment podřízeného obsahu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: d3c7215d8193d1d8a72597c44cf265f5bd400ea1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167627"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>Postupy: Vodorovné a svislé zarovnání obsahu v objektu StackPanel
Tento příklad ukazuje, jak upravit <xref:System.Windows.Controls.StackPanel.Orientation%2A> obsah v rámci <xref:System.Windows.Controls.StackPanel> prvku a také jak upravit <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> podřízený obsah.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří tři <xref:System.Windows.Controls.ListBox> prvky v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . Každý <xref:System.Windows.Controls.ListBox> představuje možné hodnoty <xref:System.Windows.Controls.StackPanel.Orientation%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> vlastností, a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.Controls.StackPanel> . Když uživatel vybere hodnotu v některém z <xref:System.Windows.Controls.ListBox> elementů, změní se přidružená vlastnost <xref:System.Windows.Controls.StackPanel> a jejích podřízených <xref:System.Windows.Controls.Button> elementů.  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 Následující soubor s kódem na pozadí definuje změny událostí, které jsou přidruženy k <xref:System.Windows.Controls.ListBox> změnám výběru. <xref:System.Windows.Controls.StackPanel>je identifikován <xref:System.Windows.FrameworkElement.Name%2A> `sp1` .  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [Přehled panelů](panels-overview.md)
