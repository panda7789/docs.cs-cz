---
title: Načtení omezené hodnoty elementu (C#)
description: Přečtěte si, jak získat omezené hodnoty elementu. Hodnota s omezeným prvkem je určena pouze pro konkrétní prvek.
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 597859e5b66606aa0cff9c1a475e79e6b66c39fc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301577"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a>Načtení omezené hodnoty elementu (C#)
Toto téma ukazuje, jak získat omezené hodnoty elementu. Nedávná hodnota je hodnota pouze konkrétního prvku, na rozdíl od hloubkové hodnoty, která zahrnuje hodnoty všech podřízených prvků zřetězených do jednoho řetězce.  
  
 Při načítání hodnoty prvku pomocí přetypování nebo <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnosti načtete hloubkovou hodnotu. Pro načtení omezené hodnoty můžete použít `ShallowValue` metodu rozšíření, jak je znázorněno v následujícím příkladu. Načtení omezené hodnoty je užitečné, pokud chcete vybrat prvky na základě jejich obsahu.  
  
 V následujícím příkladu je deklarována metoda rozšíření, která načte s nejomezeným hodnotou elementu. Potom používá metodu rozšíření v dotazu k vypsání všech prvků, které obsahují počítanou hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující textový soubor, Report.xml, je zdrojem tohoto příkladu.  
  
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
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md)
