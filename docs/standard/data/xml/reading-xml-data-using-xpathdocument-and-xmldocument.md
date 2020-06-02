---
title: Načítání dat XML pomocí XPathDocument a XmlDocument
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
ms.openlocfilehash: da1cb81c819e55f572e9faaabef4dd49ee7397de
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288677"
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a><span data-ttu-id="29fb9-102">Načítání dat XML pomocí XPathDocument a XmlDocument</span><span class="sxs-lookup"><span data-stu-id="29fb9-102">Reading XML Data using XPathDocument and XmlDocument</span></span>
<span data-ttu-id="29fb9-103">Existují dva způsoby, jak číst dokument XML v <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="29fb9-103">There are two ways to read an XML document in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="29fb9-104">Jedním z nich je čtení dokumentu XML pomocí třídy jen pro čtení <xref:System.Xml.XPath.XPathDocument> a druhý je čtení dokumentu XML pomocí upravitelné <xref:System.Xml.XmlDocument> třídy v <xref:System.Xml?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="29fb9-104">One is to read an XML document using the read-only <xref:System.Xml.XPath.XPathDocument> class and the other is to read an XML document using the editable <xref:System.Xml.XmlDocument> class in the <xref:System.Xml?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a><span data-ttu-id="29fb9-105">Čtení dokumentů XML pomocí třídy XPathDocument</span><span class="sxs-lookup"><span data-stu-id="29fb9-105">Reading XML Documents using the XPathDocument Class</span></span>  
 <span data-ttu-id="29fb9-106"><xref:System.Xml.XPath.XPathDocument>Třída poskytuje rychlé znázornění dokumentu XML, který je jen pro čtení a který je v paměti, pomocí datového modelu XPath.</span><span class="sxs-lookup"><span data-stu-id="29fb9-106">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="29fb9-107">Instance <xref:System.Xml.XPath.XPathDocument> třídy jsou vytvořeny pomocí některého z šesti konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="29fb9-107">Instances of the <xref:System.Xml.XPath.XPathDocument> class are created using one of its six constructors.</span></span> <span data-ttu-id="29fb9-108">Tyto konstruktory umožňují číst dokument XML pomocí <xref:System.IO.Stream> <xref:System.IO.TextReader> objektu, nebo <xref:System.Xml.XmlReader> , a také `string` cestu k souboru XML.</span><span class="sxs-lookup"><span data-stu-id="29fb9-108">These constructors allow you to read an XML document using a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="29fb9-109">Následující příklad znázorňuje použití <xref:System.Xml.XPath.XPathDocument> `string` konstruktoru třídy pro čtení dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="29fb9-109">The following example illustrates using the <xref:System.Xml.XPath.XPathDocument> class's `string` constructor to read an XML document.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a><span data-ttu-id="29fb9-110">Čtení dokumentů XML pomocí třídy XmlDocument</span><span class="sxs-lookup"><span data-stu-id="29fb9-110">Reading XML Documents using the XmlDocument Class</span></span>  
 <span data-ttu-id="29fb9-111"><xref:System.Xml.XmlDocument>Třída je upravitelná reprezentace v paměti dokumentu XML implementující model DOM (Document Object Model) W3C (DOM) úrovně 1 Core a Core DOM úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="29fb9-111">The <xref:System.Xml.XmlDocument> class is an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="29fb9-112">Instance <xref:System.Xml.XmlDocument> třídy jsou vytvořeny pomocí jednoho ze tří konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="29fb9-112">Instances of the <xref:System.Xml.XmlDocument> class are created using one of its three constructors.</span></span> <span data-ttu-id="29fb9-113">Můžete vytvořit nový prázdný <xref:System.Xml.XmlDocument> objekt voláním <xref:System.Xml.XmlDocument> konstruktoru třídy bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="29fb9-113">You can create a new, empty <xref:System.Xml.XmlDocument> object by calling the <xref:System.Xml.XmlDocument> class constructor with no parameters.</span></span> <span data-ttu-id="29fb9-114">Po volání konstruktoru použijte <xref:System.Xml.XmlDocument.Load%2A> metodu pro načtení dat XML do nového <xref:System.Xml.XmlDocument> objektu z <xref:System.IO.Stream> <xref:System.IO.TextReader> objektu, nebo <xref:System.Xml.XmlReader> , a také `string` cestu k souboru XML.</span><span class="sxs-lookup"><span data-stu-id="29fb9-114">After calling the constructor, use the <xref:System.Xml.XmlDocument.Load%2A> method to load XML data into the new <xref:System.Xml.XmlDocument> object from a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="29fb9-115">Následující příklad znázorňuje použití <xref:System.Xml.XmlDocument> konstruktoru třídy bez parametrů a <xref:System.Xml.XmlDocument.Load%2A> metody pro čtení dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="29fb9-115">The following example illustrates using the <xref:System.Xml.XmlDocument> class constructor with no parameters and the <xref:System.Xml.XmlDocument.Load%2A> method to read an XML document.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a><span data-ttu-id="29fb9-116">Určení kódování dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="29fb9-116">Determining the Encoding of an XML Document</span></span>  
 <span data-ttu-id="29fb9-117"><xref:System.Xml.XmlReader>Objekt lze použít ke čtení dokumentu XML a k vytvoření <xref:System.Xml.XPath.XPathDocument> a vytváření objektů, <xref:System.Xml.XmlDocument> jak je znázorněno v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="29fb9-117">An <xref:System.Xml.XmlReader> object can be used to read an XML document and to create <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> objects as shown in the previous sections.</span></span> <span data-ttu-id="29fb9-118"><xref:System.Xml.XmlReader>Objekt však může číst data, která nejsou kódována a v důsledku toho neposkytuje žádné informace o kódování.</span><span class="sxs-lookup"><span data-stu-id="29fb9-118">However, an <xref:System.Xml.XmlReader> object may read data that is not encoded and as a result does not provide any encoding information.</span></span>  
  
 <span data-ttu-id="29fb9-119"><xref:System.Xml.XmlTextReader>Třída dědí z <xref:System.Xml.XmlReader> třídy, poskytuje informace o kódování pomocí své <xref:System.Xml.XmlTextReader.Encoding%2A> vlastnosti a lze ji použít k vytvoření <xref:System.Xml.XPath.XPathDocument> objektu nebo objektu <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="29fb9-119">The <xref:System.Xml.XmlTextReader> class inherits from the <xref:System.Xml.XmlReader> class, provides encoding information using its <xref:System.Xml.XmlTextReader.Encoding%2A> property, and can be used to create an <xref:System.Xml.XPath.XPathDocument> object or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="29fb9-120">Další informace o informacích o kódování, které poskytuje <xref:System.Xml.XmlTextReader> třída, naleznete v části <xref:System.Xml.XmlTextReader.Encoding%2A> vlastnost v <xref:System.Xml.XmlTextReader> dokumentaci třídy.</span><span class="sxs-lookup"><span data-stu-id="29fb9-120">For more information about the encoding information provided by the <xref:System.Xml.XmlTextReader> class, see the <xref:System.Xml.XmlTextReader.Encoding%2A> property in the <xref:System.Xml.XmlTextReader> class reference documentation.</span></span>  
  
