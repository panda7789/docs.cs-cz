---
title: Přístup k atributům pomocí reflexe (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: e5cbce8529cc7554a8edacb2d83dabb73a495eec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827642"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>Přístup k atributům pomocí reflexe (Visual Basic)
Fakt, že můžete definovat vlastní atributy a umístit je do zdrojového kódu by nízké hodnoty bez nějaký způsob načtení těchto informací a funguje na něj. Pomocí reflexe můžete načíst informace, které se definoval pomocí vlastních atributů. Metoda klíče `GetCustomAttributes`, která vrací pole objektů, které jsou za běhu ekvivalenty atributy zdrojového kódu. Tato metoda má několik přetížených verzí. Další informace naleznete v tématu <xref:System.Attribute>.  
  
 Specifikace atribut jako:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 je koncepčním ekvivalentem tohoto:  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 Však není spuštěn kód do `SampleClass` dotaz na atributy. Volání `GetCustomAttributes` na `SampleClass` způsobí, že `Author` objekt má být vytvořen a inicializován, jak je uvedeno výše. Pokud třída má další atributy, dalších atributů objektů jsou vytvořeny podobně. `GetCustomAttributes` Vrátí `Author` objektu a dalších atributů objektů v poli. Můžete iterovat přes toto pole určit atributy, které byly použity na základě typu každý prvek pole a extrahovat informace z atributů objektů.  
  
## <a name="example"></a>Příklad  
 Tady je úplný příklad. Vlastní atribut je definován, použít pro několik entit a načteny prostřednictvím reflexe.  
  
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
- [Průvodce programováním v jazyce Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Načítání informací uložených v atributech](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atributy (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
