---
title: 'Postupy: filtru na volitelný Element (C#)'
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: aa6eb5c9f661a27729c409edcc44b75377498925
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320167"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="161ce-102">Postupy: filtru na volitelný Element (C#)</span><span class="sxs-lookup"><span data-stu-id="161ce-102">How to: Filter on an Optional Element (C#)</span></span>
<span data-ttu-id="161ce-103">Někdy budete chtít filtrovat pro element, i když si nejste jisti, že existuje v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="161ce-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="161ce-104">Hledání se má provést, takže pokud určitý element nemá podřízený element, pomocí filtrování pro něj nespouštějí výjimka odkazu s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="161ce-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="161ce-105">V následujícím příkladu `Child5` element nemá `Type` podřízeného elementu, ale dotaz stále provádí správně.</span><span class="sxs-lookup"><span data-stu-id="161ce-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="161ce-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="161ce-106">Example</span></span>  
 <span data-ttu-id="161ce-107">Tento příklad používá <xref:System.Xml.Linq.Extensions.Elements%2A> metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="161ce-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
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
  
 <span data-ttu-id="161ce-108">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="161ce-108">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="161ce-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="161ce-109">Example</span></span>  
 <span data-ttu-id="161ce-110">Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="161ce-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="161ce-111">Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="161ce-111">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="161ce-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="161ce-112">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="161ce-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="161ce-113">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="161ce-114">Základní dotazy (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="161ce-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="161ce-115">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="161ce-115">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="161ce-116">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="161ce-116">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
