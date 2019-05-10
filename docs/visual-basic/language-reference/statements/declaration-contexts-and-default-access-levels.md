---
title: Kontexty deklarace a výchozí úrovně přístupu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: 05c2d6420526b660ead2f50eba7feb6b20524705
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623945"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Kontexty deklarace a výchozí úrovně přístupu (Visual Basic)
Toto téma popisuje typy jazyka Visual Basic, které mohou být deklarovány v rámci které typy a jaké úroveň přístupu ve výchozím nastavení, pokud není zadána.  
  
## <a name="declaration-context-levels"></a>Úrovně kontextu deklarace  
 *Kontext deklarace* programovací element je oblasti kódu, ve kterém je deklarována. To je často jiný programový element, který pak volá *obsahující element*.  
  
 Kontexty deklarace úrovně jsou následující:  
  
- *Úroveň Namespace* – v rámci zdrojového souboru nebo oboru názvů, ale není v rozsahu třídy, struktury, modul nebo rozhraní  
  
- *Úroveň modulu* – v rámci třídy, struktury, modul nebo rozhraní, ale ne v rámci proceduru nebo blok  
  
- *Úroveň procedury* – uvnitř procedury nebo bloku (jako například `If` nebo `For`)  
  
 V následující tabulce jsou uvedeny výchozí úrovně přístupu pro různé deklarovaný programový prvek, v závislosti na jejich kontexty deklarace.  
  
|Element deklarovaný|Úroveň Namespace|Úroveň modulu|Úroveň procedury|  
|----------------------|---------------------|------------------|---------------------|  
|Proměnné ([Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md))|Nepovoleno|`Private` (`Public` v `Structure`, není povoleno v `Interface`)|`Public`|  
|Konstanty ([Const – příkaz](../../../visual-basic/language-reference/statements/const-statement.md))|Nepovoleno|`Private` (`Public` v `Structure`, není povoleno v `Interface`)|`Public`|  
|Výčet ([Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|Nepovoleno|  
|Třídy ([Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|Nepovoleno|  
|Struktury ([struktury příkaz](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|Nepovoleno|  
|Modul ([Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|Nepovoleno|Nepovoleno|  
|Rozhraní ([Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|Nepovoleno|  
|Postup ([funkce příkaz](../../../visual-basic/language-reference/statements/function-statement.md), [dílčí příkaz](../../../visual-basic/language-reference/statements/sub-statement.md))|Nepovoleno|`Public`|Nepovoleno|  
|Externí odkaz ([deklaraci příkazu](../../../visual-basic/language-reference/statements/declare-statement.md))|Nepovoleno|`Public` (není povolené v `Interface`)|Nepovoleno|  
|– Operátor ([Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md))|Nepovoleno|`Public` (není povolené v `Interface` nebo `Module`)|Nepovoleno|  
|Vlastnosti ([Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md))|Nepovoleno|`Public`|Nepovoleno|  
|Výchozí vlastnost ([výchozí](../../../visual-basic/language-reference/modifiers/default.md))|Nepovoleno|`Public` (není povolené v `Module`)|Nepovoleno|  
|Události ([Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md))|Nepovoleno|`Public`|Nepovoleno|  
|Delegáta ([Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|Nepovoleno|  
  
 Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Viz také:

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
