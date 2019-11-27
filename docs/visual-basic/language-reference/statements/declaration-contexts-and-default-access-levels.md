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
ms.openlocfilehash: 1ba25d830b1e7529bdf09c1195cc1fe7f9b2243b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354106"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Kontexty deklarace a výchozí úrovně přístupu (Visual Basic)
Toto téma popisuje, které typy Visual Basic lze deklarovat v rámci které jiné typy a na jaké úrovni přístupu jsou výchozí, pokud nejsou zadány.  
  
## <a name="declaration-context-levels"></a>Úrovně kontextu deklarace  
 *Kontext deklarace* programovacího prvku je oblast kódu, ve které je deklarována. Toto je často další programovací prvek, který se pak nazývá *obsahující element*.  
  
 Úrovně kontextů deklarace jsou následující:  
  
- *Úroveň oboru názvů* – v rámci zdrojového souboru nebo oboru názvů, ale ne v rámci třídy, struktury, modulu nebo rozhraní  
  
- *Úroveň modulu* – v rámci třídy, struktury, modulu nebo rozhraní, ale ne v rámci procedury nebo bloku  
  
- *Úroveň procedury* – v rámci procedury nebo bloku (například `If` nebo `For`)  
  
 V následující tabulce jsou uvedeny výchozí úrovně přístupu pro různé deklarované programovací prvky, v závislosti na kontextech deklarace.  
  
|Deklarovaný element|Úroveň oboru názvů|Úroveň modulu|Úroveň procedury|  
|----------------------|---------------------|------------------|---------------------|  
|Proměnná ([Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md))|Není povoleno|`Private` (`Public` v `Structure`, není povoleno v `Interface`)|`Public`|  
|Konstanta ([příkaz const](../../../visual-basic/language-reference/statements/const-statement.md))|Není povoleno|`Private` (`Public` v `Structure`, není povoleno v `Interface`)|`Public`|  
|Enumeration ([Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|Není povoleno|  
|Class –[příkaz (Class](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|Není povoleno|  
|Structure ([příkaz struktury](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|Není povoleno|  
|Module ([příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|Není povoleno|Není povoleno|  
|Interface –[příkaz (Interface](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|Není povoleno|  
|Procedura ([příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md), [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md))|Není povoleno|`Public`|Není povoleno|  
|Externí odkaz ([deklarace příkazu](../../../visual-basic/language-reference/statements/declare-statement.md))|Není povoleno|`Public` (není povoleno v `Interface`)|Není povoleno|  
|([Operátor příkazu](../../../visual-basic/language-reference/statements/operator-statement.md)) – operátor|Není povoleno|`Public` (není povoleno v `Interface` nebo `Module`)|Není povoleno|  
|Property – vlastnost ([příkaz](../../../visual-basic/language-reference/statements/property-statement.md))|Není povoleno|`Public`|Není povoleno|  
|Výchozí vlastnost ([výchozí](../../../visual-basic/language-reference/modifiers/default.md))|Není povoleno|`Public` (není povoleno v `Module`)|Není povoleno|  
|Event ([příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md))|Není povoleno|`Public`|Není povoleno|  
|Delegate ([delegát – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|Není povoleno|  
  
 Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Viz také:

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
