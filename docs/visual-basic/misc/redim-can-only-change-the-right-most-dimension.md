---
title: '&#39;ReDim&#39; lze měnit pouze rozměr nejvíce vpravo'
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 94e0fe81f7e750a67943b68f2db700e3a7831da1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502583"
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a>&#39;ReDim&#39; lze měnit pouze rozměr nejvíce vpravo
A `ReDim` příkaz pokusil použít `Preserve` – klíčové slovo Chcete-li změnit dimenze pole, která není poslední dimenze. Při použití `Preserve`, změníte velikost jenom poslední dimenze pole. Pro všechny ostatní dimenze je nutné zadat stejnou velikost jako u existujícího pole.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte `Preserve` – klíčové slovo.  
  
## <a name="see-also"></a>Viz také  
 [Pole v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [Rozměry pole v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [Příkaz ReDim](../../visual-basic/language-reference/statements/redim-statement.md)  
 [Příkaz Dim](../../visual-basic/language-reference/statements/dim-statement.md)  
 [Zachovat – odstranit](https://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
