---
title: "Načítání dat XML pomocí XPathDocument a třídou XMLDocument nastavenou na"
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
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 607d9d3616db0d0bd431fa2ca0b6aee03a85f896
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a><span data-ttu-id="451c8-102">Načítání dat XML pomocí XPathDocument a třídou XMLDocument nastavenou na</span><span class="sxs-lookup"><span data-stu-id="451c8-102">Reading XML Data using XPathDocument and XmlDocument</span></span>
<span data-ttu-id="451c8-103">Existují dva způsoby, jak číst dokument XML v <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="451c8-103">There are two ways to read an XML document in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="451c8-104">Jedna je číst dokument XML pomocí jen pro čtení <xref:System.Xml.XPath.XPathDocument> třídy a druhá je číst dokument XML pomocí upravitelné <xref:System.Xml.XmlDocument> třídy v <xref:System.Xml?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="451c8-104">One is to read an XML document using the read-only <xref:System.Xml.XPath.XPathDocument> class and the other is to read an XML document using the editable <xref:System.Xml.XmlDocument> class in the <xref:System.Xml?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a><span data-ttu-id="451c8-105">Čtení XML – dokumenty pomocí třídy XPathDocument</span><span class="sxs-lookup"><span data-stu-id="451c8-105">Reading XML Documents using the XPathDocument Class</span></span>  
 <span data-ttu-id="451c8-106"><xref:System.Xml.XPath.XPathDocument> Třída poskytuje rychlé, jen pro čtení, v paměti reprezentace dokumentu XML pomocí modelu dat XPath.</span><span class="sxs-lookup"><span data-stu-id="451c8-106">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="451c8-107">Instance <xref:System.Xml.XPath.XPathDocument> třídy jsou vytvořeny pomocí jednoho z jeho šest konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="451c8-107">Instances of the <xref:System.Xml.XPath.XPathDocument> class are created using one of its six constructors.</span></span> <span data-ttu-id="451c8-108">Tyto konstruktory umožňují čtení dokumentu XML pomocí <xref:System.IO.Stream>, <xref:System.IO.TextReader>, nebo <xref:System.Xml.XmlReader> objekt, a taky `string` cestu k souboru XML.</span><span class="sxs-lookup"><span data-stu-id="451c8-108">These constructors allow you to read an XML document using a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="451c8-109">Následující příklad ilustruje, pomocí <xref:System.Xml.XPath.XPathDocument> třídy `string` konstruktor číst dokument XML.</span><span class="sxs-lookup"><span data-stu-id="451c8-109">The following example illustrates using the <xref:System.Xml.XPath.XPathDocument> class's `string` constructor to read an XML document.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a><span data-ttu-id="451c8-110">Čtení XML – dokumenty pomocí třídy třídou XMLDocument nastavenou na</span><span class="sxs-lookup"><span data-stu-id="451c8-110">Reading XML Documents using the XmlDocument Class</span></span>  
 <span data-ttu-id="451c8-111"><xref:System.Xml.XmlDocument> Třída je reprezentaci upravovat v paměti dokumentu XML, které implementují základní úroveň 1 W3C Model Document Object (DOM) a základní DOM Level 2.</span><span class="sxs-lookup"><span data-stu-id="451c8-111">The <xref:System.Xml.XmlDocument> class is an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="451c8-112">Instance <xref:System.Xml.XmlDocument> třídy jsou vytvořeny pomocí jednoho z jeho tři konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="451c8-112">Instances of the <xref:System.Xml.XmlDocument> class are created using one of its three constructors.</span></span> <span data-ttu-id="451c8-113">Můžete vytvořit nový, prázdný <xref:System.Xml.XmlDocument> objekt voláním <xref:System.Xml.XmlDocument> třída – konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="451c8-113">You can create a new, empty <xref:System.Xml.XmlDocument> object by calling the <xref:System.Xml.XmlDocument> class constructor with no parameters.</span></span> <span data-ttu-id="451c8-114">Po volání metody konstruktoru, použijte <xref:System.Xml.XmlDocument.Load%2A> metodu pro načtení dat XML do nové <xref:System.Xml.XmlDocument> objektu z <xref:System.IO.Stream>, <xref:System.IO.TextReader>, nebo <xref:System.Xml.XmlReader> objekt, a taky `string` cestu k souboru XML.</span><span class="sxs-lookup"><span data-stu-id="451c8-114">After calling the constructor, use the <xref:System.Xml.XmlDocument.Load%2A> method to load XML data into the new <xref:System.Xml.XmlDocument> object from a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="451c8-115">Následující příklad ilustruje, pomocí <xref:System.Xml.XmlDocument> třída – konstruktor bez parametrů a <xref:System.Xml.XmlDocument.Load%2A> metoda číst dokument XML.</span><span class="sxs-lookup"><span data-stu-id="451c8-115">The following example illustrates using the <xref:System.Xml.XmlDocument> class constructor with no parameters and the <xref:System.Xml.XmlDocument.Load%2A> method to read an XML document.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a><span data-ttu-id="451c8-116">Určení kódování dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="451c8-116">Determining the Encoding of an XML Document</span></span>  
 <span data-ttu-id="451c8-117"><xref:System.Xml.XmlReader> Objekt lze použít ke čtení dokumentu XML a vytvořte <xref:System.Xml.XPath.XPathDocument> a <xref:System.Xml.XmlDocument> objekty, jak je znázorněno v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="451c8-117">An <xref:System.Xml.XmlReader> object can be used to read an XML document and to create <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> objects as shown in the previous sections.</span></span> <span data-ttu-id="451c8-118">Však <xref:System.Xml.XmlReader> objekt lze číst data, která není kódovaný a v důsledku neposkytuje žádné kódování informace.</span><span class="sxs-lookup"><span data-stu-id="451c8-118">However, an <xref:System.Xml.XmlReader> object may read data that is not encoded and as a result does not provide any encoding information.</span></span>  
  
 <span data-ttu-id="451c8-119"><xref:System.Xml.XmlTextReader> Třída dědí z <xref:System.Xml.XmlReader> třídy, poskytuje kódování informací pomocí jeho <xref:System.Xml.XmlTextReader.Encoding%2A> vlastnost a můžete použít k vytvoření <xref:System.Xml.XPath.XPathDocument> objekt nebo <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="451c8-119">The <xref:System.Xml.XmlTextReader> class inherits from the <xref:System.Xml.XmlReader> class, provides encoding information using its <xref:System.Xml.XmlTextReader.Encoding%2A> property, and can be used to create an <xref:System.Xml.XPath.XPathDocument> object or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="451c8-120">Další informace o kódování poskytnuté informace o <xref:System.Xml.XmlTextReader> třídy najdete v tématu <xref:System.Xml.XmlTextReader.Encoding%2A> vlastnost <xref:System.Xml.XmlTextReader> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="451c8-120">For more information about the encoding information provided by the <xref:System.Xml.XmlTextReader> class, see the <xref:System.Xml.XmlTextReader.Encoding%2A> property in the <xref:System.Xml.XmlTextReader> class reference documentation.</span></span>  
  
