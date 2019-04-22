---
title: Přístupový objekt 'Get' vlastnosti '<propertyname>' není dostupný.
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 8fb78f3c14708c79f1910e202287c25a3b2213b7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814403"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a>Získat přistupující objekt vlastnosti '\<propertyname >' není dostupný
Příkaz se pokusí načíst hodnotu vlastnosti, pokud nemá přístup k vlastnosti `Get` postup.  
  
 Pokud [získat příkaz](../../../visual-basic/language-reference/statements/get-statement.md) je označená pomocí více omezující přístup k úrovni než jeho [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md), pokus o čtení hodnoty vlastnosti by mohlo selhat v následujících případech:  
  
-   `Get` Označený příkaz [privátní](../../../visual-basic/language-reference/modifiers/private.md) a volající kód je mimo třídy nebo struktury, ve kterém je definována vlastnost.  
  
-   `Get` Označený příkaz [chráněné](../../../visual-basic/language-reference/modifiers/protected.md) a volající kód je v odvozené třídě, ani není v dané třídy nebo struktury, ve kterém je definována vlastnost.  
  
-   `Get` Označený příkaz [Friend](../../../visual-basic/language-reference/modifiers/friend.md) a volající kód není ve stejném sestavení, ve kterém je definována vlastnost.  
  
 **ID chyby:** BC31103  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud máte kontrolu nad zdrojový kód, který definuje vlastnost, vezměte v úvahu deklaraci `Get` postup se stejnou úrovní přístupu jako samotné vlastnosti.  
  
-   Pokud máte kontrolu nad zdrojový kód, který definuje vlastnost, nebo musíte omezit `Get` postup úroveň přístupu více, než se pokusí přesunout příkaz, který čte hodnoty vlastnosti do oblasti kódu, který má lepší přístup k samotné, vlastnosti Vlastnost.  
  
## <a name="see-also"></a>Viz také:

- [Procedury vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
