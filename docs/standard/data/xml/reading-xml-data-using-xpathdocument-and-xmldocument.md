---
title: Čtení dat XML pomocí XPathDocument a XmlDocument
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69e22328c39ae68acc4baff12775b49fbac80696
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869964"
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a>Čtení dat XML pomocí XPathDocument a XmlDocument
Existují dva způsoby, jak číst v dokumentu XML <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů. Jeden je ke čtení dokumentu XML pomocí jen pro čtení <xref:System.Xml.XPath.XPathDocument> třídy a druhý je ke čtení dokumentu XML pomocí upravitelné <xref:System.Xml.XmlDocument> třídy v <xref:System.Xml?displayProperty=nameWithType> oboru názvů.  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a>Čtení dokumentů XML pomocí XPathDocument třídy  
 <xref:System.Xml.XPath.XPathDocument> Třída poskytuje rychlé, jen pro čtení, v paměti reprezentace dokumentu XML pomocí modelu dat XPath. Instance <xref:System.Xml.XPath.XPathDocument> třídy jsou vytvořeny pomocí jedné z jejích šesti konstruktorů. Tyto konstruktory umožňují čtení dokumentu XML pomocí <xref:System.IO.Stream>, <xref:System.IO.TextReader>, nebo <xref:System.Xml.XmlReader> objektu, jakož i `string` cestu k souboru XML.  
  
 Následující příklad ukazuje použití <xref:System.Xml.XPath.XPathDocument> třídy `string` konstruktor ke čtení dokumentu XML.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a>Čtení dokumentů XML pomocí třídy XmlDocument  
 <xref:System.Xml.XmlDocument> Třídy je upravitelné reprezentací implementace základní úrovně 1 W3C Document Object Model (DOM) a základní modelu DOM úrovně 2 dokumentu XML v paměti. Instance <xref:System.Xml.XmlDocument> třídy jsou vytvořeny pomocí jedné z jeho tři konstruktory. Můžete vytvořit nový, prázdný <xref:System.Xml.XmlDocument> objektu voláním <xref:System.Xml.XmlDocument> třída konstruktor bez parametrů. Po volání konstruktoru, použijte <xref:System.Xml.XmlDocument.Load%2A> metodu pro načtení dat XML do nového <xref:System.Xml.XmlDocument> objektu z <xref:System.IO.Stream>, <xref:System.IO.TextReader>, nebo <xref:System.Xml.XmlReader> objektu, stejně jako `string` cestu k souboru XML.  
  
 Následující příklad ukazuje použití <xref:System.Xml.XmlDocument> třída konstruktor bez parametrů a <xref:System.Xml.XmlDocument.Load%2A> metodu za účelem čtení dokumentu XML.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a>Určení kódování dokumentu XML  
 <xref:System.Xml.XmlReader> Objekt lze použít ke čtení dokumentu XML a vytvořit <xref:System.Xml.XPath.XPathDocument> a <xref:System.Xml.XmlDocument> objektů, jak je znázorněno v předchozích částech. Nicméně <xref:System.Xml.XmlReader> objekt může číst data, která není kódovaný a v důsledku neposkytuje žádné informace o kódování.  
  
 <xref:System.Xml.XmlTextReader> Třída dědí z <xref:System.Xml.XmlReader> třídy, poskytuje kódování informací pomocí jeho <xref:System.Xml.XmlTextReader.Encoding%2A> vlastnost a můžete použít k vytvoření <xref:System.Xml.XPath.XPathDocument> objektu nebo <xref:System.Xml.XmlDocument> objektu.  
  
 Další informace o kódování na základě informací poskytnutých <xref:System.Xml.XmlTextReader> najdete v tématu <xref:System.Xml.XmlTextReader.Encoding%2A> vlastnost <xref:System.Xml.XmlTextReader> třídy referenční dokumentaci.  
  
## <a name="creating-xpathnavigator-objects"></a>Vytváření objektů s objektem XPathNavigator nastaveným na  
 Po přečtení dokumentu XML do jedné <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu, můžete vytvořit <xref:System.Xml.XPath.XPathNavigator> objektu k výběru, vyhodnocení, přejděte a v některých případech může upravovat podkladová data XML.  
  
 Jak <xref:System.Xml.XPath.XPathDocument> a <xref:System.Xml.XmlDocument> třídy, navíc k <xref:System.Xml.XmlNode> třídy, implementujte <xref:System.Xml.XPath.IXPathNavigable> rozhraní <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů. V důsledku toho poskytují všechny třídy <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> metodu, která vrátí <xref:System.Xml.XPath.XPathNavigator> objektu.  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a>Úpravy dokumentů XML pomocí XPathNavigator třídy  
 Kromě výběr, vyhodnocení a navigace v datech XML <xref:System.Xml.XPath.XPathNavigator> třídy lze použít k úpravě dokumentu XML v některých případech založené na objektu, který byl vytvořen.  
  
 <xref:System.Xml.XPath.XPathDocument> Třídy je jen pro čtení při <xref:System.Xml.XmlDocument> třída je upravovat a v důsledku toho <xref:System.Xml.XPath.XPathNavigator> objekty vytvořené z <xref:System.Xml.XPath.XPathDocument> objektu nelze použít k úpravě dokumentu XML při vytvořených ze <xref:System.Xml.XmlDocument> objekt může. <xref:System.Xml.XPath.XPathDocument> Třída by měla sloužit ke čtení dokumentu XML. V případech, kdy potřebujete upravit dokument XML, nebo vyžadují přístup k další funkce poskytovaná modulem <xref:System.Xml.XmlDocument> třídy, jako je zpracování událostí <xref:System.Xml.XmlDocument> třída by měla být použita.  
  
 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Vlastnost <xref:System.Xml.XPath.XPathNavigator> Určuje třídu, pokud <xref:System.Xml.XPath.XPathNavigator> objekt může upravovat XML data.  
  
 Následující tabulka popisuje výhody <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> vlastností pro každou třídu.  
  
|<xref:System.Xml.XPath.IXPathNavigable> Implementace|<xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Hodnota|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [Přístup k datům XML pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [Úpravy dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
- [Ověření schématu pomocí XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
