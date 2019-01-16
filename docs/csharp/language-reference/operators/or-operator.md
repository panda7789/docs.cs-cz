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
ms.openlocfilehash: 185ea3aabff4794ec08cca541773dbec3574ab4b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333509"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="78aa5-102">| – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="78aa5-102">| operator (C# Reference)</span></span>

<span data-ttu-id="78aa5-103">Binární `|` pro integrální typy jsou předdefinované operátory a `bool`.</span><span class="sxs-lookup"><span data-stu-id="78aa5-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="78aa5-104">Pro integrální typy `|` vypočítá bitový OR jeho operandu.</span><span class="sxs-lookup"><span data-stu-id="78aa5-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="78aa5-105">Pro `bool` operandy, `|` vypočítá logický operátor OR operandů; to znamená, výsledek je `false` pouze v případě jsou oba operandy jeho `false`.</span><span class="sxs-lookup"><span data-stu-id="78aa5-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="78aa5-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78aa5-106">Remarks</span></span>

<span data-ttu-id="78aa5-107">Binární soubor `|` operátor vyhodnotí oba operandy bez ohledu na to první hodnotu, oproti k [operátor podmíněného OR](conditional-or-operator.md) `||`.</span><span class="sxs-lookup"><span data-stu-id="78aa5-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator](conditional-or-operator.md) `||`.</span></span>

<span data-ttu-id="78aa5-108">Lze přetěžovat uživatelsky definované typy `|` – operátor (viz [operátor](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="78aa5-108">User-defined types can overload the `|` operator (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="78aa5-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="78aa5-109">Example</span></span>

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a><span data-ttu-id="78aa5-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78aa5-110">See also</span></span>

- [<span data-ttu-id="78aa5-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="78aa5-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="78aa5-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="78aa5-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="78aa5-113">C#operátory</span><span class="sxs-lookup"><span data-stu-id="78aa5-113">C# operators</span></span>](index.md)