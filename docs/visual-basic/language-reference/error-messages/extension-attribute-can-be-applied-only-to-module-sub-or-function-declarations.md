---
title: '&#39;Rozšíření&#39; atribut se dá použít jenom s &#39;modulu&#39;, &#39;Sub&#39;, nebo &#39;funkce&#39; deklarace'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: fabd602f31a362fe33954253d565e86a065e0a83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718231"
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>&#39;Rozšíření&#39; atribut se dá použít jenom s &#39;modulu&#39;, &#39;Sub&#39;, nebo &#39;funkce&#39; deklarace
Jediný způsob, jak rozšířit datový typ v jazyce Visual Basic je definovat rozšiřující metodu v modulu standard. Metoda rozšíření může být `Sub` procedury nebo `Function` postup. Všechny metody rozšíření musí být označeny pomocí atributu rozšíření `<Extension()>`, z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> oboru názvů. Volitelně může být označena modul, který obsahuje metodu rozšíření stejným způsobem. Žádné další použití atributu rozšíření není platný.  
  
 **ID chyby:** BC36550  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odebrání atributu rozšíření.  
  
-   Změnit návrh rozšíření jako metoda, definována v nadřazeném modulu.  
  
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
