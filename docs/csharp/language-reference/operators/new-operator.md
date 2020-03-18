---
title: nový operátor - odkaz Jazyka C#
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 84131bc503a106961419a27fc4e3e0f2d82306a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846230"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="d4f8a-102">nový operátor (odkaz C# )</span><span class="sxs-lookup"><span data-stu-id="d4f8a-102">new operator (C# reference)</span></span>

<span data-ttu-id="d4f8a-103">Operátor `new` vytvoří novou instanci typu.</span><span class="sxs-lookup"><span data-stu-id="d4f8a-103">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="d4f8a-104">Klíčové slovo můžete také použít jako [modifikátor deklarace člena](../keywords/new-modifier.md) nebo [omezení obecného typu](../keywords/new-constraint.md). `new`</span><span class="sxs-lookup"><span data-stu-id="d4f8a-104">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="d4f8a-105">Vyvolání konstruktoru</span><span class="sxs-lookup"><span data-stu-id="d4f8a-105">Constructor invocation</span></span>

<span data-ttu-id="d4f8a-106">Chcete-li vytvořit novou instanci typu, obvykle vyvolat jeden z [konstruktorů](../../programming-guide/classes-and-structs/constructors.md) tohoto typu pomocí operátoru: `new`</span><span class="sxs-lookup"><span data-stu-id="d4f8a-106">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](snippets/NewOperator.cs#Constructor)]

<span data-ttu-id="d4f8a-107">[Inicializátor objektu nebo](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) `new` kolekce s operátorem můžete použít k vytvoření instance a inicializaci objektu v jednom příkazu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="d4f8a-107">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](snippets/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="d4f8a-108">Vytvoření pole</span><span class="sxs-lookup"><span data-stu-id="d4f8a-108">Array creation</span></span>

<span data-ttu-id="d4f8a-109">`new` Operátor můžete také použít k vytvoření instance pole, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="d4f8a-109">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](snippets/NewOperator.cs#Array)]

<span data-ttu-id="d4f8a-110">Pomocí syntaxe inicializace pole vytvořte instanci pole a naplňte ji prvky v jednom příkazu.</span><span class="sxs-lookup"><span data-stu-id="d4f8a-110">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="d4f8a-111">Následující příklad ukazuje různé způsoby, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="d4f8a-111">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](snippets/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="d4f8a-112">Další informace o polích naleznete v [tématu Arrays](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="d4f8a-112">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="d4f8a-113">Vytváření instancí anonymních typů</span><span class="sxs-lookup"><span data-stu-id="d4f8a-113">Instantiation of anonymous types</span></span>

<span data-ttu-id="d4f8a-114">Chcete-li vytvořit instanci [anonymního typu](../../programming-guide/classes-and-structs/anonymous-types.md), použijte syntaxi inicializačního operátoru `new` a objektu:</span><span class="sxs-lookup"><span data-stu-id="d4f8a-114">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](snippets/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="d4f8a-115">Zničení instancí typu</span><span class="sxs-lookup"><span data-stu-id="d4f8a-115">Destruction of type instances</span></span>

<span data-ttu-id="d4f8a-116">Není třeba zničit dříve vytvořené instance typu.</span><span class="sxs-lookup"><span data-stu-id="d4f8a-116">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="d4f8a-117">Instance referenčních i hodnotových typů jsou automaticky zničeny.</span><span class="sxs-lookup"><span data-stu-id="d4f8a-117">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="d4f8a-118">Instance typů hodnot jsou zničeny, jakmile je zničen kontext, který je obsahuje.</span><span class="sxs-lookup"><span data-stu-id="d4f8a-118">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="d4f8a-119">Instance typů odkazů jsou zničeny [systémem uvolňování paměti](../../../standard/garbage-collection/index.md) v neurčeném čase po odebrání posledního odkazu na ně.</span><span class="sxs-lookup"><span data-stu-id="d4f8a-119">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="d4f8a-120">Pro instance typu, které obsahují nespravované prostředky, například popisovač souboru, se doporučuje použít deterministické vyčištění, aby bylo zajištěno, že prostředky, které obsahují, budou vydány co nejdříve.</span><span class="sxs-lookup"><span data-stu-id="d4f8a-120">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="d4f8a-121">Další informace naleznete <xref:System.IDisposable?displayProperty=nameWithType> v odkazu rozhraní API a [using prohlášení](../keywords/using-statement.md) článku.</span><span class="sxs-lookup"><span data-stu-id="d4f8a-121">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="d4f8a-122">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="d4f8a-122">Operator overloadability</span></span>

<span data-ttu-id="d4f8a-123">Uživatelem definovaný typ nemůže `new` přetížit operátor.</span><span class="sxs-lookup"><span data-stu-id="d4f8a-123">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d4f8a-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d4f8a-124">C# language specification</span></span>

<span data-ttu-id="d4f8a-125">Další informace naleznete [v části Nový operátor](~/_csharplang/spec/expressions.md#the-new-operator) specifikace jazyka [C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d4f8a-125">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4f8a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4f8a-126">See also</span></span>

- [<span data-ttu-id="d4f8a-127">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="d4f8a-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d4f8a-128">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d4f8a-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="d4f8a-129">Inicializátory objektů a kolekcí</span><span class="sxs-lookup"><span data-stu-id="d4f8a-129">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
