---
title: "Kontexty deklarace a výchozí úrovně přístupu (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b89b74a6c0393f6a52a0b5c1ddf6f66c505564ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Kontexty deklarace a výchozí úrovně přístupu (Visual Basic)
Toto téma popisuje, jaké typy jazyka Visual Basic můžete deklarované v rámci které jiné typy a co jejich úrovně přístupu jako výchozí, pokud není zadána.  
  
## <a name="declaration-context-levels"></a>Deklarace kontextu úrovně  
 *Deklarace kontextu* programovací element je oblast kódu, ve kterém je deklarovaná. Tento problém je často jiné programovací element, který je pak volána *obsahující element*.  
  
 Úrovně pro kontexty deklarace jsou následující:  
  
-   *Úroveň Namespace* – v rámci zdrojový soubor nebo obor názvů, ale ne v rámci třídy, struktury, modul nebo rozhraní  
  
-   *Úroveň modulu* – v rámci třídy, struktury, modul nebo rozhraní, ale není uvnitř procedury nebo bloku  
  
-   *Úroveň procedury* – uvnitř procedury nebo bloku (jako například `If` nebo `For`)  
  
 Následující tabulka uvádí výchozí úrovně přístupu pro různé deklarované programovací elementy, v závislosti na jejich kontexty deklarace.  
  
|Deklarovaný element|Namespace úroveň|Úroveň modulu|Úroveň procedury|  
|----------------------|---------------------|------------------|---------------------|  
|Proměnné ([Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md))|Není povoleno|`Private`(`Public` v `Structure`, není povoleno v `Interface`)|`Public`|  
|Konstantní ([Const – příkaz](../../../visual-basic/language-reference/statements/const-statement.md))|Není povoleno|`Private`(`Public` v `Structure`, není povoleno v `Interface`)|`Public`|  
|Výčet ([Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|Není povoleno|  
|Třídy ([Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|Není povoleno|  
|Struktury ([struktury příkaz](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|Není povoleno|  
|Modul ([Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|Není povoleno|Není povoleno|  
|Rozhraní ([Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|Není povoleno|  
|Postup ([funkce příkaz](../../../visual-basic/language-reference/statements/function-statement.md), [Sub příkaz](../../../visual-basic/language-reference/statements/sub-statement.md))|Není povoleno|`Public`|Není povoleno|  
|Externí odkaz ([deklarovat příkaz](../../../visual-basic/language-reference/statements/declare-statement.md))|Není povoleno|`Public`(není povoleno v `Interface`)|Není povoleno|  
|Operátor ([Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md))|Není povoleno|`Public`(není povoleno v `Interface` nebo `Module`)|Není povoleno|  
|Vlastnost ([Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md))|Není povoleno|`Public`|Není povoleno|  
|Výchozí vlastnosti ([výchozí](../../../visual-basic/language-reference/modifiers/default.md))|Není povoleno|`Public`(není povoleno v `Module`)|Není povoleno|  
|Události ([Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md))|Není povoleno|`Public`|Není povoleno|  
|Delegát ([Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|Není povoleno|  
  
 Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Viz také  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Privátní](../../../visual-basic/language-reference/modifiers/private.md)  
 [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)
