---
title: Delegate – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
ms.openlocfilehash: f9df40c3ca721ca97b575a05377bbac29a29aec9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560604"
---
# <a name="delegate-c-reference"></a><span data-ttu-id="9a52a-102">delegate (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9a52a-102">delegate (C# Reference)</span></span>

<span data-ttu-id="9a52a-103">Deklarace typu delegáta je podobná signatuře metody.</span><span class="sxs-lookup"><span data-stu-id="9a52a-103">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="9a52a-104">Nemá návratovou hodnotu a libovolný počet parametrů typu:</span><span class="sxs-lookup"><span data-stu-id="9a52a-104">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void TestDelegate(string message);
public delegate int TestDelegate(MyType m, long num);
```

<span data-ttu-id="9a52a-105">A `delegate` je typem odkazu, který můžete použít k zapouzdření pojmenovaná nebo anonymní metodu.</span><span class="sxs-lookup"><span data-stu-id="9a52a-105">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="9a52a-106">Delegáti jsou podobní ukazatelům na funkci v jazyce C++; Delegáti jsou však typově bezpečné a zabezpečené.</span><span class="sxs-lookup"><span data-stu-id="9a52a-106">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="9a52a-107">Aplikace delegátů viz [delegáti](../../../csharp/programming-guide/delegates/index.md) a [obecných delegátů](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="9a52a-107">For applications of delegates, see [Delegates](../../../csharp/programming-guide/delegates/index.md) and [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="9a52a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a52a-108">Remarks</span></span>

<span data-ttu-id="9a52a-109">Delegáti jsou základem [události](../../../csharp/programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="9a52a-109">Delegates are the basis for [Events](../../../csharp/programming-guide/events/index.md).</span></span>

<span data-ttu-id="9a52a-110">Delegát může být vytvořena tím, že přidružíte buď pomocí pojmenovaných nebo anonymní metodu.</span><span class="sxs-lookup"><span data-stu-id="9a52a-110">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span> <span data-ttu-id="9a52a-111">Další informace najdete v tématu [metody s názvem](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) a [anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="9a52a-111">For more information, see [Named Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) and [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>

<span data-ttu-id="9a52a-112">Delegát musí být vytvořena pomocí metody nebo lambda výraz, který je kompatibilní návratový typ a vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="9a52a-112">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="9a52a-113">Další informace o stupeň odchylky, který je povolen v podpisu metody, naleznete v tématu [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="9a52a-113">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="9a52a-114">Pro použití s anonymní metody delegáta a kód k ní být přidruženo jsou deklarovány společně.</span><span class="sxs-lookup"><span data-stu-id="9a52a-114">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> <span data-ttu-id="9a52a-115">Oba způsoby konkretizujete delegátů jsou popsány v této části.</span><span class="sxs-lookup"><span data-stu-id="9a52a-115">Both ways of instantiating delegates are discussed in this section.</span></span>

## <a name="example"></a><span data-ttu-id="9a52a-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a52a-116">Example</span></span>

[!code-csharp[csrefKeywordsTypes#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="9a52a-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9a52a-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9a52a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a52a-118">See also</span></span>

- [<span data-ttu-id="9a52a-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9a52a-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="9a52a-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9a52a-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9a52a-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9a52a-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="9a52a-122">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="9a52a-122">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)
- [<span data-ttu-id="9a52a-123">Delegáti</span><span class="sxs-lookup"><span data-stu-id="9a52a-123">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="9a52a-124">Události</span><span class="sxs-lookup"><span data-stu-id="9a52a-124">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="9a52a-125">Delegáti s pojmenovanými vs. anonymními metodami</span><span class="sxs-lookup"><span data-stu-id="9a52a-125">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
- [<span data-ttu-id="9a52a-126">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="9a52a-126">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
- [<span data-ttu-id="9a52a-127">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="9a52a-127">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
