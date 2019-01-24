---
title: "'ReDim' lze měnit pouze rozměr nejvíce vpravo"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 97eedabd550be397f9cdffc5fd864d7a88c30c31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714201"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>'ReDim' lze měnit pouze rozměr nejvíce vpravo
A `ReDim` příkaz pokusil použít `Preserve` – klíčové slovo Chcete-li změnit dimenze pole, která není poslední dimenze. Při použití `Preserve`, změníte velikost jenom poslední dimenze pole. Pro všechny ostatní dimenze je nutné zadat stejnou velikost jako u existujícího pole.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte `Preserve` – klíčové slovo.  
  
## <a name="see-also"></a>Viz také:
- [Pole v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [Rozměry pole v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [Příkaz ReDim](../../visual-basic/language-reference/statements/redim-statement.md)
- [Příkaz Dim](../../visual-basic/language-reference/statements/dim-statement.md)
- [Zachovat – odstranit](https://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
