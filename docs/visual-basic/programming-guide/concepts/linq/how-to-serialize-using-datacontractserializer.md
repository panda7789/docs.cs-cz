---
title: "Postupy: serializace použití DataContractSerializer (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecaea518-8a0f-4249-b4e5-9b3fb0cdd8ad
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e86409b3b1ff499a3be789e1a22947dff6011517
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-serialize-using-datacontractserializer-visual-basic"></a>Postupy: serializace použití DataContractSerializer (Visual Basic)
Toto téma ukazuje příklad, který serializuje a deserializuje pomocí <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří mnoho objektů, které obsahují <xref:System.Xml.Linq.XElement> objekty. Pak je serializuje do textových souborů a pak je deserializuje z textových souborů.  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Linq  
Imports System.IO  
Imports System.Runtime.Serialization  
  
Public Class XLinqTest  
    Shared Sub Main()  
        Test(Of XElement)(CreateXElement())  
        Test(Of XElementContainer)(New XElementContainer())  
        Test(Of XElementNullContainer)(New XElementNullContainer())  
    End Sub  
  
    Public Shared Sub Test(Of T)(ByRef obj)  
        Dim s As DataContractSerializer = New DataContractSerializer(GetType(T))  
        Using fs As FileStream = File.Open("test" & GetType(T).Name & ".xml", FileMode.Create)  
            Console.WriteLine("Testing for type: {0}", GetType(T))  
            s.WriteObject(fs, obj)  
        End Using  
  
        Using fs As FileStream = File.Open("test" & GetType(T).Name & ".xml", FileMode.Open)  
            Dim s2 As Object = s.ReadObject(fs)  
            If s2 Is Nothing Then  
                Console.WriteLine("  Deserialized object is null (Nothing in VB)")  
            Else  
                Console.WriteLine("  Deserialized type: {0}", s2.GetType())  
            End If  
        End Using  
    End Sub  
  
    Public Shared Function CreateXElement() As XElement  
        Return New XElement(XName.Get("NameInNamespace", "http://www.adventure-works.org"))  
    End Function  
End Class  
  
<DataContract()> _  
Public Class XElementContainer  
    <DataMember()> _  
    Public member As XElement  
  
    Public Sub XElementContainer()  
        member = XLinqTest.CreateXElement()  
    End Sub  
End Class  
  
<DataContract()> _  
Public Class XElementNullContainer  
    <DataMember()> _  
    Public member As XElement  
  
    Public Sub XElementNullContainer()  
        member = Nothing  
    End Sub  
End Class  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
  
## <a name="see-also"></a>Viz také  
 [Serializace grafů objektů, které obsahují XElement objekty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-object-graphs-that-contain-xelement-objects.md)
