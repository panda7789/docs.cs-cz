---
title: Výrazu '#If' nebo '#ElseIf' musí předcházet odpovídající výraz '#ElseIf'.
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 4832fb80cfbe42c7a1303e0de69f36784711c05a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803360"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>Výrazu '#If' nebo '#ElseIf' musí předcházet odpovídající výraz '#ElseIf'.
`#ElseIf` je direktivy podmíněné kompilace. `#ElseIf` Klauzule musí předcházet párový příkaz `#If` nebo `#ElseIf` klauzuli.  
  
 **ID chyby:** BC30014  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zkontrolujte, že předchozí `#If` nebo `#ElseIf` nebyl byl oddělen od to `#ElseIf` použité bloku podmíněné kompilace nebo nesprávně umístěné `#End If`.  
  
2. Pokud `#ElseIf` předchází `#Else` směrnice, buď odeberte `#Else` nebo změňte ji na `#ElseIf`.  
  
3. Pokud všechno ostatní je v pořadí, přidejte `#If` na začátku bloku podmíněné kompilace.  
  
## <a name="see-also"></a>Viz také:

- [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
