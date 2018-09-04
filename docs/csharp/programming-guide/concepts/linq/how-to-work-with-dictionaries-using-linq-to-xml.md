---
title: 'Postupy: práce se slovníky pomocí LINQ to XML (C#)'
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: afe4fafb9963b4fc429f441349f8190c9a1e5bac
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43531978"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="00111-102">Postupy: práce se slovníky pomocí LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="00111-102">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>
<span data-ttu-id="00111-103">Často je vhodné převést zpět na další datové struktury typy prvků datové struktury do XML a XML.</span><span class="sxs-lookup"><span data-stu-id="00111-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="00111-104">Toto téma popisuje konkrétní implementaci tohoto přístupu obecné převedením <xref:System.Collections.Generic.Dictionary%602> XML a naopak.</span><span class="sxs-lookup"><span data-stu-id="00111-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00111-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="00111-105">Example</span></span>  
 <span data-ttu-id="00111-106">Tento příklad používá určitou formu funkční konstrukce, ve kterém dotaz nové projekty <xref:System.Xml.Linq.XElement> objekty a výsledné kolekce je předán jako argument pro konstruktor kořenové <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="00111-106">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
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
  
 <span data-ttu-id="00111-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="00111-107">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="00111-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="00111-108">Example</span></span>  
 <span data-ttu-id="00111-109">Následující kód vytvoří slovník ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="00111-109">The following code creates a dictionary from XML.</span></span>  
  
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
  
 <span data-ttu-id="00111-110">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="00111-110">This code produces the following output:</span></span>  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="00111-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="00111-111">See Also</span></span>

- [<span data-ttu-id="00111-112">Projekce a transformace (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="00111-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
