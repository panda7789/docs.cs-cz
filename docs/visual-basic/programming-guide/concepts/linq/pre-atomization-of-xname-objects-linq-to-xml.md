---
title: Předběžná atomizace objektů XName (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: 250b7aa8060c8196c28725fded090e2a63a0ee54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665842"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="d621e-102">Předběžná atomizace objektů XName (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d621e-102">Pre-Atomization of XName Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="d621e-103">Jedním ze způsobů ke zlepšení výkonu v technologii LINQ to XML je předem atomizovat <xref:System.Xml.Linq.XName> objekty.</span><span class="sxs-lookup"><span data-stu-id="d621e-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="d621e-104">Předběžná atomizace znamená, že přiřadíte řetězec na <xref:System.Xml.Linq.XName> objektu před vytvořením stromu XML pomocí konstruktory <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="d621e-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="d621e-105">Pak namísto předáním řetězce do konstruktoru, který byste použili implicitní převod z řetězce na <xref:System.Xml.Linq.XName>, předáte inicializovaná zpráva <xref:System.Xml.Linq.XName> objektu.</span><span class="sxs-lookup"><span data-stu-id="d621e-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="d621e-106">To zlepšuje výkon při vytváření velké stromu XML, ve které se opakují konkrétní názvy.</span><span class="sxs-lookup"><span data-stu-id="d621e-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="d621e-107">K tomuto účelu deklarujete a inicializujete <xref:System.Xml.Linq.XName> objekty před vytvoření stromu XML a pak použít <xref:System.Xml.Linq.XName> objekty místo zadávání řetězců pro názvy prvků a atributů.</span><span class="sxs-lookup"><span data-stu-id="d621e-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="d621e-108">Tato technika může přinést výrazné zvýšení výkonu při vytváření velký počet elementů (nebo atributy) se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="d621e-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="d621e-109">Předběžná atomizace byste měli testovat s váš scénář se rozhodnout, pokud byste ji měli používat.</span><span class="sxs-lookup"><span data-stu-id="d621e-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d621e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="d621e-110">Example</span></span>  
 <span data-ttu-id="d621e-111">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="d621e-111">The following example demonstrates this.</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="d621e-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d621e-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="d621e-113">Následující příklad ukazuje stejný postup, pokud dokument XML je v oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="d621e-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="d621e-114">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d621e-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="d621e-115">Následující příklad je podobné co se pravděpodobně setkáte v reálném světě.</span><span class="sxs-lookup"><span data-stu-id="d621e-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="d621e-116">V tomto příkladu obsah elementu, který je poskytnut pomocí dotazu:</span><span class="sxs-lookup"><span data-stu-id="d621e-116">In this example, the content of the element is supplied by a query:</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 <span data-ttu-id="d621e-117">V předchozím příkladu vrací lepší výsledky než následující příklad, ve kterém názvy nejsou předem atomizované objekty:</span><span class="sxs-lookup"><span data-stu-id="d621e-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="d621e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d621e-118">See also</span></span>

- [<span data-ttu-id="d621e-119">Výkon (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d621e-119">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
- [<span data-ttu-id="d621e-120">Atomizované objekty XName a Xnamespace (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d621e-120">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
