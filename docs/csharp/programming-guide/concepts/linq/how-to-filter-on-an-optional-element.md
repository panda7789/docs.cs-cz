---
title: Jak filtrovat volitelný prvek (C#)
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: c9f844619cbb3d7a66ca66989baa900e0fd7bc2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141250"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="0a3d0-102">Jak filtrovat volitelný prvek (C#)</span><span class="sxs-lookup"><span data-stu-id="0a3d0-102">How to filter on an optional element (C#)</span></span>
<span data-ttu-id="0a3d0-103">Někdy chcete filtrovat prvek, i když si nejste jisti, že existuje v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0a3d0-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="0a3d0-104">Hledání by měla být provedena tak, aby pokud konkrétní prvek nemá podřízený prvek, nespustíte výjimku nulového odkazu filtrováním pro něj.</span><span class="sxs-lookup"><span data-stu-id="0a3d0-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="0a3d0-105">V následujícím příkladu `Child5` prvek nemá `Type` podřízený prvek, ale dotaz se stále provádí správně.</span><span class="sxs-lookup"><span data-stu-id="0a3d0-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a3d0-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a3d0-106">Example</span></span>  
 <span data-ttu-id="0a3d0-107">Tento příklad <xref:System.Xml.Linq.Extensions.Elements%2A> používá metodu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="0a3d0-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
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
  
 <span data-ttu-id="0a3d0-108">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0a3d0-108">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="0a3d0-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a3d0-109">Example</span></span>  
 <span data-ttu-id="0a3d0-110">Následující příklad ukazuje stejný dotaz pro jazyk XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0a3d0-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="0a3d0-111">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0a3d0-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="0a3d0-112">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0a3d0-112">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a3d0-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a3d0-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0a3d0-114">Standardní operátory dotazů – přehled (C#)</span><span class="sxs-lookup"><span data-stu-id="0a3d0-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="0a3d0-115">Projekční operace (C#)</span><span class="sxs-lookup"><span data-stu-id="0a3d0-115">Projection Operations (C#)</span></span>](./projection-operations.md)
