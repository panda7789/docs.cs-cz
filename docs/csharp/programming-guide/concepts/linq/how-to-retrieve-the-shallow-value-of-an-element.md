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
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="fa845-104">Načtení omezené hodnoty elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="fa845-104">How to retrieve the shallow value of an element (C#)</span></span>
<span data-ttu-id="fa845-105">Toto téma ukazuje, jak získat omezené hodnoty elementu.</span><span class="sxs-lookup"><span data-stu-id="fa845-105">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="fa845-106">Nedávná hodnota je hodnota pouze konkrétního prvku, na rozdíl od hloubkové hodnoty, která zahrnuje hodnoty všech podřízených prvků zřetězených do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="fa845-106">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="fa845-107">Při načítání hodnoty prvku pomocí přetypování nebo <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnosti načtete hloubkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fa845-107">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="fa845-108">Pro načtení omezené hodnoty můžete použít `ShallowValue` metodu rozšíření, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fa845-108">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="fa845-109">Načtení omezené hodnoty je užitečné, pokud chcete vybrat prvky na základě jejich obsahu.</span><span class="sxs-lookup"><span data-stu-id="fa845-109">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="fa845-110">V následujícím příkladu je deklarována metoda rozšíření, která načte s nejomezeným hodnotou elementu.</span><span class="sxs-lookup"><span data-stu-id="fa845-110">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="fa845-111">Potom používá metodu rozšíření v dotazu k vypsání všech prvků, které obsahují počítanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fa845-111">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa845-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa845-112">Example</span></span>  
 <span data-ttu-id="fa845-113">Následující textový soubor, Report.xml, je zdrojem tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="fa845-113">The following text file, Report.xml, is the source for this example.</span></span>  
  
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
  
 <span data-ttu-id="fa845-114">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="fa845-114">This example produces the following output:</span></span>  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa845-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa845-115">See also</span></span>

- [<span data-ttu-id="fa845-116">LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="fa845-116">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
