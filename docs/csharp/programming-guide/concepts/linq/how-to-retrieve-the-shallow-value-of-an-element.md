---
title: 'Postupy: Načtení mělké hodnoty elementu (C#)'
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 593fe1c22664f1e4e8322cb8816e58f4721c5bf8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667701"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a>Postupy: Načtení mělké hodnoty elementu (C#)
Toto téma ukazuje, jak získat mělké hodnoty elementu. Mělké hodnoty je hodnota konkrétní elementu, na rozdíl od hloubkové hodnotu, která obsahuje hodnoty všechny podřízené prvky, které jsou spojeny do jednoho řetězce.  
  
 Při načítání hodnotu prvku pomocí obou přetypování nebo <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnost, získáte podrobné hodnotu. K načtení mělké hodnoty, můžete použít `ShallowValue` rozšiřující metoda, jak je znázorněno v následujícím příkladu. Načtení mělké hodnoty je užitečné, pokud chcete vybrat elementy na základě jejich obsahu.  
  
 Následující příklad deklaruje metodu rozšíření, která načte mělké hodnoty elementu. Pak používá metody rozšíření v dotazu k výpisu všech prvků, které obsahují počítané hodnoty.  
  
## <a name="example"></a>Příklad  
 Následující textový soubor, Report.xml, je zdrojem pro účely tohoto příkladu.  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a>Viz také:

- [Osy LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
