---
title: "'ReDim' lze měnit pouze rozměr nejvíce vpravo"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: d20d0374cd5183b6216d1c6e5b138256cf0a4f17
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738952"
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
