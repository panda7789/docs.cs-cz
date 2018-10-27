---
title: Byl očekáván konec příkazu.
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 8df756009ebe3a0613ec47018d938151829214df
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50039020"
---
# <a name="end-of-statement-expected"></a>Byl očekáván konec příkazu.
Příkaz je syntakticky úplný, ale další programovací element dodržovat elementu, který příkaz se dokončí. Vyžaduje na konci každý příkaz se znakem ukončení řádku.
  
 Ukončení řádku rozdělí řádky znaků zdrojový soubor jazyka Visual Basic. Příkladem řádku jsou kódování Unicode návrat na začátek řádku návratový znak (& HD, High Density), Unicode odřádkování znak (& HA), a Unicode návrat znak následovaný znak odřádkování Unicode. Další informace o řádku, najdete v článku [specifikace jazyka Visual Basic](~/_vblang/spec/lexical-grammar.md#line-terminators).
  
 **ID chyby:** BC30205
  
## <a name="to-correct-this-error"></a>Oprava této chyby
  
1.  Zaškrtněte, pokud chcete zobrazit, pokud dva různé příkazy neúmyslně byly uvedeny na stejném řádku.
  
2.  Vložte a znak ukončení řádku za prvkem, který se příkaz dokončí.
  
## <a name="see-also"></a>Viz také  
 [Postupy: Přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
