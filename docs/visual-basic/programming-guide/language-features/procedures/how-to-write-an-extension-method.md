---
title: 'Postupy: Zápis metody rozšíření (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 7a7a9d16d9f69071e9d1dacb0558f7ca92e1d21e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631034"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Postupy: Zápis metody rozšíření (Visual Basic)
Metody rozšíření umožňují přidat metody do existující třídy. Metodu rozšíření lze volat, jako kdyby byla instancí této třídy.

### <a name="to-define-an-extension-method"></a>Definování rozšiřující metody

1. Otevřete v aplikaci Visual Studio novou nebo existující aplikaci Visual Basic.

2. V horní části souboru, ve kterém chcete definovat metodu rozšíření, zahrňte následující příkaz import:

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. V rámci modulu ve vaší nové nebo existující aplikaci spusťte definici metody s atributem rozšíření:

    ```vb
    <Extension()>
    ```

4. Deklarujte svou metodu běžným způsobem, s tím rozdílem, že typ prvního parametru musí být datový typ, který chcete zvětšit.

    ```vb
    <Extension()>
    Public Sub SubName (ByVal para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a>Příklad
 Následující příklad deklaruje metodu rozšíření v modulu `StringExtensions`. Druhý modul, `Module1`, naimportuje `StringExtensions` a zavolá metodu. Metoda rozšíření musí být v oboru, pokud je volána. Metoda `PrintAndPunctuate` rozšíření<xref:System.String> rozšiřuje třídu o metodu, která zobrazuje instanci řetězce následovaný řetězcem interpunkčních znamének odeslaných v podobě parametru.
  
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
  
 Všimněte si, že metoda je definována se dvěma parametry a volána pouze s jedním. První parametr, `aString`v definici metody je vázán na `example`, instance `String` , která volá metodu. Výstup příkladu je následující:
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Rozšiřující metody](./extension-methods.md)
- [Příkaz Module](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Obor v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
