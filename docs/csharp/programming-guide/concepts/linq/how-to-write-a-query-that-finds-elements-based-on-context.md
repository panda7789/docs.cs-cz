---
title: Jak napsat dotaz, který najde elementy na základě Context (C#)
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 3fc131fdeb8dbf8871bfa455bc54eab0eeca7022
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348369"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a>Jak napsat dotaz, který najde elementy na základě Context (C#)
Někdy může být nutné napsat dotaz, který vybere prvky na základě jejich kontextu. Je možné, že budete chtít filtrovat na základě předchozích nebo následujících prvků na stejné úrovni. Je možné, že budete chtít filtrovat na základě podřízených nebo nadřazených prvků.  
  
 To můžete provést tak, že zapíšete dotaz a použijete výsledky dotazu v klauzuli `where`. Pokud je nutné nejprve otestovat proti hodnotě null a potom otestovat hodnotu, je vhodnější provést dotaz v klauzuli `let` a potom použít výsledky v klauzuli `where`.  
  
## <a name="example"></a>Příklad  
 Následující příklad vybere všechny `p` prvky, které bezprostředně následuje `ul` element.  
  
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
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
