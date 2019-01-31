---
title: << = – operátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: 0a005efa19be24f9adbf9031f562a30f9c1b0e34
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258731"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e0b9a-102">\<\<= – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="e0b9a-102">\<\<= operator (C# Reference)</span></span>

<span data-ttu-id="e0b9a-103">Operátor přiřazení posunutí doleva.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-103">The left-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0b9a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0b9a-104">Remarks</span></span>

<span data-ttu-id="e0b9a-105">Výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="e0b9a-105">An expression of the form</span></span>

```csharp
x <<= y
```

<span data-ttu-id="e0b9a-106">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="e0b9a-106">is evaluated as</span></span>

```csharp
x = x << y
```

<span data-ttu-id="e0b9a-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="e0b9a-108">[<< Operátor](left-shift-operator.md) posune `x` doleva o počet bitů určený `y`.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-108">The [<< operator](left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>

<span data-ttu-id="e0b9a-109">`<<=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [<< operátor](left-shift-operator.md) (naleznete v tématu [operátor](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="e0b9a-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](left-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="e0b9a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0b9a-110">Example</span></span>

[!code-csharp[csRefOperators#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#12)]

## <a name="see-also"></a><span data-ttu-id="e0b9a-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0b9a-111">See also</span></span>

- [<span data-ttu-id="e0b9a-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e0b9a-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e0b9a-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e0b9a-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e0b9a-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e0b9a-114">C# Operators</span></span>](index.md)
