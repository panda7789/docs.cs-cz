---
title: Toto pole nelze upravovat nebo je dočasně uzamčeno.
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 4a86460104b6c4d9d6791e60f6f377cec0030425
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363030"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Toto pole nelze upravovat nebo je dočasně uzamčeno (Visual Basic).
Tato chyba má následující možné příčiny:  
  
- Použití `ReDim` ke změně počtu prvků pole s pevnou velikostí.  
  
- Předimenzování dynamického pole na úrovni modulu, ve kterém jeden prvek byl předán jako argument procedury. Pokud je předán element, je pole uzamčeno, aby nedošlo k zrušení přidělení paměti pro parametr reference v rámci procedury.  
  
- Pokus o přiřazení hodnoty k `Variant` proměnné obsahující pole, ale `Variant` je aktuálně uzamčena.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zajistěte, aby původní pole bylo dynamické a nikoli pevně `ReDim` deklarované deklarací (Pokud je pole deklarováno v rámci procedury), nebo deklarací, aniž by bylo nutné určit počet prvků (Pokud je pole deklarováno na úrovni modulu.  
  
2. Určete, zda opravdu potřebujete předat element, protože je viditelný v rámci všech procedur v modulu.  
  
3. Určete, co zamkne `Variant` a opraví ho.  
  
## <a name="see-also"></a>Viz také

- [Pole](../../programming-guide/language-features/arrays/index.md)
