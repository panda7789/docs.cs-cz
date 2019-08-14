---
title: = > – odkaz C# na operátora
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 3b3a5c2e96e92271da66cbd8f1039a9ec97544fa
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971223"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0d26d-102">= > – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="0d26d-102">=> operator (C# reference)</span></span>

<span data-ttu-id="0d26d-103">`=>` Token je podporován ve dvou formách: jako operátor lambda a jako oddělovač názvu člena a implementace člena v definici těla výrazu.</span><span class="sxs-lookup"><span data-stu-id="0d26d-103">The `=>` token is supported in two forms: as the lambda operator and as a separator of a member name and the member implementation in an expression body definition.</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="0d26d-104">Lambda – operátor</span><span class="sxs-lookup"><span data-stu-id="0d26d-104">Lambda operator</span></span>

<span data-ttu-id="0d26d-105">Ve [výrazech lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)operátor `=>` lambda odděluje vstupní proměnné na levé straně od těla lambda na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="0d26d-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input variables on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="0d26d-106">Následující příklad používá funkci [LINQ](../../programming-guide/concepts/linq/index.md) s syntaxí Method k předvedení použití výrazů lambda:</span><span class="sxs-lookup"><span data-stu-id="0d26d-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="0d26d-107">Vstupní proměnné výrazů lambda jsou silného typu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="0d26d-107">Input variables of lambda expressions are strongly typed at compile time.</span></span> <span data-ttu-id="0d26d-108">Když kompilátor může odvodit typy vstupních proměnných, jako v předchozím příkladu, můžete vynechat deklarace typu.</span><span class="sxs-lookup"><span data-stu-id="0d26d-108">When the compiler can infer the types of input variables, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="0d26d-109">Pokud potřebujete zadat typ vstupních proměnných, je nutné provést tento postup pro každou proměnnou, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="0d26d-109">If you need to specify the type of input variables, you must do that for each variable, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="0d26d-110">Následující příklad ukazuje, jak definovat výraz lambda bez vstupních proměnných:</span><span class="sxs-lookup"><span data-stu-id="0d26d-110">The following example shows how to define a lambda expression without input variables:</span></span>

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="0d26d-111">Další informace naleznete v tématu [lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0d26d-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="0d26d-112">Definice těla výrazu</span><span class="sxs-lookup"><span data-stu-id="0d26d-112">Expression body definition</span></span>

<span data-ttu-id="0d26d-113">Definice těla výrazu má následující obecnou syntaxi:</span><span class="sxs-lookup"><span data-stu-id="0d26d-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="0d26d-114">kde `expression` je platný výraz.</span><span class="sxs-lookup"><span data-stu-id="0d26d-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="0d26d-115">Návratový typ `expression` musí být implicitně převoditelný na návratový typ člena.</span><span class="sxs-lookup"><span data-stu-id="0d26d-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="0d26d-116">Pokud je `void` návratový typ člena nebo je-li členem konstruktor, finalizační metoda nebo vlastnost `set` přistupující objekt, `expression` musí být [*výraz příkazu*](~/_csharplang/spec/statements.md#expression-statements), který může být libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="0d26d-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements); it can be of any type then.</span></span>

<span data-ttu-id="0d26d-117">Následující příklad ukazuje definici těla výrazu pro `Person.ToString` metodu:</span><span class="sxs-lookup"><span data-stu-id="0d26d-117">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="0d26d-118">Tato definice metody je zkráceným zněním:</span><span class="sxs-lookup"><span data-stu-id="0d26d-118">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="0d26d-119">Definice textu výrazu pro metody a vlastnosti jen pro čtení jsou podporovány od C# 6.</span><span class="sxs-lookup"><span data-stu-id="0d26d-119">Expression body definitions for methods and read-only properties are supported starting with C# 6.</span></span> <span data-ttu-id="0d26d-120">Definice textu výrazu pro konstruktory, finalizační metody, přistupující objekty vlastnosti a indexery jsou podporovány od C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="0d26d-120">Expression body definitions for constructors, finalizers, property accessors, and indexers are supported starting with C# 7.0.</span></span>

<span data-ttu-id="0d26d-121">Další informace naleznete v tématu [Expression-těle Members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="0d26d-121">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="0d26d-122">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="0d26d-122">Operator overloadability</span></span>

<span data-ttu-id="0d26d-123">`=>` Operátor nemůže být přetížený.</span><span class="sxs-lookup"><span data-stu-id="0d26d-123">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0d26d-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0d26d-124">C# language specification</span></span>

<span data-ttu-id="0d26d-125">Další informace naleznete v části [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0d26d-125">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d26d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d26d-126">See also</span></span>

- [<span data-ttu-id="0d26d-127">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="0d26d-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0d26d-128">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0d26d-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="0d26d-129">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="0d26d-129">Lambda expressions</span></span>](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="0d26d-130">Členové tvoření výrazy</span><span class="sxs-lookup"><span data-stu-id="0d26d-130">Expression-bodied members</span></span>](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)
