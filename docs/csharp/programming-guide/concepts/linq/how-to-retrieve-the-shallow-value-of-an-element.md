---
title: "Postupy: načtení hodnoty bez podstruktury elementu (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5dcbe3faa457a4880a85f5827d0e5c4808b6a44b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="fca40-102">Postupy: načtení hodnoty bez podstruktury elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="fca40-102">How to: Retrieve the Shallow Value of an Element (C#)</span></span>
<span data-ttu-id="fca40-103">Toto téma ukazuje, jak získat bez podstruktury hodnotu elementu.</span><span class="sxs-lookup"><span data-stu-id="fca40-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="fca40-104">Bez podstruktury hodnota je hodnota pouze konkrétní elementu oproti hloubkové hodnotu, která obsahuje hodnoty všechny podřízené elementy zřetězen do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="fca40-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="fca40-105">Pokud načítáte hodnotu prvku s použitím buď přetypování nebo <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnost načíst hloubkové hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fca40-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="fca40-106">Chcete-li načíst bez podstruktury hodnotu, můžete použít `ShallowValue` rozšíření metoda, jak je znázorněno v příkladu toto.</span><span class="sxs-lookup"><span data-stu-id="fca40-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the follwing example.</span></span> <span data-ttu-id="fca40-107">Načítání bez podstruktury hodnota je užitečné, pokud chcete vybrat elementy na základě jejich obsahu.</span><span class="sxs-lookup"><span data-stu-id="fca40-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="fca40-108">Následující příklad uvádí metody rozšíření, která načte bez podstruktury hodnotu elementu.</span><span class="sxs-lookup"><span data-stu-id="fca40-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="fca40-109">Pak používá metoda rozšíření v dotazu seznam všechny elementy, které obsahují počítanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fca40-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fca40-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="fca40-110">Example</span></span>  
 <span data-ttu-id="fca40-111">Následující textový soubor, Report.xml, je zdrojem v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="fca40-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
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
  
 <span data-ttu-id="fca40-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="fca40-112">This example produces the following output:</span></span>  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="fca40-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="fca40-113">See Also</span></span>  
 [<span data-ttu-id="fca40-114">Technologie LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="fca40-114">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
