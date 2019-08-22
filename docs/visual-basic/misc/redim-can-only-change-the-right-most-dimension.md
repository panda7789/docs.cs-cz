---
title: Příkaz ReDim může změnit jenom rozměr, který je nejvíce vpravo.
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: f38bcb99b682ace497859b67fe3bb829bbc80c4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664410"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>Příkaz ReDim může změnit jenom rozměr, který je nejvíce vpravo.
Příkaz se pokusil o `Preserve` použití klíčového slova pro změnu rozměru pole, které není poslední dimenzí. `ReDim` Při použití `Preserve`můžete změnit velikost jenom na poslední rozměr pole. Pro všechny ostatní dimenze je nutné zadat stejnou velikost jako pro existující pole.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- `Preserve` Odeberte klíčové slovo.  
  
## <a name="see-also"></a>Viz také:

- [Pole v jazyce Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Rozměry pole v Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [Příkaz ReDim](../../visual-basic/language-reference/statements/redim-statement.md)
- [Příkaz Dim](../../visual-basic/language-reference/statements/dim-statement.md)
