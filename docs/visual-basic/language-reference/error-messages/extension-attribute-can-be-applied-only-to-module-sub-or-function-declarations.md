---
title: Atribut 'Extension' lze použít pouze v deklaracích 'Module', 'Sub' nebo 'Function'.
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: a4561359e4d7cb0f6ebe44a5deb09b3374556ed8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801644"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>Atribut 'Extension' lze použít pouze v deklaracích 'Module', 'Sub' nebo 'Function'.
Jediný způsob, jak rozšířit datový typ v jazyce Visual Basic je definovat rozšiřující metodu v modulu standard. Metoda rozšíření může být `Sub` procedury nebo `Function` postup. Všechny metody rozšíření musí být označeny pomocí atributu rozšíření `<Extension()>`, z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> oboru názvů. Volitelně může být označena modul, který obsahuje metodu rozšíření stejným způsobem. Žádné další použití atributu rozšíření není platný.  
  
 **ID chyby:** BC36550  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odebrání atributu rozšíření.  
  
- Změnit návrh rozšíření jako metoda, definována v nadřazeném modulu.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje `Print` metodu `String` datového typu.  
  
```  
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

- [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Rozšiřující metody](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)
