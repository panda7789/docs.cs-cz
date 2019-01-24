---
title: '&#39;#ElseIf&#39; musí předcházet párový příkaz &#39;#If&#39; nebo &#39;#ElseIf&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 1e63595ee573e9356f6870a02b2131897c725baf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505780"
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a><span data-ttu-id="97d70-102">&#39;#ElseIf&#39; musí předcházet párový příkaz &#39;#If&#39; nebo &#39;#ElseIf&#39;</span><span class="sxs-lookup"><span data-stu-id="97d70-102">&#39;#ElseIf&#39; must be preceded by a matching &#39;#If&#39; or &#39;#ElseIf&#39;</span></span>
<span data-ttu-id="97d70-103">`#ElseIf` je direktivy podmíněné kompilace.</span><span class="sxs-lookup"><span data-stu-id="97d70-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="97d70-104">`#ElseIf` Klauzule musí předcházet párový příkaz `#If` nebo `#ElseIf` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="97d70-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>  
  
 <span data-ttu-id="97d70-105">**ID chyby:** BC30014</span><span class="sxs-lookup"><span data-stu-id="97d70-105">**Error ID:** BC30014</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="97d70-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="97d70-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="97d70-107">Zkontrolujte, že předchozí `#If` nebo `#ElseIf` nebyl byl oddělen od to `#ElseIf` použité bloku podmíněné kompilace nebo nesprávně umístěné `#End If`.</span><span class="sxs-lookup"><span data-stu-id="97d70-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>  
  
2.  <span data-ttu-id="97d70-108">Pokud `#ElseIf` předchází `#Else` směrnice, buď odeberte `#Else` nebo změňte ji na `#ElseIf`.</span><span class="sxs-lookup"><span data-stu-id="97d70-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>  
  
3.  <span data-ttu-id="97d70-109">Pokud všechno ostatní je v pořadí, přidejte `#If` na začátku bloku podmíněné kompilace.</span><span class="sxs-lookup"><span data-stu-id="97d70-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d70-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97d70-110">See also</span></span>
- [<span data-ttu-id="97d70-111">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="97d70-111">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
