---
title: Načtení omezené hodnoty elementu (C#)
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: b9b69b5a18106f82d13cb54208c2362f8239711e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347450"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="c0d85-102">Načtení omezené hodnoty elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="c0d85-102">How to retrieve the shallow value of an element (C#)</span></span>
<span data-ttu-id="c0d85-103">Toto téma ukazuje, jak získat omezené hodnoty elementu.</span><span class="sxs-lookup"><span data-stu-id="c0d85-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="c0d85-104">Nedávná hodnota je hodnota pouze konkrétního prvku, na rozdíl od hloubkové hodnoty, která zahrnuje hodnoty všech podřízených prvků zřetězených do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="c0d85-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="c0d85-105">Při načítání hodnoty prvku pomocí přetypování nebo vlastnosti <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> načtete hloubkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c0d85-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="c0d85-106">K načtení omezené hodnoty můžete použít metodu rozšíření `ShallowValue`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c0d85-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="c0d85-107">Načtení omezené hodnoty je užitečné, pokud chcete vybrat prvky na základě jejich obsahu.</span><span class="sxs-lookup"><span data-stu-id="c0d85-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="c0d85-108">V následujícím příkladu je deklarována metoda rozšíření, která načte s nejomezeným hodnotou elementu.</span><span class="sxs-lookup"><span data-stu-id="c0d85-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="c0d85-109">Potom používá metodu rozšíření v dotazu k vypsání všech prvků, které obsahují počítanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c0d85-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0d85-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0d85-110">Example</span></span>  
 <span data-ttu-id="c0d85-111">Následující textový soubor, Report. XML, je zdrojem tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="c0d85-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
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
  
 <span data-ttu-id="c0d85-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c0d85-112">This example produces the following output:</span></span>  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0d85-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0d85-113">See also</span></span>

- [<span data-ttu-id="c0d85-114">LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="c0d85-114">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
