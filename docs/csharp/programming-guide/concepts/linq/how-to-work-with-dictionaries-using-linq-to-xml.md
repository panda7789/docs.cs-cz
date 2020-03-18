---
title: Jak pracovat se slovníky pomocí LINQ na XML (C#)
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: 1a98293f208e80e969362fca27014ecd2e5c4183
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347229"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="5e5e5-102">Jak pracovat se slovníky pomocí LINQ na XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5e5e5-102">How to work with dictionaries using LINQ to XML (C#)</span></span>
<span data-ttu-id="5e5e5-103">Často je vhodné převést různé datové struktury na XML a XML zpět na jiné datové struktury.</span><span class="sxs-lookup"><span data-stu-id="5e5e5-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="5e5e5-104">Toto téma ukazuje konkrétní implementaci tohoto obecného přístupu převodem a <xref:System.Collections.Generic.Dictionary%602> na XML a zpět.</span><span class="sxs-lookup"><span data-stu-id="5e5e5-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e5e5-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e5e5-105">Example</span></span>  
 <span data-ttu-id="5e5e5-106">Tento příklad používá formu funkční konstrukce, ve <xref:System.Xml.Linq.XElement> kterém dotaz promítá nové objekty a výsledná <xref:System.Xml.Linq.XElement> kolekce je předána jako argument konstruktoru kořenového objektu.</span><span class="sxs-lookup"><span data-stu-id="5e5e5-106">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
Dictionary<string, string> dict = new Dictionary<string, string>();  
dict.Add("Child1", "Value1");  
dict.Add("Child2", "Value2");  
dict.Add("Child3", "Value3");  
dict.Add("Child4", "Value4");  
XElement root = new XElement("Root",  
    from keyValue in dict  
    select new XElement(keyValue.Key, keyValue.Value)  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="5e5e5-107">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5e5e5-107">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="5e5e5-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e5e5-108">Example</span></span>  
 <span data-ttu-id="5e5e5-109">Následující kód vytvoří slovník z XML.</span><span class="sxs-lookup"><span data-stu-id="5e5e5-109">The following code creates a dictionary from XML.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "Value1"),  
    new XElement("Child2", "Value2"),  
    new XElement("Child3", "Value3"),  
    new XElement("Child4", "Value4")  
);  
  
Dictionary<string, string> dict = new Dictionary<string, string>();  
foreach (XElement el in root.Elements())  
    dict.Add(el.Name.LocalName, el.Value);  
foreach (string str in dict.Keys)  
    Console.WriteLine("{0}:{1}", str, dict[str]);  
```  
  
 <span data-ttu-id="5e5e5-110">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5e5e5-110">This code produces the following output:</span></span>  
  
```output  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
