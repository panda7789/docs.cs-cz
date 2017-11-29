---
title: "Postupy: vytvoření hierarchii pomocí seskupení (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0213d59e-5f76-438c-9cab-4bf11f7b971d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aa0272e03022038c6dc464516998fad948f30e59
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-hierarchy-using-grouping-c"></a><span data-ttu-id="c84a3-102">Postupy: vytvoření hierarchii pomocí seskupení (C#)</span><span class="sxs-lookup"><span data-stu-id="c84a3-102">How to: Create Hierarchy Using Grouping (C#)</span></span>
<span data-ttu-id="c84a3-103">Tento příklad ukazuje, jak k seskupení dat a pak generování XML podle seskupení.</span><span class="sxs-lookup"><span data-stu-id="c84a3-103">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c84a3-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c84a3-104">Example</span></span>  
 <span data-ttu-id="c84a3-105">Tato data příklad první skupin podle kategorií, pak generuje nový soubor XML, ve kterém hierarchii XML odráží seskupení.</span><span class="sxs-lookup"><span data-stu-id="c84a3-105">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="c84a3-106">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Číselná Data (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c84a3-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement doc = XElement.Load("Data.xml");  
var newData =  
    new XElement("Root",  
        from data in doc.Elements("Data")  
        group data by (string)data.Element("Category") into groupedData  
        select new XElement("Group",  
            new XAttribute("ID", groupedData.Key),  
            from g in groupedData  
            select new XElement("Data",  
                g.Element("Quantity"),  
                g.Element("Price")  
            )  
        )  
    );  
Console.WriteLine(newData);  
```  
  
 <span data-ttu-id="c84a3-107">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c84a3-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Group ID="A">  
    <Data>  
      <Quantity>3</Quantity>  
      <Price>24.50</Price>  
    </Data>  
    <Data>  
      <Quantity>5</Quantity>  
      <Price>4.95</Price>  
    </Data>  
    <Data>  
      <Quantity>3</Quantity>  
      <Price>66.00</Price>  
    </Data>  
    <Data>  
      <Quantity>15</Quantity>  
      <Price>29.00</Price>  
    </Data>  
  </Group>  
  <Group ID="B">  
    <Data>  
      <Quantity>1</Quantity>  
      <Price>89.99</Price>  
    </Data>  
    <Data>  
      <Quantity>10</Quantity>  
      <Price>.99</Price>  
    </Data>  
    <Data>  
      <Quantity>8</Quantity>  
      <Price>6.99</Price>  
    </Data>  
  </Group>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c84a3-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="c84a3-108">See Also</span></span>  
 [<span data-ttu-id="c84a3-109">Pokročilé techniky dotazu (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c84a3-109">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
