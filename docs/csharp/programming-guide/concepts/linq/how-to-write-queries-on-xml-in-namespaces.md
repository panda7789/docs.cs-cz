---
title: Zápis dotazů na XML v oborech názvů (C#)
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: a8b8d55daaad1ae00e43fed897080ed7a62fafab
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337377"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Zápis dotazů na XML v oborech názvů (C#)
Chcete-li zapsat dotaz na XML, který je v oboru názvů, je nutné použít <xref:System.Xml.Linq.XName> objekty, které mají správný obor názvů.  
  
 C#Nejběžnějším přístupem je inicializovat <xref:System.Xml.Linq.XNamespace> pomocí řetězce, který obsahuje identifikátor URI, potom použít přetížení operátoru sčítání ke kombinování oboru názvů s místním názvem.  
  
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
 V C#systému píšete dotazy stejným způsobem bez ohledu na to, zda píšete dotazy ve stromu XML, který používá obor názvů s předponou nebo ve stromu XML s výchozím oborem názvů.  
  
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

- [Přehled oborů názvů (LINQ to XML)C#()](namespaces-overview-linq-to-xml.md)
