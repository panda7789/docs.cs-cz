---
title: 'Postupy: Načtení kolekce atributů (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: d535f56507812855f08b31417124b4408dfea017
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599813"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="0a384-102">Postupy: Načtení kolekce atributů (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0a384-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0a384-103">Toto téma představuje <xref:System.Xml.Linq.XElement.Attributes%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0a384-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="0a384-104">Tato metoda načte atributy elementu.</span><span class="sxs-lookup"><span data-stu-id="0a384-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a384-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a384-105">Example</span></span>  
 <span data-ttu-id="0a384-106">Následující příklad ukazuje, jak k iteraci v rámci kolekce atributů elementu.</span><span class="sxs-lookup"><span data-stu-id="0a384-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="0a384-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0a384-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a384-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a384-108">See also</span></span>

- [<span data-ttu-id="0a384-109">Osy LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0a384-109">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
