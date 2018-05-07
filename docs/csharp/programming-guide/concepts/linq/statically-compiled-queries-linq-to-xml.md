---
title: Staticky kompilované dotazy (technologie LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: b429a5711be942349365019fc71291f78fccc652
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a>Staticky kompilované dotazy (technologie LINQ to XML) (C#)
Jedním z nejdůležitějších výkonu výhody LINQ to XML, naproti tomu <xref:System.Xml.XmlDocument>, že dotazy v technologii LINQ to XML nejsou staticky kompiluje, zatímco dotazů XPath je nutné interpretovat v době běhu. Tato funkce je založená na technologii LINQ to XML, takže není nutné provést další kroky pro jejich výhod, ale je vhodné pochopit rozdíl při výběru mezi tyto technologie. Toto téma vysvětluje rozdíly.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Staticky kompilované dotazy vs. XPath  
 Následující příklad ukazuje, jak získat následnickým elementům se zadaným názvem a atribut se zadanou hodnotou.  
  
 Toto je ekvivalentní výraz XPath:  
  
```  
//Address[@Type='Shipping']  
```  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Výraz dotazu v tomto příkladu je znovu zapsána ve kompilátor syntaxe dotazu na základě metod. Následující příklad, který je napsána v syntaxi dotazu na základě metod, vytvoří stejné výsledky jako předchozí:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <xref:System.Linq.Enumerable.Where%2A> Metoda je metody rozšíření. Další informace najdete v tématu [rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Protože <xref:System.Linq.Enumerable.Where%2A> je metody rozšíření dotazu výše je kompilovat, jako by byl napsán následujícím způsobem:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Tento příklad vytvoří stejné výsledky jako předchozí dva příklady. To ukazuje na skutečnost, že dotazy jsou efektivně zkompilovány do volání metod staticky propojený. To, v kombinaci s odložené provedení sémantika iterátory, zvyšuje výkon. Další informace o sémantiku odložené provedení iterátory najdete v tématu [odložené provedení a opožděné vyhodnocení v technologii LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  Tyto příklady jsou zástupce kód, který může zapisovat do kompilátoru. Skutečná implementace může mírně lišit od těchto příkladech, ale výkonu budou stejné nebo podobné tyto příklady.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Provádění výrazech XPath s třídou XMLDocument nastavenou na  
 Následující příklad používá <xref:System.Xml.XmlDocument> k provádění stejných výsledků jako v předchozích příkladech:  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 Tento dotaz vrací stejný výstup jako příklady, které používají technologie LINQ to XML; jediným rozdílem je, že technologie LINQ to XML odsazení tištěných XML, zatímco <xref:System.Xml.XmlDocument> neexistuje.  
  
 Ale <xref:System.Xml.XmlDocument> přístup obecně nebude provádět i technologie LINQ to XML, protože <xref:System.Xml.XmlNode.SelectNodes%2A> metoda musí udělejte interně pokaždé, když se označuje jako:  
  
-   Analyzuje řetězec, který obsahuje výraz XPath, nejnovější řetězec do tokenů.  
  
-   Ověřuje tokeny, abyste měli jistotu, že výraz XPath je neplatný.  
  
-   Převádí výraz do stromu interní výrazů.  
  
-   Iteruje uzly, správně výběr uzlů pro sadu výsledků dotazu na základě vyhodnocení výrazu.  
  
 Toto je podstatně více, než podle odpovídající dotazu LINQ to XML. Rozdíl konkrétní výkon se liší pro různé typy dotazů, ale v obecné technologie LINQ to XML dotazy menší práci a proto provádět lepší, než zhodnocení výrazech XPath pomocí <xref:System.Xml.XmlDocument>.  
  
## <a name="see-also"></a>Viz také  
 [Výkon (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
