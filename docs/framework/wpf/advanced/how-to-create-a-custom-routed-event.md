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
ms.openlocfilehash: cbfb88af4e35e3f090248982bb14d6b7a3a03cef
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401464"
---
# <a name="how-to-create-a-custom-routed-event"></a><span data-ttu-id="038ee-102">Postupy: Vytvoření vlastní směrované události</span><span class="sxs-lookup"><span data-stu-id="038ee-102">How to: Create a Custom Routed Event</span></span>
<span data-ttu-id="038ee-103">Aby vaše vlastní událost podporovala směrování událostí, je nutné ji zaregistrovat <xref:System.Windows.RoutedEvent> <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="038ee-103">For your custom event to support event routing, you need to register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="038ee-104">Tento příklad ukazuje základy vytvoření vlastní směrované události.</span><span class="sxs-lookup"><span data-stu-id="038ee-104">This example demonstrates the basics of creating a custom routed event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="038ee-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="038ee-105">Example</span></span>  
 <span data-ttu-id="038ee-106">Jak je znázorněno v následujícím příkladu, nejprve zaregistrujete <xref:System.Windows.RoutedEvent> <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="038ee-106">As shown in the following example, you first register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="038ee-107">Podle konvence <xref:System.Windows.RoutedEvent> by měl název statického pole končit ***událostí***přípony.</span><span class="sxs-lookup"><span data-stu-id="038ee-107">By convention, the <xref:System.Windows.RoutedEvent> static field name should end with the suffix ***Event***.</span></span> <span data-ttu-id="038ee-108">V tomto příkladu je název události `Tap` a strategie směrování události je. <xref:System.Windows.RoutingStrategy.Bubble></span><span class="sxs-lookup"><span data-stu-id="038ee-108">In this example, the name of the event is `Tap` and the routing strategy of the event is <xref:System.Windows.RoutingStrategy.Bubble>.</span></span> <span data-ttu-id="038ee-109">Po volání registrace můžete pro událost zadat doplňky pro přístup k modulům CLR (Common Language Runtime) a odebrat je.</span><span class="sxs-lookup"><span data-stu-id="038ee-109">After the registration call, you can provide add-and-remove common language runtime (CLR) event accessors for the event.</span></span>  
  
 <span data-ttu-id="038ee-110">Všimněte si, že i když se událost vyvolá prostřednictvím `OnTap` virtuální metody v tomto konkrétním příkladu, jak vyvoláte událost nebo jak vaše událost reaguje na změny, závisí na vašich potřebách.</span><span class="sxs-lookup"><span data-stu-id="038ee-110">Note that even though the event is raised through the `OnTap` virtual method in this particular example, how you raise your event or how your event responds to changes depends on your needs.</span></span>  
  
 <span data-ttu-id="038ee-111">Všimněte si také, že tento příklad v podstatě implementuje celou podtřídu <xref:System.Windows.Controls.Button>třídy; tato podtřída je sestavena jako samostatné sestavení a poté vytvořena instance jako vlastní třída na samostatné [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránce.</span><span class="sxs-lookup"><span data-stu-id="038ee-111">Note also that this example basically implements an entire subclass of <xref:System.Windows.Controls.Button>; that subclass is built as a separate assembly and then instantiated as a custom class on a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="038ee-112">To je znázornění konceptu, který mohou být ovládací prvky podtříd vloženy do stromů složených z jiných ovládacích prvků a v této situaci mají vlastní události na těchto ovládacích prvcích stejné možnosti směrování událostí jako všechny nativní [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prvky.</span><span class="sxs-lookup"><span data-stu-id="038ee-112">This is to illustrate the concept that subclassed controls can be inserted into trees composed of other controls, and that in this situation, custom events on these controls have the very same event routing capabilities as any native [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] element does.</span></span>  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 <span data-ttu-id="038ee-113">Události tunelového propojení jsou vytvářeny stejným způsobem, ale <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> s nastavením <xref:System.Windows.RoutingStrategy.Tunnel> na při volání registrace.</span><span class="sxs-lookup"><span data-stu-id="038ee-113">Tunneling events are created the same way, but with <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> set to <xref:System.Windows.RoutingStrategy.Tunnel> in the registration call.</span></span> <span data-ttu-id="038ee-114">Podle konvence jsou události tunelu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v v předponě ve slově Preview.</span><span class="sxs-lookup"><span data-stu-id="038ee-114">By convention, tunneling events in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] are prefixed with the word "Preview".</span></span>  
  
 <span data-ttu-id="038ee-115">Příklad toho, jak fungují události probublávání, najdete v tématu [zpracování směrované události](how-to-handle-a-routed-event.md).</span><span class="sxs-lookup"><span data-stu-id="038ee-115">To see an example of how bubbling events work, see [Handle a Routed Event](how-to-handle-a-routed-event.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="038ee-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="038ee-116">See also</span></span>

- [<span data-ttu-id="038ee-117">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="038ee-117">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="038ee-118">Přehled vstupu</span><span class="sxs-lookup"><span data-stu-id="038ee-118">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="038ee-119">Přehled vytváření ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="038ee-119">Control Authoring Overview</span></span>](../controls/control-authoring-overview.md)
