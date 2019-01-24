---
title: 'Postupy: Filtrování volitelného elementu (C#)'
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: 1aeb234365fa5d02911f70bb70a860258ce62f30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540108"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="4cdae-102">Postupy: Filtrování volitelného elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="4cdae-102">How to: Filter on an Optional Element (C#)</span></span>
<span data-ttu-id="4cdae-103">Někdy budete chtít filtrovat pro element, i když si nejste jisti, že objekt že existuje v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4cdae-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="4cdae-104">Hledání by měl provádět tak, že pokud konkrétní element nemá podřízený element, pomocí filtrování pro něj nespouštějí výjimka nulového odkazu.</span><span class="sxs-lookup"><span data-stu-id="4cdae-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="4cdae-105">V následujícím příkladu `Child5` nemá element `Type` podřízený element, ale dotaz stále se provede správně.</span><span class="sxs-lookup"><span data-stu-id="4cdae-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cdae-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cdae-106">Example</span></span>  
 <span data-ttu-id="4cdae-107">V tomto příkladu <xref:System.Xml.Linq.Extensions.Elements%2A> – metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="4cdae-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
var cList =  
    from typeElement in root.Elements().Elements("Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element("Text");  
foreach(string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="4cdae-108">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4cdae-108">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="4cdae-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cdae-109">Example</span></span>  
 <span data-ttu-id="4cdae-110">Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4cdae-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="4cdae-111">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="4cdae-111">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
XNamespace ad = "http://www.adatum.com";  
var cList =  
    from typeElement in root.Elements().Elements(ad + "Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element(ad + "Text");  
foreach (string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="4cdae-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4cdae-112">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cdae-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cdae-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4cdae-114">Základní dotazy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4cdae-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="4cdae-115">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="4cdae-115">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="4cdae-116">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="4cdae-116">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
