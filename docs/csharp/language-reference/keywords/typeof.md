---
title: typeof – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 3fa82a6faee345be77fc8ea3f5aa3342adecb0f5
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244840"
---
# <a name="typeof-c-reference"></a><span data-ttu-id="1ed49-102">typeof (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1ed49-102">typeof (C# Reference)</span></span>

<span data-ttu-id="1ed49-103">Používá k získání <xref:System.Type?displayProperty=nameWithType> pro typ objektu.</span><span class="sxs-lookup"><span data-stu-id="1ed49-103">Used to obtain the <xref:System.Type?displayProperty=nameWithType> object for a type.</span></span> <span data-ttu-id="1ed49-104">A `typeof` výrazu má následující podobu:</span><span class="sxs-lookup"><span data-stu-id="1ed49-104">A `typeof` expression takes the following form:</span></span>

```csharp
System.Type type = typeof(int);
```

## <a name="remarks"></a><span data-ttu-id="1ed49-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ed49-105">Remarks</span></span>

<span data-ttu-id="1ed49-106">Pokud chcete získat run-time typu výrazu, můžete použít metodu rozhraní .NET Framework <xref:System.Object.GetType%2A>, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1ed49-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>

```csharp
int i = 0;
System.Type type = i.GetType();
```

<span data-ttu-id="1ed49-107">`typeof` Operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="1ed49-107">The `typeof` operator cannot be overloaded.</span></span>

<span data-ttu-id="1ed49-108">`typeof` Operátor můžete použít také u otevřených obecných typů.</span><span class="sxs-lookup"><span data-stu-id="1ed49-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="1ed49-109">Typy s více než jeden parametr typu musí mít odpovídající počet čárek ve specifikaci.</span><span class="sxs-lookup"><span data-stu-id="1ed49-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="1ed49-110">Následující příklad ukazuje, jak zjistit, jestli návratový typ metody je obecný <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="1ed49-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="1ed49-111"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> Vrátí `null` návratový typ není-li <xref:System.Collections.Generic.IEnumerable%601> obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1ed49-111"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> will return `null` if the return type is not an <xref:System.Collections.Generic.IEnumerable%601> generic type.</span></span>

[!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]

## <a name="example"></a><span data-ttu-id="1ed49-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ed49-112">Example</span></span>

[!code-csharp[csrefKeywordsOperator#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#12)] 

## <a name="example"></a><span data-ttu-id="1ed49-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ed49-113">Example</span></span>

<span data-ttu-id="1ed49-114">Tento příklad používá <xref:System.Object.GetType%2A> metodu pro určení typu, který se používá pro jiné výsledek číselné výpočtu.</span><span class="sxs-lookup"><span data-stu-id="1ed49-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="1ed49-115">To závisí na požadavky na úložiště z výsledné číslo.</span><span class="sxs-lookup"><span data-stu-id="1ed49-115">This depends on the storage requirements of the resulting number.</span></span>

[!code-csharp[csrefKeywordsOperator#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#13)]

## <a name="c-language-specification"></a><span data-ttu-id="1ed49-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1ed49-116">C# language specification</span></span>

<span data-ttu-id="1ed49-117">Další informace najdete v tématu [operátor typeof](~/_csharplang/spec/expressions.md#the-typeof-operator) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="1ed49-117">For more information, see [The typeof operator](~/_csharplang/spec/expressions.md#the-typeof-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="1ed49-118">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="1ed49-118">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ed49-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ed49-119">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- [<span data-ttu-id="1ed49-120">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1ed49-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="1ed49-121">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1ed49-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1ed49-122">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1ed49-122">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="1ed49-123">is</span><span class="sxs-lookup"><span data-stu-id="1ed49-123">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="1ed49-124">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="1ed49-124">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)