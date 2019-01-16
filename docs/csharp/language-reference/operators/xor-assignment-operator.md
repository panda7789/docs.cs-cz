---
title: ^ = – operátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: 12189d6469a9716d3b7ebcffef23423a75692d1a
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333548"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="be018-102">^ = – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="be018-102">^= operator (C# Reference)</span></span>

<span data-ttu-id="be018-103">Operátor přiřazení exkluzivní disjunkce OR.</span><span class="sxs-lookup"><span data-stu-id="be018-103">The exclusive-OR assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="be018-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="be018-104">Remarks</span></span>

<span data-ttu-id="be018-105">Výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="be018-105">An expression of the form</span></span>

```csharp
x ^= y
```

<span data-ttu-id="be018-106">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="be018-106">is evaluated as</span></span>

```csharp
x = x ^ y
```

<span data-ttu-id="be018-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="be018-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="be018-108">[^ – Operátor](xor-operator.md) provádí bitový exkluzivní operátor OR operaci na celočíselných operandech a logické exkluzivní disjunkce OR na [bool](../keywords/bool.md) operandy.</span><span class="sxs-lookup"><span data-stu-id="be018-108">The [^ operator](xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../keywords/bool.md) operands.</span></span>

<span data-ttu-id="be018-109">^ = – Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [^ – operátor](xor-operator.md) (naleznete v tématu [operátor](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="be018-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](xor-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="be018-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="be018-110">Example</span></span>

[!code-csharp[csRefOperators#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#23)]

## <a name="see-also"></a><span data-ttu-id="be018-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be018-111">See also</span></span>

- [<span data-ttu-id="be018-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="be018-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="be018-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="be018-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="be018-114">C#operátory</span><span class="sxs-lookup"><span data-stu-id="be018-114">C# operators</span></span>](index.md)