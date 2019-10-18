---
title: Přístup k atributům pomocí reflexe (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: a50c308a66637768dbe0089e612fcfe73bafdfa2
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524346"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>Přístup k atributům pomocí reflexe (Visual Basic)

Fakt, že můžete definovat vlastní atributy a umístit je do zdrojového kódu, by měl být malými hodnotami bez jakéhokoli způsobu, jak tyto informace načítat a na ni bude působit. Pomocí reflexe můžete načíst informace, které byly definovány s vlastními atributy. Klíčovou metodou je `GetCustomAttributes`, která vrací pole objektů, které jsou ekvivalenty v době běhu atributů zdrojového kódu. Tato metoda má několik přetížených verzí. Další informace najdete v tématu <xref:System.Attribute>.

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

Kód však není proveden, dokud není `SampleClass` dotazování pro atributy. Volání `GetCustomAttributes` v `SampleClass` způsobí, že se objekt `Author` vytvoří a inicializuje jako výše. Pokud má třída jiné atributy, další objekty atributů jsou konstruovány podobně. `GetCustomAttributes` pak vrátí objekt `Author` a všechny objekty atributů v poli. Pak můžete iterovat přes toto pole, určit, jaké atributy byly aplikovány na základě typu každého prvku pole a extrahovat informace z objektů atributů.

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

## <a name="see-also"></a>Viz také:

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Průvodce programováním Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Načítání informací uložených v atributech](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atributy (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
