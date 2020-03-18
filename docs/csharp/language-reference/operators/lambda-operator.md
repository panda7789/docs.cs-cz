---
title: = operátor> - odkaz Jazyka C#
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 15c02e11610866f359e3e3a7e2751ded918154b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846246"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="60e2a-102">= operátor> (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="60e2a-102">=> operator (C# reference)</span></span>

<span data-ttu-id="60e2a-103">Token `=>` je podporován ve dvou formách: jako [operátor lambda](#lambda-operator) a jako oddělovač názvu člena a implementace člena v [definici těla výrazu](#expression-body-definition).</span><span class="sxs-lookup"><span data-stu-id="60e2a-103">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="60e2a-104">Lambda operátor</span><span class="sxs-lookup"><span data-stu-id="60e2a-104">Lambda operator</span></span>

<span data-ttu-id="60e2a-105">V [lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md), lambda operátor `=>` odděluje vstupní parametry na levé straně od lambda těla na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="60e2a-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="60e2a-106">Následující příklad používá funkci [LINQ](../../programming-guide/concepts/linq/index.md) se syntaxí metody k předvedení použití výrazů lambda:</span><span class="sxs-lookup"><span data-stu-id="60e2a-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](snippets/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="60e2a-107">Vstupní parametry výrazu lambda jsou silně zadány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="60e2a-107">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="60e2a-108">Když kompilátor můžete odvodit typy vstupních parametrů, jako v předchozím příkladu, můžete vynechat deklarace typu.</span><span class="sxs-lookup"><span data-stu-id="60e2a-108">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="60e2a-109">Pokud potřebujete zadat typ vstupních parametrů, musíte to udělat pro každý parametr, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="60e2a-109">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](snippets/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="60e2a-110">Následující příklad ukazuje, jak definovat výraz lambda bez vstupních parametrů:</span><span class="sxs-lookup"><span data-stu-id="60e2a-110">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](snippets/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="60e2a-111">Další informace naleznete v tématu [Lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="60e2a-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="60e2a-112">Definice těla výrazu</span><span class="sxs-lookup"><span data-stu-id="60e2a-112">Expression body definition</span></span>

<span data-ttu-id="60e2a-113">Definice těla výrazu má následující obecnou syntaxi:</span><span class="sxs-lookup"><span data-stu-id="60e2a-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="60e2a-114">kde `expression` je platný výraz.</span><span class="sxs-lookup"><span data-stu-id="60e2a-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="60e2a-115">Návratový typ `expression` musí být implicitně převoditelný na návratový typ člena.</span><span class="sxs-lookup"><span data-stu-id="60e2a-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="60e2a-116">Pokud je návratový typ `void` člena nebo pokud je člen konstruktorem, `set` finalizační `expression` metoda nebo přistupující objekt vlastnosti musí být [*výraz emisi ,*](~/_csharplang/spec/statements.md#expression-statements)který může být libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="60e2a-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements), which can be of any type.</span></span>

<span data-ttu-id="60e2a-117">Následující příklad ukazuje definici těla výrazu pro metodu: `Person.ToString`</span><span class="sxs-lookup"><span data-stu-id="60e2a-117">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="60e2a-118">Jedná se o zkrácenou verzi následující definice metody:</span><span class="sxs-lookup"><span data-stu-id="60e2a-118">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="60e2a-119">Definice těla výrazu pro metody, operátory a vlastnosti jen pro čtení jsou podporovány počínaje C# 6.</span><span class="sxs-lookup"><span data-stu-id="60e2a-119">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="60e2a-120">Definice těla výrazu pro konstruktory, finalizační metody a přístupové objekty vlastností a indexeru jsou podporovány počínaje C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="60e2a-120">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="60e2a-121">Další informace naleznete v [tématu Expression-tělesně členy](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="60e2a-121">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="60e2a-122">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="60e2a-122">Operator overloadability</span></span>

<span data-ttu-id="60e2a-123">Operátor `=>` nemůže být přetížen.</span><span class="sxs-lookup"><span data-stu-id="60e2a-123">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="60e2a-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="60e2a-124">C# language specification</span></span>

<span data-ttu-id="60e2a-125">Další informace o operátoru lambda naleznete v části [Anonymní výrazy funkcí](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="60e2a-125">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="60e2a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="60e2a-126">See also</span></span>

- [<span data-ttu-id="60e2a-127">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="60e2a-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="60e2a-128">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="60e2a-128">C# operators</span></span>](index.md)
