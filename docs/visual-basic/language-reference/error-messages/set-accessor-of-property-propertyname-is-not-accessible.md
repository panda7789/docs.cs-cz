---
title: Přístupový objekt 'Set' vlastnosti '<propertyname>' není dostupný.
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 1539eb1652d93402c349c65f77a3edc65b3beb57
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277560"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a>Nastavte přistupující objekt vlastnosti '\<propertyname >' není dostupný
Příkaz se pokusí uložit hodnotu vlastnosti nemá přístup k vlastnosti `Set` postup.  
  
 Pokud [nastavit příkaz](../../../visual-basic/language-reference/statements/set-statement.md) je označená pomocí více omezující přístup k úrovni než jeho [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md), pokus o nastavení hodnoty vlastností by mohlo selhat v následujících případech:  
  
-   `Set` Označený příkaz [privátní](../../../visual-basic/language-reference/modifiers/private.md) a volající kód je mimo třídy nebo struktury, ve kterém je definována vlastnost.  
  
-   `Set` Označený příkaz [chráněné](../../../visual-basic/language-reference/modifiers/protected.md) a volající kód je v odvozené třídě, ani není v dané třídy nebo struktury, ve kterém je definována vlastnost.  
  
-   `Set` Označený příkaz [Friend](../../../visual-basic/language-reference/modifiers/friend.md) a volající kód není ve stejném sestavení, ve kterém je definována vlastnost.  
  
 **ID chyby:** BC31102  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud máte kontrolu nad zdrojový kód, který definuje vlastnost, vezměte v úvahu deklaraci `Set` postup se stejnou úrovní přístupu jako samotné vlastnosti.  
  
-   Pokud máte kontrolu nad zdrojový kód, který definuje vlastnost, nebo musíte omezit `Set` postup úroveň přístupu více, než se pokusí přesunout příkaz, který nastavuje hodnotu vlastnosti do oblasti kódu, který má lepší přístup k samotné, vlastnosti Vlastnost.  
  
## <a name="see-also"></a>Viz také:
- [Procedury vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
