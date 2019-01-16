---
title: '* = – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 2038f3b55d46f3503496275b3d25b17663b8c1db
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333431"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9ea1e-102">\*= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9ea1e-102">\*= Operator (C# Reference)</span></span>

<span data-ttu-id="9ea1e-103">Operátor přiřazení binárního násobení.</span><span class="sxs-lookup"><span data-stu-id="9ea1e-103">The binary multiplication assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ea1e-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ea1e-104">Remarks</span></span>

<span data-ttu-id="9ea1e-105">Pomocí výrazu `*=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="9ea1e-105">An expression using the `*=` assignment operator, such as</span></span>

```csharp
x *= y
```

<span data-ttu-id="9ea1e-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="9ea1e-106">is equivalent to</span></span>

```csharp
x = x * y
```

<span data-ttu-id="9ea1e-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="9ea1e-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="9ea1e-108">[ \* Operátor](multiplication-operator.md) předdefinovaných číselných typů k provedení násobení.</span><span class="sxs-lookup"><span data-stu-id="9ea1e-108">The [\* operator](multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>

<span data-ttu-id="9ea1e-109">`*=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [ \* operátor](multiplication-operator.md) (naleznete v tématu [operátor](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="9ea1e-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [\* operator](multiplication-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="9ea1e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ea1e-110">Example</span></span>

[!code-csharp[csRefOperators#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#13)]

## <a name="see-also"></a><span data-ttu-id="9ea1e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ea1e-111">See also</span></span>

- [<span data-ttu-id="9ea1e-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9ea1e-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9ea1e-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9ea1e-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9ea1e-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9ea1e-114">C# Operators</span></span>](index.md)
