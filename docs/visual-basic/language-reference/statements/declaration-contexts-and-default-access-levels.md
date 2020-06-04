---
title: Kontexty deklarace a výchozí úrovně přístupu
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: b5bb943a062ac648f88645fb6de1acb42213071c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404794"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Kontexty deklarace a výchozí úrovně přístupu (Visual Basic)
Toto téma popisuje, které typy Visual Basic lze deklarovat v rámci které jiné typy a na jaké úrovni přístupu jsou výchozí, pokud nejsou zadány.  
  
## <a name="declaration-context-levels"></a>Úrovně kontextu deklarace  
 *Kontext deklarace* programovacího prvku je oblast kódu, ve které je deklarována. Toto je často další programovací prvek, který se pak nazývá *obsahující element*.  
  
 Úrovně kontextů deklarace jsou následující:  
  
- *Úroveň oboru názvů* – v rámci zdrojového souboru nebo oboru názvů, ale ne v rámci třídy, struktury, modulu nebo rozhraní  
  
- *Úroveň modulu* – v rámci třídy, struktury, modulu nebo rozhraní, ale ne v rámci procedury nebo bloku  
  
- *Úroveň procedury* – v rámci procedury nebo bloku (například `If` nebo `For` )  
  
 V následující tabulce jsou uvedeny výchozí úrovně přístupu pro různé deklarované programovací prvky, v závislosti na kontextech deklarace.  
  
|Deklarovaný element|Úroveň oboru názvů|Úroveň modulu|Úroveň procedury|  
|----------------------|---------------------|------------------|---------------------|  
|Proměnná ([Dim – příkaz](dim-statement.md))|Nepovolené|`Private`( `Public` v `Structure` , není povoleno v `Interface` )|`Public`|  
|Konstanta ([příkaz const](const-statement.md))|Nepovolené|`Private`( `Public` v `Structure` , není povoleno v `Interface` )|`Public`|  
|Enumeration ([Enum – příkaz](enum-statement.md))|`Friend`|`Public`|Nepovolené|  
|Class –[příkaz (Class](class-statement.md))|`Friend`|`Public`|Nepovolené|  
|Structure ([příkaz struktury](structure-statement.md))|`Friend`|`Public`|Nepovolené|  
|Module ([příkaz Module](module-statement.md))|`Friend`|Nepovolené|Nepovolené|  
|Interface –[příkaz (Interface](interface-statement.md))|`Friend`|`Public`|Nepovolené|  
|Procedura ([příkaz Function](function-statement.md), [Sub Statement](sub-statement.md))|Nepovolené|`Public`|Nepovolené|  
|Externí odkaz ([deklarace příkazu](declare-statement.md))|Nepovolené|`Public`(není povoleno v nástroji `Interface` )|Nepovolené|  
|([Operátor příkazu](operator-statement.md)) – operátor|Nepovolené|`Public`(není povoleno v `Interface` OR `Module` )|Nepovolené|  
|Property – vlastnost ([příkaz](property-statement.md))|Nepovolené|`Public`|Nepovolené|  
|Výchozí vlastnost ([výchozí](../modifiers/default.md))|Nepovolené|`Public`(není povoleno v nástroji `Module` )|Nepovolené|  
|Event ([příkaz Event](event-statement.md))|Nepovolené|`Public`|Nepovolené|  
|Delegate ([delegát – příkaz](delegate-statement.md))|`Friend`|`Public`|Nepovolené|  
  
 Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Viz také

- [Friend](../modifiers/friend.md)
- [Hlášen](../modifiers/private.md)
- [Republik](../modifiers/public.md)
