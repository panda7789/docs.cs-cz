---
title: Událost '<eventname1>' nemůže implementovat událost '<eventname2>' v rozhraní '<interface>' , protože se neshodují jejich typy delegátů '<delegate1>' a '<delegate2>'.
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 32d6733580de8798a66c30d486b8439befd2af19
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409605"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a>Událost '\<eventname1>' nemůže implementovat událost '\<eventname2>' v rozhraní '\<interface>' , protože se neshodují jejich typy delegátů '\<delegate1>' a '\<delegate2>'.
Visual Basic nemůže implementovat událost, protože typ delegáta události neodpovídá typu delegáta události v rozhraní. K této chybě může dojít, pokud v rozhraní definujete více událostí a pak se pokusíte o jejich implementaci společně se stejnou událostí. Událost může implementovat dvě nebo více událostí pouze v případě, že všechny implementované události jsou deklarovány pomocí `As` syntaxe a určí stejný typ delegáta.  
  
 **ID chyby:** BC31423  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Implementujte události samostatně.  
  
     —nebo—  
  
- Definujte události v rozhraní pomocí `As` syntaxe a zadejte stejný typ delegáta.  
  
## <a name="see-also"></a>Viz také

- [Event – příkaz](../statements/event-statement.md)
- [Delegate – příkaz](../statements/delegate-statement.md)
- [Události](../../programming-guide/language-features/events/index.md)
