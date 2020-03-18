---
title: Jak vytvořit hierarchii pomocí seskupení (C#)
ms.date: 07/20/2015
ms.assetid: 0213d59e-5f76-438c-9cab-4bf11f7b971d
ms.openlocfilehash: c5a96b02595446b2efa01868cc88377c3a5151c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141299"
---
# <a name="how-to-create-hierarchy-using-grouping-c"></a><span data-ttu-id="176ec-102">Jak vytvořit hierarchii pomocí seskupení (C#)</span><span class="sxs-lookup"><span data-stu-id="176ec-102">How to create hierarchy using grouping (C#)</span></span>
<span data-ttu-id="176ec-103">Tento příklad ukazuje, jak seskupit data a potom generovat XML na základě seskupení.</span><span class="sxs-lookup"><span data-stu-id="176ec-103">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="176ec-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="176ec-104">Example</span></span>  
 <span data-ttu-id="176ec-105">Tento příklad nejprve seskupí data podle kategorie a poté vygeneruje nový soubor XML, ve kterém hierarchie XML odráží seskupení.</span><span class="sxs-lookup"><span data-stu-id="176ec-105">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="176ec-106">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Numerická data (LINQ to XML).](./sample-xml-file-numerical-data-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="176ec-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="176ec-107">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="176ec-107">This example produces the following output:</span></span>  
  
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
