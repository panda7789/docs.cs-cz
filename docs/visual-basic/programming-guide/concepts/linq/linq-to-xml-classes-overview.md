---
title: "Technologie LINQ to XML přehled třídy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f22f1b7e4f94acda3a9279baf92fbce0840e55ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-classes-overview-visual-basic"></a><span data-ttu-id="63251-102">Technologie LINQ to XML přehled třídy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63251-102">LINQ to XML Classes Overview (Visual Basic)</span></span>
<span data-ttu-id="63251-103">Toto téma obsahuje seznam [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] třídy v <xref:System.Xml.Linq> obor názvů a krátký popis každého.</span><span class="sxs-lookup"><span data-stu-id="63251-103">This topic provides a list of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="63251-104">Technologie LINQ to XML třídy</span><span class="sxs-lookup"><span data-stu-id="63251-104">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="63251-105">XAttribute – třída</span><span class="sxs-lookup"><span data-stu-id="63251-105">XAttribute Class</span></span>  
 <span data-ttu-id="63251-106"><xref:System.Xml.Linq.XAttribute>představuje atribut XML.</span><span class="sxs-lookup"><span data-stu-id="63251-106"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="63251-107">Podrobné informace a příklady naleznete v tématu [XAttribute přehledu třídy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="63251-107">For detailed information and examples, see [XAttribute Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="63251-108">XCData – třída</span><span class="sxs-lookup"><span data-stu-id="63251-108">XCData Class</span></span>  
 <span data-ttu-id="63251-109"><xref:System.Xml.Linq.XCData>představuje uzel text CDATA.</span><span class="sxs-lookup"><span data-stu-id="63251-109"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="63251-110">XComment – třída</span><span class="sxs-lookup"><span data-stu-id="63251-110">XComment Class</span></span>  
 <span data-ttu-id="63251-111"><xref:System.Xml.Linq.XComment>představuje komentáře jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="63251-111"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="63251-112">XContainer – třída</span><span class="sxs-lookup"><span data-stu-id="63251-112">XContainer Class</span></span>  
 <span data-ttu-id="63251-113"><xref:System.Xml.Linq.XContainer>je abstraktní základní třída pro všechny uzly, které může mít podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="63251-113"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="63251-114">Následující třídy odvozovat <xref:System.Xml.Linq.XContainer> třídy:</span><span class="sxs-lookup"><span data-stu-id="63251-114">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="63251-115">XDeclaration – třída</span><span class="sxs-lookup"><span data-stu-id="63251-115">XDeclaration Class</span></span>  
 <span data-ttu-id="63251-116"><xref:System.Xml.Linq.XDeclaration>představuje deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="63251-116"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="63251-117">Deklarace XML se používá k deklaraci XML verze a kódování dokumentu.</span><span class="sxs-lookup"><span data-stu-id="63251-117">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="63251-118">Kromě toho deklarace XML určuje, zda je v dokumentu XML samostatné.</span><span class="sxs-lookup"><span data-stu-id="63251-118">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="63251-119">Pokud dokument je samostatná, neexistují žádné externí značek deklarace v externí DTD nebo v entitu externí parametr na něj odkazovat z vnitřní podmnožiny.</span><span class="sxs-lookup"><span data-stu-id="63251-119">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="63251-120">XDocument – třída</span><span class="sxs-lookup"><span data-stu-id="63251-120">XDocument Class</span></span>  
 <span data-ttu-id="63251-121"><xref:System.Xml.Linq.XDocument>představuje dokument XML.</span><span class="sxs-lookup"><span data-stu-id="63251-121"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="63251-122">Podrobné informace a příklady naleznete v tématu [XDocument přehledu třídy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="63251-122">For detailed information and examples, see [XDocument Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="63251-123">XDocumentType – třída</span><span class="sxs-lookup"><span data-stu-id="63251-123">XDocumentType Class</span></span>  
 <span data-ttu-id="63251-124"><xref:System.Xml.Linq.XDocumentType>představuje definice pro typ dokumentu XML (DTD).</span><span class="sxs-lookup"><span data-stu-id="63251-124"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="63251-125">XElement – třída</span><span class="sxs-lookup"><span data-stu-id="63251-125">XElement Class</span></span>  
 <span data-ttu-id="63251-126"><xref:System.Xml.Linq.XElement>reprezentuje element, XML.</span><span class="sxs-lookup"><span data-stu-id="63251-126"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="63251-127">Podrobné informace a příklady naleznete v tématu [XElement přehledu třídy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="63251-127">For detailed information and examples, see [XElement Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="63251-128">XName – třída</span><span class="sxs-lookup"><span data-stu-id="63251-128">XName Class</span></span>  
 <span data-ttu-id="63251-129"><xref:System.Xml.Linq.XName>představuje názvy elementů (<xref:System.Xml.Linq.XElement>) a atributy (<xref:System.Xml.Linq.XAttribute>).</span><span class="sxs-lookup"><span data-stu-id="63251-129"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="63251-130">Podrobné informace a příklady naleznete v tématu [XDocument přehledu třídy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="63251-130">For detailed information and examples, see [XDocument Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="63251-131">zajišťují, aby názvy XML maximálně jednoduché.</span><span class="sxs-lookup"><span data-stu-id="63251-131"> is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="63251-132">Z důvodu jejich složitost XML názvy jsou často považuje za rozšířená v kódu XML.</span><span class="sxs-lookup"><span data-stu-id="63251-132">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="63251-133">Tato složitost dodává pravděpodobně, nikoli z oborů názvů, které vývojáři použít pravidelně při programování, ale z předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="63251-133">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="63251-134">Namespace předpony může být užitečná ke snížení stisknutí kláves potřebné při zadávání XML, nebo k usnadnění XML.</span><span class="sxs-lookup"><span data-stu-id="63251-134">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="63251-135">Ale předpony jsou často zástupce pro používání úplné obor názvů XML a není nutné ve většině případů.</span><span class="sxs-lookup"><span data-stu-id="63251-135">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="63251-136">Vyřešte všechny předpony na jejich odpovídající obor názvů XML zjednodušuje názvů XML.</span><span class="sxs-lookup"><span data-stu-id="63251-136"> simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="63251-137">Jsou k dispozici, pokud jsou požadována prostřednictvím předpony <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="63251-137">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="63251-138">Je možné, pokud je to nezbytné, aby se předpony oboru názvů řízení.</span><span class="sxs-lookup"><span data-stu-id="63251-138">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="63251-139">V některých případech Pokud pracujete s jinými systémy XML, jako je například XSLT nebo XAML, je nutné určit předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="63251-139">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="63251-140">Například pokud máte výraz XPath, který používá předpony oboru názvů a vložené do šablonu stylů XSLT, je musí ověřit, že je váš dokument XML serializovat s příznakem předpony oboru názvů, které se shodují s těmi, použít ve výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="63251-140">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="63251-141">XNamespace – třída</span><span class="sxs-lookup"><span data-stu-id="63251-141">XNamespace Class</span></span>  
 <span data-ttu-id="63251-142"><xref:System.Xml.Linq.XNamespace>představuje obor názvů pro <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="63251-142"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="63251-143">Obory názvů jsou součástí <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="63251-143">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="63251-144">XNode – třída</span><span class="sxs-lookup"><span data-stu-id="63251-144">XNode Class</span></span>  
 <span data-ttu-id="63251-145"><xref:System.Xml.Linq.XNode>je abstraktní třída, která představuje uzlů stromu XML.</span><span class="sxs-lookup"><span data-stu-id="63251-145"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="63251-146">Následující třídy odvozovat <xref:System.Xml.Linq.XNode> třídy:</span><span class="sxs-lookup"><span data-stu-id="63251-146">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
-   <xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="63251-147">XNodeDocumentOrderComparer – třída</span><span class="sxs-lookup"><span data-stu-id="63251-147">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="63251-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer>poskytuje funkce pro porovnání uzlů pro jejich dokument pořadí.</span><span class="sxs-lookup"><span data-stu-id="63251-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="63251-149">XNodeEqualityComparer – třída</span><span class="sxs-lookup"><span data-stu-id="63251-149">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="63251-150"><xref:System.Xml.Linq.XNodeEqualityComparer>poskytuje funkce pro porovnání uzlů pro rovnosti hodnoty.</span><span class="sxs-lookup"><span data-stu-id="63251-150"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="63251-151">XObjektu – třída</span><span class="sxs-lookup"><span data-stu-id="63251-151">XObject Class</span></span>  
 <span data-ttu-id="63251-152"><xref:System.Xml.Linq.XObject>je abstraktní základní třída z <xref:System.Xml.Linq.XNode> a <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="63251-152"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="63251-153">Nabízí funkce, poznámky a události.</span><span class="sxs-lookup"><span data-stu-id="63251-153">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="63251-154">XObjectChange – třída</span><span class="sxs-lookup"><span data-stu-id="63251-154">XObjectChange Class</span></span>  
 <span data-ttu-id="63251-155"><xref:System.Xml.Linq.XObjectChange>Určuje typ události, když událost se vyvolá pro <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="63251-155"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="63251-156">XObjectChangeEventArgs – třída</span><span class="sxs-lookup"><span data-stu-id="63251-156">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="63251-157"><xref:System.Xml.Linq.XObjectChangeEventArgs>poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed> události.</span><span class="sxs-lookup"><span data-stu-id="63251-157"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="63251-158">XProcessingInstruction – třída</span><span class="sxs-lookup"><span data-stu-id="63251-158">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="63251-159"><xref:System.Xml.Linq.XProcessingInstruction>představuje instrukcí pro zpracování XML.</span><span class="sxs-lookup"><span data-stu-id="63251-159"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="63251-160">Zpracování instrukcí komunikuje informace, které aplikace, která zpracovává soubor XML.</span><span class="sxs-lookup"><span data-stu-id="63251-160">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="63251-161">XText – třída</span><span class="sxs-lookup"><span data-stu-id="63251-161">XText Class</span></span>  
 <span data-ttu-id="63251-162"><xref:System.Xml.Linq.XText>představuje uzel text.</span><span class="sxs-lookup"><span data-stu-id="63251-162"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="63251-163">Ve většině případů není nutné k použití této třídy.</span><span class="sxs-lookup"><span data-stu-id="63251-163">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="63251-164">Tato třída se používá hlavně pro smíšený obsah.</span><span class="sxs-lookup"><span data-stu-id="63251-164">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63251-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="63251-165">See Also</span></span>  
 [<span data-ttu-id="63251-166">Technologie LINQ to přehled programování v XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63251-166">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
