---
title: Jak načíst kolekci atributů (LINQ to XML) (C#)
description: Metoda atributů v jazyce C# načítá atributy prvku. Tento LINQ to XML příklad provede iteraci kolekcí atributů elementu.
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 5994086db6133530e63eb1328a7b524d30a0797d
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103378"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a>Jak načíst kolekci atributů (LINQ to XML) (C#)
Toto téma představuje <xref:System.Xml.Linq.XElement.Attributes%2A> metodu. Tato metoda načte atributy elementu.  
  
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
  
## <a name="see-also"></a>Viz také

- [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md)
