---
title: Načítání dat XML pomocí XPathDocument a XmlDocument
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
ms.openlocfilehash: 87ae96944f9a9f2bbcefb54c343f429c75c3022d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710385"
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a>Načítání dat XML pomocí XPathDocument a XmlDocument
Existují dva způsoby, jak číst dokument XML v <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů. Jedním z nich je čtení dokumentu XML pomocí třídy jen <xref:System.Xml.XPath.XPathDocument> pro čtení a druhý je čtení dokumentu XML pomocí upravitelné <xref:System.Xml.XmlDocument> třídy v <xref:System.Xml?displayProperty=nameWithType> oboru názvů.  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a>Čtení dokumentů XML pomocí třídy XPathDocument  
 <xref:System.Xml.XPath.XPathDocument> Třída poskytuje rychlé znázornění dokumentu XML, který je jen pro čtení a který je v paměti, pomocí datového modelu XPath. Instance <xref:System.Xml.XPath.XPathDocument> třídy jsou vytvořeny pomocí některého z šesti konstruktorů. Tyto konstruktory umožňují číst dokument XML pomocí <xref:System.IO.Stream>objektu, <xref:System.IO.TextReader>nebo <xref:System.Xml.XmlReader> , a také `string` cestu k souboru XML.  
  
 Následující příklad znázorňuje použití <xref:System.Xml.XPath.XPathDocument> `string` konstruktoru třídy pro čtení dokumentu XML.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a>Čtení dokumentů XML pomocí třídy XmlDocument  
 <xref:System.Xml.XmlDocument> Třída je upravitelná reprezentace v paměti dokumentu XML implementující model DOM (Document Object Model) W3C (DOM) úrovně 1 Core a Core DOM úrovně 2. Instance <xref:System.Xml.XmlDocument> třídy jsou vytvořeny pomocí jednoho ze tří konstruktorů. Můžete vytvořit nový prázdný <xref:System.Xml.XmlDocument> objekt voláním konstruktoru <xref:System.Xml.XmlDocument> třídy bez parametrů. Po volání konstruktoru použijte <xref:System.Xml.XmlDocument.Load%2A> metodu pro načtení dat XML do nového <xref:System.Xml.XmlDocument> objektu z objektu <xref:System.IO.Stream>, <xref:System.IO.TextReader>nebo <xref:System.Xml.XmlReader> , a také `string` cestu k souboru XML.  
  
 Následující příklad znázorňuje použití konstruktoru <xref:System.Xml.XmlDocument> třídy bez parametrů a <xref:System.Xml.XmlDocument.Load%2A> metody pro čtení dokumentu XML.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a>Určení kódování dokumentu XML  
 <xref:System.Xml.XmlReader> Objekt lze použít ke čtení dokumentu XML a k vytvoření a <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> vytváření objektů, jak je znázorněno v předchozích částech. <xref:System.Xml.XmlReader> Objekt však může číst data, která nejsou kódována a v důsledku toho neposkytuje žádné informace o kódování.  
  
 <xref:System.Xml.XmlTextReader> <xref:System.Xml.XmlReader> Třída dědí z třídy, poskytuje informace o kódování pomocí <xref:System.Xml.XmlTextReader.Encoding%2A> své vlastnosti a lze ji použít k vytvoření <xref:System.Xml.XPath.XPathDocument> objektu nebo <xref:System.Xml.XmlDocument> objektu.  
  
 Další informace o informacích o kódování, které poskytuje <xref:System.Xml.XmlTextReader> třída, naleznete v <xref:System.Xml.XmlTextReader.Encoding%2A> části vlastnost v <xref:System.Xml.XmlTextReader> dokumentaci třídy.  
  
## <a name="creating-xpathnavigator-objects"></a>Vytváření objektů XPathNavigator  
 Po přečtení dokumentu XML do objektu <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> můžete vytvořit <xref:System.Xml.XPath.XPathNavigator> objekt pro výběr, vyhodnocení, procházení a v některých případech upravit podkladová data XML.  
  
 <xref:System.Xml.XPath.XPathDocument> Třídy <xref:System.Xml.XmlDocument> i <xref:System.Xml.XmlNode> také implementují <xref:System.Xml.XPath.IXPathNavigable> rozhraní <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů. V důsledku toho všechny tři třídy poskytují <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> metodu, která vrací <xref:System.Xml.XPath.XPathNavigator> objekt.  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a>Úpravy dokumentů XML pomocí třídy XPathNavigator  
 Kromě výběru, vyhodnocení a navigace v datech XML lze <xref:System.Xml.XPath.XPathNavigator> třídu použít k úpravě dokumentu XML v některých případech, a to na základě objektu, který jej vytvořil.  
  
 <xref:System.Xml.XPath.XPathDocument> Třída je jen pro čtení, je- <xref:System.Xml.XmlDocument> li třída upravitelná a v důsledku toho <xref:System.Xml.XPath.XPathNavigator> objekty vytvořené z <xref:System.Xml.XPath.XPathDocument> objektu nelze použít k úpravě dokumentu XML, zatímco jsou vytvořeny z <xref:System.Xml.XmlDocument> objektu. <xref:System.Xml.XPath.XPathDocument> Třída by měla být použita pouze pro čtení dokumentu XML. V případech, kdy potřebujete upravit dokument XML nebo vyžadovat přístup k dalším funkcím poskytovaným <xref:System.Xml.XmlDocument> třídou, jako je zpracování událostí, je <xref:System.Xml.XmlDocument> třeba použít třídu.  
  
 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy určuje, zda <xref:System.Xml.XPath.XPathNavigator> objekt může upravovat data XML.  
  
 Následující tabulka popisuje hodnotu <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> vlastnosti pro každou třídu.  
  
|<xref:System.Xml.XPath.IXPathNavigable>Provádění|<xref:System.Xml.XPath.XPathNavigator.CanEdit%2A>Osa|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Přístup k datům XML pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [Úpravy dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
- [Ověření schématu pomocí XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
