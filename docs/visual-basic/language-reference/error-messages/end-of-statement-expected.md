---
title: "Byl očekáván konec příkazu."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords: BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4934952015cb4871bcd90cef982eab5425b1617f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="end-of-statement-expected"></a>Byl očekáván konec příkazu.
Příkaz je syntakticky dokončení, ale další programovací element odpovídá elementu, který dokončí příkaz. Na konci každé příkaz vyžádáním ukončení řádku.
  
 Ukončení řádku rozděluje znaky jazyka Visual Basic zdrojového souboru do řádky. Příkladem konců řádku jsou kódování Unicode znaků CR návratový znak (& HD) kódování Unicode konce řádku znak (& HA), a znak Unicode vrátí znak, za nímž následuje znak Unicode konce řádku. Další informace o konců řádku najdete v tématu [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).
  
 **ID chyby:** BC30205
  
## <a name="to-correct-this-error"></a>Oprava této chyby
  
1.  Zkontrolujte, pokud dva různé příkazy nechtěně byly uvedeny na stejném řádku.
  
2.  Po elementu, který dokončí příkaz INSERT a ukončení řádku.
  
## <a name="see-also"></a>Viz také  
 [Postupy: přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
