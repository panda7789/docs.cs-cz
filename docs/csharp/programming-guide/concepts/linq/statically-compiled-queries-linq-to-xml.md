---
title: Staticky kompilované dotazy (LINQ to XML) (C#)
description: Přečtěte si o staticky kompilovaných dotazech v LINQ to XML v jazyce C# a o tom, jak se liší od dotazů XPath, které je nutné interpretovat za běhu.
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: cd2e6a6507311d5fc17215a22c70bd0449292b6f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302305"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a>Staticky kompilované dotazy (LINQ to XML) (C#)
Jedna z nejdůležitějších výhod výkonu LINQ to XML, na rozdíl od <xref:System.Xml.XmlDocument> , je, že dotazy v LINQ to XML jsou staticky kompilovány, zatímco dotazy XPath musí být interpretovány za běhu. Tato funkce je integrovaná do LINQ to XML, takže není nutné provádět další kroky, abyste je mohli využít, ale je užitečné pochopit rozdíl mezi těmito dvěma technologiemi. Toto téma popisuje rozdíl.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Staticky kompilované dotazy vs. XPath  
 Následující příklad ukazuje, jak získat odvozené prvky se zadaným názvem a s atributem se zadanou hodnotou.  
  
 Následuje ekvivalentní výraz XPath:`//Address[@Type='Shipping']`
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Výraz dotazu v tomto příkladu je znovu napsán kompilátorem do syntaxe dotazu založeného na metodě. Následující příklad, který je napsán v syntaxi dotazu založeného na metodách, vytváří stejné výsledky jako předchozí:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <xref:System.Linq.Enumerable.Where%2A>Metoda je rozšiřující metoda. Další informace naleznete v tématu [metody rozšíření](../../classes-and-structs/extension-methods.md). Vzhledem k tomu <xref:System.Linq.Enumerable.Where%2A> , že je metoda rozšíření, je dotaz výše zkompilován, jako by byl napsán takto:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Tento příklad vytváří přesně stejné výsledky jako v předchozích dvou příkladech. To ukazuje fakt, že dotazy jsou efektivně zkompilovány do staticky propojených volání metody. V kombinaci s sémantikou pro odložené provádění iterátorů zvyšuje výkon. Další informace o devodit sémantikě iterátorů naleznete [v tématu Odložené provádění a opožděné hodnocení v LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
> Tyto příklady jsou zástupci kódu, který kompilátor může zapisovat. Skutečná implementace se může mírně lišit od těchto příkladů, ale výkon bude stejný nebo podobný jako v těchto příkladech.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Provádění výrazů XPath s XmlDocument  
 Následující příklad používá <xref:System.Xml.XmlDocument> k dosažení stejných výsledků jako předchozí příklady:  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 Tento dotaz vrátí stejný výstup jako příklady, které používají LINQ to XML; Jediným rozdílem je, že LINQ to XML odsadí vytištěný XML, zatímco <xref:System.Xml.XmlDocument> ne.  
  
 Obecně se ale <xref:System.Xml.XmlDocument> neprovádí ani LINQ to XML, protože <xref:System.Xml.XmlNode.SelectNodes%2A> Metoda musí provést následující interně při každém volání:  
  
- Analyzuje řetězec, který obsahuje výraz XPath a přerušuje řetězec na tokeny.  
  
- Ověřuje tokeny, aby bylo zajištěno, že je výraz XPath platný.  
  
- Převede výraz do vnitřního stromu výrazu.  
  
- Projde uzly a odpovídajícím způsobem vybere uzly sady výsledků na základě vyhodnocení výrazu.  
  
 To je podstatně větší než práce prováděná odpovídajícím dotazem LINQ to XML. Konkrétní rozdíl mezi výkonem se liší v různých typech dotazů, ale obecně LINQ to XML dotazy méně fungují, a proto je lepší, než vyhodnocování výrazů XPath pomocí <xref:System.Xml.XmlDocument> .  
