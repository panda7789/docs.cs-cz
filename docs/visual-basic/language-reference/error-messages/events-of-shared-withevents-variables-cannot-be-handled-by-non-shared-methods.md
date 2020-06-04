---
title: Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: fc163c1069aa6f41766664e0fa5f5a9c34a1f73d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409566"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.
Proměnná deklarovaná s `Shared` modifikátorem je sdílená proměnná. Sdílená proměnná identifikuje přesně jedno umístění úložiště. Proměnná deklarovaná pomocí modifikátoru vyhodnotí `WithEvents` , že typ, ke kterému proměnná patří, zpracovává sadu událostí, které proměnná vyvolává. Když je přiřazena hodnota proměnné, vlastnost vytvořená deklarací odřadí `WithEvents` všechny existující obslužné rutiny události a připojí novou obslužnou rutinu události prostřednictvím `Add` metody.  
  
 **ID chyby:** BC30594  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Deklarujte obslužnou rutinu události `Shared` .  
  
## <a name="see-also"></a>Viz také

- [Shared](../modifiers/shared.md)
- [WithEvents](../modifiers/withevents.md)
