---
title: '[] – Operátor - C# odkaz'
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
ms.openlocfilehash: c464dab1ebf62d33b74c83b8d5c3c563fef4e77c
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307120"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d9ff9-102">[] – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d9ff9-102">[] Operator (C# Reference)</span></span>

<span data-ttu-id="d9ff9-103">Hranaté závorky, `[]`, se obvykle používají pro přístup k prvkům pole, indexovací člen nebo ukazatel.</span><span class="sxs-lookup"><span data-stu-id="d9ff9-103">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

<span data-ttu-id="d9ff9-104">Další informace o přístup k prvkům ukazatel, naleznete v tématu [postupy: přístup k elementu pole pomocí ukazatele](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="d9ff9-104">For more information about pointer element access, see [How to: access an array element with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).</span></span>

<span data-ttu-id="d9ff9-105">Můžete také použít hranaté závorky k určení [atributy](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="d9ff9-105">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="array-access"></a><span data-ttu-id="d9ff9-106">Přístup k poli</span><span class="sxs-lookup"><span data-stu-id="d9ff9-106">Array access</span></span>

<span data-ttu-id="d9ff9-107">Následující příklad ukazuje, jak přistupovat k prvkům pole:</span><span class="sxs-lookup"><span data-stu-id="d9ff9-107">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Arrays)]

<span data-ttu-id="d9ff9-108">Pokud pole indexu je mimo hranice odpovídající dimenze v poli, <xref:System.IndexOutOfRangeException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d9ff9-108">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="d9ff9-109">Jak ukazuje předchozí příklad, také použít hranaté závorky v deklaraci typu pole a vytvoření instance pole instance.</span><span class="sxs-lookup"><span data-stu-id="d9ff9-109">As the preceding example shows, you also use square brackets in declaration of an array type and instantiation of array instances.</span></span>

<span data-ttu-id="d9ff9-110">Další informace o polích naleznete v tématu [pole](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="d9ff9-110">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="indexer-access"></a><span data-ttu-id="d9ff9-111">Přístup indexeru</span><span class="sxs-lookup"><span data-stu-id="d9ff9-111">Indexer access</span></span>

<span data-ttu-id="d9ff9-112">Následující příklad používá .NET <xref:System.Collections.Generic.Dictionary%602> typu k předvedení přístup indexeru:</span><span class="sxs-lookup"><span data-stu-id="d9ff9-112">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Indexers)]

<span data-ttu-id="d9ff9-113">Indexery umožňují index instance typu uživatelem definované v podobným způsobem jako indexování pole.</span><span class="sxs-lookup"><span data-stu-id="d9ff9-113">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="d9ff9-114">Na rozdíl od indexy pole, které musí být celé číslo, mohou být deklarovány argumenty indexeru být libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="d9ff9-114">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="d9ff9-115">Další informace o indexerech najdete v tématu [indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="d9ff9-115">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="d9ff9-116">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="d9ff9-116">Operator overloadability</span></span>

<span data-ttu-id="d9ff9-117">Přístup k prvkům `[]` není považováno za očekával se přetěžovatelný operátor.</span><span class="sxs-lookup"><span data-stu-id="d9ff9-117">Element access `[]` is not considered an overloadable operator.</span></span> <span data-ttu-id="d9ff9-118">Použití [indexery](../../programming-guide/indexers/index.md) pro podporu indexování pomocí uživatelem definovaných typů.</span><span class="sxs-lookup"><span data-stu-id="d9ff9-118">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d9ff9-119">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d9ff9-119">C# language specification</span></span>

<span data-ttu-id="d9ff9-120">Další informace najdete v tématu [přístup k prvkům](~/_csharplang/spec/expressions.md#element-access) a [přístup k prvkům ukazatel](~/_csharplang/spec/unsafe-code.md#pointer-element-access) oddíly [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d9ff9-120">For more information, see the [Element access](~/_csharplang/spec/expressions.md#element-access) and [Pointer element access](~/_csharplang/spec/unsafe-code.md#pointer-element-access) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9ff9-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9ff9-121">See also</span></span>

- [<span data-ttu-id="d9ff9-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d9ff9-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d9ff9-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d9ff9-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d9ff9-124">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d9ff9-124">C# Operators</span></span>](index.md)
- [<span data-ttu-id="d9ff9-125">Pole</span><span class="sxs-lookup"><span data-stu-id="d9ff9-125">Arrays</span></span>](../../programming-guide/arrays/index.md)
- [<span data-ttu-id="d9ff9-126">Indexery</span><span class="sxs-lookup"><span data-stu-id="d9ff9-126">Indexers</span></span>](../../programming-guide/indexers/index.md)
- [<span data-ttu-id="d9ff9-127">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="d9ff9-127">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="d9ff9-128">Atributy</span><span class="sxs-lookup"><span data-stu-id="d9ff9-128">Attributes</span></span>](../../programming-guide/concepts/attributes/index.md)
