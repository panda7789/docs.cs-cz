---
title: Byl očekáván konec příkazu.
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 1ce5c793a09df34ac17e70e3253e98108bf76fb8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321471"
---
# <a name="end-of-statement-expected"></a>Byl očekáván konec příkazu.
Příkaz je syntakticky úplný, ale další programovací element dodržovat elementu, který příkaz se dokončí. Vyžaduje na konci každý příkaz se znakem ukončení řádku.
  
 Ukončení řádku rozdělí řádky znaků zdrojový soubor jazyka Visual Basic. Příkladem řádku jsou kódování Unicode návrat na začátek řádku návratový znak (& HD, High Density), Unicode odřádkování znak (& HA), a Unicode návrat znak následovaný znak odřádkování Unicode. Další informace o řádku, najdete v článku [specifikace jazyka Visual Basic](~/_vblang/spec/lexical-grammar.md#line-terminators).
  
 **ID chyby:** BC30205
  
## <a name="to-correct-this-error"></a>Oprava této chyby
  
1. Zaškrtněte, pokud chcete zobrazit, pokud dva různé příkazy neúmyslně byly uvedeny na stejném řádku.
  
2. Vložte a znak ukončení řádku za prvkem, který se příkaz dokončí.
  
## <a name="see-also"></a>Viz také:

- [Postupy: Přerušení a kombinování příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
