---
title: 'Postupy: Zápis metody rozšíření (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 31ccb18e0e6d1569764ec2a67201d7f758129425
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332761"
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
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a>Příklad

 Následující příklad deklaruje metodu rozšíření v modulu `StringExtensions`. Druhý modul, `Module1`, importuje `StringExtensions` a volá metodu. Metoda rozšíření musí být v oboru, pokud je volána. Metoda rozšíření `PrintAndPunctuate` rozšiřuje třídu <xref:System.String> s metodou, která zobrazuje instanci řetězce následovaný řetězcem interpunkčních znamének odeslaných v podobě parametru.
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
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
  
 Všimněte si, že metoda je definována se dvěma parametry a volána pouze s jedním. První parametr `aString` v definici metody je vázán na `example`, instance `String`, která volá metodu. Výstup příkladu je následující:
  
 ```console
 Hello?
 Hello!!!!
 ```
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Rozšiřující metody](extension-methods.md)
- [Příkaz Module](../../../language-reference/statements/module-statement.md)
- [Parametry a argumenty procedury](procedure-parameters-and-arguments.md)
- [Obor v Visual Basic](../declared-elements/scope.md)
