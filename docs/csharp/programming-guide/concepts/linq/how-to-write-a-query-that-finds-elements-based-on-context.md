---
title: Jak napsat dotaz, který vyhledá prvky na základě kontextu (C#)
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 3fc131fdeb8dbf8871bfa455bc54eab0eeca7022
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75348369"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a>Jak napsat dotaz, který vyhledá prvky na základě kontextu (C#)
Někdy může být nutné napsat dotaz, který vybere prvky na základě jejich kontextu. Můžete chtít filtrovat na základě předchozínebo následující prvky na stejné úrovni. Můžete chtít filtrovat na základě podřízených nebo nadřazené prvky.  
  
 To lze provést zápisem dotazu a pomocí výsledků `where` dotazu v klauzuli. Pokud máte nejprve test proti null a potom otestovat hodnotu, je `let` vhodnější provést dotaz v `where` klauzuli a potom použít výsledky v klauzuli.  
  
## <a name="example"></a>Příklad  
 Následující příklad vybere `p` všechny prvky, které `ul` jsou bezprostředně následuje prvek.  
  
```csharp  
XElement doc = XElement.Parse(@"<Root>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants("p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name.LocalName == "ul"  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro jazyk XML, který je v oboru názvů. Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
XNamespace ad = "http://www.adatum.com";  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants(ad + "p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name == ad.GetName("ul")  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
