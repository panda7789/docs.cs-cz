---
title: Přehled třídy XDocument
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: cbc1ccca53978da07f31c0ba7e54eca9f06b0e72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349294"
---
# <a name="xdocument-class-overview-visual-basic"></a><span data-ttu-id="bde7f-102">XDocument Class Overview (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bde7f-102">XDocument Class Overview (Visual Basic)</span></span>
<span data-ttu-id="bde7f-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span><span class="sxs-lookup"><span data-stu-id="bde7f-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="bde7f-104">Overview of the XDocument class</span><span class="sxs-lookup"><span data-stu-id="bde7f-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="bde7f-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span><span class="sxs-lookup"><span data-stu-id="bde7f-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="bde7f-106">This includes an XML declaration, processing instructions, and comments.</span><span class="sxs-lookup"><span data-stu-id="bde7f-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="bde7f-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span><span class="sxs-lookup"><span data-stu-id="bde7f-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="bde7f-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="bde7f-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="bde7f-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span><span class="sxs-lookup"><span data-stu-id="bde7f-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="bde7f-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="bde7f-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="bde7f-111">Therefore, it can contain child nodes.</span><span class="sxs-lookup"><span data-stu-id="bde7f-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="bde7f-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span><span class="sxs-lookup"><span data-stu-id="bde7f-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="bde7f-113">This reflects the XML standard that there can be only one root element in an XML document.</span><span class="sxs-lookup"><span data-stu-id="bde7f-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="bde7f-114">Components of XDocument</span><span class="sxs-lookup"><span data-stu-id="bde7f-114">Components of XDocument</span></span>  
 <span data-ttu-id="bde7f-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span><span class="sxs-lookup"><span data-stu-id="bde7f-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="bde7f-116">One <xref:System.Xml.Linq.XDeclaration> object.</span><span class="sxs-lookup"><span data-stu-id="bde7f-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="bde7f-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span><span class="sxs-lookup"><span data-stu-id="bde7f-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="bde7f-118">One <xref:System.Xml.Linq.XElement> object.</span><span class="sxs-lookup"><span data-stu-id="bde7f-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="bde7f-119">This is the root node of the XML document.</span><span class="sxs-lookup"><span data-stu-id="bde7f-119">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="bde7f-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span><span class="sxs-lookup"><span data-stu-id="bde7f-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="bde7f-121">A processing instruction communicates information to an application that processes the XML.</span><span class="sxs-lookup"><span data-stu-id="bde7f-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="bde7f-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span><span class="sxs-lookup"><span data-stu-id="bde7f-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="bde7f-123">The comments will be siblings to the root element.</span><span class="sxs-lookup"><span data-stu-id="bde7f-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="bde7f-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span><span class="sxs-lookup"><span data-stu-id="bde7f-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="bde7f-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span><span class="sxs-lookup"><span data-stu-id="bde7f-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="bde7f-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span><span class="sxs-lookup"><span data-stu-id="bde7f-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="bde7f-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span><span class="sxs-lookup"><span data-stu-id="bde7f-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="bde7f-128">Using XElement without XDocument</span><span class="sxs-lookup"><span data-stu-id="bde7f-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="bde7f-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span><span class="sxs-lookup"><span data-stu-id="bde7f-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="bde7f-130">In many cases, your application will not require that you create a document.</span><span class="sxs-lookup"><span data-stu-id="bde7f-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="bde7f-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span><span class="sxs-lookup"><span data-stu-id="bde7f-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="bde7f-132">Using XDocument</span><span class="sxs-lookup"><span data-stu-id="bde7f-132">Using XDocument</span></span>  
 <span data-ttu-id="bde7f-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="bde7f-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="bde7f-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span><span class="sxs-lookup"><span data-stu-id="bde7f-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
                       <!--This is a comment.-->  
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
                       <Pubs>  
                           <Book>  
                               <Title>Artifacts of Roman Civilization</Title>  
                               <Author>Moreno, Jordao</Author>  
                           </Book>  
                           <Book>  
                               <Title>Midieval Tools and Implements</Title>  
                               <Author>Gazit, Inbar</Author>  
                           </Book>  
                       </Pubs>  
                       <!--This is another comment.-->  
doc.Save("test.xml")  
```  
  
 <span data-ttu-id="bde7f-135">When you examine the file test.xml, you get the following output:</span><span class="sxs-lookup"><span data-stu-id="bde7f-135">When you examine the file test.xml, you get the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a><span data-ttu-id="bde7f-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bde7f-136">See also</span></span>

- [<span data-ttu-id="bde7f-137">LINQ to XML Programming Overview (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bde7f-137">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
