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
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="508d9-102">Postupy: Načtení mělké hodnoty elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="508d9-102">How to: Retrieve the Shallow Value of an Element (C#)</span></span>
<span data-ttu-id="508d9-103">Toto téma ukazuje, jak získat mělké hodnoty elementu.</span><span class="sxs-lookup"><span data-stu-id="508d9-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="508d9-104">Mělké hodnoty je hodnota konkrétní elementu, na rozdíl od hloubkové hodnotu, která obsahuje hodnoty všechny podřízené prvky, které jsou spojeny do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="508d9-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="508d9-105">Při načítání hodnotu prvku pomocí obou přetypování nebo <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnost, získáte podrobné hodnotu.</span><span class="sxs-lookup"><span data-stu-id="508d9-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="508d9-106">K načtení mělké hodnoty, můžete použít `ShallowValue` rozšiřující metoda, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="508d9-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="508d9-107">Načtení mělké hodnoty je užitečné, pokud chcete vybrat elementy na základě jejich obsahu.</span><span class="sxs-lookup"><span data-stu-id="508d9-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="508d9-108">Následující příklad deklaruje metodu rozšíření, která načte mělké hodnoty elementu.</span><span class="sxs-lookup"><span data-stu-id="508d9-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="508d9-109">Pak používá metody rozšíření v dotazu k výpisu všech prvků, které obsahují počítané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="508d9-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="508d9-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="508d9-110">Example</span></span>  
 <span data-ttu-id="508d9-111">Následující textový soubor, Report.xml, je zdrojem pro účely tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="508d9-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
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
  
 <span data-ttu-id="508d9-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="508d9-112">This example produces the following output:</span></span>  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="508d9-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="508d9-113">See also</span></span>

- [<span data-ttu-id="508d9-114">Osy LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="508d9-114">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
