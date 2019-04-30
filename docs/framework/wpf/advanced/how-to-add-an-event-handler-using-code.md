---
title: 'Postupy: Přidání obslužné rutiny události pomocí kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: 10f8e0899e61d5d54589c910bdcbcd92d8ee947c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777062"
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="ffc81-102">Postupy: Přidání obslužné rutiny události pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="ffc81-102">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="ffc81-103">Tento příklad ukazuje, jak přidat obslužnou rutinu události k prvku pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="ffc81-103">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="ffc81-104">Pokud chcete přidat obslužnou rutinu události pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementu a na stránce značek, obsahující prvek již byl načten, je nutné přidat obslužnou rutinu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="ffc81-104">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="ffc81-105">Případně pokud vytváříte nahoru stromem prvků pro aplikaci zcela pomocí kódu a nedeklarováním všechny prvky pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete volat konkrétní metody pro přidání obslužné rutiny událostí do stromu vytvořený element.</span><span class="sxs-lookup"><span data-stu-id="ffc81-105">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffc81-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ffc81-106">Example</span></span>  
 <span data-ttu-id="ffc81-107">Následující příklad přidá nový <xref:System.Windows.Controls.Button> na existující stránku, který je původně definována v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ffc81-107">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="ffc81-108">Soubor kódu na pozadí implementuje metodu obslužné rutiny události a pak přidá tuto metodu jako novou obslužnou rutinu události na <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="ffc81-108">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="ffc81-109">C# Příklad používá `+=` operátor přiřazení obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="ffc81-109">The C# example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="ffc81-110">To je stejný operátor, který slouží k přiřazení obslužnou rutinu v [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] model zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="ffc81-110">This is the same operator that is used to assign a handler in the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event handling model.</span></span> <span data-ttu-id="ffc81-111">Microsoft Visual Basic nepodporuje tento operátor jako způsob přidání obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="ffc81-111">Microsoft Visual Basic does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="ffc81-112">Místo toho vyžaduje jednu z dvou technik:</span><span class="sxs-lookup"><span data-stu-id="ffc81-112">It instead requires one of two techniques:</span></span>  
  
- <span data-ttu-id="ffc81-113">Použití <xref:System.Windows.UIElement.AddHandler%2A> metody společně s `AddressOf` operátor tak, aby odkazovaly implementaci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ffc81-113">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
- <span data-ttu-id="ffc81-114">Použití `Handles` – klíčové slovo jako součást definice obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ffc81-114">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="ffc81-115">Tato technika, tady není ukázaný; Zobrazit [jazyka Visual Basic a WPF zpracování událostí](visual-basic-and-wpf-event-handling.md).</span><span class="sxs-lookup"><span data-stu-id="ffc81-115">This technique is not shown here; see [Visual Basic and WPF Event Handling](visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  <span data-ttu-id="ffc81-116">Přidání obslužné rutiny událostí v původně analyzovaný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránka je mnohem jednodušší.</span><span class="sxs-lookup"><span data-stu-id="ffc81-116">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="ffc81-117">V rámci elementu objektu, ve které chcete přidat obslužnou rutinu události přidejte atribut, který odpovídá názvu události, ke které chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="ffc81-117">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="ffc81-118">Hodnota tohoto atributu zadejte jako název obslužné metody událostí, který jste definovali v souboru kódu na pozadí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="ffc81-118">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="ffc81-119">Další informace najdete v tématu [přehled XAML (WPF)](xaml-overview-wpf.md) nebo [směrovat Přehled událostí](routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ffc81-119">For more information, see [XAML Overview (WPF)](xaml-overview-wpf.md) or [Routed Events Overview](routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffc81-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ffc81-120">See also</span></span>

- [<span data-ttu-id="ffc81-121">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="ffc81-121">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="ffc81-122">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="ffc81-122">How-to Topics</span></span>](events-how-to-topics.md)
