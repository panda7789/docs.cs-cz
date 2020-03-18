---
title: Jak načíst kolekci atributů (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 02871b38c3b1a1ed64fa6ca808e193811cd7f721
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347646"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="1effc-102">Jak načíst kolekci atributů (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1effc-102">How to retrieve a collection of attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="1effc-103">Toto téma <xref:System.Xml.Linq.XElement.Attributes%2A> představuje metodu.</span><span class="sxs-lookup"><span data-stu-id="1effc-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="1effc-104">Tato metoda načte atributy prvku.</span><span class="sxs-lookup"><span data-stu-id="1effc-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1effc-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1effc-105">Example</span></span>  
 <span data-ttu-id="1effc-106">Následující příklad ukazuje, jak iterate prostřednictvím kolekce atributů prvku.</span><span class="sxs-lookup"><span data-stu-id="1effc-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="1effc-107">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1effc-107">This code produces the following output:</span></span>  
  
```output  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="1effc-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="1effc-108">See also</span></span>

- [<span data-ttu-id="1effc-109">LINQ na osy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="1effc-109">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
