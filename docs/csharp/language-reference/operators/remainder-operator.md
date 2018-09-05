---
title: '% – operátor (Referenční dokumentace jazyka C#)'
ms.date: 04/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: 477f2491e6d2efe6b5c327efb371843d0bf12c26
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723870"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="78d97-102">% – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="78d97-102">% Operator (C# Reference)</span></span>
<span data-ttu-id="78d97-103">Operátor zbytku (`%`) vypočítá zbytek po dělení svůj první operand jeho sekundu.</span><span class="sxs-lookup"><span data-stu-id="78d97-103">The remainder operator (`%`) computes the remainder after dividing its first operand by its second.</span></span> <span data-ttu-id="78d97-104">Všechny číselné typy obsahuje předdefinované operátory zbytek.</span><span class="sxs-lookup"><span data-stu-id="78d97-104">All numeric types have predefined remainder operators.</span></span> 
  
## <a name="remarks"></a><span data-ttu-id="78d97-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78d97-105">Remarks</span></span>  
 <span data-ttu-id="78d97-106">Vzorec `a % b` vždy vrátí hodnotu v rozsahu `(-b, b)`exkluzivní (nikdy může vrátit `b` nebo `-b`), vedení znaménko podíl.</span><span class="sxs-lookup"><span data-stu-id="78d97-106">The formula `a % b` will always return a value on the range `(-b, b)`, exclusive (it can never return `b` or `-b`), keeping the sign of the dividend.</span></span> <span data-ttu-id="78d97-107">Operátor zbytku pro dělení celého čísla splňuje pravidlo `a % b = a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="78d97-107">For integer division, the remainder operator satisfies the rule `a % b = a - (a / b) * b`.</span></span>
  
 <span data-ttu-id="78d97-108">Toto je Nezaměňovat s canonical modulus, které splňuje pravidlo podobné, ale s floored dělení a vrací hodnoty v rozsahu `[0, b)`.</span><span class="sxs-lookup"><span data-stu-id="78d97-108">This is not to be confused with canonical modulus, which satisfies a similar rule but with floored division and returns values on the range `[0, b)`.</span></span> <span data-ttu-id="78d97-109">C# nemá operátor numerického zbytku canonical.</span><span class="sxs-lookup"><span data-stu-id="78d97-109">C# does not have an operator for canonical modulus.</span></span> <span data-ttu-id="78d97-110">Chování je však stejný pro pozitivní dividendy.</span><span class="sxs-lookup"><span data-stu-id="78d97-110">However, the behavior is the same for positive dividends.</span></span>
  
 <span data-ttu-id="78d97-111">Lze přetěžovat uživatelsky definované typy `%` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="78d97-111">User-defined types can overload the `%` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="78d97-112">Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="78d97-112">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78d97-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="78d97-113">Example</span></span>  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="78d97-114">Komentáře</span><span class="sxs-lookup"><span data-stu-id="78d97-114">Comments</span></span>  
 <span data-ttu-id="78d97-115">Všimněte si zaokrouhlovací chyby související s typem double.</span><span class="sxs-lookup"><span data-stu-id="78d97-115">Note the round-off errors associated with the double type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78d97-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="78d97-116">See Also</span></span>

- [<span data-ttu-id="78d97-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="78d97-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="78d97-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="78d97-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="78d97-119">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="78d97-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
