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
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a>&#39;#ElseIf&#39; musí předcházet odpovídající &#39;#If&#39; nebo &#39;#ElseIf&#39;
`#ElseIf` představuje direktivu Podmíněná kompilace. `#ElseIf` Klauzule musí předcházet odpovídající `#If` nebo `#ElseIf` klauzule.  
  
 **ID chyby:** BC30014  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, že předchozím `#If` nebo `#ElseIf` nebyl rozdělené z tohoto `#ElseIf` bloku použité Podmíněná kompilace nebo nesprávně umístěné `#End If`.  
  
2.  Pokud `#ElseIf` předchází `#Else` – direktiva, buď odeberte `#Else` nebo změnit jeho `#ElseIf`.  
  
3.  Pokud všechno ostatní v pořadí, přidejte `#If` na začátek bloku Podmíněná kompilace.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
