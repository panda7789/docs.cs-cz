---
title: 'Postupy: Vytvoření vlastní směrované události'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: f6d043dc2975770fe9111c6266096eefb3fe15b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671691"
---
# <a name="how-to-create-a-custom-routed-event"></a><span data-ttu-id="8ab11-102">Postupy: Vytvoření vlastní směrované události</span><span class="sxs-lookup"><span data-stu-id="8ab11-102">How to: Create a Custom Routed Event</span></span>
<span data-ttu-id="8ab11-103">Pro vaše vlastní událost, podporu směrování událostí, budete muset zaregistrovat <xref:System.Windows.RoutedEvent> pomocí <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8ab11-103">For your custom event to support event routing, you need to register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="8ab11-104">Tento příklad ukazuje základní informace o vytvoření vlastní směrované události.</span><span class="sxs-lookup"><span data-stu-id="8ab11-104">This example demonstrates the basics of creating a custom routed event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ab11-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ab11-105">Example</span></span>  
 <span data-ttu-id="8ab11-106">Jak je znázorněno v následujícím příkladu, nejprve zaregistrovat <xref:System.Windows.RoutedEvent> pomocí <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8ab11-106">As shown in the following example, you first register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="8ab11-107">Podle konvence <xref:System.Windows.RoutedEvent> statické pole Název musí končit příponou ***události***.</span><span class="sxs-lookup"><span data-stu-id="8ab11-107">By convention, the <xref:System.Windows.RoutedEvent> static field name should end with the suffix ***Event***.</span></span> <span data-ttu-id="8ab11-108">V tomto příkladu je název události `Tap` a strategie směrování události je <xref:System.Windows.RoutingStrategy.Bubble>.</span><span class="sxs-lookup"><span data-stu-id="8ab11-108">In this example, the name of the event is `Tap` and the routing strategy of the event is <xref:System.Windows.RoutingStrategy.Bubble>.</span></span> <span data-ttu-id="8ab11-109">Po volání registrace může poskytnout přidávat a odebírat [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] přístupových objektů událostí pro událost.</span><span class="sxs-lookup"><span data-stu-id="8ab11-109">After the registration call, you can provide add-and-remove [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event accessors for the event.</span></span>  
  
 <span data-ttu-id="8ab11-110">Všimněte si, že i když se vyvolá událost prostřednictvím `OnTap` virtuální metoda v tomto konkrétním příkladu, jak vyvolat události nebo jak událost reaguje na změny závisí na požadavcích.</span><span class="sxs-lookup"><span data-stu-id="8ab11-110">Note that even though the event is raised through the `OnTap` virtual method in this particular example, how you raise your event or how your event responds to changes depends on your needs.</span></span>  
  
 <span data-ttu-id="8ab11-111">Všimněte si také, že v tomto příkladu v podstatě implementuje celý podtřídou třídy <xref:System.Windows.Controls.Button>; tento podtřídy je vytvořen jako samostatné sestavení a pak vytvořit instanci jako vlastní třídu na samostatném [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="8ab11-111">Note also that this example basically implements an entire subclass of <xref:System.Windows.Controls.Button>; that subclass is built as a separate assembly and then instantiated as a custom class on a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="8ab11-112">Toto je pro ilustraci koncepci, že rozčleněné ovládací prvky mohou být zařazeny do stromové struktury skládá z jiných ovládacích prvků a, v takovém případě vlastní události do těchto ovládacích prvků mají stejné možnosti směrování událostí jako nativní [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nemá element.</span><span class="sxs-lookup"><span data-stu-id="8ab11-112">This is to illustrate the concept that subclassed controls can be inserted into trees composed of other controls, and that in this situation, custom events on these controls have the very same event routing capabilities as any native [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] element does.</span></span>  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 <span data-ttu-id="8ab11-113">Tunelového propojení budou vytvořeny události, stejný způsobem, ale s <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> nastavena na <xref:System.Windows.RoutingStrategy.Tunnel> při volání metody registrace.</span><span class="sxs-lookup"><span data-stu-id="8ab11-113">Tunneling events are created the same way, but with <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> set to <xref:System.Windows.RoutingStrategy.Tunnel> in the registration call.</span></span> <span data-ttu-id="8ab11-114">Podle konvence, tunelové propojení událostí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mají předponu slovo "Verze Preview".</span><span class="sxs-lookup"><span data-stu-id="8ab11-114">By convention, tunneling events in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] are prefixed with the word "Preview".</span></span>  
  
 <span data-ttu-id="8ab11-115">Příkladem práce jak šíření událostí najdete v tématu [zpracování události směrovat](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).</span><span class="sxs-lookup"><span data-stu-id="8ab11-115">To see an example of how bubbling events work, see [Handle a Routed Event](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab11-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ab11-116">See also</span></span>
- [<span data-ttu-id="8ab11-117">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="8ab11-117">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [<span data-ttu-id="8ab11-118">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="8ab11-118">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
- [<span data-ttu-id="8ab11-119">Přehled vytváření ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="8ab11-119">Control Authoring Overview</span></span>](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
