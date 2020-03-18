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
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a>Jak pracovat se slovníky pomocí LINQ na XML (C#)
Často je vhodné převést různé datové struktury na XML a XML zpět na jiné datové struktury. Toto téma ukazuje konkrétní implementaci tohoto obecného přístupu převodem a <xref:System.Collections.Generic.Dictionary%602> na XML a zpět.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá formu funkční konstrukce, ve <xref:System.Xml.Linq.XElement> kterém dotaz promítá nové objekty a výsledná <xref:System.Xml.Linq.XElement> kolekce je předána jako argument konstruktoru kořenového objektu.  
  
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
  
 Výsledkem tohoto kódu je následující výstup:  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří slovník z XML.  
  
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
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
