---
title: "& č. 39; ReDim & č. 39; lze změnit pouze dimenze nejvíce vpravo"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 989a06f94824dfd051d1a7d2e7749dbb8c8e11a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a>& č. 39; ReDim & č. 39; lze změnit pouze dimenze nejvíce vpravo
A `ReDim` příkaz pokusil použít `Preserve` – klíčové slovo Chcete-li změnit dimenze pole, které není poslední dimenze. Při použití `Preserve`, můžete změnit velikost pouze poslední dimenze pole. Pro všechny další dimenze musíte zadat stejnou velikost jako existující pole.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte `Preserve` – klíčové slovo.  
  
## <a name="see-also"></a>Viz také  
 [Pole v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [Rozměry pole v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [ReDim – příkaz](../../visual-basic/language-reference/statements/redim-statement.md)  
 [Dim – příkaz](../../visual-basic/language-reference/statements/dim-statement.md)  
 [Zachovat – odstranit](http://msdn.microsoft.com/en-us/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
