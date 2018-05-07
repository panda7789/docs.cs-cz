---
title: 'Postupy: zápis dotaz, který vyhledá elementy na základě kontextu (C#)'
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 3b09be121c3e1da12614d1c09a806b09386732df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a>Postupy: zápis dotaz, který vyhledá elementy na základě kontextu (C#)
V některých případech můžete chtít vytvořit dotaz, který vybere elementy na základě jejich kontextu. Můžete filtrovat na základě před nebo po prvků. Můžete filtrovat na základě podřízené domény nebo nadřazenými prvky.  
  
 To provedete zadáním dotazu a použitím výsledků dotazu v `where` klauzule. Pokud musíte nejprve porovnat s hodnotou null a otestujte hodnota, je pohodlnější udělat dotazu `let` klauzule a pak použijte výsledky v `where` klauzule.  
  
## <a name="example"></a>Příklad  
 Následující příklad vybere všechny `p` prvky, které jsou bezprostředně následované `ul` elementu.  
  
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
  
 Tento kód vytvoří následující výstup:  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů. Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
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
  
 Tento kód vytvoří následující výstup:  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XElement.Parse%2A>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A>  
 <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
 <xref:System.Linq.Enumerable.FirstOrDefault%2A>  
 [Základní dotazy (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
