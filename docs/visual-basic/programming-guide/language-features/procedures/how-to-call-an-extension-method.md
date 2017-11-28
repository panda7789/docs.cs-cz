---
title: "Postupy: Volání metody rozšíření (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 25b5a86af15694e6f64f96a5d5d645a01f8f1f12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Postupy: Volání metody rozšíření (Visual Basic)
Rozšiřující metody umožňují přidání metody do existující třídy. Po metody rozšíření je deklarovaný a začlenění do oboru, můžete ji volat jako metodu instance typu, který rozšiřuje ji. Další informace o tom, jak zápis metody rozšíření najdete v tématu [postupy: zápis metody rozšíření](./how-to-write-an-extension-method.md).  
  
 Následující pokyny naleznete v metodě rozšíření `PrintAndPunctuate`, který se zobrazí řetězec instanci, která následuje libovolnou hodnotu vyvolá se odesílá ve pro druhý parametr `punc`.  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 Metoda musí být v oboru, když je volána.  
  
### <a name="to-call-an-extension-method"></a>Volání metody rozšíření  
  
1.  Deklarace proměnné, která má datový typ prvního parametru metody rozšíření. Pro `PrintAndPunctuate`, musíte <xref:System.String> proměnné:  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  Proměnná se volání metody rozšíření, a jeho hodnota je vázána na první parametr `aString`. Zobrazí příkaz následující volání `Ready?`.  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     Všimněte si, že volání této metody rozšíření vypadá stejně jako všechna volání <xref:System.String> instance metody, které vyžadují jeden parametr:  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  Deklarování jiné proměnné řetězce a volání metody zjistíte, že funguje s libovolným řetězcem.  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     Výsledkem je, tentokrát: `or not!!!`.  
  
## <a name="example"></a>Příklad  
 Následující kód je kompletní příklad vytvoření a použití metody jednoduché rozšíření.  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports ConsoleApplication1.StringExtensions  
  
Module Module1  
  
    Sub Main()  
  
        Dim example = "Hello"  
        example.PrintAndPunctuate(".")  
        example.PrintAndPunctuate("!!!!")  
  
        Dim example2 = "Goodbye"  
        example2.PrintAndPunctuate("?")  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
End Module  
  
' Output:  
' Hello.  
' Hello!!!!  
' Goodbye?  
```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: zápis metody rozšíření](./how-to-write-an-extension-method.md)  
 [Metody rozšíření](./extension-methods.md)  
 [Rozsah v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
