---
title: Jak psát dotazy na XML v oborech názvů (C#)
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: a8b8d55daaad1ae00e43fed897080ed7a62fafab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75337377"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Jak psát dotazy na XML v oborech názvů (C#)
Chcete-li napsat dotaz na jazyk XML, který <xref:System.Xml.Linq.XName> je v oboru názvů, je nutné použít objekty, které mají správný obor názvů.  
  
 Pro C#, nejběžnější přístup je inicializovat <xref:System.Xml.Linq.XNamespace> pomocí řetězce, který obsahuje identifikátor URI, pak použijte přetížení operátoru sčítání kombinovat obor názvů s místním názvem.  
  
 První sada příkladů v tomto tématu ukazuje, jak vytvořit strom XML ve výchozím oboru názvů. Druhá sada ukazuje, jak vytvořit strom XML v oboru názvů s předponou.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří strom XML, který je ve výchozím oboru názvů. Potom načte kolekci prvků.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a>Příklad  
 V jazyce C# píšete dotazy stejným způsobem bez ohledu na to, zda píšete dotazy na strom XML, který používá obor názvů s předponou nebo ve stromu XML s výchozím oborem názvů.  
  
 Následující příklad vytvoří strom XML, který je v oboru názvů s předponou. Potom načte kolekci prvků.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a>Viz také

- [Obory názvů – přehled (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)
