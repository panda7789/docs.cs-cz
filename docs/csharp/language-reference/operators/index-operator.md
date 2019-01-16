---
title: '[] – operátor - C# odkaz'
ms.custom: seodec18
ms.date: 01/10/2019
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 948ce238058307631cf0e5a7a5e3d72664233052
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333392"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="fb18a-102">[] – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="fb18a-102">[] operator (C# Reference)</span></span>

<span data-ttu-id="fb18a-103">Hranaté závorky, `[]`, se obvykle používají pro přístup k prvkům pole, indexovací člen nebo ukazatel.</span><span class="sxs-lookup"><span data-stu-id="fb18a-103">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

<span data-ttu-id="fb18a-104">Další informace o přístup k prvkům ukazatel, naleznete v tématu [postupy: přístup k elementu pole pomocí ukazatele](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="fb18a-104">For more information about pointer element access, see [How to: access an array element with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span></span>

<span data-ttu-id="fb18a-105">Můžete také použít hranaté závorky k určení [atributy](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="fb18a-105">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="array-access"></a><span data-ttu-id="fb18a-106">Přístup k poli</span><span class="sxs-lookup"><span data-stu-id="fb18a-106">Array access</span></span>

<span data-ttu-id="fb18a-107">Následující příklad ukazuje, jak přistupovat k prvkům pole:</span><span class="sxs-lookup"><span data-stu-id="fb18a-107">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Arrays)]

<span data-ttu-id="fb18a-108">Pokud pole indexu je mimo hranice odpovídající dimenze v poli, <xref:System.IndexOutOfRangeException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="fb18a-108">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="fb18a-109">Jak ukazuje předchozí příklad, také použít hranaté závorky v deklaraci typu pole a vytvoření instance pole instance.</span><span class="sxs-lookup"><span data-stu-id="fb18a-109">As the preceding example shows, you also use square brackets in declaration of an array type and instantiation of array instances.</span></span>

<span data-ttu-id="fb18a-110">Další informace o polích naleznete v tématu [pole](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb18a-110">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="indexer-access"></a><span data-ttu-id="fb18a-111">Přístup indexeru</span><span class="sxs-lookup"><span data-stu-id="fb18a-111">Indexer access</span></span>

<span data-ttu-id="fb18a-112">Následující příklad používá .NET <xref:System.Collections.Generic.Dictionary%602> typu k předvedení přístup indexeru:</span><span class="sxs-lookup"><span data-stu-id="fb18a-112">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Indexers)]

<span data-ttu-id="fb18a-113">Indexery umožňují index instance typu uživatelem definované v podobným způsobem jako indexování pole.</span><span class="sxs-lookup"><span data-stu-id="fb18a-113">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="fb18a-114">Na rozdíl od indexy pole, které musí být celé číslo, mohou být deklarovány argumenty indexeru být libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="fb18a-114">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="fb18a-115">Další informace o indexerech najdete v tématu [indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb18a-115">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="fb18a-116">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="fb18a-116">Operator overloadability</span></span>

<span data-ttu-id="fb18a-117">Přístup k prvkům `[]` není považováno za očekával se přetěžovatelný operátor.</span><span class="sxs-lookup"><span data-stu-id="fb18a-117">Element access `[]` is not considered an overloadable operator.</span></span> <span data-ttu-id="fb18a-118">Použití [indexery](../../programming-guide/indexers/index.md) pro podporu indexování pomocí uživatelem definovaných typů.</span><span class="sxs-lookup"><span data-stu-id="fb18a-118">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fb18a-119">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fb18a-119">C# language specification</span></span>

<span data-ttu-id="fb18a-120">Další informace najdete v tématu [přístup k prvkům](~/_csharplang/spec/expressions.md#element-access) a [přístup k prvkům ukazatel](~/_csharplang/spec/unsafe-code.md#pointer-element-access) oddíly [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb18a-120">For more information, see the [Element access](~/_csharplang/spec/expressions.md#element-access) and [Pointer element access](~/_csharplang/spec/unsafe-code.md#pointer-element-access) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb18a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb18a-121">See also</span></span>

- [<span data-ttu-id="fb18a-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fb18a-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fb18a-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fb18a-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fb18a-124">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fb18a-124">C# Operators</span></span>](index.md)
- [<span data-ttu-id="fb18a-125">Pole</span><span class="sxs-lookup"><span data-stu-id="fb18a-125">Arrays</span></span>](../../programming-guide/arrays/index.md)
- [<span data-ttu-id="fb18a-126">Indexery</span><span class="sxs-lookup"><span data-stu-id="fb18a-126">Indexers</span></span>](../../programming-guide/indexers/index.md)
- [<span data-ttu-id="fb18a-127">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="fb18a-127">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="fb18a-128">Atributy</span><span class="sxs-lookup"><span data-stu-id="fb18a-128">Attributes</span></span>](../../programming-guide/concepts/attributes/index.md)