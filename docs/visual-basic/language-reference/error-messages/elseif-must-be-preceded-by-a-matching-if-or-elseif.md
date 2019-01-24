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
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a>&#39;#ElseIf&#39; musí předcházet párový příkaz &#39;#If&#39; nebo &#39;#ElseIf&#39;
`#ElseIf` je direktivy podmíněné kompilace. `#ElseIf` Klauzule musí předcházet párový příkaz `#If` nebo `#ElseIf` klauzuli.  
  
 **ID chyby:** BC30014  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, že předchozí `#If` nebo `#ElseIf` nebyl byl oddělen od to `#ElseIf` použité bloku podmíněné kompilace nebo nesprávně umístěné `#End If`.  
  
2.  Pokud `#ElseIf` předchází `#Else` směrnice, buď odeberte `#Else` nebo změňte ji na `#ElseIf`.  
  
3.  Pokud všechno ostatní je v pořadí, přidejte `#If` na začátku bloku podmíněné kompilace.  
  
## <a name="see-also"></a>Viz také:
- [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
