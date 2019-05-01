---
title: "'ReDim' nelze změnit počet rozměrů"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: b6bb78c3f1d7224e6e4b432fd3aef4589f2f1cd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964889"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a>'ReDim' nelze změnit počet rozměrů
Operace se pokusí použít `ReDim` prohlášení, chcete-li změnit pořadí (počet rozměrů) pole. `ReDim` můžete změnit velikost nejmíň jeden rozměry pole, které již byl dříve deklarován, ale nedá se změnit pořadí tohoto pole.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že máte v úmyslu změnit pole pořadí a ne velikosti jeho rozměry a pokud je to možné, použijte `Dim` deklarovat nové pole s požadovaný počet rozměrů.  
  
## <a name="see-also"></a>Viz také:

- [Pole v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [Rozměry pole v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [Příkaz ReDim](../../visual-basic/language-reference/statements/redim-statement.md)
- [Příkaz Dim](../../visual-basic/language-reference/statements/dim-statement.md)
