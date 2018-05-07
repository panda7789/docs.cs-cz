---
title: 'Postupy: Změna barvy elementu použitím událostí fokusu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
ms.openlocfilehash: d8d8a3e8b24021cf8a5f916ce3f291a3b66d9411
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a>Postupy: Změna barvy elementu použitím událostí fokusu
Tento příklad ukazuje, jak změnit barvu elementu při získá a ztratí fokus pomocí <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus> události.  
  
 V tomto příkladu se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a soubor kódu.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] vytvoří uživatelského rozhraní, které se skládá ze dvou <xref:System.Windows.Controls.Button> objekty a připojí obslužné rutiny události pro <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus> události <xref:System.Windows.Controls.Button> objekty.  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 Následující kód vytvoří <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus> obslužné rutiny událostí.  Když <xref:System.Windows.Controls.Button> zvýšení klávesové fokus, <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> se změní na červený.  Když <xref:System.Windows.Controls.Button> ztratí fokus klávesnice <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> se změní zpět na prázdné.  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled vstupu](../../../../docs/framework/wpf/advanced/input-overview.md)
