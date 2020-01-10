---
title: Explicitní implementace rozhraní – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: ac90726fd50f104d1b9251d4f9b097b721ea5e7d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75701755"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="1d519-102">Implementace explicitního rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1d519-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="1d519-103">Pokud [Třída](../../language-reference/keywords/class.md) implementuje dvě rozhraní, která obsahují člena se stejnou signaturou, pak implementace tohoto člena na třídu způsobí, že obě rozhraní budou používat tento člen jako svou implementaci.</span><span class="sxs-lookup"><span data-stu-id="1d519-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="1d519-104">V následujícím příkladu všechna volání `Paint` vyvolat stejnou metodu.</span><span class="sxs-lookup"><span data-stu-id="1d519-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#39)]  
  
 <span data-ttu-id="1d519-105">Pokud dva členy [rozhraní](../../language-reference/keywords/interface.md) neprovádějí stejnou funkci, může však vést k nesprávné implementaci jednoho nebo obou rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1d519-105">If the two [interface](../../language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="1d519-106">Je možné implementovat člena rozhraní explicitně – vytvořením členu třídy, který je volán pouze prostřednictvím rozhraní a je specifický pro toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1d519-106">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="1d519-107">Toho lze dosáhnout pojmenováním člena třídy názvem rozhraní a tečkou.</span><span class="sxs-lookup"><span data-stu-id="1d519-107">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="1d519-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1d519-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#40)]  
  
 <span data-ttu-id="1d519-109">Člen třídy `IControl.Paint` je k dispozici pouze prostřednictvím rozhraní `IControl` a `ISurface.Paint` je k dispozici pouze prostřednictvím `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="1d519-109">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="1d519-110">Implementace obou metod jsou oddělené a nejsou k dispozici přímo na třídě.</span><span class="sxs-lookup"><span data-stu-id="1d519-110">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="1d519-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1d519-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#41)]  
  
 <span data-ttu-id="1d519-112">Explicitní implementace je také použita k vyřešení případů, kde dvě rozhraní každý deklaruje různé členy stejného názvu, jako je například vlastnost a metoda:</span><span class="sxs-lookup"><span data-stu-id="1d519-112">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#42)]  
  
 <span data-ttu-id="1d519-113">Pro implementaci obou rozhraní musí třída použít explicitní implementaci buď pro vlastnost P, nebo pro metodu P nebo pro obojí, aby nedošlo k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1d519-113">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="1d519-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1d519-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#43)]  
  
## <a name="see-also"></a><span data-ttu-id="1d519-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d519-115">See also</span></span>

- [<span data-ttu-id="1d519-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1d519-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1d519-117">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="1d519-117">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="1d519-118">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d519-118">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="1d519-119">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="1d519-119">Inheritance</span></span>](../classes-and-structs/inheritance.md)
