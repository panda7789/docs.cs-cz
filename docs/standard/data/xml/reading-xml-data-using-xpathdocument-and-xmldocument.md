---
title: Načítání dat XML pomocí XPathDocument a třídou XMLDocument nastavenou na
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc8e1b85543fca0281b6433dd5c87c28b37818db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a>Načítání dat XML pomocí XPathDocument a třídou XMLDocument nastavenou na
Existují dva způsoby, jak číst dokument XML v <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů. Jedna je číst dokument XML pomocí jen pro čtení <xref:System.Xml.XPath.XPathDocument> třídy a druhá je číst dokument XML pomocí upravitelné <xref:System.Xml.XmlDocument> třídy v <xref:System.Xml?displayProperty=nameWithType> oboru názvů.  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a>Čtení XML – dokumenty pomocí třídy XPathDocument  
 <xref:System.Xml.XPath.XPathDocument> Třída poskytuje rychlé, jen pro čtení, v paměti reprezentace dokumentu XML pomocí modelu dat XPath. Instance <xref:System.Xml.XPath.XPathDocument> třídy jsou vytvořeny pomocí jednoho z jeho šest konstruktorů. Tyto konstruktory umožňují čtení dokumentu XML pomocí <xref:System.IO.Stream>, <xref:System.IO.TextReader>, nebo <xref:System.Xml.XmlReader> objekt, a taky `string` cestu k souboru XML.  
  
 Následující příklad ilustruje, pomocí <xref:System.Xml.XPath.XPathDocument> třídy `string` konstruktor číst dokument XML.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a>Čtení XML – dokumenty pomocí třídy třídou XMLDocument nastavenou na  
 <xref:System.Xml.XmlDocument> Třída je reprezentaci upravovat v paměti dokumentu XML, které implementují základní úroveň 1 W3C Model Document Object (DOM) a základní DOM Level 2. Instance <xref:System.Xml.XmlDocument> třídy jsou vytvořeny pomocí jednoho z jeho tři konstruktorů. Můžete vytvořit nový, prázdný <xref:System.Xml.XmlDocument> objekt voláním <xref:System.Xml.XmlDocument> třída – konstruktor bez parametrů. Po volání metody konstruktoru, použijte <xref:System.Xml.XmlDocument.Load%2A> metodu pro načtení dat XML do nové <xref:System.Xml.XmlDocument> objektu z <xref:System.IO.Stream>, <xref:System.IO.TextReader>, nebo <xref:System.Xml.XmlReader> objekt, a taky `string` cestu k souboru XML.  
  
 Následující příklad ilustruje, pomocí <xref:System.Xml.XmlDocument> třída – konstruktor bez parametrů a <xref:System.Xml.XmlDocument.Load%2A> metoda číst dokument XML.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a>Určení kódování dokumentu XML  
 <xref:System.Xml.XmlReader> Objekt lze použít ke čtení dokumentu XML a vytvořte <xref:System.Xml.XPath.XPathDocument> a <xref:System.Xml.XmlDocument> objekty, jak je znázorněno v předchozích částech. Však <xref:System.Xml.XmlReader> objekt lze číst data, která není kódovaný a v důsledku neposkytuje žádné kódování informace.  
  
 <xref:System.Xml.XmlTextReader> Třída dědí z <xref:System.Xml.XmlReader> třídy, poskytuje kódování informací pomocí jeho <xref:System.Xml.XmlTextReader.Encoding%2A> vlastnost a můžete použít k vytvoření <xref:System.Xml.XPath.XPathDocument> objekt nebo <xref:System.Xml.XmlDocument> objektu.  
  
 Další informace o kódování poskytnuté informace o <xref:System.Xml.XmlTextReader> třídy najdete v tématu <xref:System.Xml.XmlTextReader.Encoding%2A> vlastnost <xref:System.Xml.XmlTextReader> třídy referenční dokumentaci k nástroji.  
  
## <a name="creating-xpathnavigator-objects"></a>Vytváření objektem XPathNavigator nastaveným na objekty  
 Přečtěte si dokument XML do buď <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objekt, můžete vytvořit <xref:System.Xml.XPath.XPathNavigator> objektu k výběru, vyhodnotit, přejděte a v některých případech upravit základní data XML.  
  
 Jak <xref:System.Xml.XPath.XPathDocument> a <xref:System.Xml.XmlDocument> třídy kromě k <xref:System.Xml.XmlNode> třídy, implementovat <xref:System.Xml.XPath.IXPathNavigable> rozhraní <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů. Výsledkem je, zadejte všechny tři třídy <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> metodu, která vrátí <xref:System.Xml.XPath.XPathNavigator> objektu.  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a>XML – dokumenty pomocí třídy objektem XPathNavigator nastaveným na úpravy  
 Kromě výběru, hodnocení a navigace v datech XML <xref:System.Xml.XPath.XPathNavigator> třídu lze použít pro úpravu dokumentu XML v některých případech založeného na objektu, která ji vytvořila.  
  
 <xref:System.Xml.XPath.XPathDocument> Třída je jen pro čtení při <xref:System.Xml.XmlDocument> třída je upravovat a v důsledku toho <xref:System.Xml.XPath.XPathNavigator> objekty vytvořené z <xref:System.Xml.XPath.XPathDocument> objekt nelze použít, chcete-li upravit dokument XML při nebyla vytvořena z <xref:System.Xml.XmlDocument> můžete objekt. <xref:System.Xml.XPath.XPathDocument> Třída slouží ke čtení dokumentu XML. V případech, kdy potřebujete upravit dokument XML nebo vyžadují přístup k další funkce poskytované službou <xref:System.Xml.XmlDocument> třídy, jako je zpracování událostí <xref:System.Xml.XmlDocument> třída by měla být použita.  
  
 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Vlastnost <xref:System.Xml.XPath.XPathNavigator> Určuje třídu, pokud <xref:System.Xml.XPath.XPathNavigator> objekt může upravit XML data.  
  
 Následující tabulka popisuje hodnotu <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> vlastnosti pro každou třídu.  
  
|<xref:System.Xml.XPath.IXPathNavigable> Implementace|<xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Hodnota|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Přístup k datům XML pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [Úpravy dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [Ověření schématu pomocí XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
