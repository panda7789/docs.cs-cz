---
title: Příkaz ReDim nemůže měnit počet rozměrů.
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: b2404927c2faf30d1d058d2163fd5d67e1a52e1e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358164"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a>Příkaz ReDim nemůže měnit počet rozměrů.
Operace se pokusí použít `ReDim` příkaz ke změně pořadí (počet rozměrů) pole. `ReDim`může změnit velikost jedné nebo více dimenzí pole, které je již formálně deklarované, ale nemůže změnit rozměr pole.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že máte v úmyslu změnit pořadí pole, nikoli velikost jeho rozměrů, a pokud je to možné, použijte `Dim` k deklaraci nového pole s požadovaným pořadím.  
  
## <a name="see-also"></a>Viz také

- [Pole v jazyce Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Rozměry pole v Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim – příkaz](../language-reference/statements/redim-statement.md)
- [Dim – příkaz](../language-reference/statements/dim-statement.md)
