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
ms.openlocfilehash: f789317defe3f4b44b37e6d94d37b974d003bcae
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967000"
---
# <a name="extract-xml-data-using-xpathnavigator"></a><span data-ttu-id="a72fa-102">Extrahování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a72fa-102">Extract XML Data Using XPathNavigator</span></span>
<span data-ttu-id="a72fa-103">Dokument XML lze v .NET Framework společnosti Microsoft znázornit několika různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="a72fa-103">There are several different ways to represent an XML document in the Microsoft .NET Framework.</span></span> <span data-ttu-id="a72fa-104"><xref:System.String>To zahrnuje použití <xref:System.Xml.XPath.XPathDocument> třídy, nebo <xref:System.Xml.XmlReader>pomocí tříd, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>nebo.</span><span class="sxs-lookup"><span data-stu-id="a72fa-104">This includes using a <xref:System.String>, or by using the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, or <xref:System.Xml.XPath.XPathDocument> classes.</span></span> <span data-ttu-id="a72fa-105">Aby bylo možné se pohybovat mezi těmito různými <xref:System.Xml.XPath.XPathNavigator> reprezentacemi dokumentu XML, poskytuje třída množství metod a vlastností pro extrakci XML <xref:System.String>jako <xref:System.Xml.XmlReader> objekt nebo <xref:System.Xml.XmlWriter> objekt.</span><span class="sxs-lookup"><span data-stu-id="a72fa-105">To facilitate moving between these different representations of an XML document, the <xref:System.Xml.XPath.XPathNavigator> class provides a number of methods and properties for extracting the XML as a <xref:System.String>, <xref:System.Xml.XmlReader> object or <xref:System.Xml.XmlWriter> object.</span></span>  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a><span data-ttu-id="a72fa-106">Převod XPathNavigator na řetězec</span><span class="sxs-lookup"><span data-stu-id="a72fa-106">Convert an XPathNavigator to a String</span></span>  
 <span data-ttu-id="a72fa-107"><xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Vlastnost<xref:System.Xml.XPath.XPathNavigator> třídy slouží k získání značky celého dokumentu XML nebo pouze označení jednoho uzlu a jeho podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="a72fa-107">The <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class is used to get the markup of the entire XML document or just the markup of a single node and its child nodes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a72fa-108"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Vlastnost získá označení pouze podřízených uzlů uzlu.</span><span class="sxs-lookup"><span data-stu-id="a72fa-108">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property gets the markup of just the child nodes of a node.</span></span>  
  
 <span data-ttu-id="a72fa-109">Následující příklad kódu ukazuje, jak uložit celý dokument XML obsažený v <xref:System.Xml.XPath.XPathNavigator> objektu <xref:System.String>jako a také v jednom uzlu a jeho podřízených uzlech.</span><span class="sxs-lookup"><span data-stu-id="a72fa-109">The following code example shows how to save an entire XML document contained in an <xref:System.Xml.XPath.XPathNavigator> object as a <xref:System.String>, as well as a single node and its child nodes.</span></span>  
  
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
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a><span data-ttu-id="a72fa-110">Převod XPathNavigator na XmlReader</span><span class="sxs-lookup"><span data-stu-id="a72fa-110">Convert an XPathNavigator to an XmlReader</span></span>  
 <span data-ttu-id="a72fa-111">Metoda se používá pro streamování celého obsahu dokumentu XML nebo pouze jednoho uzlu a jeho podřízených uzlů <xref:System.Xml.XmlReader> objektu. <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A></span><span class="sxs-lookup"><span data-stu-id="a72fa-111">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlReader> object.</span></span>  
  
 <span data-ttu-id="a72fa-112">Když je <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader.ReadState%2A> <xref:System.Xml.ReadState.Initial>objekt vytvořen s aktuálním uzlem a jeho podřízenými uzly, vlastnost objektu je nastavena na hodnotu. <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="a72fa-112">When the <xref:System.Xml.XmlReader> object is created with the current node and its child nodes, the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.Initial>.</span></span> <span data-ttu-id="a72fa-113">Při prvním <xref:System.Xml.XmlReader.Read%2A>volánímetody <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XPath.XPathNavigator>je objekt přesunut do aktuálního uzlu. <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="a72fa-113">When the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.Read%2A> method is called for the first time, the <xref:System.Xml.XmlReader> is moved to the current node of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="a72fa-114">Nový <xref:System.Xml.XmlReader> objekt bude pokračovat v čtení, dokud nebude dosaženo konce stromu XML.</span><span class="sxs-lookup"><span data-stu-id="a72fa-114">The new <xref:System.Xml.XmlReader> object continues to read until the end of the XML tree is reached.</span></span> <span data-ttu-id="a72fa-115"><xref:System.Xml.XmlReader.Read%2A> V tomto okamžiku se metoda vrátí <xref:System.Xml.XmlReader> `false` a <xref:System.Xml.XmlReader.ReadState%2A> vlastnost objektu je nastavena na <xref:System.Xml.ReadState.EndOfFile>.</span><span class="sxs-lookup"><span data-stu-id="a72fa-115">At this point, the <xref:System.Xml.XmlReader.Read%2A> method returns `false` and the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.EndOfFile>.</span></span>  
  
 <span data-ttu-id="a72fa-116">Pozice objektu je beze změny vytvořením nebo přesunem <xref:System.Xml.XmlReader> objektu. <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="a72fa-116">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation or movement of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="a72fa-117"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda je platná pouze v případě, že je umístěna na elementu nebo kořenovém uzlu.</span><span class="sxs-lookup"><span data-stu-id="a72fa-117">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is only valid when positioned on an element or root node.</span></span>  
  
 <span data-ttu-id="a72fa-118">Následující příklad ukazuje, jak získat <xref:System.Xml.XmlReader> objekt obsahující celý dokument XML <xref:System.Xml.XPath.XPathDocument> v objektu a také jeden uzel a jeho podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="a72fa-118">The following example shows how to get an <xref:System.Xml.XmlReader> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
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
  
 <span data-ttu-id="a72fa-119">Příklad přebírá `books.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="a72fa-119">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a><span data-ttu-id="a72fa-120">Převod XPathNavigator na XmlWriter</span><span class="sxs-lookup"><span data-stu-id="a72fa-120">Converting an XPathNavigator to an XmlWriter</span></span>  
 <span data-ttu-id="a72fa-121">Metoda se používá pro streamování celého obsahu dokumentu XML nebo pouze jednoho uzlu a jeho podřízených uzlů <xref:System.Xml.XmlWriter> objektu. <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A></span><span class="sxs-lookup"><span data-stu-id="a72fa-121">The <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="a72fa-122">Pozice objektu je beze změny vytvoření <xref:System.Xml.XmlWriter> objektu. <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="a72fa-122">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation of the <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="a72fa-123">Následující příklad ukazuje, jak získat <xref:System.Xml.XmlWriter> objekt obsahující celý dokument XML <xref:System.Xml.XPath.XPathDocument> v objektu a také jeden uzel a jeho podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="a72fa-123">The following example shows how to get an <xref:System.Xml.XmlWriter> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
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
  
 <span data-ttu-id="a72fa-124">Příklad převezme soubor `books.xml` , který byl nalezen dříve v tomto tématu, jako vstup.</span><span class="sxs-lookup"><span data-stu-id="a72fa-124">The example takes the `books.xml` file found earlier in this topic as input.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a72fa-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a72fa-125">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="a72fa-126">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="a72fa-126">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="a72fa-127">Navigace v sadě uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a72fa-127">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="a72fa-128">Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a72fa-128">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="a72fa-129">Přístup k datům XML silného typu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a72fa-129">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
