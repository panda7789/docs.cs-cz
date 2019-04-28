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
ms.openlocfilehash: f218414bf60a86b95461d747fb6c557f03bcfcb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660447"
---
# <a name="typeof-c-reference"></a><span data-ttu-id="1f51b-102">typeof (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1f51b-102">typeof (C# Reference)</span></span>

<span data-ttu-id="1f51b-103">Používá k získání <xref:System.Type?displayProperty=nameWithType> pro typ objektu.</span><span class="sxs-lookup"><span data-stu-id="1f51b-103">Used to obtain the <xref:System.Type?displayProperty=nameWithType> object for a type.</span></span> <span data-ttu-id="1f51b-104">A `typeof` výrazu má následující podobu:</span><span class="sxs-lookup"><span data-stu-id="1f51b-104">A `typeof` expression takes the following form:</span></span>

```csharp
System.Type type = typeof(int);
```

## <a name="remarks"></a><span data-ttu-id="1f51b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f51b-105">Remarks</span></span>

<span data-ttu-id="1f51b-106">Pokud chcete získat run-time typu výrazu, můžete použít metodu rozhraní .NET Framework <xref:System.Object.GetType%2A>, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1f51b-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>

```csharp
int i = 0;
System.Type type = i.GetType();
```

<span data-ttu-id="1f51b-107">`typeof` Operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="1f51b-107">The `typeof` operator cannot be overloaded.</span></span>

<span data-ttu-id="1f51b-108">`typeof` Operátor můžete použít také u otevřených obecných typů.</span><span class="sxs-lookup"><span data-stu-id="1f51b-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="1f51b-109">Typy s více než jeden parametr typu musí mít odpovídající počet čárek ve specifikaci.</span><span class="sxs-lookup"><span data-stu-id="1f51b-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="1f51b-110">Například <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWIthType> má dva argumenty typu, proto použijete jednu čárku:</span><span class="sxs-lookup"><span data-stu-id="1f51b-110">For example, the <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWIthType> has two type arguments, so you use one comma:</span></span>

```csharp
Type t = typeof(System.Collection.Generic.Dictionary<,>);
```

<span data-ttu-id="1f51b-111">Následující příklad ukazuje, jak zjistit, jestli návratový typ metody je obecný <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="1f51b-111">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="1f51b-112"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> Vrátí `null` návratový typ není-li <xref:System.Collections.Generic.IEnumerable%601> obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1f51b-112"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> will return `null` if the return type is not an <xref:System.Collections.Generic.IEnumerable%601> generic type.</span></span>

[!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]

## <a name="example"></a><span data-ttu-id="1f51b-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f51b-113">Example</span></span>

[!code-csharp[csrefKeywordsOperator#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#12)] 

## <a name="example"></a><span data-ttu-id="1f51b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f51b-114">Example</span></span>

<span data-ttu-id="1f51b-115">Tento příklad používá <xref:System.Object.GetType%2A> metodu pro určení typu, který se používá pro jiné výsledek číselné výpočtu.</span><span class="sxs-lookup"><span data-stu-id="1f51b-115">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="1f51b-116">To závisí na požadavky na úložiště z výsledné číslo.</span><span class="sxs-lookup"><span data-stu-id="1f51b-116">This depends on the storage requirements of the resulting number.</span></span>

[!code-csharp[csrefKeywordsOperator#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#13)]

## <a name="c-language-specification"></a><span data-ttu-id="1f51b-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1f51b-117">C# language specification</span></span>

<span data-ttu-id="1f51b-118">Další informace najdete v tématu [operátor typeof](~/_csharplang/spec/expressions.md#the-typeof-operator) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f51b-118">For more information, see [The typeof operator](~/_csharplang/spec/expressions.md#the-typeof-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="1f51b-119">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="1f51b-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f51b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f51b-120">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- [<span data-ttu-id="1f51b-121">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1f51b-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="1f51b-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1f51b-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1f51b-123">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1f51b-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="1f51b-124">is</span><span class="sxs-lookup"><span data-stu-id="1f51b-124">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="1f51b-125">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="1f51b-125">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
