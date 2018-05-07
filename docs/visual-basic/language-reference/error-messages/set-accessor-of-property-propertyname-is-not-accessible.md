---
title: '&#39;Nastavit&#39; přistupujícího objektu vlastnosti &#39; &lt;propertyname&gt; &#39; není dostupný'
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: d047d03755de89d4740482db4845d5db72003ac0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39;Nastavit&#39; přistupujícího objektu vlastnosti &#39; &lt;propertyname&gt; &#39; není dostupný
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
 [Procedury vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
