---
title: Staticky kompilované dotazy (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 98725cece1006ba13afb64bb8ae17ae6e62c53cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253035"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a>Staticky kompilované dotazy (LINQ to XML) (C#)
Jedním z nejdůležitějších výhod výkonu LINQ na <xref:System.Xml.XmlDocument>XML, na rozdíl od , je, že dotazy v LINQ na XML jsou staticky kompilovány, zatímco dotazy XPath musí být interpretovány za běhu. Tato funkce je integrována do LINQ do XML, takže není nutné provádět další kroky, abyste ji mohli využít, ale je užitečné pochopit rozdíl při výběru mezi těmito dvěma technologiemi. Toto téma vysvětluje rozdíl.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Staticky zkompilované dotazy vs. XPath  
 Následující příklad ukazuje, jak získat potomek prvky se zadaným názvem a s atributem se zadanou hodnotou.  
  
 Následující je ekvivalentní výraz XPath:`//Address[@Type='Shipping']`
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Výraz dotazu v tomto příkladu je přepsán kompilátorem na syntaxi dotazu na základě metody. Následující příklad, který je napsán v syntaxi dotazu založené na metodě, vytváří stejné výsledky jako předchozí:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Metoda <xref:System.Linq.Enumerable.Where%2A> je metoda rozšíření. Další informace naleznete v [tématu Metody rozšíření](../../classes-and-structs/extension-methods.md). Protože <xref:System.Linq.Enumerable.Where%2A> je metoda rozšíření, výše uvedený dotaz je zkompilován, jako by byly zapsány takto:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Tento příklad vytváří přesně stejné výsledky jako předchozí dva příklady. To ilustruje skutečnost, že dotazy jsou efektivně kompilovány do staticky propojené volání metod. To v kombinaci s odloženou sémantikou sémantiky iterátorů zlepšuje výkon. Další informace o odložené spuštění sémantiku iterátorů naleznete [v tématu Odložené spuštění a Opožděné vyhodnocení v LINQ na XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
> Tyto příklady jsou reprezentativní pro kód, který může napsat kompilátor. Skutečná implementace se může mírně lišit od těchto příkladů, ale výkon bude stejný nebo podobný těmto příkladům.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Spuštění výrazů XPath s dokumentem XmlDocument  
 Následující příklad <xref:System.Xml.XmlDocument> používá k dosažení stejných výsledků jako v předchozích příkladech:  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 Tento dotaz vrátí stejný výstup jako příklady, které používají LINQ do XML; jediným rozdílem je, že LINQ na XML odsazuje vytištěný XML, zatímco <xref:System.Xml.XmlDocument> není.  
  
 <xref:System.Xml.XmlDocument> Však přístup obecně neprovádí stejně jako LINQ <xref:System.Xml.XmlNode.SelectNodes%2A> do XML, protože metoda musí provést následující interně pokaždé, když je volána:  
  
- Analyzuje řetězec, který obsahuje výraz XPath, rozdělení řetězce na tokeny.  
  
- Ověří tokeny a ujistěte se, že výraz XPath je platný.  
  
- Převádí výraz do stromu vnitřního výrazu.  
  
- Iterem prostřednictvím uzlů, vhodně výběru uzlů pro sadu výsledků na základě vyhodnocení výrazu.  
  
 To je výrazně více než práce provedené odpovídající LINQ na dotaz XML. Konkrétní rozdíl výkonu se liší pro různé typy dotazů, ale obecně LINQ na XML dotazy méně práce, a <xref:System.Xml.XmlDocument>proto provádět lépe, než vyhodnocení xpath výrazy pomocí .  
