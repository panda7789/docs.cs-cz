---
title: "Předběžné atomizace XName objektů (technologie LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 967e41afc70290a4e4bdccabb8f3f4dd4ac4f6ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>Předběžné atomizace XName objektů (technologie LINQ to XML) (Visual Basic)
Jeden způsob, jak zlepšit výkon v technologii LINQ to XML je předem atomizovat <xref:System.Xml.Linq.XName> objekty. Předběžné atomizace znamená, že přiřadíte řetězec tak, aby <xref:System.Xml.Linq.XName> objektu před vytvořením stromu XML pomocí konstruktorů systému <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> třídy. Potom neprochází řetězec konstruktoru, které byste použili implicitní převod z řetězce na <xref:System.Xml.Linq.XName>, předáte inicializovaná <xref:System.Xml.Linq.XName> objektu.  
  
 To zvyšuje výkon, když vytvoříte velké stromu XML, ve které se opakují konkrétní názvy. K tomuto účelu deklarace a inicializace <xref:System.Xml.Linq.XName> objekty předtím, než můžete vytvořit stromu XML a potom pomocí <xref:System.Xml.Linq.XName> objekty místo zadání řetězce pro název elementu a atributu. Tento postup mohou přinést výrazné zvýšení výkonu při vytváření velký počet elementů (nebo atributy) se stejným názvem.  
  
 Měli byste otestovat před atomizace s váš scénář se rozhodnout, pokud by ji použít.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje to.  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 Následující příklad ukazuje stejným způsobem, kde je v dokumentu XML v oboru názvů:  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 V následujícím příkladu je více podobná co pravděpodobně dojde v reálném světě. V tomto příkladu je obsah elementu poskytl dotazu:  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 Předchozí příklad provádí lépe než následující příklad, ve které nejsou předem atomized názvy:  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>Viz také  
 [Výkon (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)  
 [Atomized XName a XNamespace objekty (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
