---
title: Přístup k atributům pomocí reflexe
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: c0da5c4ae00eb2bc80b10f63f4bfd39763445e55
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400755"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>Přístup k atributům pomocí reflexe (Visual Basic)

Fakt, že můžete definovat vlastní atributy a umístit je do zdrojového kódu, by měl být malými hodnotami bez jakéhokoli způsobu, jak tyto informace načítat a na ni bude působit. Pomocí reflexe můžete načíst informace, které byly definovány s vlastními atributy. Klíčovou metodou je `GetCustomAttributes` , která vrací pole objektů, které jsou ekvivalenty zdrojového kódu v době běhu. Tato metoda má několik přetížených verzí. Další informace naleznete v tématu <xref:System.Attribute>.

Specifikace atributu jako:

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

 je koncepční ekvivalent:

```vb
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")
anonymousAuthorObject.version = 1.1
```

Kód však není proveden, dokud `SampleClass` není dotazován na atributy. Volání `GetCustomAttributes` na způsobí, že se objekt sestrojí `SampleClass` `Author` a inicializuje podle výše uvedeného. Pokud má třída jiné atributy, další objekty atributů jsou konstruovány podobně. `GetCustomAttributes`pak vrátí `Author` objekt a všechny objekty atributů v poli. Pak můžete iterovat přes toto pole, určit, jaké atributy byly aplikovány na základě typu každého prvku pole a extrahovat informace z objektů atributů.

## <a name="example"></a>Příklad

Tady je kompletní příklad. Vlastní atribut je definován, aplikován na několik entit a načten prostřednictvím reflexe.

```vb
' Multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName

        ' Default value
        version = 1.0
    End Sub

    Function GetName() As String
        Return name
    End Function
End Class

' Class with the Author attribute
<Author("P. Ackerman")>
Public Class FirstClass
End Class

' Class without the Author attribute
Public Class SecondClass
End Class

' Class with multiple Author attributes.
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>
Public Class ThirdClass
End Class

Class TestAuthorAttribute
    Sub Main()
        PrintAuthorInfo(GetType(FirstClass))
        PrintAuthorInfo(GetType(SecondClass))
        PrintAuthorInfo(GetType(ThirdClass))
    End Sub

    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)
        System.Console.WriteLine("Author information for {0}", t)

        ' Using reflection
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)

        ' Displaying output
        For Each attr In attrs
            Dim a As Author = CType(attr, Author)
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)
        Next
    End Sub

    ' Output:
    '   Author information for FirstClass
    '     P. Ackerman, version 1.00
    ' Author information for SecondClass
    ' Author information for ThirdClass
    '  R. Koch, version 2.00
    '  P. Ackerman, version 1.00

End Class
```

## <a name="see-also"></a>Viz také

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Příručka k programování v jazyce Visual Basic](../../index.md)
- [Načítání informací uložených v atributech](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [Reflexe (Visual Basic)](../reflection.md)
- [Atributy (Visual Basic)](../../../language-reference/attributes.md)
- [Vytváření vlastních atributů (Visual Basic)](creating-custom-attributes.md)
