---
title: Výrazu '#If' nebo '#ElseIf' musí předcházet odpovídající výraz '#ElseIf'.
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 808cf35fb05da092cdef560721b2f667778aa78f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409657"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a><span data-ttu-id="bd900-102">Výrazu '#If' nebo '#ElseIf' musí předcházet odpovídající výraz '#ElseIf'.</span><span class="sxs-lookup"><span data-stu-id="bd900-102">'#ElseIf' must be preceded by a matching '#If' or '#ElseIf'</span></span>
<span data-ttu-id="bd900-103">`#ElseIf`je podmíněná direktiva kompilace.</span><span class="sxs-lookup"><span data-stu-id="bd900-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="bd900-104">`#ElseIf`Před klauzulí musí předcházet párové `#If` `#ElseIf` klauzuli OR.</span><span class="sxs-lookup"><span data-stu-id="bd900-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>  
  
 <span data-ttu-id="bd900-105">**ID chyby:** BC30014</span><span class="sxs-lookup"><span data-stu-id="bd900-105">**Error ID:** BC30014</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bd900-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="bd900-106">To correct this error</span></span>  
  
1. <span data-ttu-id="bd900-107">Zajistěte, aby předchozí nebo nedošlo k tomu, že v rámci kterých se v rámci `#If` `#ElseIf` daného `#ElseIf` podmíněného kompilováného bloku nebo nesprávně nastavila `#End If` .</span><span class="sxs-lookup"><span data-stu-id="bd900-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>  
  
2. <span data-ttu-id="bd900-108">Pokud `#ElseIf` předchází `#Else` direktiva, buď ji odeberte, `#Else` nebo ji změňte na `#ElseIf` .</span><span class="sxs-lookup"><span data-stu-id="bd900-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>  
  
3. <span data-ttu-id="bd900-109">Pokud je vše jiného v daném pořadí, přidejte `#If` do začátku bloku podmíněné kompilace direktivu.</span><span class="sxs-lookup"><span data-stu-id="bd900-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd900-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd900-110">See also</span></span>

- [<span data-ttu-id="bd900-111">#If... Then... #Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="bd900-111">#If...Then...#Else Directives</span></span>](../directives/if-then-else-directives.md)
