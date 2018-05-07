---
title: 'Postupy: zápis dotazů na XML v oborech názvů (C#)'
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: a5de5ffdafc2dd191a35860150e48a86a3603f3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Postupy: zápis dotazů na XML v oborech názvů (C#)
Pokud chcete napsat dotaz na XML, který je v oboru názvů, je nutné použít <xref:System.Xml.Linq.XName> objekty, které mají správný obor názvů.  
  
 Pro jazyk C#, je nejběžnější přístup k chybě při inicializaci <xref:System.Xml.Linq.XNamespace> pomocí řetězec, který obsahuje identifikátor URI, potom použijte přetížení operátor přidání kombinovat s místní název oboru názvů.  
  
 První sadu příklady v tomto tématu ukazuje, jak vytvořit strom XML ve výchozí obor názvů. Druhá sada ukazuje, jak vytvořit strom XML v oboru názvů s předponou.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří ve stromu XML, který je ve výchozí obor názvů. Potom načte kolekci elementů.  
  
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
 V jazyce C# můžete psát dotazy stejným způsobem, bez ohledu na to, jestli jsou zápis dotazů na XML stromové struktury, která používá obor názvů s předponou nebo na strom XML s výchozí obor názvů.  
  
 Následující příklad vytvoří strom XML, který je v oboru názvů s předponou. Potom načte kolekci elementů.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Práce s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
