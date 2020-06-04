---
title: 'Postupy: Načtení mělké hodnoty elementu (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
ms.openlocfilehash: 24e6b128481f56941f0a61da9766f02813a46e97
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397814"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a><span data-ttu-id="8c13a-102">Postupy: načtení omezené hodnoty elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c13a-102">How to: Retrieve the Shallow Value of an Element (Visual Basic)</span></span>

<span data-ttu-id="8c13a-103">Toto téma ukazuje, jak získat omezené hodnoty elementu.</span><span class="sxs-lookup"><span data-stu-id="8c13a-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="8c13a-104">Nedávná hodnota je hodnota pouze konkrétního prvku, na rozdíl od hloubkové hodnoty, která zahrnuje hodnoty všech podřízených prvků zřetězených do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="8c13a-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>

<span data-ttu-id="8c13a-105">Při načítání hodnoty prvku pomocí přetypování nebo <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> vlastnosti načtete hloubkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8c13a-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="8c13a-106">Pro načtení omezené hodnoty můžete použít `ShallowValue` metodu rozšíření, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8c13a-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="8c13a-107">Načtení omezené hodnoty je užitečné, pokud chcete vybrat prvky na základě jejich obsahu.</span><span class="sxs-lookup"><span data-stu-id="8c13a-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>

<span data-ttu-id="8c13a-108">V následujícím příkladu je deklarována metoda rozšíření, která načte s nejomezeným hodnotou elementu.</span><span class="sxs-lookup"><span data-stu-id="8c13a-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="8c13a-109">Potom používá metodu rozšíření v dotazu k vypsání všech prvků, které obsahují počítanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8c13a-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>

## <a name="example"></a><span data-ttu-id="8c13a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c13a-110">Example</span></span>

<span data-ttu-id="8c13a-111">Následující textový soubor, Report. XML, je zdrojem tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="8c13a-111">The following text file, Report.xml, is the source for this example.</span></span>

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

<span data-ttu-id="8c13a-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8c13a-112">This example produces the following output:</span></span>

```console
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a><span data-ttu-id="8c13a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c13a-113">See also</span></span>

- [<span data-ttu-id="8c13a-114">LINQ to XML osy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c13a-114">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
