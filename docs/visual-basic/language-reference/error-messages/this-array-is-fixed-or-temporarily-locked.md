---
title: Toto pole nelze upravovat nebo je dočasně uzamčeno (Visual Basic).
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: c74d9524ff64101ba6002e133b93c9b80e8f50a9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337965"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Toto pole nelze upravovat nebo je dočasně uzamčeno (Visual Basic).
Tato chyba má následující možné příčiny:  
  
-   Pomocí `ReDim` Chcete-li změnit počet elementů pole s pevnou velikostí.  
  
-   Redimensioning úrovni modulu dynamické pole, ve kterém jeden prvek byl předán jako argument procedury. Pokud je předán element, aby se zabránilo je uzamčen pole zrušení přidělení paměti pro referenční parametr v rámci procesu.  
  
-   Pokus o přiřazení hodnoty k `Variant` proměnnou obsahující pole, ale `Variant` je aktuálně uzamčen.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, původní pole dynamické spíše než Pevná deklarováním s `ReDim` (Pokud deklaraci pole v rámci procedury), nebo deklarací bez zadání počtu elementů (je-li deklaraci pole na úrovni modulu.  
  
2. Určete, jestli je skutečně potřeba předat elementu, protože je viditelné v rámci všechny postupy v modulu.  
  
3. Zjistit, co je uzamčení `Variant` a napravit.  
  
## <a name="see-also"></a>Viz také:

- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
