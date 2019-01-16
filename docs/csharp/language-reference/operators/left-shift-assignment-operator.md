---
title: '&lt;&lt;= – operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: 4513c4b78dea3e8102c72a43249b4a44ffa2421d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333249"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="79584-102">&lt;&lt;= – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="79584-102">&lt;&lt;= operator (C# Reference)</span></span>

<span data-ttu-id="79584-103">Operátor přiřazení posunutí doleva.</span><span class="sxs-lookup"><span data-stu-id="79584-103">The left-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="79584-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79584-104">Remarks</span></span>

<span data-ttu-id="79584-105">Výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="79584-105">An expression of the form</span></span>

```csharp
x <<= y
```

<span data-ttu-id="79584-106">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="79584-106">is evaluated as</span></span>

```csharp
x = x << y
```

<span data-ttu-id="79584-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="79584-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="79584-108">[<< Operátor](left-shift-operator.md) posune `x` doleva o počet bitů určený `y`.</span><span class="sxs-lookup"><span data-stu-id="79584-108">The [<< operator](left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>

<span data-ttu-id="79584-109">`<<=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [<< operátor](left-shift-operator.md) (naleznete v tématu [operátor](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="79584-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](left-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="79584-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="79584-110">Example</span></span>

[!code-csharp[csRefOperators#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#12)]

## <a name="see-also"></a><span data-ttu-id="79584-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79584-111">See also</span></span>

- [<span data-ttu-id="79584-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="79584-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="79584-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="79584-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="79584-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="79584-114">C# Operators</span></span>](index.md)
