---
title: "& č. 39; #ElseIf & č. 39; musí předcházet odpovídající & č. 39; #If & č. 39; nebo & č. 39; #ElseIf & č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b3a4e809e1108fcd6e116538a1947057e9548ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a>& č. 39; #ElseIf & č. 39; musí předcházet odpovídající & č. 39; #If & č. 39; nebo & č. 39; #ElseIf & č. 39;
`#ElseIf`představuje direktivu Podmíněná kompilace. `#ElseIf` Klauzule musí předcházet odpovídající `#If` nebo `#ElseIf` klauzule.  
  
 **ID chyby:** BC30014  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, že předchozím `#If` nebo `#ElseIf` nebyl rozdělené z tohoto `#ElseIf` bloku použité Podmíněná kompilace nebo nesprávně umístěné `#End If`.  
  
2.  Pokud `#ElseIf` předchází `#Else` – direktiva, buď odeberte `#Else` nebo změnit jeho `#ElseIf`.  
  
3.  Pokud všechno ostatní v pořadí, přidejte `#If` na začátek bloku Podmíněná kompilace.  
  
## <a name="see-also"></a>Viz také  
 [#If... Then... #Else – direktivy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
