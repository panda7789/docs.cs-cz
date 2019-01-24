---
title: "'ReDim' nelze změnit počet rozměrů"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: 80546b427afdafaf6e9fcea493d58cf1019e79e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638454"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a>'ReDim' nelze změnit počet rozměrů
Operace se pokusí použít `ReDim` prohlášení, chcete-li změnit pořadí (počet rozměrů) pole. `ReDim` můžete změnit velikost nejmíň jeden rozměry pole, které již byl dříve deklarován, ale nedá se změnit pořadí tohoto pole.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Ujistěte se, že máte v úmyslu změnit pole pořadí a ne velikosti jeho rozměry a pokud je to možné, použijte `Dim` deklarovat nové pole s požadovaný počet rozměrů.  
  
## <a name="see-also"></a>Viz také:
- [Pole v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [Rozměry pole v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [Příkaz ReDim](../../visual-basic/language-reference/statements/redim-statement.md)
- [Příkaz Dim](../../visual-basic/language-reference/statements/dim-statement.md)
