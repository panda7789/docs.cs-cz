---
title: '&#39;ReDim&#39; lze změnit pouze dimenze nejvíce vpravo'
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: efb98df13a7e3e378347b30b6fc00b90030ec194
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641180"
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a>&#39;ReDim&#39; lze změnit pouze dimenze nejvíce vpravo
A `ReDim` příkaz pokusil použít `Preserve` – klíčové slovo Chcete-li změnit dimenze pole, které není poslední dimenze. Při použití `Preserve`, můžete změnit velikost pouze poslední dimenze pole. Pro všechny další dimenze musíte zadat stejnou velikost jako existující pole.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte `Preserve` – klíčové slovo.  
  
## <a name="see-also"></a>Viz také  
 [Pole v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [Rozměry pole v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [Příkaz ReDim](../../visual-basic/language-reference/statements/redim-statement.md)  
 [Příkaz Dim](../../visual-basic/language-reference/statements/dim-statement.md)  
 [Zachovat – odstranit](http://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
