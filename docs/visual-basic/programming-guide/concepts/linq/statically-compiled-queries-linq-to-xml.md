---
title: Staticky kompilované dotazy (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: f020c1ed8627df8c8386a059f0cea372e8df363e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406765"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>Staticky kompilované dotazy (LINQ to XML) (Visual Basic)

Jedna z nejdůležitějších výhod výkonu LINQ to XML, na rozdíl od <xref:System.Xml.XmlDocument> , je, že dotazy v LINQ to XML jsou staticky kompilovány, zatímco dotazy XPath musí být interpretovány za běhu. Tato funkce je integrovaná do LINQ to XML, takže není nutné provádět další kroky, abyste je mohli využít, ale je užitečné pochopit rozdíl mezi těmito dvěma technologiemi. Toto téma popisuje rozdíl.

## <a name="statically-compiled-queries-vs-xpath"></a>Staticky kompilované dotazy vs. XPath

Následující příklad ukazuje, jak získat odvozené prvky se zadaným názvem a s atributem se zadanou hodnotou.

Následuje ekvivalentní výraz XPath:

```vb
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

Výraz dotazu v tomto příkladu je znovu napsán kompilátorem do syntaxe dotazu založeného na metodě. Následující příklad, který je napsán v syntaxi dotazu založeného na metodách, vytváří stejné výsledky jako předchozí:

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<xref:System.Linq.Enumerable.Where%2A>Metoda je rozšiřující metoda. Další informace naleznete v tématu [metody rozšíření](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Vzhledem k tomu <xref:System.Linq.Enumerable.Where%2A> , že je metoda rozšíření, je dotaz výše zkompilován, jako by byl napsán takto:

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

Tento příklad vytváří přesně stejné výsledky jako v předchozích dvou příkladech. To ukazuje fakt, že dotazy jsou efektivně zkompilovány do staticky propojených volání metody. V kombinaci s sémantikou pro odložené provádění iterátorů zvyšuje výkon. Další informace o devodit sémantikě iterátorů naleznete [v tématu Odložené provádění a opožděné vyhodnocení v LINQ to XML (Visual Basic)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

> [!NOTE]
> Tyto příklady jsou zástupci kódu, který kompilátor může zapisovat. Skutečná implementace se může mírně lišit od těchto příkladů, ale výkon bude stejný nebo podobný jako v těchto příkladech.

## <a name="executing-xpath-expressions-with-xmldocument"></a>Provádění výrazů XPath s XmlDocument

Následující příklad používá <xref:System.Xml.XmlDocument> k dosažení stejných výsledků jako předchozí příklady:

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

Tento dotaz vrátí stejný výstup jako příklady, které používají LINQ to XML; Jediným rozdílem je, že LINQ to XML odsadí vytištěný XML, zatímco <xref:System.Xml.XmlDocument> ne.

Obecně se ale <xref:System.Xml.XmlDocument> neprovádí ani LINQ to XML, protože <xref:System.Xml.XmlNode.SelectNodes%2A> Metoda musí provést následující interně při každém volání:

- Analyzuje řetězec, který obsahuje výraz XPath a přerušuje řetězec na tokeny.

- Ověřuje tokeny, aby bylo zajištěno, že je výraz XPath platný.

- Převede výraz do vnitřního stromu výrazu.

- Projde uzly a odpovídajícím způsobem vybere uzly sady výsledků na základě vyhodnocení výrazu.

To je podstatně větší než práce prováděná odpovídajícím dotazem LINQ to XML. Konkrétní rozdíl mezi výkonem se liší v různých typech dotazů, ale obecně LINQ to XML dotazy méně fungují, a proto je lepší, než vyhodnocování výrazů XPath pomocí <xref:System.Xml.XmlDocument> .

## <a name="see-also"></a>Viz také

- [Výkon (LINQ to XML) (Visual Basic)](performance-linq-to-xml.md)
