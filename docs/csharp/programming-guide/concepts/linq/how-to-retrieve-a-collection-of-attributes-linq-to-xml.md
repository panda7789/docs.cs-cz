---
title: 'Postupy: Načtení kolekce atributů (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: b37600f02cd012e688d161a079c3c8647545cb2c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592660"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a>Postupy: Načtení kolekce atributů (LINQ to XML) (C#)
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
  
 Tento kód generuje následující výstup:  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md)
