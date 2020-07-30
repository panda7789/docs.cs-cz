---
title: Jak ladit prázdné sady výsledků dotazu (C#)
description: Naučte se ladit prázdné sady výsledků dotazu. Tyto sady mohou nastat, pokud vývojář napsal dotaz, jako by kód XML nebyl v oboru názvů.
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: ad6d39697e5a59fe23ca700ceeb2a9860d05bb94
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302903"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a>Jak ladit prázdné sady výsledků dotazu (C#)
Jedním z nejběžnějších problémů při dotazování na stromy XML je, že pokud má strom XML výchozí obor názvů, vývojář někdy zapíše dotaz, jako by kód XML nebyl v oboru názvů.  
  
 První sada příkladů v tomto tématu ukazuje typický způsob, jakým je načten XML ve výchozím oboru názvů a je dotaz na něj nesprávně.  
  
 Druhá sada příkladů ukazuje nezbytné opravy, aby bylo možné dotazovat XML v oboru názvů.  
  
 Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který vrací prázdnou sadu výsledků dotazu.  
  
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
  
 Tento příklad vytvoří následující výsledek:  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je správně kódován.  
  
 Řešením je deklarovat a inicializovat <xref:System.Xml.Linq.XNamespace> objekt a použít ho při zadávání <xref:System.Xml.Linq.XName> objektů. V tomto případě argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody je <xref:System.Xml.Linq.XName> objekt.  
  
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
  
 Tento příklad vytvoří následující výsledek:  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
