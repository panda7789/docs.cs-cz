---
title: Čtení dat XML pomocí XPathDocument a XmlDocument
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69e22328c39ae68acc4baff12775b49fbac80696
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252828"
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a><span data-ttu-id="ea972-102">Čtení dat XML pomocí XPathDocument a XmlDocument</span><span class="sxs-lookup"><span data-stu-id="ea972-102">Reading XML Data using XPathDocument and XmlDocument</span></span>
<span data-ttu-id="ea972-103">Existují dva způsoby, jak číst v dokumentu XML <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ea972-103">There are two ways to read an XML document in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ea972-104">Jeden je ke čtení dokumentu XML pomocí jen pro čtení <xref:System.Xml.XPath.XPathDocument> třídy a druhý je ke čtení dokumentu XML pomocí upravitelné <xref:System.Xml.XmlDocument> třídy v <xref:System.Xml?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ea972-104">One is to read an XML document using the read-only <xref:System.Xml.XPath.XPathDocument> class and the other is to read an XML document using the editable <xref:System.Xml.XmlDocument> class in the <xref:System.Xml?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a><span data-ttu-id="ea972-105">Čtení dokumentů XML pomocí XPathDocument třídy</span><span class="sxs-lookup"><span data-stu-id="ea972-105">Reading XML Documents using the XPathDocument Class</span></span>  
 <span data-ttu-id="ea972-106"><xref:System.Xml.XPath.XPathDocument> Třída poskytuje rychlé, jen pro čtení, v paměti reprezentace dokumentu XML pomocí modelu dat XPath.</span><span class="sxs-lookup"><span data-stu-id="ea972-106">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="ea972-107">Instance <xref:System.Xml.XPath.XPathDocument> třídy jsou vytvořeny pomocí jedné z jejích šesti konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="ea972-107">Instances of the <xref:System.Xml.XPath.XPathDocument> class are created using one of its six constructors.</span></span> <span data-ttu-id="ea972-108">Tyto konstruktory umožňují čtení dokumentu XML pomocí <xref:System.IO.Stream>, <xref:System.IO.TextReader>, nebo <xref:System.Xml.XmlReader> objektu, jakož i `string` cestu k souboru XML.</span><span class="sxs-lookup"><span data-stu-id="ea972-108">These constructors allow you to read an XML document using a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="ea972-109">Následující příklad ukazuje použití <xref:System.Xml.XPath.XPathDocument> třídy `string` konstruktor ke čtení dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ea972-109">The following example illustrates using the <xref:System.Xml.XPath.XPathDocument> class's `string` constructor to read an XML document.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a><span data-ttu-id="ea972-110">Čtení dokumentů XML pomocí třídy XmlDocument</span><span class="sxs-lookup"><span data-stu-id="ea972-110">Reading XML Documents using the XmlDocument Class</span></span>  
 <span data-ttu-id="ea972-111"><xref:System.Xml.XmlDocument> Třídy je upravitelné reprezentací implementace základní úrovně 1 W3C Document Object Model (DOM) a základní modelu DOM úrovně 2 dokumentu XML v paměti.</span><span class="sxs-lookup"><span data-stu-id="ea972-111">The <xref:System.Xml.XmlDocument> class is an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="ea972-112">Instance <xref:System.Xml.XmlDocument> třídy jsou vytvořeny pomocí jedné z jeho tři konstruktory.</span><span class="sxs-lookup"><span data-stu-id="ea972-112">Instances of the <xref:System.Xml.XmlDocument> class are created using one of its three constructors.</span></span> <span data-ttu-id="ea972-113">Můžete vytvořit nový, prázdný <xref:System.Xml.XmlDocument> objektu voláním <xref:System.Xml.XmlDocument> třída konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="ea972-113">You can create a new, empty <xref:System.Xml.XmlDocument> object by calling the <xref:System.Xml.XmlDocument> class constructor with no parameters.</span></span> <span data-ttu-id="ea972-114">Po volání konstruktoru, použijte <xref:System.Xml.XmlDocument.Load%2A> metodu pro načtení dat XML do nového <xref:System.Xml.XmlDocument> objektu z <xref:System.IO.Stream>, <xref:System.IO.TextReader>, nebo <xref:System.Xml.XmlReader> objektu, stejně jako `string` cestu k souboru XML.</span><span class="sxs-lookup"><span data-stu-id="ea972-114">After calling the constructor, use the <xref:System.Xml.XmlDocument.Load%2A> method to load XML data into the new <xref:System.Xml.XmlDocument> object from a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="ea972-115">Následující příklad ukazuje použití <xref:System.Xml.XmlDocument> třída konstruktor bez parametrů a <xref:System.Xml.XmlDocument.Load%2A> metodu za účelem čtení dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ea972-115">The following example illustrates using the <xref:System.Xml.XmlDocument> class constructor with no parameters and the <xref:System.Xml.XmlDocument.Load%2A> method to read an XML document.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a><span data-ttu-id="ea972-116">Určení kódování dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="ea972-116">Determining the Encoding of an XML Document</span></span>  
 <span data-ttu-id="ea972-117"><xref:System.Xml.XmlReader> Objekt lze použít ke čtení dokumentu XML a vytvořit <xref:System.Xml.XPath.XPathDocument> a <xref:System.Xml.XmlDocument> objektů, jak je znázorněno v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="ea972-117">An <xref:System.Xml.XmlReader> object can be used to read an XML document and to create <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> objects as shown in the previous sections.</span></span> <span data-ttu-id="ea972-118">Nicméně <xref:System.Xml.XmlReader> objekt může číst data, která není kódovaný a v důsledku neposkytuje žádné informace o kódování.</span><span class="sxs-lookup"><span data-stu-id="ea972-118">However, an <xref:System.Xml.XmlReader> object may read data that is not encoded and as a result does not provide any encoding information.</span></span>  
  
 <span data-ttu-id="ea972-119"><xref:System.Xml.XmlTextReader> Třída dědí z <xref:System.Xml.XmlReader> třídy, poskytuje kódování informací pomocí jeho <xref:System.Xml.XmlTextReader.Encoding%2A> vlastnost a můžete použít k vytvoření <xref:System.Xml.XPath.XPathDocument> objektu nebo <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="ea972-119">The <xref:System.Xml.XmlTextReader> class inherits from the <xref:System.Xml.XmlReader> class, provides encoding information using its <xref:System.Xml.XmlTextReader.Encoding%2A> property, and can be used to create an <xref:System.Xml.XPath.XPathDocument> object or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="ea972-120">Další informace o kódování na základě informací poskytnutých <xref:System.Xml.XmlTextReader> najdete v tématu <xref:System.Xml.XmlTextReader.Encoding%2A> vlastnost <xref:System.Xml.XmlTextReader> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="ea972-120">For more information about the encoding information provided by the <xref:System.Xml.XmlTextReader> class, see the <xref:System.Xml.XmlTextReader.Encoding%2A> property in the <xref:System.Xml.XmlTextReader> class reference documentation.</span></span>  
  
