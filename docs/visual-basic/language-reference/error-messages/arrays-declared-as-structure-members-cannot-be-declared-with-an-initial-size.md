---
title: U polí deklarovaných jako členové struktury nelze deklarovat počáteční velikost.
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: de9d77aa9ea853b6f044e91878044115588ca77c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701252"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>U polí deklarovaných jako členové struktury nelze deklarovat počáteční velikost.
Pole ve struktuře je deklarováno s počáteční velikostí. Nemůžete inicializovat žádný element struktury a deklarovat velikost pole je jedna forma inicializace.  
  
 **ID chyby:** BC31043  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Definujte pole ve vaší struktuře jako dynamické (bez počáteční velikosti).  
  
2. Pokud požadujete určitou velikost pole, můžete změnit rozměr dynamického pole pomocí [příkazu ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) , pokud je váš kód spuštěn. Toto dokládá následující příklad.  
  
    ```vb  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Postupy: Definice struktury](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
