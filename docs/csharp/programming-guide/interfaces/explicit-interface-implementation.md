---
title: Explicitní implementace rozhraní – Průvodce programováním v C#
description: Třída může implementovat rozhraní, která obsahují člena se stejnou signaturou v jazyce C#. Explicitní implementace vytvoří člena třídy specifického pro jedno rozhraní.
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: a6ec328c08d1da84a11431d9400a094df8c72223
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303084"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="1a6ba-104">Implementace explicitního rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1a6ba-104">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="1a6ba-105">Pokud [Třída](../../language-reference/keywords/class.md) implementuje dvě rozhraní, která obsahují člena se stejnou signaturou, pak implementace tohoto člena na třídu způsobí, že obě rozhraní budou používat tento člen jako svou implementaci.</span><span class="sxs-lookup"><span data-stu-id="1a6ba-105">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="1a6ba-106">V následujícím příkladu všechna volání `Paint` vyvolávají stejnou metodu.</span><span class="sxs-lookup"><span data-stu-id="1a6ba-106">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="1a6ba-107">Tato první ukázka definuje typy:</span><span class="sxs-lookup"><span data-stu-id="1a6ba-107">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="1a6ba-108">Následující příklad volá metody:</span><span class="sxs-lookup"><span data-stu-id="1a6ba-108">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="1a6ba-109">Pokud dva členy rozhraní neprovádějí stejnou funkci, vede k nesprávné implementaci jednoho nebo obou rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1a6ba-109">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="1a6ba-110">Je možné implementovat člena rozhraní explicitně – vytvořením členu třídy, který je volán pouze prostřednictvím rozhraní a je specifický pro toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1a6ba-110">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="1a6ba-111">Pojmenujte člena třídy názvem rozhraní a tečkou.</span><span class="sxs-lookup"><span data-stu-id="1a6ba-111">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="1a6ba-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1a6ba-112">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="1a6ba-113">Člen třídy `IControl.Paint` je k dispozici pouze prostřednictvím `IControl` rozhraní a `ISurface.Paint` je k dispozici pouze prostřednictvím `ISurface` .</span><span class="sxs-lookup"><span data-stu-id="1a6ba-113">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="1a6ba-114">Implementace obou metod jsou oddělené a žádné nejsou k dispozici přímo na třídě.</span><span class="sxs-lookup"><span data-stu-id="1a6ba-114">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="1a6ba-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1a6ba-115">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="1a6ba-116">Explicitní implementace je také použita k vyřešení případů, kde dvě rozhraní každý deklaruje různé členy stejného názvu, jako je například vlastnost a metoda.</span><span class="sxs-lookup"><span data-stu-id="1a6ba-116">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="1a6ba-117">Pro implementaci obou rozhraní musí třída použít explicitní implementaci buď pro vlastnost `P` , nebo pro metodu `P` , nebo pro obojí, aby nedošlo k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1a6ba-117">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="1a6ba-118">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1a6ba-118">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="1a6ba-119">Počínaje [jazykem C# 8,0](../../whats-new/csharp-8.md#default-interface-methods)můžete definovat implementaci pro členy deklarované v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1a6ba-119">Beginning with [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), you can define an implementation for members declared in an interface.</span></span> <span data-ttu-id="1a6ba-120">Pokud třída dědí implementaci metody z rozhraní, je tato metoda přístupná pouze prostřednictvím odkazu typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1a6ba-120">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="1a6ba-121">Zděděný člen se nezobrazuje jako součást veřejného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1a6ba-121">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="1a6ba-122">Následující příklad definuje výchozí implementaci pro metodu rozhraní:</span><span class="sxs-lookup"><span data-stu-id="1a6ba-122">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="1a6ba-123">Následující ukázka vyvolá výchozí implementaci:</span><span class="sxs-lookup"><span data-stu-id="1a6ba-123">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="1a6ba-124">Libovolná třída, která implementuje `IControl` rozhraní, může přepsat výchozí `Paint` metodu buď jako veřejnou metodu, nebo jako explicitní implementaci rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1a6ba-124">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a6ba-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a6ba-125">See also</span></span>

- [<span data-ttu-id="1a6ba-126">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="1a6ba-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1a6ba-127">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="1a6ba-127">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="1a6ba-128">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a6ba-128">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="1a6ba-129">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="1a6ba-129">Inheritance</span></span>](../classes-and-structs/inheritance.md)