## <a name="creating-xpathnavigator-objects"></a><span data-ttu-id="451c8-121">Vytváření objektem XPathNavigator nastaveným na objekty</span><span class="sxs-lookup"><span data-stu-id="451c8-121">Creating XPathNavigator Objects</span></span>  
 <span data-ttu-id="451c8-122">Přečtěte si dokument XML do buď <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objekt, můžete vytvořit <xref:System.Xml.XPath.XPathNavigator> objektu k výběru, vyhodnotit, přejděte a v některých případech upravit základní data XML.</span><span class="sxs-lookup"><span data-stu-id="451c8-122">After you have read an XML document into either an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, you can create an <xref:System.Xml.XPath.XPathNavigator> object to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="451c8-123">Jak <xref:System.Xml.XPath.XPathDocument> a <xref:System.Xml.XmlDocument> třídy kromě k <xref:System.Xml.XmlNode> třídy, implementovat <xref:System.Xml.XPath.IXPathNavigable> rozhraní <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="451c8-123">Both the <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> classes, in addition to the <xref:System.Xml.XmlNode> class, implement the <xref:System.Xml.XPath.IXPathNavigable> interface of the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="451c8-124">Výsledkem je, zadejte všechny tři třídy <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> metodu, která vrátí <xref:System.Xml.XPath.XPathNavigator> objektu.</span><span class="sxs-lookup"><span data-stu-id="451c8-124">As a result, all three classes provide a <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> method that returns an <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a><span data-ttu-id="451c8-125">XML – dokumenty pomocí třídy objektem XPathNavigator nastaveným na úpravy</span><span class="sxs-lookup"><span data-stu-id="451c8-125">Editing XML Documents using the XPathNavigator Class</span></span>  
 <span data-ttu-id="451c8-126">Kromě výběru, hodnocení a navigace v datech XML <xref:System.Xml.XPath.XPathNavigator> třídu lze použít pro úpravu dokumentu XML v některých případech založeného na objektu, která ji vytvořila.</span><span class="sxs-lookup"><span data-stu-id="451c8-126">In addition to selecting, evaluating, and navigating XML data, the <xref:System.Xml.XPath.XPathNavigator> class can be used to edit an XML document in some cases, based on the object that created it.</span></span>  
  
 <span data-ttu-id="451c8-127"><xref:System.Xml.XPath.XPathDocument> Třída je jen pro čtení při <xref:System.Xml.XmlDocument> třída je upravovat a v důsledku toho <xref:System.Xml.XPath.XPathNavigator> objekty vytvořené z <xref:System.Xml.XPath.XPathDocument> objekt nelze použít, chcete-li upravit dokument XML při nebyla vytvořena z <xref:System.Xml.XmlDocument> můžete objekt.</span><span class="sxs-lookup"><span data-stu-id="451c8-127">The <xref:System.Xml.XPath.XPathDocument> class is read-only while the <xref:System.Xml.XmlDocument> class is editable and as a result, <xref:System.Xml.XPath.XPathNavigator> objects created from an <xref:System.Xml.XPath.XPathDocument> object cannot be used to edit an XML document while those created from an <xref:System.Xml.XmlDocument> object can.</span></span> <span data-ttu-id="451c8-128"><xref:System.Xml.XPath.XPathDocument> Třída slouží ke čtení dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="451c8-128">The <xref:System.Xml.XPath.XPathDocument> class should be used to read an XML document only.</span></span> <span data-ttu-id="451c8-129">V případech, kdy potřebujete upravit dokument XML nebo vyžadují přístup k další funkce poskytované službou <xref:System.Xml.XmlDocument> třídy, jako je zpracování událostí <xref:System.Xml.XmlDocument> třída by měla být použita.</span><span class="sxs-lookup"><span data-stu-id="451c8-129">In cases where you need to edit an XML document, or require access to the additional functionality provided by the <xref:System.Xml.XmlDocument> class, like event handling, the <xref:System.Xml.XmlDocument> class should be used.</span></span>  
  
 <span data-ttu-id="451c8-130"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Vlastnost <xref:System.Xml.XPath.XPathNavigator> Určuje třídu, pokud <xref:System.Xml.XPath.XPathNavigator> objekt může upravit XML data.</span><span class="sxs-lookup"><span data-stu-id="451c8-130">The <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class specifies if an <xref:System.Xml.XPath.XPathNavigator> object may edit XML data.</span></span>  
  
 <span data-ttu-id="451c8-131">Následující tabulka popisuje hodnotu <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> vlastnosti pro každou třídu.</span><span class="sxs-lookup"><span data-stu-id="451c8-131">The following table describes the value of the <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property for each class.</span></span>  
  
|<span data-ttu-id="451c8-132"><xref:System.Xml.XPath.IXPathNavigable>Implementace</span><span class="sxs-lookup"><span data-stu-id="451c8-132"><xref:System.Xml.XPath.IXPathNavigable> Implementation</span></span>|<span data-ttu-id="451c8-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A>Hodnota</span><span class="sxs-lookup"><span data-stu-id="451c8-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Value</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a><span data-ttu-id="451c8-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="451c8-134">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="451c8-135">Zpracování kódu XML dat pomocí jazyka XPath datový Model</span><span class="sxs-lookup"><span data-stu-id="451c8-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="451c8-136">Přístup k datům XML pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="451c8-136">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="451c8-137">Úpravy pomocí objektem XPathNavigator nastaveným na Data XML</span><span class="sxs-lookup"><span data-stu-id="451c8-137">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="451c8-138">Ověření schématu pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="451c8-138">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
