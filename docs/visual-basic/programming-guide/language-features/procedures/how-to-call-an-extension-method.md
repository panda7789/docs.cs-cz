---
title: 'Postupy: Volání metody rozšíření (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 5cb0684637a716dfec947740ba345c62eaabddd7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863672"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Postupy: Volání metody rozšíření (Visual Basic)
Rozšiřující metody umožňují přidat metody do existující třídy. Po metodu rozšíření deklarovat a přeneseny do rozsahu, můžete ji volat jako metodu instance typu, který rozšiřuje. Další informace o tom, jak psát metodu rozšíření, naleznete v tématu [jak: Zápis metody rozšíření](./how-to-write-an-extension-method.md).  
  
 Následující pokyny najdete v metodě rozšíření `PrintAndPunctuate`, instanci řetězce, která volá následuje libovolné hodnoty. Tím se zobrazí se posílá ve druhém parametru `punc`.  
  
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
  
 Metoda musí být v rozsahu, když je volána.  
  
### <a name="to-call-an-extension-method"></a>K volání metody rozšíření  
  
1. Deklarujte proměnné, která má datový typ prvního parametru metody rozšíření. Pro `PrintAndPunctuate`, je nutné <xref:System.String> proměnné:  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2. Že proměnné se vyvolat metodu rozšíření, a její hodnota je vázaná na první parametr `aString`. Následující volání příkazu se zobrazí `Ready?`.  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     Všimněte si, že volání této metody rozšíření vypadá stejně, jako je jeden z volání <xref:System.String> instanci metody, které vyžadují jeden parametr:  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3. Deklarování proměnné jiného řetězce a volání metody znovu, abyste viděli, jestli funguje s libovolným řetězcem.  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     Výsledkem této doby je: `or not!!!`.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Postupy: Zápis metody rozšíření](./how-to-write-an-extension-method.md)
- [Rozšiřující metody](./extension-methods.md)
- [Obor v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
