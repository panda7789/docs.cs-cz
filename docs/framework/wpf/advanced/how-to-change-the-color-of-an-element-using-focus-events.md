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
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a><span data-ttu-id="64204-102">Postupy: Změna barvy elementu použitím událostí fokusu</span><span class="sxs-lookup"><span data-stu-id="64204-102">How to: Change the Color of an Element Using Focus Events</span></span>
<span data-ttu-id="64204-103">Tento příklad ukazuje, jak změnit barvu prvku při nárůstu a ztrátě fokusu pomocí událostí <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="64204-103">This example shows how to change the color of an element when it gains and loses focus by using the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events.</span></span>  
  
 <span data-ttu-id="64204-104">Tento příklad se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru a souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="64204-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64204-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="64204-105">Example</span></span>  
 <span data-ttu-id="64204-106">Následující kód XAML vytvoří uživatelské rozhraní, které se skládá ze dvou objektů <xref:System.Windows.Controls.Button> a připojuje obslužné rutiny událostí pro <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus> události do objektů <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="64204-106">The following XAML creates the user interface, which consists of two <xref:System.Windows.Controls.Button> objects, and attaches event handlers for the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> events to the <xref:System.Windows.Controls.Button> objects.</span></span>  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 <span data-ttu-id="64204-107">Následující kód vytvoří na pozadí obslužné rutiny událostí <xref:System.Windows.UIElement.GotFocus> a <xref:System.Windows.UIElement.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="64204-107">The following code behind creates the <xref:System.Windows.UIElement.GotFocus> and <xref:System.Windows.UIElement.LostFocus> event handlers.</span></span>  <span data-ttu-id="64204-108">Když <xref:System.Windows.Controls.Button> získá fokus klávesnice, <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> se změní na červenou.</span><span class="sxs-lookup"><span data-stu-id="64204-108">When the <xref:System.Windows.Controls.Button> gains keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed to red.</span></span>  <span data-ttu-id="64204-109">Když <xref:System.Windows.Controls.Button> ztratí fokus klávesnice, <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> se změní zpátky na bílou.</span><span class="sxs-lookup"><span data-stu-id="64204-109">When the <xref:System.Windows.Controls.Button> loses keyboard focus, the <xref:System.Windows.Controls.Control.Background%2A> of the <xref:System.Windows.Controls.Button> is changed back to white.</span></span>  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a><span data-ttu-id="64204-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64204-110">See also</span></span>

- [<span data-ttu-id="64204-111">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="64204-111">Input Overview</span></span>](input-overview.md)
