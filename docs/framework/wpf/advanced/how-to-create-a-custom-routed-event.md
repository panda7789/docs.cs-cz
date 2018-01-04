---
title: "Postupy: Vytvoření vlastní směrované události"
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
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecd335cb08056cb8b7c696555d666f54cad81b87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-routed-event"></a><span data-ttu-id="84a68-102">Postupy: Vytvoření vlastní směrované události</span><span class="sxs-lookup"><span data-stu-id="84a68-102">How to: Create a Custom Routed Event</span></span>
<span data-ttu-id="84a68-103">Pro vaše vlastní události pro podporu směrování událostí, je třeba zaregistrovat <xref:System.Windows.RoutedEvent> pomocí <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="84a68-103">For your custom event to support event routing, you need to register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="84a68-104">Tento příklad ukazuje základní informace o vytváření vlastních směrované události.</span><span class="sxs-lookup"><span data-stu-id="84a68-104">This example demonstrates the basics of creating a custom routed event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84a68-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="84a68-105">Example</span></span>  
 <span data-ttu-id="84a68-106">Jak je znázorněno v následujícím příkladu, nejprve zaregistrovat <xref:System.Windows.RoutedEvent> pomocí <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="84a68-106">As shown in the following example, you first register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="84a68-107">Podle konvence <xref:System.Windows.RoutedEvent> statické pole name musí končit příponou ***událostí***.</span><span class="sxs-lookup"><span data-stu-id="84a68-107">By convention, the <xref:System.Windows.RoutedEvent> static field name should end with the suffix ***Event***.</span></span> <span data-ttu-id="84a68-108">V tomto příkladu je název události `Tap` a směrování strategie události je <xref:System.Windows.RoutingStrategy.Bubble>.</span><span class="sxs-lookup"><span data-stu-id="84a68-108">In this example, the name of the event is `Tap` and the routing strategy of the event is <xref:System.Windows.RoutingStrategy.Bubble>.</span></span> <span data-ttu-id="84a68-109">Po registraci volání, můžete zadat přidat a odebrat [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] přístupových objektů událostí pro událost.</span><span class="sxs-lookup"><span data-stu-id="84a68-109">After the registration call, you can provide add-and-remove [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event accessors for the event.</span></span>  
  
 <span data-ttu-id="84a68-110">Všimněte si, že i když tato událost se vyvolá prostřednictvím `OnTap` virtuální metoda v tomto konkrétním příkladu, jak vyvolat událost nebo jak událost reaguje na změny, závisí na vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="84a68-110">Note that even though the event is raised through the `OnTap` virtual method in this particular example, how you raise your event or how your event responds to changes depends on your needs.</span></span>  
  
 <span data-ttu-id="84a68-111">Všimněte si také, že v tomto příkladu v podstatě implementuje celý podtřídou třídy <xref:System.Windows.Controls.Button>; že podtřídou je vytvořené jako samostatné sestavení a pak vytvořit instance jako vlastní třída na samostatném [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="84a68-111">Note also that this example basically implements an entire subclass of <xref:System.Windows.Controls.Button>; that subclass is built as a separate assembly and then instantiated as a custom class on a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="84a68-112">Toto je k objasnění konceptu rozčleněné ovládací prvky, se vkládají do stromy skládá z jiných ovládacích prvků, a aby v této situaci vlastních událostí na tyto ovládací prvky velmi stejné funkce směrování událostí jako jakýkoli nativní [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nemá element.</span><span class="sxs-lookup"><span data-stu-id="84a68-112">This is to illustrate the concept that subclassed controls can be inserted into trees composed of other controls, and that in this situation, custom events on these controls have the very same event routing capabilities as any native [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] element does.</span></span>  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 <span data-ttu-id="84a68-113">Tunelové události jsou vytvořené stejný způsobem, ale s <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> nastavena na <xref:System.Windows.RoutingStrategy.Tunnel> ve volání registrace.</span><span class="sxs-lookup"><span data-stu-id="84a68-113">Tunneling events are created the same way, but with <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> set to <xref:System.Windows.RoutingStrategy.Tunnel> in the registration call.</span></span> <span data-ttu-id="84a68-114">Podle konvence, tunelové propojení události v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mají předponu slovo "Náhled".</span><span class="sxs-lookup"><span data-stu-id="84a68-114">By convention, tunneling events in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] are prefixed with the word "Preview".</span></span>  
  
 <span data-ttu-id="84a68-115">Příklad, jak probublávání události práce najdete v sekci [zpracování události směrovány](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).</span><span class="sxs-lookup"><span data-stu-id="84a68-115">To see an example of how bubbling events work, see [Handle a Routed Event](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84a68-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="84a68-116">See Also</span></span>  
 [<span data-ttu-id="84a68-117">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="84a68-117">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="84a68-118">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="84a68-118">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [<span data-ttu-id="84a68-119">Přehled vytváření ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="84a68-119">Control Authoring Overview</span></span>](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
