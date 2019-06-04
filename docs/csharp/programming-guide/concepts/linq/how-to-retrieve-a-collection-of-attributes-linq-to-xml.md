---
title: 'Postupy: Načtení kolekce atributů (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: d561c3bbebbf57c88ccc9043449540bca06e33fb
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486350"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="e1a67-102">Postupy: Načtení kolekce atributů (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e1a67-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="e1a67-103">Toto téma představuje <xref:System.Xml.Linq.XElement.Attributes%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e1a67-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="e1a67-104">Tato metoda načte atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="e1a67-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1a67-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1a67-105">Example</span></span>  
 <span data-ttu-id="e1a67-106">Následující příklad ukazuje, jak k iteraci v rámci kolekce atributů elementu.</span><span class="sxs-lookup"><span data-stu-id="e1a67-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="e1a67-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e1a67-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1a67-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1a67-108">See also</span></span>

- [<span data-ttu-id="e1a67-109">Osy LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e1a67-109">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)
