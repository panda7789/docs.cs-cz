---
title: "Implementace explicitního rozhraní (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b746a69484b73a4212c729e02a1256ee1c83ea41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="4111a-102">Implementace explicitního rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4111a-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="4111a-103">Pokud [třída](../../../csharp/language-reference/keywords/class.md) implementuje dvě rozhraní, které obsahují člen se stejným podpisem, pak implementace tohoto člena k třídě způsobí, že obě rozhraní pro použití tohoto člena jako jejich provádění.</span><span class="sxs-lookup"><span data-stu-id="4111a-103">If a [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="4111a-104">V následujícím příkladu, všechna volání do `Paint` vyvolání stejnou metodu.</span><span class="sxs-lookup"><span data-stu-id="4111a-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 <span data-ttu-id="4111a-105">Pokud dva [rozhraní](../../../csharp/language-reference/keywords/interface.md) členy neprovádět stejnou funkci, ale to může vést k nesprávné implementace jedno nebo obě rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4111a-105">If the two [interface](../../../csharp/language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="4111a-106">Je možné implementovat člena rozhraní explicitně – vytvoření člena třídy, která je volána pouze přes rozhraní a je specifická pro toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4111a-106">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="4111a-107">To se provádí pojmenování člen třídy s názvem rozhraní a období.</span><span class="sxs-lookup"><span data-stu-id="4111a-107">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="4111a-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4111a-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 <span data-ttu-id="4111a-109">Člen třídy `IControl.Paint` je k dispozici prostřednictvím pouze `IControl` rozhraní, a `ISurface.Paint` je k dispozici prostřednictvím `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="4111a-109">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="4111a-110">Implementace obě metody jsou samostatné a ani jeden z nich je k dispozici přímo na třídu.</span><span class="sxs-lookup"><span data-stu-id="4111a-110">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="4111a-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4111a-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 <span data-ttu-id="4111a-112">Explicitní implementace se také používá k překladu případech, kde dvě rozhraní deklarovat jiné členy se stejným názvem, jako je například vlastnosti a metody:</span><span class="sxs-lookup"><span data-stu-id="4111a-112">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 <span data-ttu-id="4111a-113">Pokud chcete implementovat obě rozhraní, třída má použít explicitní implementace pro vlastnost P nebo metoda P nebo obojí, aby se zabránilo chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="4111a-113">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="4111a-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4111a-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4111a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="4111a-115">See Also</span></span>  
 [<span data-ttu-id="4111a-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4111a-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4111a-117">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="4111a-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="4111a-118">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="4111a-118">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="4111a-119">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="4111a-119">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
