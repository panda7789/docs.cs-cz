---
title: U polí deklarovaných jako členové struktury nelze deklarovat počáteční velikost.
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 983154a144a79991c86db5056ad0e0e563a3ba73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>U polí deklarovaných jako členové struktury nelze deklarovat počáteční velikost.
Pole ve struktuře je deklarována s počáteční velikostí. Nelze inicializovat libovolný element, struktura a deklarace velikost pole je jednu formu inicializace.  
  
 **ID chyby:** BC31043  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Definujte pole v strukturu jako dynamický (žádné počáteční velikost).  
  
2.  Pokud budete potřebovat určité velikosti pole, můžete redimension dynamické pole s [ReDim – příkaz](../../../visual-basic/language-reference/statements/redim-statement.md) při spuštění kódu. Toto dokládá následující příklad.  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Postupy: definice struktury](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
