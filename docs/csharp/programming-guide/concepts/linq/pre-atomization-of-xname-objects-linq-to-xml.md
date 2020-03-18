---
title: Před rozprašování objektů XName (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 2fd754a352bd2988e52ec9c67a9915a8e587b107
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591492"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a><span data-ttu-id="8b200-102">Před rozprašování objektů XName (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8b200-102">Pre-Atomization of XName Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="8b200-103">Jedním ze způsobů, jak zlepšit výkon v LINQ <xref:System.Xml.Linq.XName> na XML je pre-atomize objekty.</span><span class="sxs-lookup"><span data-stu-id="8b200-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="8b200-104">Před rozprašováním znamená, že před <xref:System.Xml.Linq.XName> vytvořením stromu XML přiřadíte objektu <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> řetězec pomocí konstruktorů tříd a.</span><span class="sxs-lookup"><span data-stu-id="8b200-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="8b200-105">Potom namísto předání řetězce konstruktoru, který by použil implicitní převod z řetězce do <xref:System.Xml.Linq.XName>, předáte inicializovaný <xref:System.Xml.Linq.XName> objekt.</span><span class="sxs-lookup"><span data-stu-id="8b200-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="8b200-106">To zlepšuje výkon při vytváření velkého stromu XML, ve kterém se opakují určité názvy.</span><span class="sxs-lookup"><span data-stu-id="8b200-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="8b200-107">Chcete-li to provést, deklarujte a inicializovat <xref:System.Xml.Linq.XName> objekty před vytvořením stromu XML a potom použijte <xref:System.Xml.Linq.XName> objekty namísto určení řetězců pro názvy prvků a atributů.</span><span class="sxs-lookup"><span data-stu-id="8b200-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="8b200-108">Tato technika může přinést významné zvýšení výkonu, pokud vytváříte velký počet prvků (nebo atributů) se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="8b200-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="8b200-109">Měli byste otestovat pre-rozprašování s vaším scénářem rozhodnout, zda byste měli použít.</span><span class="sxs-lookup"><span data-stu-id="8b200-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b200-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b200-110">Example</span></span>  
 <span data-ttu-id="8b200-111">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="8b200-111">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="8b200-112">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8b200-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="8b200-113">Následující příklad ukazuje stejnou techniku, kde je dokument XML v oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="8b200-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
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
  
 <span data-ttu-id="8b200-114">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8b200-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="8b200-115">Následující příklad je více podobný tomu, co se pravděpodobně setkáte v reálném světě.</span><span class="sxs-lookup"><span data-stu-id="8b200-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="8b200-116">V tomto příkladu je obsah prvku dodáván dotazem:</span><span class="sxs-lookup"><span data-stu-id="8b200-116">In this example, the content of the element is supplied by a query:</span></span>  
  
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
  
 <span data-ttu-id="8b200-117">Předchozí příklad provádí lépe než v následujícím příkladu, ve kterém názvy nejsou pre-atomized:</span><span class="sxs-lookup"><span data-stu-id="8b200-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b200-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b200-118">See also</span></span>

- [<span data-ttu-id="8b200-119">Atomized XName a XNamespace objekty (LINQ na XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8b200-119">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>](./atomized-xname-and-xnamespace-objects-linq-to-xml.md)
