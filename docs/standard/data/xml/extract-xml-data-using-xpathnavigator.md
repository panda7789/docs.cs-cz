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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f80c21e7809e5b088582a51d9085a187bccae444
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="extract-xml-data-using-xpathnavigator"></a><span data-ttu-id="85eeb-102">Extrahovat pomocí objektem XPathNavigator nastaveným na Data XML</span><span class="sxs-lookup"><span data-stu-id="85eeb-102">Extract XML Data Using XPathNavigator</span></span>
<span data-ttu-id="85eeb-103">Představují dokument XML v rozhraní Microsoft .NET Framework několika různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="85eeb-103">There are several different ways to represent an XML document in the Microsoft .NET Framework.</span></span> <span data-ttu-id="85eeb-104">To zahrnuje použití <xref:System.String>, nebo pomocí <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, nebo <xref:System.Xml.XPath.XPathDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="85eeb-104">This includes using a <xref:System.String>, or by using the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, or <xref:System.Xml.XPath.XPathDocument> classes.</span></span> <span data-ttu-id="85eeb-105">Pro usnadnění přesun mezi tyto různé reprezentace dokumentu XML <xref:System.Xml.XPath.XPathNavigator> třída poskytuje několik metod a vlastností pro extrahování XML jako <xref:System.String>, <xref:System.Xml.XmlReader> objekt nebo <xref:System.Xml.XmlWriter> objektu.</span><span class="sxs-lookup"><span data-stu-id="85eeb-105">To facilitate moving between these different representations of an XML document, the <xref:System.Xml.XPath.XPathNavigator> class provides a number of methods and properties for extracting the XML as a <xref:System.String>, <xref:System.Xml.XmlReader> object or <xref:System.Xml.XmlWriter> object.</span></span>  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a><span data-ttu-id="85eeb-106">Převést objektem XPathNavigator nastaveným na řetězec</span><span class="sxs-lookup"><span data-stu-id="85eeb-106">Convert an XPathNavigator to a String</span></span>  
 <span data-ttu-id="85eeb-107"><xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Vlastnost <xref:System.Xml.XPath.XPathNavigator> třída se používá k získání značek celého dokumentu XML nebo kód jeden uzel a jeho podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="85eeb-107">The <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class is used to get the markup of the entire XML document or just the markup of a single node and its child nodes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85eeb-108"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Vlastnost získá značku právě podřízené uzly uzlu.</span><span class="sxs-lookup"><span data-stu-id="85eeb-108">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property gets the markup of just the child nodes of a node.</span></span>  
  
 <span data-ttu-id="85eeb-109">Následující příklad kódu ukazuje, jak uložit celý dokument XML obsažených v <xref:System.Xml.XPath.XPathNavigator> objekt jako <xref:System.String>, a také jeden uzel a jeho podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="85eeb-109">The following code example shows how to save an entire XML document contained in an <xref:System.Xml.XPath.XPathNavigator> object as a <xref:System.String>, as well as a single node and its child nodes.</span></span>  
  
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
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a><span data-ttu-id="85eeb-110">Převést objektem XPathNavigator nastaveným na objekt XmlReader</span><span class="sxs-lookup"><span data-stu-id="85eeb-110">Convert an XPathNavigator to an XmlReader</span></span>  
 <span data-ttu-id="85eeb-111"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda se používá k vysílání datového proudu celý obsah dokumentu XML nebo jenom jeden uzel a jeho podřízené uzly do <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="85eeb-111">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlReader> object.</span></span>  
  
 <span data-ttu-id="85eeb-112">Když <xref:System.Xml.XmlReader> s aktuálním uzlu a jeho podřízené uzly, je vytvořen objekt <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XmlReader.ReadState%2A> je nastavena na <xref:System.Xml.ReadState.Initial>.</span><span class="sxs-lookup"><span data-stu-id="85eeb-112">When the <xref:System.Xml.XmlReader> object is created with the current node and its child nodes, the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.Initial>.</span></span> <span data-ttu-id="85eeb-113">Když <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XmlReader.Read%2A> metoda je volána poprvé, <xref:System.Xml.XmlReader> je přesunout na aktuálním uzlu <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="85eeb-113">When the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.Read%2A> method is called for the first time, the <xref:System.Xml.XmlReader> is moved to the current node of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="85eeb-114">Nové <xref:System.Xml.XmlReader> objekt pokračovat ve čtení, dokud nebude dosaženo konce stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="85eeb-114">The new <xref:System.Xml.XmlReader> object continues to read until the end of the XML tree is reached.</span></span> <span data-ttu-id="85eeb-115">V tomto okamžiku <xref:System.Xml.XmlReader.Read%2A> metoda vrátí `false` a <xref:System.Xml.XmlReader> objektu <xref:System.Xml.XmlReader.ReadState%2A> je nastavena na <xref:System.Xml.ReadState.EndOfFile>.</span><span class="sxs-lookup"><span data-stu-id="85eeb-115">At this point, the <xref:System.Xml.XmlReader.Read%2A> method returns `false` and the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.EndOfFile>.</span></span>  
  
 <span data-ttu-id="85eeb-116"><xref:System.Xml.XPath.XPathNavigator> Nezměnil umístění objektu pro vytváření nebo pohyb <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="85eeb-116">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation or movement of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="85eeb-117"><xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Metoda platí, pouze když umístěný na element nebo kořenový uzel.</span><span class="sxs-lookup"><span data-stu-id="85eeb-117">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is only valid when positioned on an element or root node.</span></span>  
  
 <span data-ttu-id="85eeb-118">Následující příklad ukazuje, jak získat <xref:System.Xml.XmlReader> objekt, který obsahuje XML celého dokumentu v <xref:System.Xml.XPath.XPathDocument> objektu a také jeden uzel a jeho podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="85eeb-118">The following example shows how to get an <xref:System.Xml.XmlReader> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
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
  
 <span data-ttu-id="85eeb-119">V příkladu trvá `books.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="85eeb-119">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a><span data-ttu-id="85eeb-120">Převádění objektem XPathNavigator nastaveným na XmlWriter</span><span class="sxs-lookup"><span data-stu-id="85eeb-120">Converting an XPathNavigator to an XmlWriter</span></span>  
 <span data-ttu-id="85eeb-121"><xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> Metoda se používá k vysílání datového proudu celý obsah dokumentu XML nebo jenom jeden uzel a jeho podřízené uzly do <xref:System.Xml.XmlWriter> objektu.</span><span class="sxs-lookup"><span data-stu-id="85eeb-121">The <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="85eeb-122"><xref:System.Xml.XPath.XPathNavigator> Umístění objektu je beze změny pomocí vytvoření <xref:System.Xml.XmlWriter> objektu.</span><span class="sxs-lookup"><span data-stu-id="85eeb-122">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation of the <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="85eeb-123">Následující příklad ukazuje, jak získat <xref:System.Xml.XmlWriter> objekt, který obsahuje XML celého dokumentu v <xref:System.Xml.XPath.XPathDocument> objektu a také jeden uzel a jeho podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="85eeb-123">The following example shows how to get an <xref:System.Xml.XmlWriter> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
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
  
 <span data-ttu-id="85eeb-124">V příkladu trvá `books.xml` nalezeno dříve v tomto tématu jako vstup.</span><span class="sxs-lookup"><span data-stu-id="85eeb-124">The example takes the `books.xml` file found earlier in this topic as input.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85eeb-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="85eeb-125">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="85eeb-126">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="85eeb-126">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="85eeb-127">Navigace v sadě uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="85eeb-127">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="85eeb-128">Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="85eeb-128">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="85eeb-129">Přístup k datům XML silného typu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="85eeb-129">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
