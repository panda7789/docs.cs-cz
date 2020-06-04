---
title: Objekt nebo třída nepodporuje sadu událostí.
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: bc75e031c2d05bea3aa64774a9d3817756e51e8b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409358"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>Objekt nebo třída nepodporuje sadu událostí.
Pokusili jste se použít `WithEvents` proměnnou s komponentou, která nemůže fungovat jako zdroj události pro zadanou sadu událostí. Například jste chtěli zpracovat události objektu a pak vytvořit další objekt, který `Implements` je prvním objektem. I když byste si mohli představit události z implementovaného objektu, nejedná se vždy o případ. `Implements`implementuje pouze rozhraní pro metody a vlastnosti. `WithEvents`není podporováno pro Private `UserControls` , protože informace o typu potřebné k vyvolání `ObjectEvent` není v době běhu k dispozici.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Pro komponentu, která nemá zdrojové události, nelze události jímky.  
  
## <a name="see-also"></a>Viz také

- [WithEvents](../modifiers/withevents.md)
- [Implements – Příkaz](../statements/implements-statement.md)
