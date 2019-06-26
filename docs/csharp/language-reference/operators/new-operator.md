---
title: operátor new - C# odkaz
ms.custom: seodec18
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3d64c4805abe38c80301748ffa6b35fc87563b60
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402511"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="852f2-102">New – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="852f2-102">new operator (C# reference)</span></span>

<span data-ttu-id="852f2-103">`new` Operátor vytvoří novou instanci typu.</span><span class="sxs-lookup"><span data-stu-id="852f2-103">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="852f2-104">Můžete také použít `new` – klíčové slovo jako [modifikátoru deklarace člena](../keywords/new-modifier.md) nebo [omezení obecného typu](../keywords/new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="852f2-104">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="852f2-105">Vyvolání konstruktoru</span><span class="sxs-lookup"><span data-stu-id="852f2-105">Constructor invocation</span></span>

<span data-ttu-id="852f2-106">Pokud chcete vytvořit novou instanci typu, je obvykle vyvolat jeden z [konstruktory](../../programming-guide/classes-and-structs/constructors.md) tento typ použití `new` operátor:</span><span class="sxs-lookup"><span data-stu-id="852f2-106">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

<span data-ttu-id="852f2-107">Můžete použít [inicializátor objektu nebo kolekce](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) s `new` operátor konkretizovat a inicializovat objekt v jednom příkazu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="852f2-107">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="852f2-108">Vytvoření pole</span><span class="sxs-lookup"><span data-stu-id="852f2-108">Array creation</span></span>

<span data-ttu-id="852f2-109">Můžete také použít `new` operátoru pro vytvoření instance pole, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="852f2-109">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

<span data-ttu-id="852f2-110">Syntaxe inicializace pole použijte k vytvoření instance pole a přidejte do ní prvky v jednom příkazu.</span><span class="sxs-lookup"><span data-stu-id="852f2-110">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="852f2-111">Následující příklad ukazuje různé způsoby, jak můžete to udělat:</span><span class="sxs-lookup"><span data-stu-id="852f2-111">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="852f2-112">Další informace o polích naleznete v tématu [pole](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="852f2-112">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="852f2-113">Vytvoření instance anonymní typy</span><span class="sxs-lookup"><span data-stu-id="852f2-113">Instantiation of anonymous types</span></span>

<span data-ttu-id="852f2-114">K vytvoření instance [anonymního typu](../../programming-guide/classes-and-structs/anonymous-types.md), použijte `new` operátor a objekt syntaxe inicializátoru:</span><span class="sxs-lookup"><span data-stu-id="852f2-114">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="852f2-115">Odstranění instance typu</span><span class="sxs-lookup"><span data-stu-id="852f2-115">Destruction of type instances</span></span>

<span data-ttu-id="852f2-116">Není nutné ke zničení dříve vytvořený typ instance.</span><span class="sxs-lookup"><span data-stu-id="852f2-116">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="852f2-117">Instance typů odkazu a hodnota jsou zničeny automaticky.</span><span class="sxs-lookup"><span data-stu-id="852f2-117">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="852f2-118">Poté, co je zničen kontext, který je obsahuje, jsou zničeny instancí typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="852f2-118">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="852f2-119">Instance typů odkazů, jsou zničeny podle [systému uvolňování paměti](../../../standard/garbage-collection/index.md) neurčené době po odebrání poslední odkazy na ně.</span><span class="sxs-lookup"><span data-stu-id="852f2-119">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="852f2-120">Pro typy, které obsahují nespravované prostředky například popisovač souboru, se doporučuje využívat deterministické čištění zajistit, že se prostředky, které obsahují vydávají co nejdříve.</span><span class="sxs-lookup"><span data-stu-id="852f2-120">For types that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="852f2-121">Další informace najdete v tématu <xref:System.IDisposable?displayProperty=nameWithType> reference k rozhraní API a [příkaz using](../keywords/using-statement.md) článku.</span><span class="sxs-lookup"><span data-stu-id="852f2-121">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="852f2-122">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="852f2-122">Operator overloadability</span></span>

<span data-ttu-id="852f2-123">Uživatelem definovaný typ nejde přetížit `new` operátor.</span><span class="sxs-lookup"><span data-stu-id="852f2-123">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="852f2-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="852f2-124">C# language specification</span></span>

<span data-ttu-id="852f2-125">Další informace najdete v tématu [operátor new](~/_csharplang/spec/expressions.md#the-new-operator) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="852f2-125">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="852f2-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="852f2-126">See also</span></span>

- [<span data-ttu-id="852f2-127">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="852f2-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="852f2-128">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="852f2-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="852f2-129">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="852f2-129">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
