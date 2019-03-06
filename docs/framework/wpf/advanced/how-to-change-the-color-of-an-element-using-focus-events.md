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
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="36339-102">Postupy: Změna barvy elementu použitím událostí fokusu</span><span class="sxs-lookup"><span data-stu-id="36339-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="36339-103">Tento příklad ukazuje, jak změnit barvu elementu získává a ztratí fokus pomocí <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus> události.</span><span class="sxs-lookup"><span data-stu-id="36339-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="36339-104">Tento příklad se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor a soubor kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="36339-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36339-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="36339-105">Example</span></span>  
 <span data-ttu-id="36339-106">Následující [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] vytvoří uživatelské rozhraní, který se skládá ze dvou <xref:System.Windows.Controls.Button> objekty a připojí obslužné rutiny událostí pro <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus> události <xref:System.Windows.Controls.Button> objekty.</span><span class="sxs-lookup"><span data-stu-id="36339-106">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="36339-107">Následující kód vytvoří <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus> obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="36339-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="36339-108">Když <xref:System.Windows.Controls.Button> zisky klávesnice fokus, <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> se změní na červený.</span><span class="sxs-lookup"><span data-stu-id="36339-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="36339-109">Když <xref:System.Windows.Controls.Button> ztratí fokus klávesnice <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button> se změní zpět na bílou.</span><span class="sxs-lookup"><span data-stu-id="36339-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="36339-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36339-110">See also</span></span>
- [<span data-ttu-id="36339-111">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="36339-111">Input Overview</span></span>](input-overview.md)
