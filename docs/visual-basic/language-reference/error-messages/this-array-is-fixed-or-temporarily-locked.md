---
title: Toto pole nelze upravovat nebo je dočasně uzamčeno (Visual Basic).
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: e912bd202603d9a0f427418708ad584c7d6203e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Toto pole nelze upravovat nebo je dočasně uzamčeno (Visual Basic).
Tato chyba má následující možné příčiny:  
  
-   Pomocí `ReDim` Chcete-li změnit počet elementů pole pevné velikosti.  
  
-   Redimensioning úroveň modulu dynamická pole, ve kterém jeden element. byl předán jako argument procedury. Pokud není předán element pole je pevně nastavené zabránit rušení přidělení paměti pro parametr odkaz v rámci procesu.  
  
-   Probíhá pokus o přiřazení hodnoty k `Variant` Proměnná obsahující pole, ale `Variant` je aktuálně uzamčena.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte pole původní dynamické místo opravených deklarace její `ReDim` (Pokud pole deklarované v rámci postupu), nebo deklarováním bez určující počet elementů (je-li toto pole je deklarovaná na úrovni modulu.  
  
2.  Určete, jestli je skutečně potřeba předat elementu, protože je viditelné v rámci všechny postupy v modulu.  
  
3.  Zjistit, co je uzamčení `Variant` a napravit.  
  
## <a name="see-also"></a>Viz také  
 [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
