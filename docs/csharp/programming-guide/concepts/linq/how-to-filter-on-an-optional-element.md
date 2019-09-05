---
title: 'Postupy: Filtrovat podle volitelného prvku (C#)'
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: 0f8e17d99085ad04ed76b83bce806418ca6d60cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253823"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="90817-102">Postupy: Filtrovat podle volitelného prvku (C#)</span><span class="sxs-lookup"><span data-stu-id="90817-102">How to: Filter on an Optional Element (C#)</span></span>
<span data-ttu-id="90817-103">Někdy je vhodné vyfiltrovat element, i když si nejste jistí, že existuje v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="90817-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="90817-104">Hledání by mělo být provedeno, aby v případě, že konkrétní prvek nemá podřízený element, neaktivovali výjimku odkazu s hodnotou null filtrováním.</span><span class="sxs-lookup"><span data-stu-id="90817-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="90817-105">V následujícím příkladu `Child5` element `Type` nemá podřízený element, ale dotaz se stále provede správně.</span><span class="sxs-lookup"><span data-stu-id="90817-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90817-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="90817-106">Example</span></span>  
 <span data-ttu-id="90817-107">V tomto příkladu se <xref:System.Xml.Linq.Extensions.Elements%2A> používá metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="90817-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
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
  
 <span data-ttu-id="90817-108">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="90817-108">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="90817-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="90817-109">Example</span></span>  
 <span data-ttu-id="90817-110">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="90817-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="90817-111">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="90817-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="90817-112">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="90817-112">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="90817-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90817-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="90817-114">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="90817-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="90817-115">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="90817-115">Projection Operations (C#)</span></span>](./projection-operations.md)