## <a name="creating-xpathnavigator-objects"></a><span data-ttu-id="ea972-121">Vytváření objektů s objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="ea972-121">Creating XPathNavigator Objects</span></span>  
 <span data-ttu-id="ea972-122">Po přečtení dokumentu XML do jedné <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu, můžete vytvořit <xref:System.Xml.XPath.XPathNavigator> objektu k výběru, vyhodnocení, přejděte a v některých případech může upravovat podkladová data XML.</span><span class="sxs-lookup"><span data-stu-id="ea972-122">After you have read an XML document into either an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, you can create an <xref:System.Xml.XPath.XPathNavigator> object to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="ea972-123">Jak <xref:System.Xml.XPath.XPathDocument> a <xref:System.Xml.XmlDocument> třídy, navíc k <xref:System.Xml.XmlNode> třídy, implementujte <xref:System.Xml.XPath.IXPathNavigable> rozhraní <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ea972-123">Both the <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> classes, in addition to the <xref:System.Xml.XmlNode> class, implement the <xref:System.Xml.XPath.IXPathNavigable> interface of the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ea972-124">V důsledku toho poskytují všechny třídy <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> metodu, která vrátí <xref:System.Xml.XPath.XPathNavigator> objektu.</span><span class="sxs-lookup"><span data-stu-id="ea972-124">As a result, all three classes provide a <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> method that returns an <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a><span data-ttu-id="ea972-125">Úpravy dokumentů XML pomocí XPathNavigator třídy</span><span class="sxs-lookup"><span data-stu-id="ea972-125">Editing XML Documents using the XPathNavigator Class</span></span>  
 <span data-ttu-id="ea972-126">Kromě výběr, vyhodnocení a navigace v datech XML <xref:System.Xml.XPath.XPathNavigator> třídy lze použít k úpravě dokumentu XML v některých případech založené na objektu, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="ea972-126">In addition to selecting, evaluating, and navigating XML data, the <xref:System.Xml.XPath.XPathNavigator> class can be used to edit an XML document in some cases, based on the object that created it.</span></span>  
  
 <span data-ttu-id="ea972-127"><xref:System.Xml.XPath.XPathDocument> Třídy je jen pro čtení při <xref:System.Xml.XmlDocument> třída je upravovat a v důsledku toho <xref:System.Xml.XPath.XPathNavigator> objekty vytvořené z <xref:System.Xml.XPath.XPathDocument> objektu nelze použít k úpravě dokumentu XML při vytvořených ze <xref:System.Xml.XmlDocument> objekt může.</span><span class="sxs-lookup"><span data-stu-id="ea972-127">The <xref:System.Xml.XPath.XPathDocument> class is read-only while the <xref:System.Xml.XmlDocument> class is editable and as a result, <xref:System.Xml.XPath.XPathNavigator> objects created from an <xref:System.Xml.XPath.XPathDocument> object cannot be used to edit an XML document while those created from an <xref:System.Xml.XmlDocument> object can.</span></span> <span data-ttu-id="ea972-128"><xref:System.Xml.XPath.XPathDocument> Třída by měla sloužit ke čtení dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ea972-128">The <xref:System.Xml.XPath.XPathDocument> class should be used to read an XML document only.</span></span> <span data-ttu-id="ea972-129">V případech, kdy potřebujete upravit dokument XML, nebo vyžadují přístup k další funkce poskytovaná modulem <xref:System.Xml.XmlDocument> třídy, jako je zpracování událostí <xref:System.Xml.XmlDocument> třída by měla být použita.</span><span class="sxs-lookup"><span data-stu-id="ea972-129">In cases where you need to edit an XML document, or require access to the additional functionality provided by the <xref:System.Xml.XmlDocument> class, like event handling, the <xref:System.Xml.XmlDocument> class should be used.</span></span>  
  
 <span data-ttu-id="ea972-130"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Vlastnost <xref:System.Xml.XPath.XPathNavigator> Určuje třídu, pokud <xref:System.Xml.XPath.XPathNavigator> objekt může upravovat XML data.</span><span class="sxs-lookup"><span data-stu-id="ea972-130">The <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class specifies if an <xref:System.Xml.XPath.XPathNavigator> object may edit XML data.</span></span>  
  
 <span data-ttu-id="ea972-131">Následující tabulka popisuje výhody <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> vlastností pro každou třídu.</span><span class="sxs-lookup"><span data-stu-id="ea972-131">The following table describes the value of the <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property for each class.</span></span>  
  
|<span data-ttu-id="ea972-132"><xref:System.Xml.XPath.IXPathNavigable> Implementace</span><span class="sxs-lookup"><span data-stu-id="ea972-132"><xref:System.Xml.XPath.IXPathNavigable> Implementation</span></span>|<span data-ttu-id="ea972-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Hodnota</span><span class="sxs-lookup"><span data-stu-id="ea972-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Value</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a><span data-ttu-id="ea972-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea972-134">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="ea972-135">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="ea972-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="ea972-136">Přístup k datům XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ea972-136">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="ea972-137">Úpravy dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ea972-137">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="ea972-138">Ověření schématu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ea972-138">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
