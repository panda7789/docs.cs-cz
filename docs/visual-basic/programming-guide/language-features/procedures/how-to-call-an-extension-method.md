---
title: 'Postupy: Volání metody rozšíření (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: f2058162ab939d2619d7255c884d88c35ee63715
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512674"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Postupy: Volání metody rozšíření (Visual Basic)

Metody rozšíření umožňují přidat metody do existující třídy. Poté, co je metoda rozšíření deklarována a uvedena do rozsahu, lze ji volat jako metodu instance typu, který rozšiřuje. Další informace o tom, jak napsat rozšiřující metodu, naleznete v [tématu How to: Napište metodu](./how-to-write-an-extension-method.md)rozšíření.

 Následující pokyny odkazují na metodu `PrintAndPunctuate`rozšíření, která zobrazí instanci řetězce, která ji vyvolá, a za druhým `punc`parametrem je odeslána jakákoli hodnota.

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

Metoda musí být v oboru, pokud je volána.

### <a name="to-call-an-extension-method"></a>Volání metody rozšíření

1. Deklarujte proměnnou, která má datový typ prvního parametru metody rozšíření. `PrintAndPunctuate` Pro<xref:System.String> potřebujete proměnnou:

    ```vb
    Dim example = "Ready"
    ```

2. Tato proměnná vyvolá metodu rozšíření a její hodnota je svázána s prvním parametrem `aString`. Zobrazí `Ready?`se následující volání příkazu.

    ```vb
    example.PrintAndPunctuate("?")
    ```

     Všimněte si, že volání této metody rozšíření vypadá stejně jako volání jakékoli <xref:System.String> metody instance, která vyžaduje jeden parametr:

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. Deklarujte další řetězcovou proměnnou a zavolejte metodu znovu, abyste viděli, že funguje s libovolným řetězcem.

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     Výsledek tohoto času je: `or not!!!`.

## <a name="example"></a>Příklad
 Následující kód je kompletní příklad vytváření a použití jednoduché metody rozšíření.

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
- [Obor v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
