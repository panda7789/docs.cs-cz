---
description: New – operátor – reference jazyka C#
title: New – operátor – reference jazyka C#
ms.date: 06/25/2019
f1_keywords:
- new_CSharpKeyword
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 88ec929317d4e6c6651233c1a1aa0ce8a8cce611
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118270"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="043e6-103">New – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="043e6-103">new operator (C# reference)</span></span>

<span data-ttu-id="043e6-104">`new`Operátor vytvoří novou instanci typu.</span><span class="sxs-lookup"><span data-stu-id="043e6-104">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="043e6-105">Klíčové slovo lze použít také `new` jako [Modifikátor deklarace člena](../keywords/new-modifier.md) nebo [omezení obecného typu](../keywords/new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="043e6-105">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="043e6-106">Vyvolání konstruktoru</span><span class="sxs-lookup"><span data-stu-id="043e6-106">Constructor invocation</span></span>

<span data-ttu-id="043e6-107">Chcete-li vytvořit novou instanci typu, obvykle vyvoláte jeden z [konstruktorů](../../programming-guide/classes-and-structs/constructors.md) tohoto typu pomocí `new` operátoru:</span><span class="sxs-lookup"><span data-stu-id="043e6-107">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](snippets/shared/NewOperator.cs#Constructor)]

<span data-ttu-id="043e6-108">Můžete použít [inicializátor objektu nebo kolekce](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) s `new` operátorem pro vytvoření instance a inicializaci objektu v jednom příkazu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="043e6-108">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](snippets/shared/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="043e6-109">Vytvoření pole</span><span class="sxs-lookup"><span data-stu-id="043e6-109">Array creation</span></span>

<span data-ttu-id="043e6-110">Operátor můžete také použít `new` k vytvoření instance pole, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="043e6-110">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](snippets/shared/NewOperator.cs#Array)]

<span data-ttu-id="043e6-111">Pomocí syntaxe inicializace pole vytvořte instanci pole a naplňte ji prvky v jednom příkazu.</span><span class="sxs-lookup"><span data-stu-id="043e6-111">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="043e6-112">Následující příklad ukazuje různé způsoby, jak to lze provést:</span><span class="sxs-lookup"><span data-stu-id="043e6-112">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](snippets/shared/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="043e6-113">Další informace o polích naleznete v tématu [Arrays](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="043e6-113">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="043e6-114">Vytváření instancí anonymních typů</span><span class="sxs-lookup"><span data-stu-id="043e6-114">Instantiation of anonymous types</span></span>

<span data-ttu-id="043e6-115">Chcete-li vytvořit instanci [anonymního typu](../../programming-guide/classes-and-structs/anonymous-types.md), použijte `new` syntaxi inicializátoru operátoru a objektu:</span><span class="sxs-lookup"><span data-stu-id="043e6-115">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](snippets/shared/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="043e6-116">Zničení instancí typů</span><span class="sxs-lookup"><span data-stu-id="043e6-116">Destruction of type instances</span></span>

<span data-ttu-id="043e6-117">Nemusíte zničit dřívější vytvořené instance typu.</span><span class="sxs-lookup"><span data-stu-id="043e6-117">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="043e6-118">Instance obou typů odkaz i hodnota jsou zničeny automaticky.</span><span class="sxs-lookup"><span data-stu-id="043e6-118">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="043e6-119">Instance typů hodnot jsou zničeny ihned po zničení kontextu, který je obsahuje.</span><span class="sxs-lookup"><span data-stu-id="043e6-119">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="043e6-120">Instance typů odkazů jsou zničeny systémem [uvolňování paměti](../../../standard/garbage-collection/index.md) v některém nespecifikovaném čase po odebrání posledního odkazu na ně.</span><span class="sxs-lookup"><span data-stu-id="043e6-120">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at some unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="043e6-121">U instancí typu, které obsahují nespravované prostředky, například popisovač souboru, se doporučuje použít deterministické vyčištění, aby bylo zajištěno, že prostředky, které obsahují, budou zveřejněny co nejdříve.</span><span class="sxs-lookup"><span data-stu-id="043e6-121">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="043e6-122">Další informace najdete v tématu <xref:System.IDisposable?displayProperty=nameWithType> Reference k rozhraní API a v článku o [příkazu Using](../keywords/using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="043e6-122">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="043e6-123">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="043e6-123">Operator overloadability</span></span>

<span data-ttu-id="043e6-124">Uživatelsky definovaný typ nemůže přetížit `new` operátor.</span><span class="sxs-lookup"><span data-stu-id="043e6-124">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="043e6-125">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="043e6-125">C# language specification</span></span>

<span data-ttu-id="043e6-126">Další informace naleznete v části [New operator](~/_csharplang/spec/expressions.md#the-new-operator) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="043e6-126">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="043e6-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="043e6-127">See also</span></span>

- [<span data-ttu-id="043e6-128">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="043e6-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="043e6-129">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="043e6-129">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="043e6-130">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="043e6-130">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
