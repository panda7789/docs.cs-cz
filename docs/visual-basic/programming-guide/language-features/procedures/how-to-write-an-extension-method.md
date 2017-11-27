---
title: "Postupy: Zápis metody rozšíření (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65cdabf59886e7457a327ee9cde968a6a73f2280
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Postupy: Zápis metody rozšíření (Visual Basic)
Rozšiřující metody umožňují přidání metody do existující třídy. Rozšíření metodu lze volat, jako by šlo instance této třídy.  
  
### <a name="to-define-an-extension-method"></a>Chcete-li definovat metody rozšíření  
  
1.  Otevřete nové nebo existující aplikace Visual Basic v sadě Visual Studio.  
  
2.  V horní části souboru, ve kterém chcete definovat metody rozšíření patří následující příkaz importu:  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  V modulu v nové nebo existující aplikace začněte definici metody s atributem rozšíření:  
  
    ```  
    <Extension()>  
    ```  
  
4.  Deklarujte metodu běžným způsobem s tím rozdílem, že typ prvního parametru musí být datový typ, který chcete rozšířit.  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad uvádí metody rozšíření v modulu `StringExtensions`. Druhý modul `Module1`, naimportuje `StringExtensions` a volá metodu. Metody rozšíření musí být v oboru, když je volána. Metody rozšíření `PrintAndPunctuate` rozšiřuje <xref:System.String> se metoda, která zobrazí instanci řetězec, za nímž následuje řetězec interpunkčních znamének odesláno jako parametr.  
  
```vb  
' Declarations will typically be in a separate module.  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
```vb  
' Import the module that holds the extension method you want to use,   
' and call it.  
  
Imports ConsoleApplication2.StringExtensions  
  
Module Module1  
  
    Sub Main()  
        Dim example = "Hello"  
        example.PrintAndPunctuate("?")  
        example.PrintAndPunctuate("!!!!")  
    End Sub  
  
End Module  
```  
  
 Všimněte si, že metoda je definován s dva parametry a s názvem jen s jednou. První parametr `aString`, v metodě je vázána definice `example`, instanci `String` , který volá metodu. Výstup tohoto příkladu je následující:  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [Metody rozšíření](./extension-methods.md)  
 [Module – příkaz](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Rozsah v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
