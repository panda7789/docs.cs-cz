---
title: Staticky zkompilován dotazy (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: b26e0e21ae88ae0a40de1593294c004d394e38ed
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610671"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>Staticky zkompilován dotazy (LINQ to XML) (Visual Basic)
Jeden z vašich nejdůležitějších výkonu výhody LINQ to XML, nikoli <xref:System.Xml.XmlDocument>, dotazy v LINQ to XML nejsou staticky zkompilován, zatímco v době běhu musí být interpretován dotazy XPath. Tato funkce je založená na technologii LINQ to XML, takže není potřeba provést další kroky pro jejich výhod, ale je vhodné pochopit v čem při volbě mezi tyto technologie. Toto téma vysvětluje rozdíl.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Staticky kompilaci dotazů vs. XPath  
 Následující příklad ukazuje, jak získat Následnické prvky se zadaným názvem a atribut se zadanou hodnotou.  
  
 Toto je ekvivalentní výraz XPath:  
  
```  
//Address[@Type='Shipping']  
```  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = From el In po.Descendants("Address")  
            Where el.@Type = "Shipping"  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Výraz dotazu v tomto příkladu je znovu zapsat pomocí kompilátoru, aby syntaxe dotazů založených na volání metody. V následujícím příkladu, který je napsán v syntaxe dotazů založených na volání metody, vytvoří stejné výsledky jako předchozí:  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 <xref:System.Linq.Enumerable.Where%2A> Metoda je metodou rozšíření. Další informace najdete v tématu [rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Protože <xref:System.Linq.Enumerable.Where%2A> je metodu rozšíření se výše uvedený dotaz je zkompilován, jako by byl napsán takto:  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Tento příklad vytvoří stejné výsledky jako v předchozích dvou příkladech. To ukazuje na skutečnost, že jsou dotazy efektivně kompilovány do volání metody staticky propojené. Ve spojení se sémantika odložené provedení iterátory, přičemž zlepšuje výkon. Další informace o sémantice odložené provedení iterátory, naleznete v tématu [odložené provedení a opožděné vyhodnocení v LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  Tyto příklady jsou zástupce kód, který kompilátor může zapsat. Skutečná implementace může mírně lišit od těchto příkladech, ale výkon bude stejná nebo podobný tyto příklady.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Výrazy XPath s třídou XMLDocument nastavenou na provádění  
 Následující příklad používá <xref:System.Xml.XmlDocument> provádět stejné výsledky jako v předchozích příkladech:  
  
```vb  
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")  
Dim doc As New Xml.XmlDocument()  
doc.Load(reader)  
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")  
For Each n As Xml.XmlNode In nl  
    Console.WriteLine(n.OuterXml)  
Next  
reader.Close()  
```  
  
 Tento dotaz vrací stejný výstup jako příklady, které používají technologii LINQ to XML jediným rozdílem je, že technologie LINQ to XML odsazení tištěné XML, zatímco <xref:System.Xml.XmlDocument> tak není.  
  
 Ale <xref:System.Xml.XmlDocument> přístup obvykle neprovádí tak LINQ to XML, protože <xref:System.Xml.XmlNode.SelectNodes%2A> metoda musí takto interně pokaždé, když je volána:  
  
- Analyzuje řetězec, který obsahuje výraz XPath, rozdělení řetězec do tokenů.  
  
- Ověřuje tokeny, abyste měli jistotu, že výraz XPath je neplatný.  
  
- Převádí výraz, který strom interních výrazů.  
  
- Prochází uzly, odpovídajícím způsobem výběru uzlů pro sady výsledků na základě vyhodnocení výrazu.  
  
 To je mnohem větší než práce provádí odpovídající dotazu LINQ to XML. Rozdíl měřené liší pro jednotlivé typy dotazů, ale v obecné LINQ to XML dotazy méně práci a proto fungoval lépe, než vyhodnocení výrazů XPath pomocí <xref:System.Xml.XmlDocument>.  
  
## <a name="see-also"></a>Viz také:

- [Výkon (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
