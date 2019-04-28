---
title: 'Postupy: Vytváření dotazů na XML v názvových prostorech (C#)'
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: e6b966e90d1f7fc86efaa422ecd8afb030d97163
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667467"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Postupy: Vytváření dotazů na XML v názvových prostorech (C#)
Chcete-li napsat dotaz na XML, který je v oboru názvů, musíte použít <xref:System.Xml.Linq.XName> objekty, které mají správný obor názvů.  
  
 Pro jazyk C#, je nejběžnější přístup k inicializaci <xref:System.Xml.Linq.XNamespace> řetězec, který obsahuje identifikátor URI, pak pomocí přetížení operátoru sčítání zkombinovat s místním názvem oboru názvů.  
  
 První sada příklady v tomto tématu ukazuje, jak vytvořit stromu XML ve výchozím oboru názvů. Druhá sada ukazuje postup vytvoření stromu XML v oboru názvů s předponou.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří stromu XML, který je ve výchozím oboru názvů. Potom načte kolekci elementů.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
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
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a>Příklad  
 V jazyce C# psát dotazy stejným způsobem bez ohledu na to, zda jsou psaní dotazů na stromu XML, který používá obor názvů s předponou nebo stromu XML pomocí výchozí obor názvů.  
  
 Následující příklad vytvoří stromu XML, který je v oboru názvů s předponou. Potom načte kolekci elementů.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a>Viz také:

- [Práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
