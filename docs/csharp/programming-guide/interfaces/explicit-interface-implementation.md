---
title: Explicitní implementace rozhraní – C# Průvodce programováním
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: c6f1f849e0d4e831802b4c9b8b4bc3887363a34c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628147"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="5eb59-102">Implementace explicitního rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5eb59-102">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="5eb59-103">Pokud [Třída](../../language-reference/keywords/class.md) implementuje dvě rozhraní, která obsahují člena se stejnou signaturou, pak implementace tohoto člena na třídu způsobí, že obě rozhraní budou používat tento člen jako svou implementaci.</span><span class="sxs-lookup"><span data-stu-id="5eb59-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="5eb59-104">V následujícím příkladu všechna volání `Paint` vyvolat stejnou metodu.</span><span class="sxs-lookup"><span data-stu-id="5eb59-104">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="5eb59-105">Tato první ukázka definuje typy:</span><span class="sxs-lookup"><span data-stu-id="5eb59-105">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="5eb59-106">Následující příklad volá metody:</span><span class="sxs-lookup"><span data-stu-id="5eb59-106">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="5eb59-107">Pokud dva členy rozhraní neprovádějí stejnou funkci, vede k nesprávné implementaci jednoho nebo obou rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5eb59-107">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="5eb59-108">Je možné implementovat člena rozhraní explicitně – vytvořením členu třídy, který je volán pouze prostřednictvím rozhraní a je specifický pro toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5eb59-108">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="5eb59-109">Pojmenujte člena třídy názvem rozhraní a tečkou.</span><span class="sxs-lookup"><span data-stu-id="5eb59-109">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="5eb59-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5eb59-110">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="5eb59-111">Člen třídy `IControl.Paint` je k dispozici pouze prostřednictvím rozhraní `IControl` a `ISurface.Paint` je k dispozici pouze prostřednictvím `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="5eb59-111">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="5eb59-112">Implementace obou metod jsou oddělené a žádné nejsou k dispozici přímo na třídě.</span><span class="sxs-lookup"><span data-stu-id="5eb59-112">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="5eb59-113">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5eb59-113">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="5eb59-114">Explicitní implementace je také použita k vyřešení případů, kde dvě rozhraní každý deklaruje různé členy stejného názvu, jako je například vlastnost a metoda.</span><span class="sxs-lookup"><span data-stu-id="5eb59-114">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="5eb59-115">Pro implementaci obou rozhraní musí třída použít explicitní implementaci buď pro vlastnost `P`, nebo metodu `P`nebo obojí, aby nedošlo k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="5eb59-115">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="5eb59-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5eb59-116">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="5eb59-117">Pokud třída dědí implementaci metody z rozhraní, je tato metoda přístupná pouze prostřednictvím odkazu typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5eb59-117">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="5eb59-118">Zděděný člen se nezobrazuje jako součást veřejného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5eb59-118">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="5eb59-119">Následující příklad definuje výchozí implementaci pro metodu rozhraní:</span><span class="sxs-lookup"><span data-stu-id="5eb59-119">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="5eb59-120">Následující ukázka vyvolá výchozí implementaci:</span><span class="sxs-lookup"><span data-stu-id="5eb59-120">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="5eb59-121">Libovolná třída, která implementuje rozhraní `IControl`, může přepsat výchozí `Paint` metodu buď jako veřejnou metodu, nebo jako explicitní implementaci rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5eb59-121">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="5eb59-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="5eb59-122">See also</span></span>

- [<span data-ttu-id="5eb59-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="5eb59-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5eb59-124">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="5eb59-124">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="5eb59-125">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="5eb59-125">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="5eb59-126">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="5eb59-126">Inheritance</span></span>](../classes-and-structs/inheritance.md)
