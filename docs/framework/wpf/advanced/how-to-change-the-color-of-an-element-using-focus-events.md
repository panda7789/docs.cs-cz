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
ms.openlocfilehash: 0d2c297108da7af09e5f01551bdedc5f0ac5e9af
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361002"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a>Postupy: Změna barvy elementu použitím událostí fokusu
Tento příklad ukazuje, jak změnit barvu elementu získává a ztratí fokus pomocí <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus> události.  
  
 Tento příklad se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor a soubor kódu na pozadí.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] vytvoří uživatelské rozhraní, který se skládá ze dvou <xref:System.Windows.Controls.Button> objekty a připojí obslužné rutiny událostí pro <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus> události <xref:System.Windows.Controls.Button> objekty.  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 Následující kód vytvoří <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus> obslužných rutin událostí.  Když <xref:System.Windows.Controls.Button> zisky klávesnice fokus, <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> se změní na červený.  Když <xref:System.Windows.Controls.Button> ztratí fokus klávesnice <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> se změní zpět na bílou.  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled vstupu](input-overview.md)
