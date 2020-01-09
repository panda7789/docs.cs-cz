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
Dokument XML lze v .NET Framework společnosti Microsoft znázornit několika různými způsoby. To zahrnuje použití <xref:System.String>, nebo pomocí tříd <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>nebo <xref:System.Xml.XPath.XPathDocument>. Pro usnadnění přechodu mezi těmito různými reprezentacemi dokumentu XML poskytuje třída <xref:System.Xml.XPath.XPathNavigator> řadu metod a vlastností pro extrahování XML jako <xref:System.String>, <xref:System.Xml.XmlReader> objekt nebo objekt <xref:System.Xml.XmlWriter>.  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a>Převod XPathNavigator na řetězec  
 Vlastnost <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> třídy <xref:System.Xml.XPath.XPathNavigator> se používá k získání značky celého dokumentu XML nebo pouze označení jednoho uzlu a jeho podřízených uzlů.  
  
> [!NOTE]
> Vlastnost <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> získá označení pouze podřízených uzlů uzlu.  
  
 Následující příklad kódu ukazuje, jak uložit celý dokument XML obsažený v objektu <xref:System.Xml.XPath.XPathNavigator> jako <xref:System.String>a také v jednom uzlu a jeho podřízených uzlech.  
  
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
 Metoda <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> slouží ke streamování celého obsahu dokumentu XML nebo pouze jednoho uzlu a jeho podřízených uzlů k objektu <xref:System.Xml.XmlReader>.  
  
 Když je objekt <xref:System.Xml.XmlReader> vytvořen s aktuálním uzlem a jeho podřízenými uzly, vlastnost <xref:System.Xml.XmlReader.ReadState%2A> objektu <xref:System.Xml.XmlReader> je nastavena na <xref:System.Xml.ReadState.Initial>. Při prvním volání metody <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XmlReader.Read%2A> je <xref:System.Xml.XmlReader> přesunuta do aktuálního uzlu <xref:System.Xml.XPath.XPathNavigator>. Nový objekt <xref:System.Xml.XmlReader> pokračuje v čtení, dokud nebude dosaženo konce stromu XML. V tomto okamžiku metoda <xref:System.Xml.XmlReader.Read%2A> vrátí `false` a vlastnost <xref:System.Xml.XmlReader.ReadState%2A> objektu <xref:System.Xml.XmlReader> je nastavena na hodnotu <xref:System.Xml.ReadState.EndOfFile>.  
  
 Pozice objektu <xref:System.Xml.XPath.XPathNavigator> se nezměnila vytvořením nebo přesunutím objektu <xref:System.Xml.XmlReader>. Metoda <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> je platná pouze v případě, že je umístěna na elementu nebo kořenovém uzlu.  
  
 Následující příklad ukazuje, jak získat objekt <xref:System.Xml.XmlReader> obsahující celý dokument XML v objektu <xref:System.Xml.XPath.XPathDocument> a také jeden uzel a jeho podřízené uzly.  
  
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
  
 V příkladu se jako vstup používá soubor `books.xml`.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a>Převod XPathNavigator na XmlWriter  
 Metoda <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> slouží ke streamování celého obsahu dokumentu XML nebo pouze jednoho uzlu a jeho podřízených uzlů k objektu <xref:System.Xml.XmlWriter>.  
  
 Pozice objektu <xref:System.Xml.XPath.XPathNavigator> se nezměnila vytvořením objektu <xref:System.Xml.XmlWriter>.  
  
 Následující příklad ukazuje, jak získat objekt <xref:System.Xml.XmlWriter> obsahující celý dokument XML v objektu <xref:System.Xml.XPath.XPathDocument> a také jeden uzel a jeho podřízené uzly.  
  
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
  
 Tento příklad používá soubor `books.xml`, který byl nalezen dříve v tomto tématu jako vstup.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Navigace v sadě uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [Přístup k datům XML silného typu pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
