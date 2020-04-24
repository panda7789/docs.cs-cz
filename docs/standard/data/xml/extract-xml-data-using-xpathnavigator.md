---
title: Extrahování dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
ms.openlocfilehash: 627da3c8c45d007e677c4f92f4d5cd602d34ae84
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710853"
---
# <a name="extract-xml-data-using-xpathnavigator"></a>Extrahování dat XML pomocí XPathNavigator
Dokument XML lze v .NET Framework společnosti Microsoft znázornit několika různými způsoby. To <xref:System.String>zahrnuje použití <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> <xref:System.Xml.XPath.XPathDocument> třídy, nebo pomocí tříd,, <xref:System.Xml.XmlDocument>nebo. Aby bylo možné se pohybovat mezi těmito různými reprezentacemi dokumentu <xref:System.Xml.XPath.XPathNavigator> XML, poskytuje třída množství metod a vlastností pro extrakci XML jako <xref:System.String> <xref:System.Xml.XmlReader> objekt nebo <xref:System.Xml.XmlWriter> objekt.  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a>Převod XPathNavigator na řetězec  
 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy slouží k získání značky celého dokumentu XML nebo pouze označení jednoho uzlu a jeho podřízených uzlů.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Vlastnost získá označení pouze podřízených uzlů uzlu.  
  
 Následující příklad kódu ukazuje, jak uložit celý dokument XML obsažený v <xref:System.Xml.XPath.XPathNavigator> objektu jako <xref:System.String>a také v jednom uzlu a jeho podřízených uzlech.  
  
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
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a>Převod XPathNavigator na XmlReader  
 <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda se používá pro streamování celého obsahu dokumentu XML nebo pouze jednoho uzlu a jeho podřízených uzlů <xref:System.Xml.XmlReader> objektu.  
  
 Když je <xref:System.Xml.XmlReader> objekt vytvořen s aktuálním uzlem a jeho podřízenými uzly, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader.ReadState%2A> vlastnost objektu je nastavena na <xref:System.Xml.ReadState.Initial>hodnotu. Při prvním <xref:System.Xml.XmlReader> volání <xref:System.Xml.XmlReader.Read%2A> metody objektu <xref:System.Xml.XmlReader> je objekt přesunut do aktuálního uzlu. <xref:System.Xml.XPath.XPathNavigator> Nový <xref:System.Xml.XmlReader> objekt bude pokračovat v čtení, dokud nebude dosaženo konce stromu XML. <xref:System.Xml.XmlReader.Read%2A> V tomto okamžiku se metoda vrátí `false` a <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader.ReadState%2A> vlastnost objektu je nastavena na. <xref:System.Xml.ReadState.EndOfFile>  
  
 Pozice <xref:System.Xml.XPath.XPathNavigator> objektu je beze změny vytvořením nebo přesunem <xref:System.Xml.XmlReader> objektu. <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda je platná pouze v případě, že je umístěna na elementu nebo kořenovém uzlu.  
  
 Následující příklad ukazuje, jak získat <xref:System.Xml.XmlReader> objekt obsahující celý dokument XML v <xref:System.Xml.XPath.XPathDocument> objektu a také jeden uzel a jeho podřízené uzly.  
  
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
  
 Příklad přebírá `books.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a>Převod XPathNavigator na XmlWriter  
 <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> Metoda se používá pro streamování celého obsahu dokumentu XML nebo pouze jednoho uzlu a jeho podřízených uzlů <xref:System.Xml.XmlWriter> objektu.  
  
 Pozice <xref:System.Xml.XPath.XPathNavigator> objektu je beze změny vytvoření <xref:System.Xml.XmlWriter> objektu.  
  
 Následující příklad ukazuje, jak získat <xref:System.Xml.XmlWriter> objekt obsahující celý dokument XML v <xref:System.Xml.XPath.XPathDocument> objektu a také jeden uzel a jeho podřízené uzly.  
  
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
  
 Příklad převezme soubor `books.xml` , který byl nalezen dříve v tomto tématu, jako vstup.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Navigace v sadě uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [Přístup k datům XML silného typu pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
