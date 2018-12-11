---
title: Implementace explicitního rozhraní - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: e985da878ca4160938f29911d4313ee6cd731aeb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244827"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="b047b-102">Implementace explicitního rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b047b-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="b047b-103">Pokud [třídy](../../../csharp/language-reference/keywords/class.md) implementuje dvě rozhraní, které obsahují člena se stejnou signaturou, pak implementace člena třídy způsobí, že obě rozhraní pro použití tohoto člena jako jejich provádění.</span><span class="sxs-lookup"><span data-stu-id="b047b-103">If a [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="b047b-104">V následujícím příkladu, všechna volání do `Paint` volání stejné metody.</span><span class="sxs-lookup"><span data-stu-id="b047b-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 <span data-ttu-id="b047b-105">Pokud dvě [rozhraní](../../../csharp/language-reference/keywords/interface.md) členy nebudete provádět má stejnou funkci, ale to může vést k nesprávná implementace jedno nebo obě rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b047b-105">If the two [interface](../../../csharp/language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="b047b-106">Je možné implementovat člen rozhraní, explicitně – vytvoření člena třídy, která je jen volá prostřednictvím rozhraní a je specifické pro rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b047b-106">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="b047b-107">Toho lze dosáhnout pojmenování člena třídy se název rozhraní a tečku.</span><span class="sxs-lookup"><span data-stu-id="b047b-107">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="b047b-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b047b-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 <span data-ttu-id="b047b-109">Člen třídy `IControl.Paint` je dostupná jenom `IControl` rozhraní, a `ISurface.Paint` je dostupná jenom `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="b047b-109">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="b047b-110">Implementace obě metody jsou oddělené a ani je k dispozici přímo ve třídě.</span><span class="sxs-lookup"><span data-stu-id="b047b-110">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="b047b-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b047b-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 <span data-ttu-id="b047b-112">Explicitní implementaci se také používá k překladu případy, ve kterém dvě rozhraní deklarovat jiné členy se stejným názvem, jako jsou vlastnosti a metody:</span><span class="sxs-lookup"><span data-stu-id="b047b-112">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 <span data-ttu-id="b047b-113">Třídy musí implementovat obě rozhraní, použijte explicitní implementaci buď pro vlastnost P nebo metoda P, nebo obojí, aby se zabránilo chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b047b-113">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="b047b-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b047b-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b047b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b047b-115">See Also</span></span>

- [<span data-ttu-id="b047b-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b047b-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b047b-117">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="b047b-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="b047b-118">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="b047b-118">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
- [<span data-ttu-id="b047b-119">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="b047b-119">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
