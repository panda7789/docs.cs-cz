---
title: 'Postupy: Přidání obslužné rutiny události pomocí kódu'
description: Tento příklad slouží k získání informací o tom, jak přidat obslužnou rutinu události do prvku v Windows Presentation Foundation pomocí kódu namísto deklaracei pomocí jazyka XAML.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: b36969f7a65ccbf6c9d03b22767d9eacdc177ad1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166365"
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="b1916-103">Postupy: Přidání obslužné rutiny události pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="b1916-103">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="b1916-104">Tento příklad ukazuje, jak přidat obslužnou rutinu události do prvku pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="b1916-104">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="b1916-105">Chcete-li přidat obslužnou rutinu události do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prvku a stránku značek, která obsahuje element, již byla načtena, je nutné přidat obslužnou rutinu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="b1916-105">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="b1916-106">Případně, pokud vytváříte strom elementů pro aplikaci výhradně pomocí kódu a nedeklarujete žádné prvky pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , můžete volat konkrétní metody pro přidání obslužných rutin událostí do vytvořeného stromu elementu.</span><span class="sxs-lookup"><span data-stu-id="b1916-106">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1916-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1916-107">Example</span></span>  
 <span data-ttu-id="b1916-108">Následující příklad přidá novou <xref:System.Windows.Controls.Button> na existující stránku, která je zpočátku definována v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b1916-108">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="b1916-109">Soubor kódu na pozadí implementuje metodu obslužné rutiny události a následně přidá tuto metodu jako novou obslužnou rutinu události na <xref:System.Windows.Controls.Button> .</span><span class="sxs-lookup"><span data-stu-id="b1916-109">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="b1916-110">Příklad jazyka C# používá `+=` operátor k přiřazení obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="b1916-110">The C# example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="b1916-111">Toto je stejný operátor, který se používá k přiřazení obslužné rutiny v modelu zpracování událostí modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b1916-111">This is the same operator that is used to assign a handler in the common language runtime (CLR) event handling model.</span></span> <span data-ttu-id="b1916-112">Microsoft Visual Basic nepodporuje tento operátor jako způsob přidávání obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="b1916-112">Microsoft Visual Basic does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="b1916-113">Místo toho vyžaduje jednu ze dvou postupů:</span><span class="sxs-lookup"><span data-stu-id="b1916-113">It instead requires one of two techniques:</span></span>  
  
- <span data-ttu-id="b1916-114">Použijte <xref:System.Windows.UIElement.AddHandler%2A> metodu spolu s `AddressOf` operátorem pro odkazování na implementaci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="b1916-114">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
- <span data-ttu-id="b1916-115">Použijte `Handles` klíčové slovo jako součást definice obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="b1916-115">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="b1916-116">Tato technika se tady nezobrazuje. viz [Visual Basic a zpracování událostí WPF](visual-basic-and-wpf-event-handling.md).</span><span class="sxs-lookup"><span data-stu-id="b1916-116">This technique is not shown here; see [Visual Basic and WPF Event Handling](visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> <span data-ttu-id="b1916-117">Přidání obslužné rutiny události na původně analyzovanou [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránku je mnohem jednodušší.</span><span class="sxs-lookup"><span data-stu-id="b1916-117">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="b1916-118">V rámci elementu Object, kam chcete přidat obslužnou rutinu události, přidejte atribut, který odpovídá názvu události, kterou chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="b1916-118">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="b1916-119">Pak zadejte hodnotu tohoto atributu jako název metody obslužné rutiny události, kterou jste definovali v souboru kódu na pozadí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="b1916-119">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="b1916-120">Další informace naleznete v tématu Přehled [XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) nebo [směrované události](routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b1916-120">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md) or [Routed Events Overview](routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1916-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1916-121">See also</span></span>

- [<span data-ttu-id="b1916-122">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="b1916-122">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="b1916-123">– postupy</span><span class="sxs-lookup"><span data-stu-id="b1916-123">How-to Topics</span></span>](events-how-to-topics.md)
