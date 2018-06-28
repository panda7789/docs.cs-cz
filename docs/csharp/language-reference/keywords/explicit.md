---
title: Explicit – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: 66d271fdac0bad356ee0bafc1732e2f410854da1
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027938"
---
# <a name="explicit-c-reference"></a><span data-ttu-id="91480-102">explicit (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="91480-102">explicit (C# Reference)</span></span>

<span data-ttu-id="91480-103">`explicit` – Klíčové slovo deklaruje operátor převodu uživatelem definovaný typ, který musí být volána s přetypování.</span><span class="sxs-lookup"><span data-stu-id="91480-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span> <span data-ttu-id="91480-104">Tento operátor například převede ze třídy s názvem Fahrenheita na třídu s názvem c:</span><span class="sxs-lookup"><span data-stu-id="91480-104">For example, this operator converts from a class called Fahrenheit to a class called Celsius:</span></span>

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

<span data-ttu-id="91480-105">Tento operátor převodu nelze vyvolat takto:</span><span class="sxs-lookup"><span data-stu-id="91480-105">This conversion operator can be invoked like this:</span></span>

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

<span data-ttu-id="91480-106">Operátor převodu převede ze zdroje typu na typ cíle.</span><span class="sxs-lookup"><span data-stu-id="91480-106">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="91480-107">Typ zdroje poskytuje operátor převodu.</span><span class="sxs-lookup"><span data-stu-id="91480-107">The source type provides the conversion operator.</span></span> <span data-ttu-id="91480-108">Na rozdíl od implicitní převod musí být volána operátory explicitního převodu prostřednictvím přetypování.</span><span class="sxs-lookup"><span data-stu-id="91480-108">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="91480-109">Pokud operaci převodu může způsobit, že výjimky nebo dojít ke ztrátě informací, byste měli označit `explicit`.</span><span class="sxs-lookup"><span data-stu-id="91480-109">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="91480-110">Kompilátor zabrání bezobslužně vyvolání operaci převodu s pravděpodobně nepředpokládaného důsledky.</span><span class="sxs-lookup"><span data-stu-id="91480-110">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>

<span data-ttu-id="91480-111">Vynechání přetypování výsledky v chybě kompilace CS0266.</span><span class="sxs-lookup"><span data-stu-id="91480-111">Omitting the cast results in compile-time error CS0266.</span></span>

<span data-ttu-id="91480-112">Další informace najdete v tématu [použití operátorů převodu](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="91480-112">For more information, see [Using Conversion Operators](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="example"></a><span data-ttu-id="91480-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="91480-113">Example</span></span>

<span data-ttu-id="91480-114">Následující příklad uvádí `Fahrenheit` a `Celsius` třída, z nichž každý obsahuje operátor explicitní převod na jinou třídu.</span><span class="sxs-lookup"><span data-stu-id="91480-114">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a><span data-ttu-id="91480-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="91480-115">Example</span></span>

<span data-ttu-id="91480-116">V následujícím příkladu definuje struktury, `Digit`, která představuje jednu desítková číslice.</span><span class="sxs-lookup"><span data-stu-id="91480-116">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="91480-117">Operátor je definována pro převody z `byte` k `Digit`, ale protože ne všechny bajtů můžete převést na `Digit`, je explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="91480-117">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="91480-118">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="91480-118">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="91480-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91480-119">See also</span></span>

[<span data-ttu-id="91480-120">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="91480-120">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="91480-121">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="91480-121">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="91480-122">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="91480-122">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="91480-123">implicit</span><span class="sxs-lookup"><span data-stu-id="91480-123">implicit</span></span>](implicit.md)  
[<span data-ttu-id="91480-124">operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="91480-124">operator (C# Reference)</span></span>](operator.md)  
[<span data-ttu-id="91480-125">Postupy: Implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="91480-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
[<span data-ttu-id="91480-126">Zřetězené uživatelem definované explicitní převody v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="91480-126">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)  