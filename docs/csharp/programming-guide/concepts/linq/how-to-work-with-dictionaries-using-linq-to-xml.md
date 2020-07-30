---
title: Postup práce se slovníky pomocí LINQ to XML (C#)
description: Naučte se pracovat se slovníky pomocí LINQ to XML. Viz příklady převod slovníků na XML a XML zpátky do jiných datových struktur.
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: bdba7a2b3dfc16fab1e239ac804c317dfefb7d9e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302617"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="e402c-104">Postup práce se slovníky pomocí LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e402c-104">How to work with dictionaries using LINQ to XML (C#)</span></span>
<span data-ttu-id="e402c-105">Je často vhodné převést odrůdy datových struktur do XML a vrátit se do jiných datových struktur.</span><span class="sxs-lookup"><span data-stu-id="e402c-105">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="e402c-106">Toto téma ukazuje konkrétní implementaci tohoto obecného přístupu převodem <xref:System.Collections.Generic.Dictionary%602> na XML a zpět.</span><span class="sxs-lookup"><span data-stu-id="e402c-106">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e402c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e402c-107">Example</span></span>  
 <span data-ttu-id="e402c-108">V tomto příkladu se používá forma konstrukce funkčnosti, ve které se dotazuje na nové <xref:System.Xml.Linq.XElement> objekty a výsledná kolekce se předává jako argument konstruktoru kořenového <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="e402c-108">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
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
  
 <span data-ttu-id="e402c-109">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e402c-109">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="e402c-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e402c-110">Example</span></span>  
 <span data-ttu-id="e402c-111">Následující kód vytvoří slovník z XML.</span><span class="sxs-lookup"><span data-stu-id="e402c-111">The following code creates a dictionary from XML.</span></span>  
  
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
  
 <span data-ttu-id="e402c-112">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e402c-112">This code produces the following output:</span></span>  
  
```output  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
