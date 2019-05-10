---
title: "'ReDim' lze měnit pouze rozměr nejvíce vpravo"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 584370f356180fe8b1710a9e145018be7f2d8a0f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592296"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>'ReDim' lze měnit pouze rozměr nejvíce vpravo
A `ReDim` příkaz pokusil použít `Preserve` – klíčové slovo Chcete-li změnit dimenze pole, která není poslední dimenze. Při použití `Preserve`, změníte velikost jenom poslední dimenze pole. Pro všechny ostatní dimenze je nutné zadat stejnou velikost jako u existujícího pole.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odeberte `Preserve` – klíčové slovo.  
  
## <a name="see-also"></a>Viz také:

- [Pole v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [Rozměry pole v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [Příkaz ReDim](../../visual-basic/language-reference/statements/redim-statement.md)
- [Příkaz Dim](../../visual-basic/language-reference/statements/dim-statement.md)
