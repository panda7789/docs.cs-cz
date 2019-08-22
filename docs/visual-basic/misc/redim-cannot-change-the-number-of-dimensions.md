---
title: Příkaz ReDim nemůže měnit počet rozměrů.
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: fb60c93f988ca40305f13cca07f55a70bd779081
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664401"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a>Příkaz ReDim nemůže měnit počet rozměrů.
Operace se pokusí použít `ReDim` příkaz ke změně pořadí (počet rozměrů) pole. `ReDim`může změnit velikost jedné nebo více dimenzí pole, které je již formálně deklarované, ale nemůže změnit rozměr pole.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že máte v úmyslu změnit pořadí pole, nikoli velikost jeho rozměrů, a pokud je to možné, `Dim` použijte k deklaraci nového pole s požadovaným pořadím.  
  
## <a name="see-also"></a>Viz také:

- [Pole v jazyce Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Rozměry pole v Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [Příkaz ReDim](../../visual-basic/language-reference/statements/redim-statement.md)
- [Příkaz Dim](../../visual-basic/language-reference/statements/dim-statement.md)
