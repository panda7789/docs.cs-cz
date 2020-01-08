---
title: Jak pracovat se slovníky pomocí LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: 1a98293f208e80e969362fca27014ecd2e5c4183
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347229"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="e3649-102">Jak pracovat se slovníky pomocí LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e3649-102">How to work with dictionaries using LINQ to XML (C#)</span></span>
<span data-ttu-id="e3649-103">Je často vhodné převést odrůdy datových struktur do XML a vrátit se do jiných datových struktur.</span><span class="sxs-lookup"><span data-stu-id="e3649-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="e3649-104">Toto téma ukazuje konkrétní implementaci tohoto obecného přístupu převodem <xref:System.Collections.Generic.Dictionary%602> na XML a zpět.</span><span class="sxs-lookup"><span data-stu-id="e3649-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3649-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3649-105">Example</span></span>  
 <span data-ttu-id="e3649-106">V tomto příkladu se používá forma konstrukce funkčnosti, ve které se dotazují projekty nové <xref:System.Xml.Linq.XElement> objekty a výsledná kolekce se předává jako argument konstruktoru kořenového objektu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e3649-106">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
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
  
 <span data-ttu-id="e3649-107">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e3649-107">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="e3649-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3649-108">Example</span></span>  
 <span data-ttu-id="e3649-109">Následující kód vytvoří slovník z XML.</span><span class="sxs-lookup"><span data-stu-id="e3649-109">The following code creates a dictionary from XML.</span></span>  
  
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
  
 <span data-ttu-id="e3649-110">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e3649-110">This code produces the following output:</span></span>  
  
```output  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
