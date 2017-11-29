---
title: "& č. 39; Get & č. 39; přistupující objekt vlastnosti & č. 39; &lt;propertyname&gt;& č. 39; není dostupný"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords: BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 167e040570af1fc78ce48f5e930e54981ba909ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>& č. 39; Get & č. 39; přistupující objekt vlastnosti & č. 39; &lt;propertyname&gt;& č. 39; není dostupný
Příkaz se pokusí načíst hodnotu vlastnosti, pokud nemá přístup k vlastnosti `Get` postupu.  
  
 Pokud [získat příkaz](../../../visual-basic/language-reference/statements/get-statement.md) je označen pro přístup k více omezující než úroveň jeho [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md), pokus o čtení hodnoty vlastnosti může selhat v následujících případech:  
  
-   `Get` Je označena příkaz [privátní](../../../visual-basic/language-reference/modifiers/private.md) a kód volání je mimo třídu nebo strukturu, ve kterém je definovaný vlastnost.  
  
-   `Get` Je označena příkaz [chráněné](../../../visual-basic/language-reference/modifiers/protected.md) a volací kód nejsou v třídu nebo strukturu, ve kterém je definovaný vlastnost ani v odvozené třídě.  
  
-   `Get` Je označena příkaz [Friend](../../../visual-basic/language-reference/modifiers/friend.md) a kód volání není ve stejném sestavení, ve kterém je definovaný vlastnost.  
  
 **ID chyby:** BC31103  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud máte řízení zdrojového kódu definování vlastnost, vezměte v úvahu deklarace `Get` procedura s stejnou úroveň přístupu jako samotné vlastnosti.  
  
-   Pokud máte řízení zdrojového kódu definování vlastnost, nebo je třeba omezit `Get` postup více, než se pokusí přesunout příkaz, který čte hodnota vlastnosti v oblasti kód, který má lepší přístup k samotné, vlastnosti úroveň přístupu Vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [Procedury vlastností](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
