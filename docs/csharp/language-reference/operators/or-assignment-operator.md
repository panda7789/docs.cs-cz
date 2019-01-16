---
title: '| = – operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: f4f7806c8679af400a371decd0c367929b3fb81d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333262"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ab71b-102">| = – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="ab71b-102">|= operator (C# Reference)</span></span>

<span data-ttu-id="ab71b-103">Operátor přiřazení OR.</span><span class="sxs-lookup"><span data-stu-id="ab71b-103">The OR assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab71b-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab71b-104">Remarks</span></span>

<span data-ttu-id="ab71b-105">Pomocí výrazu `|=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="ab71b-105">An expression using the `|=` assignment operator, such as</span></span>

```csharp
x |= y
```

<span data-ttu-id="ab71b-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="ab71b-106">is equivalent to</span></span>

```csharp
x = x | y
```

<span data-ttu-id="ab71b-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="ab71b-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="ab71b-108">[ &#124; Operátor](or-operator.md) provádí bitové logické OR operace na celočíselných operandech a logický operátor OR na operandech typu bool.</span><span class="sxs-lookup"><span data-stu-id="ab71b-108">The [&#124; operator](or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>

<span data-ttu-id="ab71b-109">`|=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [ &#124; operátor](or-operator.md) (naleznete v tématu [operátor](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="ab71b-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](or-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="ab71b-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab71b-110">Example</span></span>

[!code-csharp[csRefOperators#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#10)]

## <a name="see-also"></a><span data-ttu-id="ab71b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab71b-111">See also</span></span>

- [<span data-ttu-id="ab71b-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ab71b-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ab71b-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ab71b-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ab71b-114">C#operátory</span><span class="sxs-lookup"><span data-stu-id="ab71b-114">C# operators</span></span>](index.md)