---
title: '>>= – operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 8cc341c14ee1b90fde2abb369c187e57b4ce5c00
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278977"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="bfe82-102">>> = – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="bfe82-102">>>= operator (C# Reference)</span></span>

<span data-ttu-id="bfe82-103">Operátor přiřazení posunutí doprava.</span><span class="sxs-lookup"><span data-stu-id="bfe82-103">The right-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfe82-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bfe82-104">Remarks</span></span>

<span data-ttu-id="bfe82-105">Výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="bfe82-105">An expression of the form</span></span>

```csharp
x >>= y
```

<span data-ttu-id="bfe82-106">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="bfe82-106">is evaluated as</span></span>

```csharp
x = x >> y
```

<span data-ttu-id="bfe82-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="bfe82-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="bfe82-108">[>> Operátor](right-shift-operator.md) posune `x` přímo podle zadaného množství určené `y`.</span><span class="sxs-lookup"><span data-stu-id="bfe82-108">The [>> operator](right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>

<span data-ttu-id="bfe82-109">>> = Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [>> operátor](right-shift-operator.md) (naleznete v tématu [operátor](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="bfe82-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](right-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="bfe82-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="bfe82-110">Example</span></span>

[!code-csharp[csRefOperators#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#11)]

## <a name="see-also"></a><span data-ttu-id="bfe82-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bfe82-111">See also</span></span>

- [<span data-ttu-id="bfe82-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bfe82-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bfe82-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bfe82-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bfe82-114">C#operátory</span><span class="sxs-lookup"><span data-stu-id="bfe82-114">C# operators</span></span>](index.md)