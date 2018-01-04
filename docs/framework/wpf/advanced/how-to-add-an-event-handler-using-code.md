---
title: "Postupy: Přidání obslužné rutiny události pomocí kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3abcd441219e58df2e5a0d4b66447e255c6aabd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="0ffa2-102">Postupy: Přidání obslužné rutiny události pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="0ffa2-102">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="0ffa2-103">Tento příklad ukazuje postup přidání obslužné rutiny události pro element pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="0ffa2-103">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="0ffa2-104">Pokud chcete přidat obslužné rutiny události pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] již byla načtena elementu a stránce značek, který obsahuje element, je nutné přidat obslužnou rutinu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="0ffa2-104">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="0ffa2-105">Případně pokud vytváříte nahoru k elementu pro aplikaci zcela použití kódu a není deklarace všech elementů pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete volat konkrétní metody pro přidání obslužné rutiny událostí na strom vytvořený element.</span><span class="sxs-lookup"><span data-stu-id="0ffa2-105">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ffa2-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ffa2-106">Example</span></span>  
 <span data-ttu-id="0ffa2-107">Následující příklad přidá novou <xref:System.Windows.Controls.Button> na existující stránku původně definovaného v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0ffa2-107">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="0ffa2-108">Soubor modelu code-behind implementuje metodu obslužné rutiny události a potom přidá dané metody jako novou obslužnou rutinu události na <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="0ffa2-108">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="0ffa2-109">[!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] Příklad používá `+=` operátor přiřadit obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="0ffa2-109">The [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="0ffa2-110">Toto je stejný operátor, který slouží k přiřazení obslužnou rutinu v [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] model zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="0ffa2-110">This is the same operator that is used to assign a handler in the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event handling model.</span></span> [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)]<span data-ttu-id="0ffa2-111">nepodporuje tento operátor jako způsob přidání obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="0ffa2-111"> does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="0ffa2-112">Místo toho vyžaduje jednu z dvě techniky:</span><span class="sxs-lookup"><span data-stu-id="0ffa2-112">It instead requires one of two techniques:</span></span>  
  
-   <span data-ttu-id="0ffa2-113">Použití <xref:System.Windows.UIElement.AddHandler%2A> metoda, společně s `AddressOf` operátor, chcete-li implementace obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="0ffa2-113">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
-   <span data-ttu-id="0ffa2-114">Použití `Handles` – klíčové slovo jako součást definice obslužná rutina události.</span><span class="sxs-lookup"><span data-stu-id="0ffa2-114">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="0ffa2-115">Tento postup není zobrazeny zde; v tématu [Visual Basic a zpracování události WPF](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).</span><span class="sxs-lookup"><span data-stu-id="0ffa2-115">This technique is not shown here; see [Visual Basic and WPF Event Handling](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  <span data-ttu-id="0ffa2-116">Přidání obslužné rutiny událostí v původně Analyzovaná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky je mnohem jednodušší.</span><span class="sxs-lookup"><span data-stu-id="0ffa2-116">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="0ffa2-117">V rámci objektu elementu, kde chcete přidat obslužné rutiny události přidejte atribut, který odpovídá názvu událost, která chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="0ffa2-117">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="0ffa2-118">Zadejte hodnotu tohoto atributu jako název metody obslužné rutiny události, který jste zadali v souboru kódu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="0ffa2-118">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="0ffa2-119">Další informace najdete v tématu [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) nebo [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0ffa2-119">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) or [Routed Events Overview](../../../../docs/framework/wpf/advanced/routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ffa2-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ffa2-120">See Also</span></span>  
 [<span data-ttu-id="0ffa2-121">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="0ffa2-121">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="0ffa2-122">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="0ffa2-122">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
