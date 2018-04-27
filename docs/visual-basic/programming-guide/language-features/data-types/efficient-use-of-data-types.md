---
title: Účinné používání datových typů (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4cac585cdc3072d595d2446e1937678f9ab03335
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Účinné používání datových typů (Visual Basic)
Nedeklarovaný proměnných a proměnných deklarovaných bez datový typ přiřazené `Object` datového typu. To umožňuje snadno vytvářet programy rychle, ale může to způsobit je provést pomaleji.  
  
## <a name="strong-typing"></a>Silné typování  
 Určení typů dat pro všechny proměnné se označuje jako *silného typování*. Používání silného typování má několik výhod:  
  
-   Umožňuje podporu technologie IntelliSense pro proměnných. To umožňuje zobrazit jejich vlastnosti a ostatní členové jako typ v kódu.  
  
-   Provádí se kontrola typu kompilátoru. To zachytí příkazy, které může selhat v době běhu z důvodu chyby jako např. přetečení. Volání metody také zachytávalo na objekty, které je nepodporují.  
  
-   Výsledkem rychlejší provádění kódu.  
  
## <a name="most-efficient-data-types"></a>Nejúčinnější datové typy  
 Pro proměnné, které nikdy nesmí obsahovat zlomků jsou efektivnější než nonintegral typy integrální datové typy. V jazyce Visual Basic `Integer` a `UInteger` jsou nejúčinnější číselnými typy.  
  
 Pro desetinná čísla `Double` je nejúčinnější datového typu, protože procesory na aktuální platformy provádět operace s plovoucí desetinnou čárkou v dvojitou přesností. Ale operací s `Double` nejsou tak rychlý jako u celočíselných typů jako `Integer`.  
  
## <a name="specifying-data-type"></a>Určení datový typ  
 Použití [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarovat proměnnou určitého typu. Současně můžete zadat jeho úroveň přístupu pomocí [veřejné](../../../../visual-basic/language-reference/modifiers/public.md), [chráněné](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), nebo [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo, jako v Následující příklad.  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>Převod znaků  
 `AscW` a `ChrW` funkce pracovat v kódu Unicode. Používejte je preference do `Asc` a `Chr`, které musí překládat do a z kódování Unicode.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Číselné datové typy](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Používání atributu IntelliSense](/visualstudio/ide/using-intellisense)
