---
title: Jak ladit prázdné sady výsledků dotazu (C#)
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 2716f7c525ac6bee8d2fb374e4ecc4c975d852a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141292"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a>Jak ladit prázdné sady výsledků dotazu (C#)
Jedním z nejčastějších problémů při dotazování na stromy XML je, že pokud má strom XML výchozí obor názvů, vývojář někdy zapíše dotaz, jako by xml nebyl v oboru názvů.  
  
 První sada příkladů v tomto tématu ukazuje typický způsob, jakým je načten xml ve výchozím oboru názvů a je dotazován nesprávně.  
  
 Druhá sada příkladů zobrazuje potřebné opravy, takže můžete dotazovat XML v oboru názvů.  
  
 Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření xml v oboru názvů a dotaz, který vrací prázdnou sadu výsledků.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 Tento příklad přináší následující výsledek:  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření xml v oboru názvů a dotaz, který je kódován správně.  
  
 Řešením je deklarovat a <xref:System.Xml.Linq.XNamespace> inicializovat objekt a <xref:System.Xml.Linq.XName> použít jej při zadávání objektů. V tomto případě argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody je <xref:System.Xml.Linq.XName> objekt.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 Tento příklad přináší následující výsledek:  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
