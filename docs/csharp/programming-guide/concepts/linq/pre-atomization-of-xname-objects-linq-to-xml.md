---
title: Předběžné atomizace XName objektů (technologie LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 8d793dcdfd2669fa96c92be0e0e3c3ebb8f38d0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329300"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a><span data-ttu-id="b1b21-102">Předběžné atomizace XName objektů (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b1b21-102">Pre-Atomization of XName Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b1b21-103">Jeden způsob, jak zlepšit výkon v technologii LINQ to XML je předem atomizovat <xref:System.Xml.Linq.XName> objekty.</span><span class="sxs-lookup"><span data-stu-id="b1b21-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="b1b21-104">Předběžné atomizace znamená, že přiřadíte řetězec tak, aby <xref:System.Xml.Linq.XName> objektu před vytvořením stromu XML pomocí konstruktorů systému <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="b1b21-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="b1b21-105">Potom neprochází řetězec konstruktoru, které byste použili implicitní převod z řetězce na <xref:System.Xml.Linq.XName>, předáte inicializovaná <xref:System.Xml.Linq.XName> objektu.</span><span class="sxs-lookup"><span data-stu-id="b1b21-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="b1b21-106">To zvyšuje výkon, když vytvoříte velké stromu XML, ve které se opakují konkrétní názvy.</span><span class="sxs-lookup"><span data-stu-id="b1b21-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="b1b21-107">K tomuto účelu deklarace a inicializace <xref:System.Xml.Linq.XName> objekty předtím, než můžete vytvořit stromu XML a potom pomocí <xref:System.Xml.Linq.XName> objekty místo zadání řetězce pro název elementu a atributu.</span><span class="sxs-lookup"><span data-stu-id="b1b21-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="b1b21-108">Tento postup mohou přinést výrazné zvýšení výkonu při vytváření velký počet elementů (nebo atributy) se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="b1b21-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="b1b21-109">Měli byste otestovat před atomizace s váš scénář se rozhodnout, pokud by ji použít.</span><span class="sxs-lookup"><span data-stu-id="b1b21-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1b21-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1b21-110">Example</span></span>  
 <span data-ttu-id="b1b21-111">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="b1b21-111">The following example demonstrates this.</span></span>  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="b1b21-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b1b21-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="b1b21-113">Následující příklad ukazuje stejným způsobem, kde je v dokumentu XML v oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="b1b21-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XName Root = aw + "Root";  
XName Data = aw + "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XAttribute(XNamespace.Xmlns + "aw", aw),  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="b1b21-114">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b1b21-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="b1b21-115">V následujícím příkladu je více podobná co pravděpodobně dojde v reálném světě.</span><span class="sxs-lookup"><span data-stu-id="b1b21-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="b1b21-116">V tomto příkladu je obsah elementu poskytl dotazu:</span><span class="sxs-lookup"><span data-stu-id="b1b21-116">In this example, the content of the element is supplied by a query:</span></span>  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
DateTime t1 = DateTime.Now;  
XElement root = new XElement(Root,  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement(Data,  
        new XAttribute(ID, i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
 <span data-ttu-id="b1b21-117">Předchozí příklad provádí lépe než následující příklad, ve které nejsou předem atomized názvy:</span><span class="sxs-lookup"><span data-stu-id="b1b21-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```csharp  
DateTime t1 = DateTime.Now;  
XElement root = new XElement("Root",  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement("Data",  
        new XAttribute("ID", i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1b21-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1b21-118">See Also</span></span>  
 [<span data-ttu-id="b1b21-119">Výkon (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b1b21-119">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)  
 [<span data-ttu-id="b1b21-120">Atomized XName a XNamespace objekty (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b1b21-120">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
