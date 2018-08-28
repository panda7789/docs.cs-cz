---
title: '| – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: d95fe29aa7ffab9938e8edc57999445268fe41a8
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001227"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3d1cc-102">| – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3d1cc-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="3d1cc-103">Binární `|` pro integrální typy jsou předdefinované operátory a `bool`.</span><span class="sxs-lookup"><span data-stu-id="3d1cc-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="3d1cc-104">Pro integrální typy `|` vypočítá bitový OR jeho operandu.</span><span class="sxs-lookup"><span data-stu-id="3d1cc-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="3d1cc-105">Pro `bool` operandy, `|` vypočítá logický operátor OR operandů; to znamená, výsledek je `false` pouze v případě jsou oba operandy jeho `false`.</span><span class="sxs-lookup"><span data-stu-id="3d1cc-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d1cc-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d1cc-106">Remarks</span></span>  
 <span data-ttu-id="3d1cc-107">Binární soubor `|` operátor vyhodnotí oba operandy bez ohledu na to první hodnotu, na rozdíl od [operátor podmíněného OR] (podmíněné nebo operator.md) `||`.</span><span class="sxs-lookup"><span data-stu-id="3d1cc-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator]     (conditional-or-operator.md) `||`.</span></span>
 
 <span data-ttu-id="3d1cc-108">Lze přetěžovat uživatelsky definované typy `|` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="3d1cc-108">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d1cc-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="3d1cc-109">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3d1cc-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d1cc-110">See Also</span></span>

- [<span data-ttu-id="3d1cc-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3d1cc-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="3d1cc-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3d1cc-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3d1cc-113">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3d1cc-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
