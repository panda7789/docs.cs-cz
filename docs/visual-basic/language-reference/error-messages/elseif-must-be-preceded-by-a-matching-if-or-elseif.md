---
title: '&#39;#ElseIf&#39; musí předcházet odpovídající &#39;#If&#39; nebo &#39;#ElseIf&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: ef904173b1791309f6c2722bd959cabdad1d71da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588145"
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a><span data-ttu-id="0e68b-102">&#39;#ElseIf&#39; musí předcházet odpovídající &#39;#If&#39; nebo &#39;#ElseIf&#39;</span><span class="sxs-lookup"><span data-stu-id="0e68b-102">&#39;#ElseIf&#39; must be preceded by a matching &#39;#If&#39; or &#39;#ElseIf&#39;</span></span>
<span data-ttu-id="0e68b-103">`#ElseIf` představuje direktivu Podmíněná kompilace.</span><span class="sxs-lookup"><span data-stu-id="0e68b-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="0e68b-104">`#ElseIf` Klauzule musí předcházet odpovídající `#If` nebo `#ElseIf` klauzule.</span><span class="sxs-lookup"><span data-stu-id="0e68b-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>  
  
 <span data-ttu-id="0e68b-105">**ID chyby:** BC30014</span><span class="sxs-lookup"><span data-stu-id="0e68b-105">**Error ID:** BC30014</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0e68b-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0e68b-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="0e68b-107">Zkontrolujte, že předchozím `#If` nebo `#ElseIf` nebyl rozdělené z tohoto `#ElseIf` bloku použité Podmíněná kompilace nebo nesprávně umístěné `#End If`.</span><span class="sxs-lookup"><span data-stu-id="0e68b-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>  
  
2.  <span data-ttu-id="0e68b-108">Pokud `#ElseIf` předchází `#Else` – direktiva, buď odeberte `#Else` nebo změnit jeho `#ElseIf`.</span><span class="sxs-lookup"><span data-stu-id="0e68b-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>  
  
3.  <span data-ttu-id="0e68b-109">Pokud všechno ostatní v pořadí, přidejte `#If` na začátek bloku Podmíněná kompilace.</span><span class="sxs-lookup"><span data-stu-id="0e68b-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e68b-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e68b-110">See Also</span></span>  
 [<span data-ttu-id="0e68b-111">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="0e68b-111">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
