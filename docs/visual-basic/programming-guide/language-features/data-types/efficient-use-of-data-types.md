---
title: Účinné používání datových typů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: e0cb67b4b26bf59b074bf5964f253c007fdbe719
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736166"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Účinné používání datových typů (Visual Basic)
Jsou přiřazeny nedeklarované proměnné a proměnné deklarované bez datový typ `Object` datového typu. To usnadňuje psaní programů rychle, ale může to způsobit je ke spuštění pomaleji.  
  
## <a name="strong-typing"></a>Silné typování  
 Určení typů dat pro všechny proměnné se označuje jako *silné typování*. Pomocí silných typů má několik výhod:  
  
-   Umožňuje podporu technologie IntelliSense pro proměnných. To umožňuje zobrazit jejich vlastnosti a ostatní členové při psaní v kódu.  
  
-   Využívá kontrola typu v kompilátoru. To zachycuje příkazy, které může selhat v době běhu z důvodu chyby jako např. přetečení. Také zachytí volání metod na objekty, které je nepodporují.  
  
-   To má za následek rychlejší provádění kódu.  
  
## <a name="most-efficient-data-types"></a>Nejúčinnější datové typy  
 Pro proměnné, které obsahují nikdy zlomky jsou účinnější než nonintegral typy celočíselnými datovými typy. V jazyce Visual Basic `Integer` a `UInteger` nejúčinnější číselné typy.  
  
 Pro desetinná čísla `Double` je nejúčinnější datového typu, protože procesory na aktuální platformy provádět operace s plovoucí desetinnou čárkou v dvojité přesnosti. Nicméně operace s `Double` nejsou tak rychle, stejně jako u celočíselných typů, jako `Integer`.  
  
## <a name="specifying-data-type"></a>Určení datového typu  
 Použití [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) k deklaraci proměnné určitého typu. Najednou můžete zadat jeho úroveň přístupu s použitím [veřejné](../../../../visual-basic/language-reference/modifiers/public.md), [chráněné](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), nebo [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo, jako v Následující příklad.  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>Převod znaků  
 `AscW` a `ChrW` funkce pracují v kódování Unicode. Jejich preference pro použití `Asc` a `Chr`, které musí překládat do proměnné a z kódování Unicode.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Číselné datové typy](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Používání atributu IntelliSense](/visualstudio/ide/using-intellisense)
