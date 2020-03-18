---
title: Jak načíst mělkou hodnotu prvku (C#)
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: b9b69b5a18106f82d13cb54208c2362f8239711e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347450"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a>Jak načíst mělkou hodnotu prvku (C#)
Toto téma ukazuje, jak získat mělkou hodnotu prvku. Mělká hodnota je pouze hodnota konkrétního prvku, na rozdíl od hluboké hodnoty, která zahrnuje hodnoty všech potomkových prvků zřetězených do jednoho řetězce.  
  
 Při načtení hodnoty prvku pomocí přetypování nebo <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnosti načtete hlubokou hodnotu. Chcete-li načíst mělkou `ShallowValue` hodnotu, můžete použít metodu rozšíření, jak je znázorněno v následujícím příkladu. Načítání mělké hodnoty je užitečné, pokud chcete vybrat prvky na základě jejich obsahu.  
  
 Následující příklad deklaruje metodu rozšíření, která načte mělkou hodnotu prvku. Potom používá metodu rozšíření v dotazu k zobrazení seznamu všech prvků, které obsahují vypočtenou hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující textový soubor Report.xml je zdrojem pro tento příklad.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```csharp  
public static class MyExtensions  
{  
    public static string ShallowValue(this XElement xe)  
    {  
        return xe  
               .Nodes()  
               .OfType<XText>()  
               .Aggregate(new StringBuilder(),  
                          (s, c) => s.Append(c),  
                          s => s.ToString());  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement root = XElement.Load("Report.xml");  
  
        IEnumerable<XElement> query = from el in root.Descendants()  
                                      where el.ShallowValue().StartsWith("=")  
                                      select el;  
  
        foreach (var q in query)  
        {  
            Console.WriteLine("{0}{1}{2}",  
                q.Name.ToString().PadRight(8),  
                q.Attribute("Name").ToString().PadRight(20),  
                q.ShallowValue());  
        }  
    }  
}  
```  
  
 Tento příklad vytváří následující výstup:  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a>Viz také

- [LINQ na osy XML (C#)](./linq-to-xml-axes-overview.md)
