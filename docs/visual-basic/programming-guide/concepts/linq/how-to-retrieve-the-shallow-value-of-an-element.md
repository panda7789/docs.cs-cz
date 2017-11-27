---
title: "Postupy: načtení hodnoty bez podstruktury elementu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 673b890ab842d1c18c8020eefe03d90086d1bf4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a><span data-ttu-id="a100a-102">Postupy: načtení hodnoty bez podstruktury elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a100a-102">How to: Retrieve the Shallow Value of an Element (Visual Basic)</span></span>
<span data-ttu-id="a100a-103">Toto téma ukazuje, jak získat bez podstruktury hodnotu elementu.</span><span class="sxs-lookup"><span data-stu-id="a100a-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="a100a-104">Bez podstruktury hodnota je hodnota pouze konkrétní elementu oproti hloubkové hodnotu, která obsahuje hodnoty všechny podřízené elementy zřetězen do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="a100a-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="a100a-105">Pokud načítáte hodnotu prvku s použitím buď přetypování nebo <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnost načíst hloubkové hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a100a-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="a100a-106">Chcete-li načíst bez podstruktury hodnotu, můžete použít `ShallowValue` rozšíření metoda, jak je znázorněno v příkladu toto.</span><span class="sxs-lookup"><span data-stu-id="a100a-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the follwing example.</span></span> <span data-ttu-id="a100a-107">Načítání bez podstruktury hodnota je užitečné, pokud chcete vybrat elementy na základě jejich obsahu.</span><span class="sxs-lookup"><span data-stu-id="a100a-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="a100a-108">Následující příklad uvádí metody rozšíření, která načte bez podstruktury hodnotu elementu.</span><span class="sxs-lookup"><span data-stu-id="a100a-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="a100a-109">Pak používá metoda rozšíření v dotazu seznam všechny elementy, které obsahují počítanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a100a-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a100a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a100a-110">Example</span></span>  
 <span data-ttu-id="a100a-111">Následující textový soubor, Report.xml, je zdrojem v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="a100a-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
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
  
```vb  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function ShallowValue(ByVal xe As XElement)  
        Return xe _  
               .Nodes() _  
               .OfType(Of XText)() _  
               .Aggregate(New StringBuilder(), _  
                              Function(s, c) s.Append(c), _  
                              Function(s) s.ToString())  
    End Function  
  
    Sub Main()  
        Dim root As XElement = XElement.Load("Report.xml")  
  
        Dim query As IEnumerable(Of XElement) = _  
            From el In root.Descendants() _  
            Where (el.ShallowValue().StartsWith("=")) _  
            Select el  
  
        For Each q As XElement In query  
            Console.WriteLine("{0}{1}{2}", _  
                q.Name.ToString().PadRight(8), _  
                q.Attribute("Name").ToString().PadRight(20), _  
                q.ShallowValue())  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="a100a-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a100a-112">This example produces the following output:</span></span>  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="a100a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a100a-113">See Also</span></span>  
 [<span data-ttu-id="a100a-114">Technologie LINQ to XML osy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a100a-114">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
