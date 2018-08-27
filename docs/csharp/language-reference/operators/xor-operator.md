---
title: ^ – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: b1333f9d06e2804029550e6364a225558e096431
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925295"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8b76d-102">^ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8b76d-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="8b76d-103">Binární `^` pro integrální typy jsou předdefinované operátory a `bool`.</span><span class="sxs-lookup"><span data-stu-id="8b76d-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="8b76d-104">Pro integrální typy `^` vypočítá bitový exkluzivní operátor OR z operandů.</span><span class="sxs-lookup"><span data-stu-id="8b76d-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="8b76d-105">Pro `bool` operandy, `^` vypočítá exkluzivní logické- nebo z operandů; to znamená, výsledek je `true` pouze v případě právě jeden z operandů je `true`.</span><span class="sxs-lookup"><span data-stu-id="8b76d-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b76d-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b76d-106">Remarks</span></span>  
 <span data-ttu-id="8b76d-107">Lze přetěžovat uživatelsky definované typy `^` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="8b76d-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="8b76d-108">Operace interních typů jsou obecně povoleny na výčet.</span><span class="sxs-lookup"><span data-stu-id="8b76d-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b76d-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b76d-109">Example</span></span>  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 <span data-ttu-id="8b76d-110">Výpočet `0xf8 ^ 0x3f` v předchozím příkladu provádí logické bitové exkluzivní disjunkce OR následující dvě binárních hodnot, které odpovídají šestnáctkových hodnot F8 a 3F:</span><span class="sxs-lookup"><span data-stu-id="8b76d-110">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="8b76d-111">Výsledek exkluzivní disjunkce OR je `1100 0111`, který je kompatibilní s C7 v šestnáctkové soustavě.</span><span class="sxs-lookup"><span data-stu-id="8b76d-111">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b76d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b76d-112">See Also</span></span>

- [<span data-ttu-id="8b76d-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8b76d-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="8b76d-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8b76d-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8b76d-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8b76d-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
