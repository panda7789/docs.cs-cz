---
title: Explicitní implementace rozhraní – programovací příručka jazyka C#
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: ea32a279b7c464174a7fada5ef93ccf62ef39884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167670"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="f19d9-102">Implementace explicitního rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f19d9-102">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="f19d9-103">Pokud [třída](../../language-reference/keywords/class.md) implementuje dvě rozhraní, které obsahují člen se stejným podpisem, pak implementace tohoto člena ve třídě způsobí, že obě rozhraní použít tento člen jako jejich implementace.</span><span class="sxs-lookup"><span data-stu-id="f19d9-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="f19d9-104">V následujícím příkladu všechna `Paint` volání vyvolat stejnou metodu.</span><span class="sxs-lookup"><span data-stu-id="f19d9-104">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="f19d9-105">Tato první ukázka definuje typy:</span><span class="sxs-lookup"><span data-stu-id="f19d9-105">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="f19d9-106">Následující ukázka volá metody:</span><span class="sxs-lookup"><span data-stu-id="f19d9-106">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="f19d9-107">Pokud dva členové rozhraní nevykonávají stejnou funkci, vede k nesprávné implementaci jednoho nebo obou rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f19d9-107">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="f19d9-108">Je možné implementovat člen rozhraní explicitně – vytvoření člena třídy, který je volán pouze prostřednictvím rozhraní a je specifické pro toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f19d9-108">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="f19d9-109">Pojmenujte člena třídy názvem rozhraní a tečkou.</span><span class="sxs-lookup"><span data-stu-id="f19d9-109">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="f19d9-110">Například:</span><span class="sxs-lookup"><span data-stu-id="f19d9-110">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="f19d9-111">`IControl.Paint` Člen třídy je k `IControl` dispozici `ISurface.Paint` pouze prostřednictvím `ISurface`rozhraní a je k dispozici pouze prostřednictvím .</span><span class="sxs-lookup"><span data-stu-id="f19d9-111">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="f19d9-112">Obě implementace metody jsou samostatné a ani nejsou k dispozici přímo ve třídě.</span><span class="sxs-lookup"><span data-stu-id="f19d9-112">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="f19d9-113">Například:</span><span class="sxs-lookup"><span data-stu-id="f19d9-113">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="f19d9-114">Explicitní implementace se také používá k vyřešení případů, kdy dvě rozhraní každý deklarovat různé členy se stejným názvem, jako je například vlastnost a metoda.</span><span class="sxs-lookup"><span data-stu-id="f19d9-114">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="f19d9-115">Chcete-li implementovat obě rozhraní, třída musí použít `P`explicitní implementaci `P`buď pro vlastnost , nebo metodu nebo obojí, aby se zabránilo chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f19d9-115">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="f19d9-116">Například:</span><span class="sxs-lookup"><span data-stu-id="f19d9-116">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="f19d9-117">Počínaje [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), můžete definovat implementaci pro členy deklarované v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f19d9-117">Beginning with [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), you can define an implementation for members declared in an interface.</span></span> <span data-ttu-id="f19d9-118">Pokud třída dědí implementaci metody z rozhraní, tato metoda je přístupná pouze prostřednictvím odkazu na typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f19d9-118">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="f19d9-119">Zděděný člen se nezobrazí jako součást veřejného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f19d9-119">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="f19d9-120">Následující ukázka definuje výchozí implementaci metody rozhraní:</span><span class="sxs-lookup"><span data-stu-id="f19d9-120">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="f19d9-121">Následující ukázka vyvolá výchozí implementaci:</span><span class="sxs-lookup"><span data-stu-id="f19d9-121">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="f19d9-122">Každá třída, která `IControl` implementuje rozhraní `Paint` můžete přepsat výchozí metodu, buď jako veřejnou metodu nebo jako explicitní implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f19d9-122">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="f19d9-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f19d9-123">See also</span></span>

- [<span data-ttu-id="f19d9-124">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f19d9-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f19d9-125">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="f19d9-125">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="f19d9-126">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="f19d9-126">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="f19d9-127">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="f19d9-127">Inheritance</span></span>](../classes-and-structs/inheritance.md)
