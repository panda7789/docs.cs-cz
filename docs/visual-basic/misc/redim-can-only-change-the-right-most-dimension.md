---
title: Příkaz ReDim může změnit jenom rozměr, který je nejvíce vpravo.
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 8e42e0df7b97fb96f468ce37dd4cfc52fad8c596
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358293"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>Příkaz ReDim může změnit jenom rozměr, který je nejvíce vpravo.
`ReDim`Příkaz se pokusil o použití `Preserve` klíčového slova pro změnu rozměru pole, které není poslední dimenzí. Při použití `Preserve` můžete změnit velikost jenom na poslední rozměr pole. Pro všechny ostatní dimenze je nutné zadat stejnou velikost jako pro existující pole.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odeberte `Preserve` klíčové slovo.  
  
## <a name="see-also"></a>Viz také

- [Pole v jazyce Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Rozměry pole v Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim – příkaz](../language-reference/statements/redim-statement.md)
- [Dim – příkaz](../language-reference/statements/dim-statement.md)
