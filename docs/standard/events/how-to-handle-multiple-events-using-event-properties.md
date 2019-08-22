---
title: 'Postupy: Zpracování více událostí pomocí vlastností událostí'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET Framework]
- multiple events [.NET Framework]
- event handling [.NET Framework], with multiple events
- events [.NET Framework], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 758ddc603766462fc48885406c4e4ca1162bbbaf
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666491"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="126c8-102">Postupy: Zpracování více událostí pomocí vlastností událostí</span><span class="sxs-lookup"><span data-stu-id="126c8-102">How to: Handle Multiple Events Using Event Properties</span></span>
<span data-ttu-id="126c8-103">Chcete-li použít vlastnosti událostí, je třeba definovat vlastnosti událostí ve třídě, která události vyvolá, a poté nastavit delegáty pro tyto vlastnosti událostí ve třídách, které události zpracovávají.</span><span class="sxs-lookup"><span data-stu-id="126c8-103">To use event properties, you define the event properties in the class that raises the events, and then set the delegates for the event properties in classes that handle the events.</span></span> <span data-ttu-id="126c8-104">Pro implementaci více vlastností události ve třídě musí třída interně ukládat a udržovat delegáty definované pro každou událost.</span><span class="sxs-lookup"><span data-stu-id="126c8-104">To implement multiple event properties in a class, the class must internally store and maintain the delegate defined for each event.</span></span> <span data-ttu-id="126c8-105">Typickým přístupem je implementace kolekce delegátů, která je indexována klíčem události.</span><span class="sxs-lookup"><span data-stu-id="126c8-105">A typical approach is to implement a delegate collection that is indexed by an event key.</span></span>  
  
 <span data-ttu-id="126c8-106">Chcete-li uložit delegáty pro každou událost, můžete použít <xref:System.ComponentModel.EventHandlerList> třídu nebo implementovat vlastní kolekci.</span><span class="sxs-lookup"><span data-stu-id="126c8-106">To store the delegates for each event, you can use the <xref:System.ComponentModel.EventHandlerList> class, or implement your own collection.</span></span> <span data-ttu-id="126c8-107">Třída kolekce musí poskytovat metody pro nastavení, přístup a načtení delegáta obslužné rutiny události na základě klíče události.</span><span class="sxs-lookup"><span data-stu-id="126c8-107">The collection class must provide methods for setting, accessing, and retrieving the event handler delegate based on the event key.</span></span> <span data-ttu-id="126c8-108">Můžete například použít <xref:System.Collections.Hashtable> třídu nebo <xref:System.Collections.DictionaryBase> z třídy odvodit vlastní třídu.</span><span class="sxs-lookup"><span data-stu-id="126c8-108">For example, you could use a <xref:System.Collections.Hashtable> class, or derive a custom class from the <xref:System.Collections.DictionaryBase> class.</span></span> <span data-ttu-id="126c8-109">Podrobnosti implementace kolekce delegátů nemusí být vystaveny mimo vaši třídu.</span><span class="sxs-lookup"><span data-stu-id="126c8-109">The implementation details of the delegate collection do not need to be exposed outside your class.</span></span>  
  
 <span data-ttu-id="126c8-110">Každá vlastnost události v rámci třídy definuje metodu přistupujícího objektu Add a metodu odebrání přístupového objektu.</span><span class="sxs-lookup"><span data-stu-id="126c8-110">Each event property within the class defines an add accessor method and a remove accessor method.</span></span> <span data-ttu-id="126c8-111">Přístupový objekt Add pro vlastnost události přidá instanci vstupního delegáta do kolekce Delegate.</span><span class="sxs-lookup"><span data-stu-id="126c8-111">The add accessor for an event property adds the input delegate instance to the delegate collection.</span></span> <span data-ttu-id="126c8-112">Přístupový objekt Remove pro vlastnost události odebere instanci vstupního delegáta z kolekce Delegate.</span><span class="sxs-lookup"><span data-stu-id="126c8-112">The remove accessor for an event property removes the input delegate instance from the delegate collection.</span></span> <span data-ttu-id="126c8-113">Přistupující objekty vlastnosti události používají předdefinovaný klíč pro vlastnost Event k přidání a odebrání instancí z kolekce delegátů.</span><span class="sxs-lookup"><span data-stu-id="126c8-113">The event property accessors use the predefined key for the event property to add and remove instances from the delegate collection.</span></span>  
  
### <a name="to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="126c8-114">Postup zpracování více událostí pomocí vlastností událostí</span><span class="sxs-lookup"><span data-stu-id="126c8-114">To handle multiple events using event properties</span></span>  
  
1. <span data-ttu-id="126c8-115">Definujte kolekci delegátů v rámci třídy, která vyvolá události.</span><span class="sxs-lookup"><span data-stu-id="126c8-115">Define a delegate collection within the class that raises the events.</span></span>  
  
2. <span data-ttu-id="126c8-116">Definujte klíč pro každou událost.</span><span class="sxs-lookup"><span data-stu-id="126c8-116">Define a key for each event.</span></span>  
  
3. <span data-ttu-id="126c8-117">Definujte vlastnosti události ve třídě, která vyvolává události.</span><span class="sxs-lookup"><span data-stu-id="126c8-117">Define the event properties in the class that raises the events.</span></span>  
  
4. <span data-ttu-id="126c8-118">Použijte kolekci Delegate k implementaci přístupových metod přidat a odebrat pro vlastnosti události.</span><span class="sxs-lookup"><span data-stu-id="126c8-118">Use the delegate collection to implement the add and remove accessor methods for the event properties.</span></span>  
  
5. <span data-ttu-id="126c8-119">Pomocí vlastností veřejné události můžete přidat a odebrat delegáty obslužných rutin událostí ve třídách, které zpracovávají události.</span><span class="sxs-lookup"><span data-stu-id="126c8-119">Use the public event properties to add and remove event handler delegates in the classes that handle the events.</span></span>  
  
## <a name="example"></a><span data-ttu-id="126c8-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="126c8-120">Example</span></span>  
 <span data-ttu-id="126c8-121">Následující C# příklad implementuje vlastnosti `MouseDown` události `MouseUp`a pomocí <xref:System.ComponentModel.EventHandlerList> a ukládá delegáta každé události.</span><span class="sxs-lookup"><span data-stu-id="126c8-121">The following C# example implements the event properties `MouseDown` and `MouseUp`, using an <xref:System.ComponentModel.EventHandlerList> to store each event's delegate.</span></span> <span data-ttu-id="126c8-122">Klíčová slova konstrukcí vlastností události jsou v tučném typu.</span><span class="sxs-lookup"><span data-stu-id="126c8-122">The keywords of the event property constructs are in bold type.</span></span>  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="126c8-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="126c8-123">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [<span data-ttu-id="126c8-124">Události</span><span class="sxs-lookup"><span data-stu-id="126c8-124">Events</span></span>](../../../docs/standard/events/index.md)
- <xref:System.Web.UI.Control.Events%2A?displayProperty=nameWithType>
- [<span data-ttu-id="126c8-125">Postupy: Deklarovat vlastní události pro zachování paměti</span><span class="sxs-lookup"><span data-stu-id="126c8-125">How to: Declare Custom Events To Conserve Memory</span></span>](../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
