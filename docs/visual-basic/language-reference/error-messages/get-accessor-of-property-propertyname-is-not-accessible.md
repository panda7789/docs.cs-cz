---
title: Přístupový objekt 'Get' vlastnosti '<propertyname>' není dostupný.
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: cb953671e624d5b9170aa0b3a9dd80c7ba8337e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402911"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a>Přístupový objekt 'Get' vlastnosti '\<propertyname>' není dostupný.
Příkaz se pokusí načíst hodnotu vlastnosti, pokud nemá přístup k `Get` proceduře vlastnosti.  
  
 Pokud je [příkaz Get](../statements/get-statement.md) označen s více omezující úrovní přístupu, než je jeho [příkaz Property](../statements/property-statement.md), pokus o čtení hodnoty vlastnosti může selhat v následujících případech:  
  
- `Get`Příkaz je označen jako [Private](../modifiers/private.md) a volající kód je mimo třídu nebo strukturu, ve které je vlastnost definována.  
  
- `Get`Příkaz je označen jako [Protected](../modifiers/protected.md) a volající kód není ve třídě nebo struktuře, ve které je vlastnost definována, ani v odvozené třídě.  
  
- `Get`Příkaz je označen jako [Friend](../modifiers/friend.md) a volající kód není ve stejném sestavení, ve kterém je vlastnost definovaná.  
  
 **ID chyby:** BC31103  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud máte kontrolu nad zdrojovým kódem, který definuje vlastnost, zvažte deklaraci `Get` procedury se stejnou úrovní přístupu jako vlastnost samotnou.  
  
- Pokud nemáte kontrolu nad zdrojovým kódem, který definuje vlastnost, nebo je nutné omezit `Get` úroveň přístupu k proceduře více než samotnou vlastnost, zkuste přesunout příkaz, který přečte hodnotu vlastnosti, do oblasti kódu, která má lepší přístup k vlastnosti.  
  
## <a name="see-also"></a>Viz také

- [Procedury vlastnosti](../../programming-guide/language-features/procedures/property-procedures.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
