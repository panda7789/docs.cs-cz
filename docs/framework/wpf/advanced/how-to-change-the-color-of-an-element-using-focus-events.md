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
ms.openlocfilehash: 5c59dc5f2f8f26fac69933f9ef641a3a51306619
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004832"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a>Postupy: Změna barvy elementu použitím událostí fokusu
Tento příklad ukazuje, jak změnit barvu prvku při nárůstu a ztrátě fokusu pomocí událostí <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus>.  
  
 Tento příklad se skládá ze souboru [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a souboru kódu na pozadí.  
  
## <a name="example"></a>Příklad  
 Následující kód XAML vytvoří uživatelské rozhraní, které se skládá ze dvou objektů @no__t 0 a připojuje obslužné rutiny událostí pro události <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus> k objektům <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 Následující kód na pozadí vytvoří obslužné rutiny událostí <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus>.  Když se aktivuje klávesnice <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> se změní na červenou.  Když <xref:System.Windows.Controls.Button> ztratí fokus klávesnice, <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> se změní zpátky na bílou.  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled vstupu](input-overview.md)
