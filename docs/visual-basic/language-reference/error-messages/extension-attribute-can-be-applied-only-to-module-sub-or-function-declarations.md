---
title: Atribut 'Extension' lze použít pouze v deklaracích 'Module', 'Sub' nebo 'Function'.
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 95a67a552efacf9e77dc3ebc3e0187817a6d82e2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698587"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>Atribut 'Extension' lze použít pouze v deklaracích 'Module', 'Sub' nebo 'Function'.
Jediným způsobem, jak rozšířit datový typ v Visual Basic, je definovat metodu rozšíření uvnitř standardního modulu. Metoda rozšíření může být procedura @no__t 0 nebo procedura `Function`. Všechny metody rozšíření musí být označené atributem rozšíření `<Extension()>` z oboru názvů <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>. Volitelně může být modul, který obsahuje metodu rozšíření, označen stejným způsobem. Žádné jiné použití atributu Extension není platné.  
  
 **ID chyby:** BC36550  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odeberte atribut Extension.  
  
- Přenavrhněte své rozšíření jako metodu definovanou v ohraničujícím modulu.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje metodu `Print` pro datový typ `String`.  
  
```vb  
Imports StringUtility  
Imports System.Runtime.CompilerServices  
Namespace StringUtility  
    <Extension()>   
    Module StringExtensions  
        <Extension()>   
        Public Sub Print (ByVal str As String)  
            Console.WriteLine(str)  
        End Sub  
    End Module  
End Namespace  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled atributů](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Rozšiřující metody](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)
