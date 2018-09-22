---
title: Extrahování dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d838f3d9f4c9400fbbef0fb24f5275eff2038c49
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577925"
---
# <a name="extract-xml-data-using-xpathnavigator"></a>Extrahování dat XML pomocí XPathNavigator
Představuje dokumentu XML v rozhraní Microsoft .NET Framework několika různými způsoby. Jedná se o používání <xref:System.String>, nebo pomocí <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, nebo <xref:System.Xml.XPath.XPathDocument> třídy. Pro usnadnění přesouvání mezi tyto různé reprezentace dokumentu XML <xref:System.Xml.XPath.XPathNavigator> třída poskytuje několik metod a vlastností pro extrahování XML jako <xref:System.String>, <xref:System.Xml.XmlReader> objektu nebo <xref:System.Xml.XmlWriter> objektu.  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a>Převést na řetězec, objektem XPathNavigator nastaveným na  
 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Vlastnost <xref:System.Xml.XPath.XPathNavigator> třída se používá k získání značek celého dokumentu XML nebo značky jeden uzel a jeho podřízené uzly.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Vlastnost získá značky pouze podřízené uzly uzlu.  
  
 Následující příklad kódu ukazuje, jak uložit celý dokument XML obsažených v <xref:System.Xml.XPath.XPathNavigator> objektu jako <xref:System.String>, stejně jako jeden uzel a jeho podřízených uzlů.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("input.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Save the entire input.xml document to a string.  
Dim xml As String = navigator.OuterXml  
  
' Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element)  
Dim root As String = navigator.OuterXml  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Save the entire input.xml document to a string.  
string xml = navigator.OuterXml;  
  
// Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element);  
string root = navigator.OuterXml;  
```  
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a>Převést objektem XPathNavigator nastaveným na do třídy XmlReader  
 <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda se používá ke streamování celý obsah dokumentu XML nebo jenom jeden uzel a jeho podřízené uzly <xref:System.Xml.XmlReader> objektu.  
  
 Když <xref:System.Xml.XmlReader> s aktuální uzel a jeho podřízených uzlů, je vytvořen objekt <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XmlReader.ReadState%2A> je nastavena na <xref:System.Xml.ReadState.Initial>. Když <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XmlReader.Read%2A> je metoda volána poprvé, <xref:System.Xml.XmlReader> se přesune na aktuálním uzlu <xref:System.Xml.XPath.XPathNavigator>. Nové <xref:System.Xml.XmlReader> objekt pokračovat ve čtení, dokud nebude dosaženo konce stromové struktuře XML. V tomto okamžiku <xref:System.Xml.XmlReader.Read%2A> vrátí metoda `false` a <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XmlReader.ReadState%2A> je nastavena na <xref:System.Xml.ReadState.EndOfFile>.  
  
 <xref:System.Xml.XPath.XPathNavigator> Pozici objektu je beze změny ve vytváření nebo přesun <xref:System.Xml.XmlReader> objektu. <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda je platná jenom při umístěna na elementu nebo kořenového uzlu.  
  
 Následující příklad ukazuje, jak získat <xref:System.Xml.XmlReader> objekt, který obsahuje celý kód XML dokumentů v <xref:System.Xml.XPath.XPathDocument> objektu stejně jako jeden uzel a jeho podřízených uzlů.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlReader.  
Dim xml As XmlReader = navigator.ReadSubtree()  
  
While xml.Read()  
    Console.WriteLine(xml.ReadInnerXml())  
End While  
  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlReader = navigator.ReadSubtree()  
  
While book.Read()  
    Console.WriteLine(book.ReadInnerXml())  
End While  
  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlReader.  
XmlReader xml = navigator.ReadSubtree();  
  
while (xml.Read())  
{  
    Console.WriteLine(xml.ReadInnerXml());  
}  
  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlReader book = navigator.ReadSubtree();  
  
while (book.Read())  
{  
    Console.WriteLine(book.ReadInnerXml());  
}  
  
book.Close();  
```  
  
 V příkladu přebírá `books.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a>Převod objektem XPathNavigator nastaveným na třídy XmlWriter  
 <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> Metoda se používá ke streamování celý obsah dokumentu XML nebo jenom jeden uzel a jeho podřízené uzly <xref:System.Xml.XmlWriter> objektu.  
  
 <xref:System.Xml.XPath.XPathNavigator> Pozici objektu je beze změny ve vytváření <xref:System.Xml.XmlWriter> objektu.  
  
 Následující příklad ukazuje, jak získat <xref:System.Xml.XmlWriter> objekt, který obsahuje celý kód XML dokumentů v <xref:System.Xml.XPath.XPathDocument> objektu stejně jako jeden uzel a jeho podřízených uzlů.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlWriter.  
Dim xml As XmlWriter = XmlWriter.Create("newbooks.xml")  
navigator.WriteSubtree(xml)  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlWriter = XmlWriter.Create("book.xml")  
navigator.WriteSubtree(book)  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlWriter.  
XmlWriter xml = XmlWriter.Create("newbooks.xml");  
navigator.WriteSubtree(xml);  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlWriter book = XmlWriter.Create("book.xml");  
navigator.WriteSubtree(book);  
book.Close();  
```  
  
 V příkladu přebírá `books.xml` soubor nalezen dříve v tomto tématu jako vstup.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [Navigace v sadě uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
- [Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
- [Přístup k datům XML silného typu pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
