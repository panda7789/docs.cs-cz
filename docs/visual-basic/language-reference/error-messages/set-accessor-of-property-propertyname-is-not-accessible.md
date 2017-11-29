---
title: "& č. 39; & Nastavit č. 39; přistupující objekt vlastnosti & č. 39; &lt;propertyname&gt;& č. 39; není dostupný"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords: BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9256a09b719ad3890e1d7c2cc23ffb0d40eec62f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>& č. 39; & Nastavit č. 39; přistupující objekt vlastnosti & č. 39; &lt;propertyname&gt;& č. 39; není dostupný
Příkaz se pokusí uložit hodnota vlastnosti, pokud nemá přístup k vlastnosti `Set` postupu.  
  
 Pokud [příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md) je označen pro přístup k více omezující než úroveň jeho [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md), pokus o nastavení hodnoty vlastnosti může selhat v následujících případech:  
  
-   `Set` Je označena příkaz [privátní](../../../visual-basic/language-reference/modifiers/private.md) a kód volání je mimo třídu nebo strukturu, ve kterém je definovaný vlastnost.  
  
-   `Set` Je označena příkaz [chráněné](../../../visual-basic/language-reference/modifiers/protected.md) a volací kód nejsou v třídu nebo strukturu, ve kterém je definovaný vlastnost ani v odvozené třídě.  
  
-   `Set` Je označena příkaz [Friend](../../../visual-basic/language-reference/modifiers/friend.md) a kód volání není ve stejném sestavení, ve kterém je definovaný vlastnost.  
  
 **ID chyby:** BC31102  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud máte řízení zdrojového kódu definování vlastnost, vezměte v úvahu deklarace `Set` procedura s stejnou úroveň přístupu jako samotné vlastnosti.  
  
-   Pokud máte řízení zdrojového kódu definování vlastnost, nebo je třeba omezit `Set` postup úroveň přístupu, více než samotné, vlastnosti pokusem o přesun příkaz, který nastaví hodnotu vlastnosti na kód, který má lepší přístup k oblasti Vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [Procedury vlastností](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
