---
title: "Přístup k atributům pomocí reflexe (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a4397200b5a2aa5f337dd3479b5405c1a9f245a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="66583-102">Přístup k atributům pomocí reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66583-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>
<span data-ttu-id="66583-103">Nízké hodnoty bez nějakým způsobem načtení těchto informací a funguje na něm může být skutečnost, že můžete definovat vlastní atributy a umístěte je do vašeho zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="66583-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="66583-104">Pomocí reflexe můžete načíst informace, které je definovaný s vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="66583-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="66583-105">Metoda klíče je `GetCustomAttributes`, která vrací pole objektů, které jsou ekvivalenty běhu atributů zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="66583-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="66583-106">Tato metoda má několik přetížené verzí.</span><span class="sxs-lookup"><span data-stu-id="66583-106">This method has several overloaded versions.</span></span> <span data-ttu-id="66583-107">Další informace naleznete v tématu <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="66583-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="66583-108">Specifikace atributu jako:</span><span class="sxs-lookup"><span data-stu-id="66583-108">An attribute specification such as:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="66583-109">je ekvivalentní k tomuto:</span><span class="sxs-lookup"><span data-stu-id="66583-109">is conceptually equivalent to this:</span></span>  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 <span data-ttu-id="66583-110">Však není kód spustí, dokud `SampleClass` je dotazován na atributy.</span><span class="sxs-lookup"><span data-stu-id="66583-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="66583-111">Volání metody `GetCustomAttributes` na `SampleClass` způsobí, že `Author` objekt, který má být vytvořená a inicializovat jako výše.</span><span class="sxs-lookup"><span data-stu-id="66583-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="66583-112">Pokud třída má další atributy, se vytvářejí podobně jako jiné objekty atribut.</span><span class="sxs-lookup"><span data-stu-id="66583-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="66583-113">`GetCustomAttributes`Vrátí `Author` objekt a všechny další objekty atribut v matici.</span><span class="sxs-lookup"><span data-stu-id="66583-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="66583-114">Pak můžete Iterujte přes toto pole, určit atributy, které byly použity na základě typu jednotlivých prvků pole a extrahovat informace z atributů objektů.</span><span class="sxs-lookup"><span data-stu-id="66583-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66583-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="66583-115">Example</span></span>  
 <span data-ttu-id="66583-116">Zde je kompletní příklad.</span><span class="sxs-lookup"><span data-stu-id="66583-116">Here is a complete example.</span></span> <span data-ttu-id="66583-117">Vlastní atribut je definován, použít pro několik entit a načteny prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="66583-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="66583-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="66583-118">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="66583-119">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66583-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="66583-120">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="66583-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
 [<span data-ttu-id="66583-121">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66583-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="66583-122">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66583-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="66583-123">Vytváření vlastních atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66583-123">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
