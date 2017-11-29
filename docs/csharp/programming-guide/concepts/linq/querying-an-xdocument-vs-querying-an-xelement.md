---
title: "Dotazování XDocument vs. Dotazování XElement (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b315a9b298a786cbb78eb18efd4ecf3ea8e0b90c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a><span data-ttu-id="2c5ab-102">Dotazování XDocument vs. Dotazování XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="2c5ab-102">Querying an XDocument vs. Querying an XElement (C#)</span></span>
<span data-ttu-id="2c5ab-103">Při načtení dokumentu prostřednictvím <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, si všimnete, že budete muset psát dotazy trochu jinak než při načtení prostřednictvím <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2c5ab-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="2c5ab-104">Porovnání XDocument.Load a XElement.Load</span><span class="sxs-lookup"><span data-stu-id="2c5ab-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="2c5ab-105">Při načítání dokumentu XML do <xref:System.Xml.Linq.XElement> prostřednictvím <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement> v kořenovém adresáři soubor XML obsahuje stromu kořenový element dokumentu načíst.</span><span class="sxs-lookup"><span data-stu-id="2c5ab-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="2c5ab-106">Ale při načtení dokumentem XML do <xref:System.Xml.Linq.XDocument> prostřednictvím <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, kořenu stromu je <xref:System.Xml.Linq.XDocument> uzel a kořenový element dokumentu načíst je jeden povolený podřízeným <xref:System.Xml.Linq.XElement> uzlu <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="2c5ab-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="2c5ab-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Osy fungovat relativně k kořenového uzlu.</span><span class="sxs-lookup"><span data-stu-id="2c5ab-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="2c5ab-108">Tento příklad první načte stromu XML pomocí <xref:System.Xml.Linq.XElement.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="2c5ab-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="2c5ab-109">Následně dotazy pro podřízené elementy kořenu stromu.</span><span class="sxs-lookup"><span data-stu-id="2c5ab-109">It then queries for the child elements of the root of the tree.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="2c5ab-110">Podle očekávání, tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2c5ab-110">As expected, this example produces the following output:</span></span>  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="2c5ab-111">Následující příklad je stejný jako ten výše, s výjimkou načtenou ve stromové struktuře XML <xref:System.Xml.Linq.XDocument> místo <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="2c5ab-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="2c5ab-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2c5ab-112">This example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="2c5ab-113">Všimněte si, že stejný dotaz vrátí ten `Root` uzlu namísto tří podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="2c5ab-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="2c5ab-114">Jeden z přístupů k práci s to je používat <xref:System.Xml.Linq.XDocument.Root%2A> vlastnost před přístupem k metody osy, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2c5ab-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="2c5ab-115">Tento dotaz nyní provádí stejným způsobem jako dotaz ve stromové struktuře root v <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="2c5ab-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="2c5ab-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2c5ab-116">The example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c5ab-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c5ab-117">See Also</span></span>  
 [<span data-ttu-id="2c5ab-118">Základní dotazy (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2c5ab-118">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
