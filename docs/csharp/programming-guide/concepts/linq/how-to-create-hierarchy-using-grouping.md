---
title: 'Postupy: vytvoření hierarchii pomocí seskupení (C#)'
ms.date: 07/20/2015
ms.assetid: 0213d59e-5f76-438c-9cab-4bf11f7b971d
ms.openlocfilehash: 9ad9ea723a54b50c3d5b047408fce760a8f53273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327509"
---
# <a name="how-to-create-hierarchy-using-grouping-c"></a><span data-ttu-id="c8dc4-102">Postupy: vytvoření hierarchii pomocí seskupení (C#)</span><span class="sxs-lookup"><span data-stu-id="c8dc4-102">How to: Create Hierarchy Using Grouping (C#)</span></span>
<span data-ttu-id="c8dc4-103">Tento příklad ukazuje, jak k seskupení dat a pak generování XML podle seskupení.</span><span class="sxs-lookup"><span data-stu-id="c8dc4-103">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8dc4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c8dc4-104">Example</span></span>  
 <span data-ttu-id="c8dc4-105">Tato data příklad první skupin podle kategorií, pak generuje nový soubor XML, ve kterém hierarchii XML odráží seskupení.</span><span class="sxs-lookup"><span data-stu-id="c8dc4-105">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="c8dc4-106">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Číselná Data (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c8dc4-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="c8dc4-107">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c8dc4-107">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c8dc4-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8dc4-108">See Also</span></span>  
 [<span data-ttu-id="c8dc4-109">Pokročilé techniky dotazu (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c8dc4-109">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