## <a name="creating-xpathnavigator-objects"></a><span data-ttu-id="29fb9-121">Vytváření objektů XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="29fb9-121">Creating XPathNavigator Objects</span></span>  
 <span data-ttu-id="29fb9-122">Po přečtení dokumentu XML do <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo můžete vytvořit <xref:System.Xml.XPath.XPathNavigator> objekt pro výběr, vyhodnocení, procházení a v některých případech upravit podkladová data XML.</span><span class="sxs-lookup"><span data-stu-id="29fb9-122">After you have read an XML document into either an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, you can create an <xref:System.Xml.XPath.XPathNavigator> object to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="29fb9-123"><xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> Třídy i také <xref:System.Xml.XmlNode> implementují <xref:System.Xml.XPath.IXPathNavigable> rozhraní <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="29fb9-123">Both the <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> classes, in addition to the <xref:System.Xml.XmlNode> class, implement the <xref:System.Xml.XPath.IXPathNavigable> interface of the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="29fb9-124">V důsledku toho všechny tři třídy poskytují <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> metodu, která vrací <xref:System.Xml.XPath.XPathNavigator> objekt.</span><span class="sxs-lookup"><span data-stu-id="29fb9-124">As a result, all three classes provide a <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> method that returns an <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a><span data-ttu-id="29fb9-125">Úpravy dokumentů XML pomocí třídy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="29fb9-125">Editing XML Documents using the XPathNavigator Class</span></span>  
 <span data-ttu-id="29fb9-126">Kromě výběru, vyhodnocení a navigace v datech XML <xref:System.Xml.XPath.XPathNavigator> lze třídu použít k úpravě dokumentu XML v některých případech, a to na základě objektu, který jej vytvořil.</span><span class="sxs-lookup"><span data-stu-id="29fb9-126">In addition to selecting, evaluating, and navigating XML data, the <xref:System.Xml.XPath.XPathNavigator> class can be used to edit an XML document in some cases, based on the object that created it.</span></span>  
  
 <span data-ttu-id="29fb9-127"><xref:System.Xml.XPath.XPathDocument>Třída je jen pro čtení, je-li <xref:System.Xml.XmlDocument> Třída upravitelná a v důsledku toho <xref:System.Xml.XPath.XPathNavigator> objekty vytvořené z <xref:System.Xml.XPath.XPathDocument> objektu nelze použít k úpravě dokumentu XML, zatímco jsou vytvořeny z <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="29fb9-127">The <xref:System.Xml.XPath.XPathDocument> class is read-only while the <xref:System.Xml.XmlDocument> class is editable and as a result, <xref:System.Xml.XPath.XPathNavigator> objects created from an <xref:System.Xml.XPath.XPathDocument> object cannot be used to edit an XML document while those created from an <xref:System.Xml.XmlDocument> object can.</span></span> <span data-ttu-id="29fb9-128"><xref:System.Xml.XPath.XPathDocument>Třída by měla být použita pouze pro čtení dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="29fb9-128">The <xref:System.Xml.XPath.XPathDocument> class should be used to read an XML document only.</span></span> <span data-ttu-id="29fb9-129">V případech, kdy potřebujete upravit dokument XML nebo vyžadovat přístup k dalším funkcím poskytovaným <xref:System.Xml.XmlDocument> třídou, jako je zpracování událostí, je <xref:System.Xml.XmlDocument> třeba použít třídu.</span><span class="sxs-lookup"><span data-stu-id="29fb9-129">In cases where you need to edit an XML document, or require access to the additional functionality provided by the <xref:System.Xml.XmlDocument> class, like event handling, the <xref:System.Xml.XmlDocument> class should be used.</span></span>  
  
 <span data-ttu-id="29fb9-130"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A>Vlastnost <xref:System.Xml.XPath.XPathNavigator> třídy určuje <xref:System.Xml.XPath.XPathNavigator> , zda objekt může upravovat data XML.</span><span class="sxs-lookup"><span data-stu-id="29fb9-130">The <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class specifies if an <xref:System.Xml.XPath.XPathNavigator> object may edit XML data.</span></span>  
  
 <span data-ttu-id="29fb9-131">Následující tabulka popisuje hodnotu <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> vlastnosti pro každou třídu.</span><span class="sxs-lookup"><span data-stu-id="29fb9-131">The following table describes the value of the <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property for each class.</span></span>  
  
|<span data-ttu-id="29fb9-132"><xref:System.Xml.XPath.IXPathNavigable>Provádění</span><span class="sxs-lookup"><span data-stu-id="29fb9-132"><xref:System.Xml.XPath.IXPathNavigable> Implementation</span></span>|<span data-ttu-id="29fb9-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A>Osa</span><span class="sxs-lookup"><span data-stu-id="29fb9-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Value</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a><span data-ttu-id="29fb9-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="29fb9-134">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="29fb9-135">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="29fb9-135">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="29fb9-136">Přístup k datům XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="29fb9-136">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="29fb9-137">Úpravy dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="29fb9-137">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="29fb9-138">Ověření schématu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="29fb9-138">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)
