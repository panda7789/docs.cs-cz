---
title: "Toto pole nelze upravovat nebo je dočasně uzamčeno (Visual Basic)."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: adff10d4ae61e45402df64ebaa3baf146371ff9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
