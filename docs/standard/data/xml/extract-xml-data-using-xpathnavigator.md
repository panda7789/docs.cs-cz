---
title: "Extrahovat pomocí objektem XPathNavigator nastaveným na Data XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c42539db3750ebc2a4220ef776b89bbabe6aaca3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="extract-xml-data-using-xpathnavigator"></a>Extrahovat pomocí objektem XPathNavigator nastaveným na Data XML
Představují dokument XML v rozhraní Microsoft .NET Framework několika různými způsoby. To zahrnuje použití <xref:System.String>, nebo pomocí <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, nebo <xref:System.Xml.XPath.XPathDocument> třídy. Pro usnadnění přesun mezi tyto různé reprezentace dokumentu XML <xref:System.Xml.XPath.XPathNavigator> třída poskytuje několik metod a vlastností pro extrahování XML jako <xref:System.String>, <xref:System.Xml.XmlReader> objekt nebo <xref:System.Xml.XmlWriter> objektu.  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a>Převést objektem XPathNavigator nastaveným na řetězec  
 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Vlastnost <xref:System.Xml.XPath.XPathNavigator> třída se používá k získání značek celého dokumentu XML nebo kód jeden uzel a jeho podřízené uzly.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Vlastnost získá značku právě podřízené uzly uzlu.  
  
 Následující příklad kódu ukazuje, jak uložit celý dokument XML obsažených v <xref:System.Xml.XPath.XPathNavigator> objekt jako <xref:System.String>, a také jeden uzel a jeho podřízené uzly.  
  
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
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a>Převést objektem XPathNavigator nastaveným na objekt XmlReader  
 <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda se používá k vysílání datového proudu celý obsah dokumentu XML nebo jenom jeden uzel a jeho podřízené uzly do <xref:System.Xml.XmlReader> objektu.  
  
 Když <xref:System.Xml.XmlReader> s aktuálním uzlu a jeho podřízené uzly, je vytvořen objekt <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XmlReader.ReadState%2A> je nastavena na <xref:System.Xml.ReadState.Initial>. Když <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XmlReader.Read%2A> metoda je volána poprvé, <xref:System.Xml.XmlReader> je přesunout na aktuálním uzlu <xref:System.Xml.XPath.XPathNavigator>. Nové <xref:System.Xml.XmlReader> objekt pokračovat ve čtení, dokud nebude dosaženo konce stromové struktuře XML. V tomto okamžiku <xref:System.Xml.XmlReader.Read%2A> metoda vrátí `false` a <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XmlReader.ReadState%2A> je nastavena na <xref:System.Xml.ReadState.EndOfFile>.  
  
 <xref:System.Xml.XPath.XPathNavigator> Nezměnil umístění objektu pro vytváření nebo pohyb <xref:System.Xml.XmlReader> objektu. <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda platí, pouze když umístěný na element nebo kořenový uzel.  
  
 Následující příklad ukazuje, jak získat <xref:System.Xml.XmlReader> objekt, který obsahuje XML celého dokumentu v <xref:System.Xml.XPath.XPathDocument> objektu a také jeden uzel a jeho podřízené uzly.  
  
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
  
 V příkladu trvá `books.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a>Převádění objektem XPathNavigator nastaveným na XmlWriter  
 <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> Metoda se používá k vysílání datového proudu celý obsah dokumentu XML nebo jenom jeden uzel a jeho podřízené uzly do <xref:System.Xml.XmlWriter> objektu.  
  
 <xref:System.Xml.XPath.XPathNavigator> Umístění objektu je beze změny pomocí vytvoření <xref:System.Xml.XmlWriter> objektu.  
  
 Následující příklad ukazuje, jak získat <xref:System.Xml.XmlWriter> objekt, který obsahuje XML celého dokumentu v <xref:System.Xml.XPath.XPathDocument> objektu a také jeden uzel a jeho podřízené uzly.  
  
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
  
 V příkladu trvá `books.xml` nalezeno dříve v tomto tématu jako vstup.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování kódu XML dat pomocí jazyka XPath datový Model](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Uzel navigační sady pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [Atribut a Namespace uzlu navigace pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [Přístup k důrazně zadali pomocí objektem XPathNavigator nastaveným na Data XML](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
