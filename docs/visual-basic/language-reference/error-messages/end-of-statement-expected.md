---
title: Byl očekáván konec příkazu.
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 7b91d13cbcb9d211d4ca18c8e48c7494bf6eccc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="end-of-statement-expected"></a>Byl očekáván konec příkazu.
Příkaz je syntakticky dokončení, ale další programovací element odpovídá elementu, který dokončí příkaz. Na konci každé příkaz vyžádáním ukončení řádku.
  
 Ukončení řádku rozděluje znaky jazyka Visual Basic zdrojového souboru do řádky. Příkladem konců řádku jsou kódování Unicode znaků CR návratový znak (& HD) kódování Unicode konce řádku znak (& HA), a znak Unicode vrátí znak, za nímž následuje znak Unicode konce řádku. Další informace o konců řádku najdete v tématu [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).
  
 **ID chyby:** BC30205
  
## <a name="to-correct-this-error"></a>Oprava této chyby
  
1.  Zkontrolujte, pokud dva různé příkazy nechtěně byly uvedeny na stejném řádku.
  
2.  Po elementu, který dokončí příkaz INSERT a ukončení řádku.
  
## <a name="see-also"></a>Viz také  
 [Postupy: Přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
