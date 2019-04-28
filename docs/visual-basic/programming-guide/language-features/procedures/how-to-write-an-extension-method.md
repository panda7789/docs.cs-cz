---
title: 'Postupy: Zápis metody rozšíření (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 00d62d275f7afc06e066a375dc1ffcd74b23c9ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665998"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Postupy: Zápis metody rozšíření (Visual Basic)
Rozšiřující metody umožňují přidat metody do existující třídy. Metody rozšíření lze volat, jako by šlo instanci dané třídy.  
  
### <a name="to-define-an-extension-method"></a>Chcete-li definovat metodu rozšíření  
  
1. Otevření nové nebo existující aplikace v jazyce Visual Basic v sadě Visual Studio.  
  
2. V horní části souboru, ve kterém chcete definovat rozšiřující metodu patří následující příkaz importu:  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3. V rámci modulu v nové nebo existující aplikace začněte definici metody s atributem rozšíření:  
  
    ```  
    <Extension()>  
    ```  
  
4. Deklarujte metodu běžným způsobem s tím rozdílem, že první parametr typu musí být datový typ, který chcete rozšířit.  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje rozšiřující metodu v modulu `StringExtensions`. Druhý modul `Module1`, importuje `StringExtensions` a volá metodu. Metoda rozšíření musí být v rozsahu, když je volána. Metoda rozšíření `PrintAndPunctuate` rozšiřuje <xref:System.String> třídu s metodou, která zobrazuje instanci řetězce, za nímž následuje řetězec interpunkčních znamének poslaná jako parametr.  
  
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
  
 Všimněte si, že metoda je definováno se dvěma parametry a volat pouze jednou. První parametr `aString`, v metodě definice je vázán na `example`, instanci `String` , která volá metodu. Výstup v příkladu vypadá takto:  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Rozšiřující metody](./extension-methods.md)
- [Příkaz Module](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Obor v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
