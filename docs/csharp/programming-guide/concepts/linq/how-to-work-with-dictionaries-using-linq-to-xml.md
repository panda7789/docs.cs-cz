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
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a>Jak pracovat se slovníky pomocí LINQ to XML (C#)
Je často vhodné převést odrůdy datových struktur do XML a vrátit se do jiných datových struktur. Toto téma ukazuje konkrétní implementaci tohoto obecného přístupu převodem <xref:System.Collections.Generic.Dictionary%602> na XML a zpět.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá forma konstrukce funkčnosti, ve které se dotazují projekty nové <xref:System.Xml.Linq.XElement> objekty a výsledná kolekce se předává jako argument konstruktoru kořenového objektu <xref:System.Xml.Linq.XElement>.  
  
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
