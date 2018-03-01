---
title: "& č. 39; Rozšíření & č. 39; atribut lze použít pouze k & č. 39; Modul & č. 39; & č. 39; Sub – & č. 39; nebo & č. 39; Funkce & č. 39; deklarace"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d77933c52484eb934501107d1ddad15f0eca826
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>& č. 39; Rozšíření & č. 39; atribut lze použít pouze k & č. 39; Modul & č. 39; & č. 39; Sub – & č. 39; nebo & č. 39; Funkce & č. 39; deklarace
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
 [Metody rozšíření](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md)
