---
title: Nový operátor – C# referenční informace
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: beb55f0765e7f9090f0587f1d2a06cf03ea90ab8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712660"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="4da1d-102">New – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="4da1d-102">new operator (C# reference)</span></span>

<span data-ttu-id="4da1d-103">Operátor `new` vytvoří novou instanci typu.</span><span class="sxs-lookup"><span data-stu-id="4da1d-103">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="4da1d-104">Můžete také použít klíčové slovo `new` jako [Modifikátor deklarace člena](../keywords/new-modifier.md) nebo [omezení obecného typu](../keywords/new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="4da1d-104">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="4da1d-105">Vyvolání konstruktoru</span><span class="sxs-lookup"><span data-stu-id="4da1d-105">Constructor invocation</span></span>

<span data-ttu-id="4da1d-106">Chcete-li vytvořit novou instanci typu, obvykle vyvoláte jeden z [konstruktorů](../../programming-guide/classes-and-structs/constructors.md) tohoto typu pomocí operátoru `new`:</span><span class="sxs-lookup"><span data-stu-id="4da1d-106">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

<span data-ttu-id="4da1d-107">Můžete použít [inicializátor objektu nebo kolekce](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) s operátorem `new` pro vytvoření instance a inicializaci objektu v jednom příkazu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="4da1d-107">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="4da1d-108">Vytvoření pole</span><span class="sxs-lookup"><span data-stu-id="4da1d-108">Array creation</span></span>

<span data-ttu-id="4da1d-109">Také operátor `new` slouží k vytvoření instance pole, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="4da1d-109">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

<span data-ttu-id="4da1d-110">Pomocí syntaxe inicializace pole vytvořte instanci pole a naplňte ji prvky v jednom příkazu.</span><span class="sxs-lookup"><span data-stu-id="4da1d-110">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="4da1d-111">Následující příklad ukazuje různé způsoby, jak to lze provést:</span><span class="sxs-lookup"><span data-stu-id="4da1d-111">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="4da1d-112">Další informace o polích naleznete v tématu [Arrays](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="4da1d-112">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="4da1d-113">Vytváření instancí anonymních typů</span><span class="sxs-lookup"><span data-stu-id="4da1d-113">Instantiation of anonymous types</span></span>

<span data-ttu-id="4da1d-114">Chcete-li vytvořit instanci [anonymního typu](../../programming-guide/classes-and-structs/anonymous-types.md), použijte operátor `new` a syntaxi inicializátoru objektu:</span><span class="sxs-lookup"><span data-stu-id="4da1d-114">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="4da1d-115">Zničení instancí typů</span><span class="sxs-lookup"><span data-stu-id="4da1d-115">Destruction of type instances</span></span>

<span data-ttu-id="4da1d-116">Nemusíte zničit dřívější vytvořené instance typu.</span><span class="sxs-lookup"><span data-stu-id="4da1d-116">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="4da1d-117">Instance obou typů odkaz i hodnota jsou zničeny automaticky.</span><span class="sxs-lookup"><span data-stu-id="4da1d-117">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="4da1d-118">Instance typů hodnot jsou zničeny ihned po zničení kontextu, který je obsahuje.</span><span class="sxs-lookup"><span data-stu-id="4da1d-118">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="4da1d-119">Instance typů odkazů jsou zničeny systémem [uvolňování paměti](../../../standard/garbage-collection/index.md) v nespecifikovaném čase po odebrání posledního odkazu na ně.</span><span class="sxs-lookup"><span data-stu-id="4da1d-119">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="4da1d-120">U instancí typu, které obsahují nespravované prostředky, například popisovač souboru, se doporučuje použít deterministické vyčištění, aby bylo zajištěno, že prostředky, které obsahují, budou zveřejněny co nejdříve.</span><span class="sxs-lookup"><span data-stu-id="4da1d-120">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="4da1d-121">Další informace najdete v tématu Reference k rozhraní API <xref:System.IDisposable?displayProperty=nameWithType> a v článku o [příkazu Using](../keywords/using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="4da1d-121">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4da1d-122">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="4da1d-122">Operator overloadability</span></span>

<span data-ttu-id="4da1d-123">Uživatelsky definovaný typ nemůže přetížit operátor `new`.</span><span class="sxs-lookup"><span data-stu-id="4da1d-123">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4da1d-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4da1d-124">C# language specification</span></span>

<span data-ttu-id="4da1d-125">Další informace najdete v části [Nový operátor](~/_csharplang/spec/expressions.md#the-new-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="4da1d-125">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4da1d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4da1d-126">See also</span></span>

- [<span data-ttu-id="4da1d-127">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="4da1d-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4da1d-128">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4da1d-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="4da1d-129">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="4da1d-129">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
