---
title: Jak načíst kolekci atributů (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 02871b38c3b1a1ed64fa6ca808e193811cd7f721
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347646"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a>Jak načíst kolekci atributů (LINQ to XML) (C#)
Toto téma představuje metodu <xref:System.Xml.Linq.XElement.Attributes%2A>. Tato metoda načte atributy elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak iterovat kolekcí atributů elementu.  
  
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
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md)
