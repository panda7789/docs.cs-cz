---
title: "Postupy: Zpracování směrované události"
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
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c491ff4e231d932b3714d2d059b52bad2502368c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-a-routed-event"></a><span data-ttu-id="b78f0-102">Postupy: Zpracování směrované události</span><span class="sxs-lookup"><span data-stu-id="b78f0-102">How to: Handle a Routed Event</span></span>
<span data-ttu-id="b78f0-103">Tento příklad ukazuje, jak probublávání události práci a jak napsat obslužnou rutinu, která dokáže zpracovat data směrované události.</span><span class="sxs-lookup"><span data-stu-id="b78f0-103">This example shows how bubbling events work and how to write a handler that can process the routed event data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b78f0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b78f0-104">Example</span></span>  
 <span data-ttu-id="b78f0-105">V [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elementy jsou uspořádány do stromové struktury k elementu.</span><span class="sxs-lookup"><span data-stu-id="b78f0-105">In [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elements are arranged in an element tree structure.</span></span> <span data-ttu-id="b78f0-106">Zpracování událostí, které jsou původně aktivováno podřízené elementy ve stromové struktuře element účastnit nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="b78f0-106">The parent element can participate in the handling of events that are initially raised by child elements in the element tree.</span></span> <span data-ttu-id="b78f0-107">To je možné díky směrování událostí.</span><span class="sxs-lookup"><span data-stu-id="b78f0-107">This is possible because of event routing.</span></span>  
  
 <span data-ttu-id="b78f0-108">Směrované události podle obvykle jednu ze dvou směrování strategií, šíření nebo tunelové propojení.</span><span class="sxs-lookup"><span data-stu-id="b78f0-108">Routed events typically follow one of two routing strategies, bubbling or tunneling.</span></span> <span data-ttu-id="b78f0-109">Tento příklad se zaměřuje na probublávání události a používá <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> událostí zobrazíte funguje jak směrování.</span><span class="sxs-lookup"><span data-stu-id="b78f0-109">This example focuses on the bubbling event and uses the <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> event to show how routing works.</span></span>  
  
 <span data-ttu-id="b78f0-110">Následující příklad vytvoří dvě <xref:System.Windows.Controls.Button> ovládací prvky a používá [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe k připojení obslužné rutiny události pro běžné nadřazený element, který v tomto příkladu je atribut <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="b78f0-110">The following example creates two <xref:System.Windows.Controls.Button> controls and uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax to attach an event handler to a common parent element, which in this example is <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="b78f0-111">Místo připojení jednotlivé obslužné rutiny pro každou <xref:System.Windows.Controls.Button> podřízený element v příkladu používá syntaxi atribut připojit obslužná rutina události <xref:System.Windows.Controls.StackPanel> nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="b78f0-111">Instead of attaching individual event handlers for each <xref:System.Windows.Controls.Button> child element, the example uses attribute syntax to attach the event handler to the <xref:System.Windows.Controls.StackPanel> parent element.</span></span> <span data-ttu-id="b78f0-112">Tento vzor zpracování událostí ukazuje, jak používat událostí směrování jako technika snižuje počet elementů, kde je připojen obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="b78f0-112">This event-handling pattern shows how to use event routing as a technique for reducing the number of elements where a handler is attached.</span></span> <span data-ttu-id="b78f0-113">Všechny probublávání události pro každou <xref:System.Windows.Controls.Button> směrovat přes nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="b78f0-113">All the bubbling events for each <xref:System.Windows.Controls.Button> route through the parent element.</span></span>  
  
 <span data-ttu-id="b78f0-114">Všimněte si, že v nadřazené <xref:System.Windows.Controls.StackPanel> elementu, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> název události zadaný jako atribut je částečně kvalifikovaný pojmenováním <xref:System.Windows.Controls.Button> třídy.</span><span class="sxs-lookup"><span data-stu-id="b78f0-114">Note that on the parent <xref:System.Windows.Controls.StackPanel> element, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event name specified as the attribute is partially qualified by naming the <xref:System.Windows.Controls.Button> class.</span></span> <span data-ttu-id="b78f0-115"><xref:System.Windows.Controls.Button> Třída je <xref:System.Windows.Controls.Primitives.ButtonBase> odvozené třídy, který má <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost v její členy výpis.</span><span class="sxs-lookup"><span data-stu-id="b78f0-115">The <xref:System.Windows.Controls.Button> class is a <xref:System.Windows.Controls.Primitives.ButtonBase> derived class that has the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event in its members listing.</span></span> <span data-ttu-id="b78f0-116">Tato technika částečné kvalifikace pro připojení obslužné rutiny události je nezbytný, pokud událost, která se právě zpracovává neexistuje v členy výpis elementu, kde je obslužná rutina směrované události připojen.</span><span class="sxs-lookup"><span data-stu-id="b78f0-116">This partial qualification technique for attaching an event handler is necessary if the event that is being handled does not exist in the members listing of the element where the routed event handler is attached.</span></span>  
  
 [!code-xaml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 <span data-ttu-id="b78f0-117">Následující příklad popisovače <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.</span><span class="sxs-lookup"><span data-stu-id="b78f0-117">The following example handles the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  <span data-ttu-id="b78f0-118">V příkladu sestavy, který element zpracovává události a které elementy vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="b78f0-118">The example reports which element handles the event and which element raises the event.</span></span> <span data-ttu-id="b78f0-119">Obslužné rutiny události se spustí, když uživatel klikne buď tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b78f0-119">The event handler is executed when the user clicks either button.</span></span>  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="b78f0-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b78f0-120">See Also</span></span>  
 <xref:System.Windows.RoutedEvent>  
 [<span data-ttu-id="b78f0-121">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="b78f0-121">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [<span data-ttu-id="b78f0-122">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="b78f0-122">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="b78f0-123">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="b78f0-123">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)  
 [<span data-ttu-id="b78f0-124">Podrobná syntaxe XAML</span><span class="sxs-lookup"><span data-stu-id="b78f0-124">XAML Syntax In Detail</span></span>](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
