---
title: Výrazu '#If' nebo '#ElseIf' musí předcházet odpovídající výraz '#ElseIf'.
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: fbb8ce974a618349bd4b5e7a2a25a165d91787a7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832252"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a><span data-ttu-id="03fb6-102">Výrazu '#If' nebo '#ElseIf' musí předcházet odpovídající výraz '#ElseIf'.</span><span class="sxs-lookup"><span data-stu-id="03fb6-102">'#ElseIf' must be preceded by a matching '#If' or '#ElseIf'</span></span>
<span data-ttu-id="03fb6-103">`#ElseIf` je direktivy podmíněné kompilace.</span><span class="sxs-lookup"><span data-stu-id="03fb6-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="03fb6-104">`#ElseIf` Klauzule musí předcházet párový příkaz `#If` nebo `#ElseIf` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="03fb6-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>  
  
 <span data-ttu-id="03fb6-105">**ID chyby:** BC30014</span><span class="sxs-lookup"><span data-stu-id="03fb6-105">**Error ID:** BC30014</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="03fb6-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="03fb6-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="03fb6-107">Zkontrolujte, že předchozí `#If` nebo `#ElseIf` nebyl byl oddělen od to `#ElseIf` použité bloku podmíněné kompilace nebo nesprávně umístěné `#End If`.</span><span class="sxs-lookup"><span data-stu-id="03fb6-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>  
  
2.  <span data-ttu-id="03fb6-108">Pokud `#ElseIf` předchází `#Else` směrnice, buď odeberte `#Else` nebo změňte ji na `#ElseIf`.</span><span class="sxs-lookup"><span data-stu-id="03fb6-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>  
  
3.  <span data-ttu-id="03fb6-109">Pokud všechno ostatní je v pořadí, přidejte `#If` na začátku bloku podmíněné kompilace.</span><span class="sxs-lookup"><span data-stu-id="03fb6-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03fb6-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03fb6-110">See also</span></span>

- [<span data-ttu-id="03fb6-111">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="03fb6-111">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
