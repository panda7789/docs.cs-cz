---
title: Zápis dotazů na XML v oborech názvů (C#)
description: Naučte se zapisovat dotazy do XML v oborech názvů. Pro tyto dotazy je nutné použít objekty XName, které mají správný obor názvů.
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 64eb9df1cde3b434a11e2e5410aab96993dc0fa1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303176"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Zápis dotazů na XML v oborech názvů (C#)
Chcete-li zapsat dotaz na XML, který je v oboru názvů, je nutné použít <xref:System.Xml.Linq.XName> objekty, které mají správný obor názvů.  
  
 V jazyce C# je nejběžnějším přístupem inicializace <xref:System.Xml.Linq.XNamespace> pomocí řetězce, který obsahuje identifikátor URI, a poté použití přetížení operátoru sčítání ke kombinování oboru názvů s místním názvem.  
  
 První sada příkladů v tomto tématu ukazuje, jak vytvořit strom XML ve výchozím oboru názvů. Druhá sada ukazuje, jak vytvořit strom XML v oboru názvů s předponou.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří strom XML, který je ve výchozím oboru názvů. Poté načte kolekci prvků.  
  
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
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a>Příklad  
 V jazyce C# píšete dotazy stejným způsobem bez ohledu na to, zda píšete dotazy ve stromu XML, který používá obor názvů s předponou nebo ve stromu XML s výchozím oborem názvů.  
  
 Následující příklad vytvoří strom XML, který je v oboru názvů s předponou. Poté načte kolekci prvků.  
  
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
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)
