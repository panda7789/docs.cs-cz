---
title: Explicit – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 08/24/2018
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: a260c6f1ccac6e09770f1cb8f43d5d872b4b2650
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610105"
---
# <a name="explicit-c-reference"></a><span data-ttu-id="a6578-102">explicit (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a6578-102">explicit (C# Reference)</span></span>

<span data-ttu-id="a6578-103">`explicit` – Klíčové slovo deklaruje uživatelem definovaného typu operátoru převodu, který je nutné volat s přetypování.</span><span class="sxs-lookup"><span data-stu-id="a6578-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span>

<span data-ttu-id="a6578-104">Následující příklad definuje operátor, který převede z `Fahrenheit` třídu `Celsius` třídy.</span><span class="sxs-lookup"><span data-stu-id="a6578-104">The following example defines the operator that converts from a `Fahrenheit` class to a `Celsius` class.</span></span> <span data-ttu-id="a6578-105">Operátor musí být definovány uvnitř `Fahrenheit` třídy nebo `Celsius` třídy:</span><span class="sxs-lookup"><span data-stu-id="a6578-105">The operator must be defined either inside a `Fahrenheit` class or a `Celsius` class:</span></span>

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

<span data-ttu-id="a6578-106">Vyvolání definovaný převod operátorem přetypování, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="a6578-106">You invoke the defined conversion operator with a cast, as the following example shows:</span></span>

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

<span data-ttu-id="a6578-107">Operátor převodu převede zdrojový typ na typ cíle.</span><span class="sxs-lookup"><span data-stu-id="a6578-107">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="a6578-108">Zdrojový typ obsahuje operátor převodu.</span><span class="sxs-lookup"><span data-stu-id="a6578-108">The source type provides the conversion operator.</span></span> <span data-ttu-id="a6578-109">Na rozdíl od implicitních převodů je nutné explicitní operátory převodu volat pomocí přetypování.</span><span class="sxs-lookup"><span data-stu-id="a6578-109">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="a6578-110">Pokud operaci převodu může způsobit výjimky nebo dojít ke ztrátě informací, byste měli označit `explicit`.</span><span class="sxs-lookup"><span data-stu-id="a6578-110">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="a6578-111">To zabrání tomu, aby kompilátor tiše vyvolání operace převodu s může být nepředvídatelné následky.</span><span class="sxs-lookup"><span data-stu-id="a6578-111">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>

<span data-ttu-id="a6578-112">Vynechání výsledkem přetypování CS0266 chybu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="a6578-112">Omitting the cast results in compile-time error CS0266.</span></span>

<span data-ttu-id="a6578-113">Další informace najdete v tématu [použití operátorů převodu](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a6578-113">For more information, see [Using Conversion Operators](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="example"></a><span data-ttu-id="a6578-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6578-114">Example</span></span>

<span data-ttu-id="a6578-115">Následující příklad uvádí `Fahrenheit` a `Celsius` tříd, z nichž každý obsahuje explicitní operátor převodu na třídu.</span><span class="sxs-lookup"><span data-stu-id="a6578-115">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a><span data-ttu-id="a6578-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6578-116">Example</span></span>

<span data-ttu-id="a6578-117">V následujícím příkladu definuje strukturu, `Digit`, představující jednomístné číslo.</span><span class="sxs-lookup"><span data-stu-id="a6578-117">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="a6578-118">Operátor je definována pro převod z `byte` k `Digit`, ale protože ne všechny bajty mohou být převedeny do `Digit`, je explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="a6578-118">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="a6578-119">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a6578-119">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a6578-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6578-120">See also</span></span>

- [<span data-ttu-id="a6578-121">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a6578-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a6578-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a6578-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a6578-123">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a6578-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a6578-124">implicit</span><span class="sxs-lookup"><span data-stu-id="a6578-124">implicit</span></span>](implicit.md)
- [<span data-ttu-id="a6578-125">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="a6578-125">Operator overloading</span></span>](../operators/operator-overloading.md)
- [<span data-ttu-id="a6578-126">Postupy: Implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="a6578-126">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
- [<span data-ttu-id="a6578-127">Zřetězit uživatelem definované explicitní převody v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a6578-127">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
