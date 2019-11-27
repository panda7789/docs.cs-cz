---
title: Toto pole nelze upravovat nebo je dočasně uzamčeno.
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 8d5e4add2d92a575126fb934ac3874a2e37685f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350786"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Toto pole nelze upravovat nebo je dočasně uzamčeno (Visual Basic).
Tato chyba má následující možné příčiny:  
  
- Použití `ReDim` ke změně počtu prvků pole s pevnou velikostí.  
  
- Předimenzování dynamického pole na úrovni modulu, ve kterém jeden prvek byl předán jako argument procedury. Pokud je předán element, je pole uzamčeno, aby nedošlo k zrušení přidělení paměti pro parametr reference v rámci procedury.  
  
- Došlo k pokusu o přiřazení hodnoty k proměnné `Variant` obsahující pole, ale `Variant` je aktuálně uzamčena.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zajistěte, aby původní pole bylo dynamické a nikoli pevně deklarováno pomocí `ReDim` (Pokud je pole deklarováno v rámci procedury) nebo prohlášením bez určení počtu prvků (Pokud je pole deklarováno na úrovni modulu.  
  
2. Určete, zda opravdu potřebujete předat element, protože je viditelný v rámci všech procedur v modulu.  
  
3. Určete, co zamkne `Variant` a opravte ho.  
  
## <a name="see-also"></a>Viz také:

- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
