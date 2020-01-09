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
Existují dva způsoby, jak číst dokument XML v oboru názvů <xref:System.Xml.XPath?displayProperty=nameWithType>. Jedním z nich je čtení dokumentu XML pomocí třídy <xref:System.Xml.XPath.XPathDocument> jen pro čtení a druhý je čtení dokumentu XML pomocí upravitelné <xref:System.Xml.XmlDocument> třídy v oboru názvů <xref:System.Xml?displayProperty=nameWithType>.  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a>Čtení dokumentů XML pomocí třídy XPathDocument  
 Třída <xref:System.Xml.XPath.XPathDocument> poskytuje rychlé znázornění dokumentu XML, který je jen pro čtení a který je v paměti, pomocí datového modelu XPath. Instance <xref:System.Xml.XPath.XPathDocument> třídy jsou vytvořeny pomocí některého z šesti konstruktorů. Tyto konstruktory umožňují číst dokument XML pomocí <xref:System.IO.Stream>, <xref:System.IO.TextReader>nebo <xref:System.Xml.XmlReader> objektu a také `string` cestu k souboru XML.  
  
 Následující příklad znázorňuje použití konstruktoru `string` třídy <xref:System.Xml.XPath.XPathDocument> ke čtení dokumentu XML.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a>Čtení dokumentů XML pomocí třídy XmlDocument  
 Třída <xref:System.Xml.XmlDocument> je upravitelná reprezentace v paměti dokumentu XML implementující XML úrovně 1 Core a Core DOM úrovně 2 (W3C model DOM (Document Object Model)). Instance <xref:System.Xml.XmlDocument> třídy jsou vytvořeny pomocí některého z jeho tří konstruktorů. Můžete vytvořit nový prázdný objekt <xref:System.Xml.XmlDocument> voláním konstruktoru třídy <xref:System.Xml.XmlDocument> bez parametrů. Po volání konstruktoru použijte metodu <xref:System.Xml.XmlDocument.Load%2A> k načtení dat XML do nového objektu <xref:System.Xml.XmlDocument> z objektu <xref:System.IO.Stream>, <xref:System.IO.TextReader>nebo <xref:System.Xml.XmlReader> a také `string` cestou k souboru XML.  
  
 Následující příklad znázorňuje použití konstruktoru třídy <xref:System.Xml.XmlDocument> bez parametrů a metody <xref:System.Xml.XmlDocument.Load%2A> pro čtení dokumentu XML.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a>Určení kódování dokumentu XML  
 Objekt <xref:System.Xml.XmlReader> lze použít ke čtení dokumentu XML a k vytvoření objektů <xref:System.Xml.XPath.XPathDocument> a <xref:System.Xml.XmlDocument>, jak je znázorněno v předchozích částech. Objekt <xref:System.Xml.XmlReader> však může číst nekódované data a v důsledku toho neposkytuje žádné informace o kódování.  
  
 Třída <xref:System.Xml.XmlTextReader> dědí z třídy <xref:System.Xml.XmlReader>, poskytuje informace o kódování pomocí jeho vlastnosti <xref:System.Xml.XmlTextReader.Encoding%2A> a lze jej použít k vytvoření objektu <xref:System.Xml.XPath.XPathDocument> nebo objektu <xref:System.Xml.XmlDocument>.  
  
 Další informace o informacích o kódování poskytovaných třídou <xref:System.Xml.XmlTextReader> naleznete v tématu vlastnost <xref:System.Xml.XmlTextReader.Encoding%2A> v dokumentaci třídy <xref:System.Xml.XmlTextReader> reference.  
  
## <a name="creating-xpathnavigator-objects"></a>Vytváření objektů XPathNavigator  
 Po přečtení dokumentu XML do objektu <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> můžete vytvořit objekt <xref:System.Xml.XPath.XPathNavigator> pro výběr, vyhodnocení, procházení a v některých případech upravit podkladová data XML.  
  
 <xref:System.Xml.XPath.XPathDocument> i <xref:System.Xml.XmlDocument> třídy kromě třídy <xref:System.Xml.XmlNode> implementují rozhraní <xref:System.Xml.XPath.IXPathNavigable> oboru názvů <xref:System.Xml.XPath?displayProperty=nameWithType>. V důsledku toho všechny tři třídy poskytují <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> metodu, která vrací objekt <xref:System.Xml.XPath.XPathNavigator>.  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a>Úpravy dokumentů XML pomocí třídy XPathNavigator  
 Kromě výběru, vyhodnocení a navigace XML data lze třídu <xref:System.Xml.XPath.XPathNavigator> použít k úpravám dokumentu XML v některých případech, a to na základě objektu, který jej vytvořil.  
  
 Třída <xref:System.Xml.XPath.XPathDocument> je jen pro čtení, je-li <xref:System.Xml.XmlDocument> třída upravitelná <xref:System.Xml.XPath.XPathNavigator> a v důsledku toho nelze objekty vytvořené pomocí objektu <xref:System.Xml.XPath.XPathDocument> použít k úpravě dokumentu XML, i když jsou vytvořeny z objektu <xref:System.Xml.XmlDocument>. Třída <xref:System.Xml.XPath.XPathDocument> by měla být použita pouze pro čtení dokumentu XML. V případech, kdy potřebujete upravit dokument XML nebo vyžadovat přístup k dalším funkcím poskytovaným <xref:System.Xml.XmlDocument> třídou, jako je zpracování událostí, by měla být použita třída <xref:System.Xml.XmlDocument>.  
  
 Vlastnost <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> třídy <xref:System.Xml.XPath.XPathNavigator> určuje, zda objekt <xref:System.Xml.XPath.XPathNavigator> může upravovat data XML.  
  
 Následující tabulka popisuje hodnotu vlastnosti <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> pro každou třídu.  
  
|<xref:System.Xml.XPath.IXPathNavigable> implementace|Hodnota <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A>|  
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
