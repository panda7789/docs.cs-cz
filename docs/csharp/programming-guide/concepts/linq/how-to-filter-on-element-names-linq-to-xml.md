---
title: 'Postupy: filtru na názvy elementu (technologie LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: f54b9008ff90922e2c275c51c6965c92cb4e6a36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323258"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="9cfd2-102">Postupy: filtru na názvy elementu (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9cfd2-102">How to: Filter on Element Names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="9cfd2-103">Při volání jedné z metod, které vracejí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, můžete filtrovat podle názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="9cfd2-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cfd2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9cfd2-104">Example</span></span>  
 <span data-ttu-id="9cfd2-105">Tento příklad načte kolekce potomky, které je filtrován tak, aby obsahovala pouze následníky se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="9cfd2-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="9cfd2-106">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: typické nákupní objednávka (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="9cfd2-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="9cfd2-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9cfd2-107">This code produces the following output:</span></span>  
  
```  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="9cfd2-108">Jiné metody, které vracejí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> kolekce postupují stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="9cfd2-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="9cfd2-109">Jejich podpisy jsou podobné <xref:System.Xml.Linq.XContainer.Elements%2A> a <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="9cfd2-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="9cfd2-110">Následuje úplný seznam metod, které mají podobné podpisy metoda:</span><span class="sxs-lookup"><span data-stu-id="9cfd2-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
-   <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="9cfd2-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="9cfd2-111">Example</span></span>  
 <span data-ttu-id="9cfd2-112">Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9cfd2-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="9cfd2-113">Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="9cfd2-113">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="9cfd2-114">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: typické nákupní objednávka v Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="9cfd2-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="9cfd2-115">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9cfd2-115">This code produces the following output:</span></span>  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="9cfd2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cfd2-116">See Also</span></span>  
 [<span data-ttu-id="9cfd2-117">Technologie LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="9cfd2-117">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
