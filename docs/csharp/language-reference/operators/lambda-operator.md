---
title: = > – odkaz C# na operátora
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 5df1ae60ddc298f75d70db7769ec1bf1d21b8ef2
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239284"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2f534-102">= > – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="2f534-102">=> operator (C# reference)</span></span>

<span data-ttu-id="2f534-103">Token `=>` je podporován ve dvou formách: jako [operátor lambda](#lambda-operator) a jako oddělovač názvu člena a implementace člena v [definici těla výrazu](#expression-body-definition).</span><span class="sxs-lookup"><span data-stu-id="2f534-103">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="2f534-104">Lambda – operátor</span><span class="sxs-lookup"><span data-stu-id="2f534-104">Lambda operator</span></span>

<span data-ttu-id="2f534-105">Ve [výrazech lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)`=>` operátor lambda odděluje vstupní parametry na levé straně od těla lambda na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="2f534-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="2f534-106">Následující příklad používá funkci [LINQ](../../programming-guide/concepts/linq/index.md) s syntaxí Method k předvedení použití výrazů lambda:</span><span class="sxs-lookup"><span data-stu-id="2f534-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="2f534-107">Vstupní parametry výrazu lambda jsou silného typu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="2f534-107">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="2f534-108">Pokud kompilátor může odvodit typy vstupních parametrů, jako v předchozím příkladu, můžete vynechat deklarace typu.</span><span class="sxs-lookup"><span data-stu-id="2f534-108">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="2f534-109">Pokud potřebujete zadat typ vstupních parametrů, je nutné provést tento postup pro každý parametr, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="2f534-109">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="2f534-110">Následující příklad ukazuje, jak definovat výraz lambda bez vstupních parametrů:</span><span class="sxs-lookup"><span data-stu-id="2f534-110">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="2f534-111">Další informace naleznete v tématu [lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2f534-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="2f534-112">Definice těla výrazu</span><span class="sxs-lookup"><span data-stu-id="2f534-112">Expression body definition</span></span>

<span data-ttu-id="2f534-113">Definice těla výrazu má následující obecnou syntaxi:</span><span class="sxs-lookup"><span data-stu-id="2f534-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="2f534-114">kde `expression` je platný výraz.</span><span class="sxs-lookup"><span data-stu-id="2f534-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="2f534-115">Návratový typ `expression` musí být implicitně převoditelný na návratový typ člena.</span><span class="sxs-lookup"><span data-stu-id="2f534-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="2f534-116">Pokud je návratový typ člena `void` nebo je-li členem konstruktor, finalizační metoda nebo vlastnost přístupového objektu `set`, `expression` musí být [*výraz příkazu*](~/_csharplang/spec/statements.md#expression-statements), který může být libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="2f534-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements), which can be of any type.</span></span>

<span data-ttu-id="2f534-117">Následující příklad ukazuje definici těla výrazu pro `Person.ToString` metodu:</span><span class="sxs-lookup"><span data-stu-id="2f534-117">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="2f534-118">Tato definice metody je zkráceným zněním:</span><span class="sxs-lookup"><span data-stu-id="2f534-118">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="2f534-119">Definice textu výrazu pro metody, operátory a vlastnosti jen pro čtení jsou podporovány od C# 6.</span><span class="sxs-lookup"><span data-stu-id="2f534-119">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="2f534-120">Definice těla výrazu pro konstruktory, finalizační metody a vlastnosti a přistupující objekty indexeru jsou podporovány od C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="2f534-120">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="2f534-121">Další informace naleznete v tématu [Expression-těle Members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="2f534-121">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="2f534-122">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="2f534-122">Operator overloadability</span></span>

<span data-ttu-id="2f534-123">Operátor `=>` nemůže být přetížený.</span><span class="sxs-lookup"><span data-stu-id="2f534-123">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2f534-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2f534-124">C# language specification</span></span>

<span data-ttu-id="2f534-125">Další informace o operátoru lambda naleznete v části [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2f534-125">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2f534-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f534-126">See also</span></span>

- [<span data-ttu-id="2f534-127">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="2f534-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2f534-128">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2f534-128">C# operators</span></span>](index.md)
