---
title: Přístup k atributům pomocí reflexe (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: dca476eef392a2f57d0c66727c53e0e53310d679
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>Přístup k atributům pomocí reflexe (Visual Basic)
Nízké hodnoty bez nějakým způsobem načtení těchto informací a funguje na něm může být skutečnost, že můžete definovat vlastní atributy a umístěte je do vašeho zdrojového kódu. Pomocí reflexe můžete načíst informace, které je definovaný s vlastní atributy. Metoda klíče je `GetCustomAttributes`, která vrací pole objektů, které jsou ekvivalenty běhu atributů zdrojového kódu. Tato metoda má několik přetížené verzí. Další informace naleznete v tématu <xref:System.Attribute>.  
  
 Specifikace atributu jako:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 je ekvivalentní k tomuto:  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 Však není kód spustí, dokud `SampleClass` je dotazován na atributy. Volání metody `GetCustomAttributes` na `SampleClass` způsobí, že `Author` objekt, který má být vytvořená a inicializovat jako výše. Pokud třída má další atributy, se vytvářejí podobně jako jiné objekty atribut. `GetCustomAttributes` Vrátí `Author` objekt a všechny další objekty atribut v matici. Pak můžete Iterujte přes toto pole, určit atributy, které byly použity na základě typu jednotlivých prvků pole a extrahovat informace z atributů objektů.  
  
## <a name="example"></a>Příklad  
 Zde je kompletní příklad. Vlastní atribut je definován, použít pro několik entit a načteny prostřednictvím reflexe.  
  
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
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Průvodce programováním v jazyce Visual Basic](../../../../visual-basic/programming-guide/index.md)  
 [Načítání informací uložených v atributech](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
 [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Atributy (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [Vytváření vlastních atributů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
