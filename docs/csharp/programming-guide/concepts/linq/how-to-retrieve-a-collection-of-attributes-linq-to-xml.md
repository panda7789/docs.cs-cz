---
title: 'Postupy: načtení kolekci atributů (technologie LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 73e548b100893652b63dfcc69669eabce655efa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317840"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="ac7c0-102">Postupy: načtení kolekci atributů (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ac7c0-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="ac7c0-103">Toto téma představuje <xref:System.Xml.Linq.XElement.Attributes%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ac7c0-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="ac7c0-104">Tato metoda načte atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="ac7c0-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac7c0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac7c0-105">Example</span></span>  
 <span data-ttu-id="ac7c0-106">Následující příklad ukazuje, jak k iteraci v rámci kolekce atributů elementu.</span><span class="sxs-lookup"><span data-stu-id="ac7c0-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
```csharp  
XElement val = new XElement("Value",  
    new XAttribute("ID", "1243"),  
    new XAttribute("Type", "int"),  
    new XAttribute("ConvertableTo", "double"),  
    "100");  
IEnumerable<XAttribute> listOfAttributes =  
    from att in val.Attributes()  
    select att;  
foreach (XAttribute a in listOfAttributes)  
    Console.WriteLine(a);  
```  
  
 <span data-ttu-id="ac7c0-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ac7c0-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac7c0-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac7c0-108">See Also</span></span>  
 [<span data-ttu-id="ac7c0-109">Technologie LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="ac7c0-109">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
