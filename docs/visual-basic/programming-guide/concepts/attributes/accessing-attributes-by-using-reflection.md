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
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="e7cee-102">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7cee-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>

<span data-ttu-id="e7cee-103">Fakt, že můžete definovat vlastní atributy a umístit je do zdrojového kódu, by měl být malými hodnotami bez jakéhokoli způsobu, jak tyto informace načítat a na ni bude působit.</span><span class="sxs-lookup"><span data-stu-id="e7cee-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="e7cee-104">Pomocí reflexe můžete načíst informace, které byly definovány s vlastními atributy.</span><span class="sxs-lookup"><span data-stu-id="e7cee-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="e7cee-105">Klíčovou metodou je `GetCustomAttributes` , která vrací pole objektů, které jsou ekvivalenty zdrojového kódu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e7cee-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="e7cee-106">Tato metoda má několik přetížených verzí.</span><span class="sxs-lookup"><span data-stu-id="e7cee-106">This method has several overloaded versions.</span></span> <span data-ttu-id="e7cee-107">Další informace naleznete v tématu <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="e7cee-107">For more information, see <xref:System.Attribute>.</span></span>

<span data-ttu-id="e7cee-108">Specifikace atributu jako:</span><span class="sxs-lookup"><span data-stu-id="e7cee-108">An attribute specification such as:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

 <span data-ttu-id="e7cee-109">je koncepční ekvivalent:</span><span class="sxs-lookup"><span data-stu-id="e7cee-109">is conceptually equivalent to this:</span></span>

```vb
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")
anonymousAuthorObject.version = 1.1
```

<span data-ttu-id="e7cee-110">Kód však není proveden, dokud `SampleClass` není dotazován na atributy.</span><span class="sxs-lookup"><span data-stu-id="e7cee-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="e7cee-111">Volání `GetCustomAttributes` na způsobí, že se objekt sestrojí `SampleClass` `Author` a inicializuje podle výše uvedeného.</span><span class="sxs-lookup"><span data-stu-id="e7cee-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="e7cee-112">Pokud má třída jiné atributy, další objekty atributů jsou konstruovány podobně.</span><span class="sxs-lookup"><span data-stu-id="e7cee-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="e7cee-113">`GetCustomAttributes`pak vrátí `Author` objekt a všechny objekty atributů v poli.</span><span class="sxs-lookup"><span data-stu-id="e7cee-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="e7cee-114">Pak můžete iterovat přes toto pole, určit, jaké atributy byly aplikovány na základě typu každého prvku pole a extrahovat informace z objektů atributů.</span><span class="sxs-lookup"><span data-stu-id="e7cee-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>

## <a name="example"></a><span data-ttu-id="e7cee-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7cee-115">Example</span></span>

<span data-ttu-id="e7cee-116">Tady je kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="e7cee-116">Here is a complete example.</span></span> <span data-ttu-id="e7cee-117">Vlastní atribut je definován, aplikován na několik entit a načten prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="e7cee-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e7cee-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7cee-118">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="e7cee-119">Příručka k programování v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7cee-119">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="e7cee-120">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="e7cee-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="e7cee-121">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7cee-121">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="e7cee-122">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7cee-122">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="e7cee-123">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7cee-123">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
