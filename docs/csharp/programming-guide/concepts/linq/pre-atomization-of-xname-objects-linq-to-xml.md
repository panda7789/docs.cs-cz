---
title: Předběžná Atomace objektů XName (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 2fd754a352bd2988e52ec9c67a9915a8e587b107
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591492"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a><span data-ttu-id="73b8d-102">Předběžná Atomace objektů XName (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="73b8d-102">Pre-Atomization of XName Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="73b8d-103">Jedním ze způsobů, jak zlepšit výkon v LINQ to XML, je atomizovat <xref:System.Xml.Linq.XName> objekty.</span><span class="sxs-lookup"><span data-stu-id="73b8d-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="73b8d-104">Před vytvořením stromu XML pomocí konstruktorů <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XElement> tříd a <xref:System.Xml.Linq.XAttribute> se před vytvořením stromu XML přiřadí řetězec k objektu.</span><span class="sxs-lookup"><span data-stu-id="73b8d-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="73b8d-105">Místo předání řetězce konstruktoru, který by použil implicitní převod z řetězce na <xref:System.Xml.Linq.XName>, předáte inicializovaný <xref:System.Xml.Linq.XName> objekt.</span><span class="sxs-lookup"><span data-stu-id="73b8d-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="73b8d-106">To zlepšuje výkon při vytváření velkého stromu XML, ve kterém se konkrétní názvy opakují.</span><span class="sxs-lookup"><span data-stu-id="73b8d-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="73b8d-107">Chcete-li to provést, deklarujete <xref:System.Xml.Linq.XName> a inicializujete objekty před vytvořením stromu XML a pak <xref:System.Xml.Linq.XName> použijte objekty namísto zadávání řetězců pro element a názvy atributů.</span><span class="sxs-lookup"><span data-stu-id="73b8d-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="73b8d-108">Tato technika může přinést výrazné zvýšení výkonu, pokud vytváříte velký počet prvků (nebo atributů) se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="73b8d-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="73b8d-109">Před tím, než se rozhodnete, jestli ho chcete použít, byste měli testovat předběžnou atomaci ve svém scénáři.</span><span class="sxs-lookup"><span data-stu-id="73b8d-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73b8d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="73b8d-110">Example</span></span>  
 <span data-ttu-id="73b8d-111">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="73b8d-111">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="73b8d-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="73b8d-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="73b8d-113">Následující příklad ukazuje stejnou techniku, kde je dokument XML v oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="73b8d-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
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
  
 <span data-ttu-id="73b8d-114">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="73b8d-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="73b8d-115">Následující příklad se podobá tomu, co se vám pravděpodobně setkáte v reálném světě.</span><span class="sxs-lookup"><span data-stu-id="73b8d-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="73b8d-116">V tomto příkladu je obsah elementu dodán dotazem:</span><span class="sxs-lookup"><span data-stu-id="73b8d-116">In this example, the content of the element is supplied by a query:</span></span>  
  
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
  
 <span data-ttu-id="73b8d-117">Předchozí příklad provede lepší, než následující příklad, ve kterém názvy nejsou předběžně atomované:</span><span class="sxs-lookup"><span data-stu-id="73b8d-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73b8d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73b8d-118">See also</span></span>

- [<span data-ttu-id="73b8d-119">Atomované XName a objekty XNamespace (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="73b8d-119">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>](./atomized-xname-and-xnamespace-objects-linq-to-xml.md)
