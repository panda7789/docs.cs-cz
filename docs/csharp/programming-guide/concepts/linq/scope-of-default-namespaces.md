---
title: Obor výchozích názvových prostorů v jazyce C#
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 7615351f6e5f8b18bd6466a83d54aa65a6c99b50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253037"
---
# <a name="scope-of-default-namespaces-in-c"></a>Rozsah výchozích oborů názvů v C\#
Výchozí obory názvů jako reprezentované ve stromu XML nejsou pro dotazy v oboru. Pokud máte XML, který je ve výchozím oboru <xref:System.Xml.Linq.XNamespace> názvů, stále musíte deklarovat proměnnou a zkombinovat ji s místním názvem, abyste vytvořili kvalifikovaný název, který bude použit v dotazu.  
  
 Jedním z nejčastějších problémů při dotazování na stromy XML je, že pokud má strom XML výchozí obor názvů, vývojář někdy zapíše dotaz, jako by xml nebyl v oboru názvů.  
  
 První sada příkladů v tomto tématu ukazuje typický způsob, jakým je načten xml ve výchozím oboru názvů, ale je dotazován nesprávně.  
  
 Druhá sada příkladů zobrazuje potřebné opravy, takže můžete dotazovat XML v oboru názvů.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření xml v oboru názvů a dotaz, který vrací prázdnou sadu výsledků.  
  
### <a name="code"></a>kód  
  
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
  
### <a name="comments"></a>Komentáře  
 Tento příklad přináší následující výsledek:  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření xml v oboru názvů a dotaz, který je kódován správně.  
  
 Na rozdíl od nesprávně kódované příklad výše, správný přístup při použití Jazyka <xref:System.Xml.Linq.XNamespace> C# je deklarovat <xref:System.Xml.Linq.XName> a inicializovat objekt a použít při zadávání objektů. V tomto případě argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody je <xref:System.Xml.Linq.XName> objekt.  
  
### <a name="code"></a>kód  
  
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
  
### <a name="comments"></a>Komentáře  
 Tento příklad přináší následující výsledek:  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Viz také

- [Obory názvů – přehled (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)
