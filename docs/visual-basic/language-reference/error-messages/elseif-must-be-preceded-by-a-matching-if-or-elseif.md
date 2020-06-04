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
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>Výrazu '#If' nebo '#ElseIf' musí předcházet odpovídající výraz '#ElseIf'.
`#ElseIf`je podmíněná direktiva kompilace. `#ElseIf`Před klauzulí musí předcházet párové `#If` `#ElseIf` klauzuli OR.  
  
 **ID chyby:** BC30014  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zajistěte, aby předchozí nebo nedošlo k tomu, že v rámci kterých se v rámci `#If` `#ElseIf` daného `#ElseIf` podmíněného kompilováného bloku nebo nesprávně nastavila `#End If` .  
  
2. Pokud `#ElseIf` předchází `#Else` direktiva, buď ji odeberte, `#Else` nebo ji změňte na `#ElseIf` .  
  
3. Pokud je vše jiného v daném pořadí, přidejte `#If` do začátku bloku podmíněné kompilace direktivu.  
  
## <a name="see-also"></a>Viz také

- [#If... Then... #Else – direktivy](../directives/if-then-else-directives.md)
