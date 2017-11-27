---
title: "Postupy: práce s slovník pomocí technologie LINQ to XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 422b9381596e06214e6116a3ba3c9d2b63c8651f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="b521a-102">Postupy: práce s slovník pomocí technologie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b521a-102">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>
<span data-ttu-id="b521a-103">Často je vhodnější převést zpět na jiné datové struktury typy datové struktury XML a XML.</span><span class="sxs-lookup"><span data-stu-id="b521a-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="b521a-104">Toto téma ukazuje na konkrétní implementace tento obecné přístup tím, že převedete <xref:System.Collections.Generic.Dictionary%602> do XML a zpět.</span><span class="sxs-lookup"><span data-stu-id="b521a-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b521a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b521a-105">Example</span></span>  
 <span data-ttu-id="b521a-106">Tento příklad používá formu funkční konstrukce, ve kterém dotazu nové projekty <xref:System.Xml.Linq.XElement> objekty a výsledný kolekci, je jako argument předaný konstruktoru kořenové <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="b521a-106">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
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
  
 <span data-ttu-id="b521a-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b521a-107">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="b521a-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="b521a-108">Example</span></span>  
 <span data-ttu-id="b521a-109">Následující kód vytvoří adresář ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="b521a-109">The following code creates a dictionary from XML.</span></span>  
  
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
  
 <span data-ttu-id="b521a-110">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b521a-110">This code produces the following output:</span></span>  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="b521a-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b521a-111">See Also</span></span>  
 [<span data-ttu-id="b521a-112">Projekce a transformace (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b521a-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
