---
title: 'Postupy: Serializace pomocí třídy XmlSerializer'
ms.date: 07/20/2015
ms.assetid: cace24eb-0f43-4016-8e4b-199e5ef73a1c
ms.openlocfilehash: 2265ad2129a4dc243f82c562058dbe5436fa418b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397762"
---
# <a name="how-to-serialize-using-xmlserializer-visual-basic"></a><span data-ttu-id="8e188-102">Postupy: serializace pomocí XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e188-102">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>
<span data-ttu-id="8e188-103">Toto téma ukazuje příklad, který serializace a deserializace používá <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="8e188-103">This topic shows an example that serializes and deserializes using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e188-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e188-104">Example</span></span>  
 <span data-ttu-id="8e188-105">Následující příklad vytvoří počet objektů, které obsahují <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="8e188-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="8e188-106">Pak je zaserializace do paměťového proudu a pak je deserializace z paměťového proudu.</span><span class="sxs-lookup"><span data-stu-id="8e188-106">It then serializes them to a memory stream, and then deserializes them from the memory stream.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Linq  
Imports System.IO  
Imports System.Runtime.Serialization  
Imports System.Xml.Serialization  
  
Public Class XElementContainer  
    Public member As XElement  
  
    Public Sub XElementContainer()  
        member = XLinqTest.CreateXElement()  
    End Sub  
  
    Overrides Function ToString() As String  
        Return member.ToString()  
    End Function  
End Class  
  
Public Class XElementNullContainer  
    Public member As XElement  
  
    Public Sub XElementNullContainer()  
        member = Nothing  
    End Sub  
End Class  
  
Public Class XLinqTest  
    Shared Sub Main()  
        Test(Of XElementNullContainer)(New XElementNullContainer())  
        Test(Of XElement)(CreateXElement())  
        Test(Of XElementContainer)(New XElementContainer())  
    End Sub  
  
    Public Shared Function CreateXElement() As XElement  
        Dim ns As XNamespace = "http://www.adventure-works.com"  
        Return New XElement(ns + "aw")  
    End Function  
  
    Public Shared Sub Test(Of T)(ByRef obj)  
        Using stream As New MemoryStream()  
            Dim s As XmlSerializer = New XmlSerializer(GetType(T))  
            Console.WriteLine("Testing for type: {0}", GetType(T))  
            s.Serialize(XmlWriter.Create(stream), obj)  
            stream.Flush()  
            stream.Seek(0, SeekOrigin.Begin)  
            Dim o As Object = s.Deserialize(XmlReader.Create(stream))  
            Console.WriteLine("  Deserialized type: {0}", o.GetType())  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="8e188-107">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8e188-107">This example produces the following output:</span></span>  
  
```console  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e188-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e188-108">See also</span></span>

- [<span data-ttu-id="8e188-109">Serializace grafů objektů, které obsahují objekty XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e188-109">Serializing Object Graphs that Contain XElement Objects (Visual Basic)</span></span>](serializing-object-graphs-that-contain-xelement-objects.md)
