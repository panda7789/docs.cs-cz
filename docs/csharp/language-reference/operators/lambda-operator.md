---
title: = > – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 0cded9d23d67e6afc8b01d6711e42759b4b51fab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689148"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f6e59-102">= > – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="f6e59-102">=> operator (C# Reference)</span></span>

<span data-ttu-id="f6e59-103">`=>` Token je podporován ve dvou formách: jako operátor lambda a jako oddělovač názvu členu a implementace členu v definici tělo výrazu.</span><span class="sxs-lookup"><span data-stu-id="f6e59-103">The `=>` token is supported in two forms: as the lambda operator and as a separator of a member name and the member implementation in an expression body definition.</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="f6e59-104">Lambda – operátor</span><span class="sxs-lookup"><span data-stu-id="f6e59-104">Lambda operator</span></span>

<span data-ttu-id="f6e59-105">V [výrazy lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md), operátor lambda `=>` odděluje vstupních proměnných na levé straně od hlavní část výrazu lambda na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="f6e59-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input variables on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="f6e59-106">V následujícím příkladu [LINQ](../../programming-guide/concepts/linq/index.md) funkce pomocí syntaxe metody k předvedení použití lambda výrazů:</span><span class="sxs-lookup"><span data-stu-id="f6e59-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#InferredTypes)]

<span data-ttu-id="f6e59-107">Vstupních proměnných, výrazů lambda jsou silného typu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="f6e59-107">Input variables of lambda expressions are strongly typed at compile time.</span></span> <span data-ttu-id="f6e59-108">Když kompilátor může odvodit typ vstupních proměnných, stejně jako v předchozím příkladu, můžete vynechat deklarace typů.</span><span class="sxs-lookup"><span data-stu-id="f6e59-108">When the compiler can infer the types of input variables, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="f6e59-109">Pokud je třeba zadat typ vstupních proměnných, je nutné použít pro každou proměnnou, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f6e59-109">If you need to specify the type of input variables, you must do that for each variable, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#ExplicitTypes)]

<span data-ttu-id="f6e59-110">Následující příklad ukazuje, jak definovat výraz lambda bez vstupních proměnných:</span><span class="sxs-lookup"><span data-stu-id="f6e59-110">The following example shows how to define a lambda expression without input variables:</span></span>

[!code-csharp-interactive[without input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#WithoutInput)]

<span data-ttu-id="f6e59-111">Další informace najdete v tématu [výrazy Lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f6e59-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="f6e59-112">Definice textu výrazu</span><span class="sxs-lookup"><span data-stu-id="f6e59-112">Expression body definition</span></span>

<span data-ttu-id="f6e59-113">Definice těla výrazu má následující obecnou syntaxi:</span><span class="sxs-lookup"><span data-stu-id="f6e59-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="f6e59-114">kde *výraz* je platný výraz.</span><span class="sxs-lookup"><span data-stu-id="f6e59-114">where *expression* is a valid expression.</span></span> <span data-ttu-id="f6e59-115">Všimněte si, že *výraz* může být *výrazu příkazu* pouze pokud je člen návratový typ je `void`, nebo pokud je člen konstruktoru, finalizační metodu nebo vlastnost `set` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="f6e59-115">Note that *expression* can be a *statement expression* only if the member's return type is `void`, or if the member is a constructor, a finalizer, or a property `set` accessor.</span></span>

<span data-ttu-id="f6e59-116">Následující příklad ukazuje definici tělo výrazu pro `Person.ToString` metody:</span><span class="sxs-lookup"><span data-stu-id="f6e59-116">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="f6e59-117">Je zkrácená verze následující definici metody:</span><span class="sxs-lookup"><span data-stu-id="f6e59-117">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="f6e59-118">Definice těla výrazu pro metody a vlastnosti jen pro čtení jsou podporovány od verze C# 6.</span><span class="sxs-lookup"><span data-stu-id="f6e59-118">Expression body definitions for methods and read-only properties are supported starting with C# 6.</span></span> <span data-ttu-id="f6e59-119">Definice těla výrazu pro konstruktory, finalizační metody, přistupující objekty vlastnosti a indexery jsou podporovány od verze C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="f6e59-119">Expression body definitions for constructors, finalizers, property accessors, and indexers are supported starting with C# 7.0.</span></span>

<span data-ttu-id="f6e59-120">Další informace najdete v tématu [členové tvoření](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="f6e59-120">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="f6e59-121">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="f6e59-121">Operator overloadability</span></span>

<span data-ttu-id="f6e59-122">`=>` Operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="f6e59-122">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f6e59-123">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f6e59-123">C# language specification</span></span>

<span data-ttu-id="f6e59-124">Další informace najdete v tématu [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f6e59-124">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6e59-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6e59-125">See also</span></span>

- [<span data-ttu-id="f6e59-126">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f6e59-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f6e59-127">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f6e59-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f6e59-128">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f6e59-128">C# Operators</span></span>](index.md)
- [<span data-ttu-id="f6e59-129">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="f6e59-129">Lambda expressions</span></span>](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="f6e59-130">Členové tvoření výrazy</span><span class="sxs-lookup"><span data-stu-id="f6e59-130">Expression-bodied members</span></span>](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)