---
title: '| Operator - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 38f8e21dbd07868441e0c4fbb6074f9897905222
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312875"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c2cdd-102">| – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="c2cdd-102">| operator (C# Reference)</span></span>

<span data-ttu-id="c2cdd-103">Binární `|` pro integrální typy jsou předdefinované operátory a `bool`.</span><span class="sxs-lookup"><span data-stu-id="c2cdd-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="c2cdd-104">Pro integrální typy `|` vypočítá bitový OR jeho operandu.</span><span class="sxs-lookup"><span data-stu-id="c2cdd-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="c2cdd-105">Pro `bool` operandy, `|` vypočítá logický operátor OR operandů; to znamená, výsledek je `false` pouze v případě jsou oba operandy jeho `false`.</span><span class="sxs-lookup"><span data-stu-id="c2cdd-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c2cdd-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2cdd-106">Remarks</span></span>

<span data-ttu-id="c2cdd-107">Binární soubor `|` operátor vyhodnotí oba operandy bez ohledu na to první hodnotu, oproti k [operátor podmíněného OR](boolean-logical-operators.md#conditional-logical-or-operator-) `||`.</span><span class="sxs-lookup"><span data-stu-id="c2cdd-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator](boolean-logical-operators.md#conditional-logical-or-operator-) `||`.</span></span>

<span data-ttu-id="c2cdd-108">Lze přetěžovat uživatelsky definované typy `|` – operátor (viz [operátor](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="c2cdd-108">User-defined types can overload the `|` operator (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="c2cdd-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2cdd-109">Example</span></span>

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a><span data-ttu-id="c2cdd-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2cdd-110">See also</span></span>

- [<span data-ttu-id="c2cdd-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c2cdd-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c2cdd-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c2cdd-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c2cdd-113">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c2cdd-113">C# operators</span></span>](index.md)