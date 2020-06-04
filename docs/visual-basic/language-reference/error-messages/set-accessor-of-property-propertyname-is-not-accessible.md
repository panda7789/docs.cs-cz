---
title: Přístupový objekt 'Set' vlastnosti '<propertyname>' není dostupný.
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 077533a5b1fe241b61ded9516ad8f450d7dbbf5e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400341"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a>Přístupový objekt 'Set' vlastnosti '\<propertyname>' není dostupný.
Příkaz se pokusí uložit hodnotu vlastnosti, pokud nemá přístup k `Set` proceduře vlastnosti.  
  
 Pokud je [příkaz set](../statements/set-statement.md) označený s více omezující úrovní přístupu, než je jeho [příkaz Property](../statements/property-statement.md), pokus o nastavení hodnoty vlastnosti může selhat v následujících případech:  
  
- `Set`Příkaz je označen jako [Private](../modifiers/private.md) a volající kód je mimo třídu nebo strukturu, ve které je vlastnost definována.  
  
- `Set`Příkaz je označen jako [Protected](../modifiers/protected.md) a volající kód není ve třídě nebo struktuře, ve které je vlastnost definována, ani v odvozené třídě.  
  
- `Set`Příkaz je označen jako [Friend](../modifiers/friend.md) a volající kód není ve stejném sestavení, ve kterém je vlastnost definovaná.  
  
 **ID chyby:** BC31102  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud máte kontrolu nad zdrojovým kódem, který definuje vlastnost, zvažte deklaraci `Set` procedury se stejnou úrovní přístupu jako vlastnost samotnou.  
  
- Pokud nemáte kontrolu nad zdrojovým kódem, který definuje vlastnost, nebo je nutné omezit `Set` úroveň přístupu k proceduře více než samotnou vlastnost, zkuste přesunout příkaz, který nastaví hodnotu vlastnosti na oblast kódu, který má lepší přístup k vlastnosti.  
  
## <a name="see-also"></a>Viz také

- [Procedury vlastnosti](../../programming-guide/language-features/procedures/property-procedures.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
