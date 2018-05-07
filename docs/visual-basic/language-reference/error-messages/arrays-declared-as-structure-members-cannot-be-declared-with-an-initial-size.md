---
title: U polí deklarovaných jako členové struktury nelze deklarovat počáteční velikost.
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 0a7424e5dbfadd78c4071ba5b76086b7f6c9b94a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Postupy: Definice struktury](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
