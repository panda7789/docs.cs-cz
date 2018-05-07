---
title: 'Postupy: načtení hodnoty bez podstruktury elementu (C#)'
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 47c7cdd118a14070ea3a005bda88b55cc7075185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a>Postupy: načtení hodnoty bez podstruktury elementu (C#)
Toto téma ukazuje, jak získat bez podstruktury hodnotu elementu. Bez podstruktury hodnota je hodnota pouze konkrétní elementu oproti hloubkové hodnotu, která obsahuje hodnoty všechny podřízené elementy zřetězen do jednoho řetězce.  
  
 Pokud načítáte hodnotu prvku s použitím buď přetypování nebo <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnost načíst hloubkové hodnotu. Chcete-li načíst bez podstruktury hodnotu, můžete použít `ShallowValue` rozšíření metoda, jak je znázorněno v příkladu toto. Načítání bez podstruktury hodnota je užitečné, pokud chcete vybrat elementy na základě jejich obsahu.  
  
 Následující příklad uvádí metody rozšíření, která načte bez podstruktury hodnotu elementu. Pak používá metoda rozšíření v dotazu seznam všechny elementy, které obsahují počítanou hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující textový soubor, Report.xml, je zdrojem v tomto příkladu.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML osy (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
