---
title: 'Postupy: Volání metody rozšíření'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: a19705a8f90833d48869df26a18d19b0ad1488e0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340395"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Postupy: Volání metody rozšíření (Visual Basic)

Metody rozšíření umožňují přidat metody do existující třídy. Poté, co je metoda rozšíření deklarována a uvedena do rozsahu, lze ji volat jako metodu instance typu, který rozšiřuje. Další informace o tom, jak napsat rozšiřující metodu, naleznete v tématu [How to: Write a Extension](./how-to-write-an-extension-method.md).

 Následující pokyny odkazují na metodu rozšíření `PrintAndPunctuate`, která zobrazí instanci řetězce, která ji vyvolá, a za druhým parametrem je odeslána jakákoli hodnota, `punc`.

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

1. Deklarujte proměnnou, která má datový typ prvního parametru metody rozšíření. Pro `PrintAndPunctuate`potřebujete <xref:System.String> proměnnou:

    ```vb
    Dim example = "Ready"
    ```

2. Tato proměnná vyvolá metodu rozšíření a její hodnota je svázána s prvním parametrem `aString`. Následující volání příkazu zobrazí `Ready?`.

    ```vb
    example.PrintAndPunctuate("?")
    ```

     Všimněte si, že volání této metody rozšíření vypadá stejně jako volání libovolné metody instance <xref:System.String>, která vyžaduje jeden parametr:

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. Deklarujte další řetězcovou proměnnou a zavolejte metodu znovu, abyste viděli, že funguje s libovolným řetězcem.

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     Výsledek tohoto času: `or not!!!`.

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

- [Postupy: Zápis rozšiřující metody](./how-to-write-an-extension-method.md)
- [Rozšiřující metody](./extension-methods.md)
- [Obor v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
