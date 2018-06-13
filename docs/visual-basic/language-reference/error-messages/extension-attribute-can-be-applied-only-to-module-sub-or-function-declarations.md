---
title: '&#39;Rozšíření&#39; atribut lze použít pouze &#39;modulu&#39;, &#39;Sub&#39;, nebo &#39;funkce&#39; deklarace'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: d7f8829cb879d612711ac6bcc6bf4aa065fbe323
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587316"
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>&#39;Rozšíření&#39; atribut lze použít pouze &#39;modulu&#39;, &#39;Sub&#39;, nebo &#39;funkce&#39; deklarace
Jediný způsob, jak rozšířit datový typ v jazyce Visual Basic je definovat metody rozšíření uvnitř standardní modulu. Rozšíření metoda může být `Sub` postup nebo `Function` postupu. Všechny metody rozšíření musí být označen atributem rozšíření, `<Extension()>`, z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> oboru názvů. Modul, který obsahuje metody rozšíření Volitelně mohou být označeny stejným způsobem. Žádné jiné použití atributu rozšíření je platný.  
  
 **ID chyby:** BC36550  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte atribut rozšíření.  
  
-   Změnit návrh rozšíření jako metodu, definované v nadřazených modulu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje `Print` metodu `String` datového typu.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Rozšiřující metody](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)
