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
ms.openlocfilehash: 999df9db0819a5f33e21a29b892de0a8854dd5d8
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028162"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8aa75-102">| – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8aa75-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="8aa75-103">Binární `|` pro integrální typy jsou předdefinované operátory a `bool`.</span><span class="sxs-lookup"><span data-stu-id="8aa75-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="8aa75-104">Pro integrální typy `|` vypočítá bitový OR jeho operandu.</span><span class="sxs-lookup"><span data-stu-id="8aa75-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="8aa75-105">Pro `bool` operandy, `|` vypočítá logický operátor OR operandů; to znamená, výsledek je `false` pouze v případě jsou oba operandy jeho `false`.</span><span class="sxs-lookup"><span data-stu-id="8aa75-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8aa75-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8aa75-106">Remarks</span></span>  
 <span data-ttu-id="8aa75-107">Binární soubor `|` operátor vyhodnotí oba operandy bez ohledu na to první hodnotu, oproti k [operátor podmíněného OR](conditional-or-operator.md) `||`.</span><span class="sxs-lookup"><span data-stu-id="8aa75-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator](conditional-or-operator.md) `||`.</span></span>
 
 <span data-ttu-id="8aa75-108">Lze přetěžovat uživatelsky definované typy `|` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="8aa75-108">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8aa75-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="8aa75-109">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8aa75-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="8aa75-110">See Also</span></span>

- [<span data-ttu-id="8aa75-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8aa75-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="8aa75-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8aa75-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8aa75-113">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8aa75-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
