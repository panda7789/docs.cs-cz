---
title: Přehled tříd LINQ to XML (C#)
description: Tento článek shrnuje LINQ to XML třídy v jazyce C# v System.Xml. Obor názvů LINQ s krátkým popisem každého.
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 34508f86792cdc7589569b8f12584ffc4379a5fb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165435"
---
# <a name="linq-to-xml-classes-overview-c"></a><span data-ttu-id="2fd08-103">Přehled tříd LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2fd08-103">LINQ to XML Classes Overview (C#)</span></span>
<span data-ttu-id="2fd08-104">Toto téma poskytuje seznam [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tříd v <xref:System.Xml.Linq> oboru názvů a stručný popis každého z nich.</span><span class="sxs-lookup"><span data-stu-id="2fd08-104">This topic provides a list of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="2fd08-105">Třídy LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="2fd08-105">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="2fd08-106">XAttribute – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-106">XAttribute Class</span></span>  
 <span data-ttu-id="2fd08-107"><xref:System.Xml.Linq.XAttribute>představuje atribut XML.</span><span class="sxs-lookup"><span data-stu-id="2fd08-107"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="2fd08-108">Podrobné informace a příklady naleznete v tématu [XAttribute Class Overview (C#)](./xattribute-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2fd08-108">For detailed information and examples, see [XAttribute Class Overview (C#)](./xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="2fd08-109">XCData – Třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-109">XCData Class</span></span>  
 <span data-ttu-id="2fd08-110"><xref:System.Xml.Linq.XCData>představuje textový uzel CDATA.</span><span class="sxs-lookup"><span data-stu-id="2fd08-110"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="2fd08-111">XComment – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-111">XComment Class</span></span>  
 <span data-ttu-id="2fd08-112"><xref:System.Xml.Linq.XComment>představuje komentář XML.</span><span class="sxs-lookup"><span data-stu-id="2fd08-112"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="2fd08-113">XContainer – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-113">XContainer Class</span></span>  
 <span data-ttu-id="2fd08-114"><xref:System.Xml.Linq.XContainer>je abstraktní základní třída pro všechny uzly, které mohou mít podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="2fd08-114"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="2fd08-115">Následující třídy jsou odvozeny z <xref:System.Xml.Linq.XContainer> třídy:</span><span class="sxs-lookup"><span data-stu-id="2fd08-115">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="2fd08-116">XDeclaration – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-116">XDeclaration Class</span></span>  
 <span data-ttu-id="2fd08-117"><xref:System.Xml.Linq.XDeclaration>představuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="2fd08-117"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="2fd08-118">Deklarace XML se používá k deklaraci verze XML a kódování dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2fd08-118">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="2fd08-119">Kromě toho deklarace XML určuje, zda je dokument XML samostatný.</span><span class="sxs-lookup"><span data-stu-id="2fd08-119">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="2fd08-120">Pokud je dokument samostatný, neexistují žádná deklarace externích značek, ani externí deklarace DTD, nebo externí parametr entity, na kterou se odkazuje z vnitřní podmnožiny.</span><span class="sxs-lookup"><span data-stu-id="2fd08-120">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="2fd08-121">XDocument – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-121">XDocument Class</span></span>  
 <span data-ttu-id="2fd08-122"><xref:System.Xml.Linq.XDocument>představuje dokument XML.</span><span class="sxs-lookup"><span data-stu-id="2fd08-122"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="2fd08-123">Podrobné informace a příklady naleznete v tématu [Přehled třídy XDocument (C#)](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2fd08-123">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="2fd08-124">XDocumentType – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-124">XDocumentType Class</span></span>  
 <span data-ttu-id="2fd08-125"><xref:System.Xml.Linq.XDocumentType>představuje definici typu dokumentu XML (DTD).</span><span class="sxs-lookup"><span data-stu-id="2fd08-125"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="2fd08-126">XElement – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-126">XElement Class</span></span>  
 <span data-ttu-id="2fd08-127"><xref:System.Xml.Linq.XElement>představuje XML element.</span><span class="sxs-lookup"><span data-stu-id="2fd08-127"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="2fd08-128">Podrobné informace a příklady naleznete v tématu [XElement Class Overview (C#)](./xelement-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2fd08-128">For detailed information and examples, see [XElement Class Overview (C#)](./xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="2fd08-129">XName – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-129">XName Class</span></span>  
 <span data-ttu-id="2fd08-130"><xref:System.Xml.Linq.XName>představuje názvy elementů ( <xref:System.Xml.Linq.XElement> ) a atributů ( <xref:System.Xml.Linq.XAttribute> ).</span><span class="sxs-lookup"><span data-stu-id="2fd08-130"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="2fd08-131">Podrobné informace a příklady naleznete v tématu [Přehled třídy XDocument (C#)](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2fd08-131">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2fd08-132">je navržena tak, aby co nejjednodušší názvy XML.</span><span class="sxs-lookup"><span data-stu-id="2fd08-132">is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="2fd08-133">V důsledku jejich složitosti se názvy XML často považují za pokročilé téma v XML.</span><span class="sxs-lookup"><span data-stu-id="2fd08-133">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="2fd08-134">Pravděpodobně, Tato složitost nepochází z oborů názvů, které vývojáři pravidelně používají při programování, ale z prefixů oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2fd08-134">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="2fd08-135">Předpony oboru názvů mohou být užitečné ke zmenšování klávesových úhozů vyžadovaných při zadávání XML nebo ke snazšímu čtení XML.</span><span class="sxs-lookup"><span data-stu-id="2fd08-135">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="2fd08-136">Předpony jsou však často pouze zástupci pro použití plného oboru názvů XML a ve většině případů nejsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="2fd08-136">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2fd08-137">zjednodušuje názvy XML tím, že překládá všechny předpony na jejich odpovídající obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="2fd08-137">simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="2fd08-138">Předpony jsou k dispozici, pokud jsou požadovány, prostřednictvím <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2fd08-138">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="2fd08-139">V případě potřeby je možné řídit předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2fd08-139">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="2fd08-140">V některých případech, pokud pracujete s jinými systémy XML, jako jsou XSLT nebo XAML, je nutné řídit předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2fd08-140">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="2fd08-141">Například pokud máte výraz XPath, který používá předpony oboru názvů a je vložen do šablony stylů XSLT, je nutné zajistit, aby byl dokument XML serializován s předponami oboru názvů, které odpovídají hodnotám používaným ve výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="2fd08-141">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="2fd08-142">XNamespace – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-142">XNamespace Class</span></span>  
 <span data-ttu-id="2fd08-143"><xref:System.Xml.Linq.XNamespace>představuje obor názvů pro <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="2fd08-143"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="2fd08-144">Obory názvů jsou součástí <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="2fd08-144">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="2fd08-145">XNode – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-145">XNode Class</span></span>  
 <span data-ttu-id="2fd08-146"><xref:System.Xml.Linq.XNode>je abstraktní třída, která představuje uzly stromu XML.</span><span class="sxs-lookup"><span data-stu-id="2fd08-146"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="2fd08-147">Následující třídy jsou odvozeny z <xref:System.Xml.Linq.XNode> třídy:</span><span class="sxs-lookup"><span data-stu-id="2fd08-147">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="2fd08-148">XNodeDocumentOrderComparer – Třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-148">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="2fd08-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer>poskytuje funkce pro porovnání uzlů pro jejich pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="2fd08-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="2fd08-150">XNodeEqualityComparer – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-150">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="2fd08-151"><xref:System.Xml.Linq.XNodeEqualityComparer>poskytuje funkce pro porovnání uzlů pro rovnost hodnot.</span><span class="sxs-lookup"><span data-stu-id="2fd08-151"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="2fd08-152">XObject – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-152">XObject Class</span></span>  
 <span data-ttu-id="2fd08-153"><xref:System.Xml.Linq.XObject>je abstraktní základní třída <xref:System.Xml.Linq.XNode> a <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="2fd08-153"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="2fd08-154">Poskytuje funkce pro anotace a události.</span><span class="sxs-lookup"><span data-stu-id="2fd08-154">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="2fd08-155">XObjectChange – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-155">XObjectChange Class</span></span>  
 <span data-ttu-id="2fd08-156"><xref:System.Xml.Linq.XObjectChange>Určuje typ události při vyvolání události pro <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="2fd08-156"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="2fd08-157">XObjectChangeEventArgs – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-157">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="2fd08-158"><xref:System.Xml.Linq.XObjectChangeEventArgs>poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> události a <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="2fd08-158"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="2fd08-159">XProcessingInstruction – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-159">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="2fd08-160"><xref:System.Xml.Linq.XProcessingInstruction>představuje instrukci pro zpracování XML.</span><span class="sxs-lookup"><span data-stu-id="2fd08-160"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="2fd08-161">Instrukce pro zpracování sděluje informace aplikaci, která zpracovává XML.</span><span class="sxs-lookup"><span data-stu-id="2fd08-161">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="2fd08-162">XText – třída</span><span class="sxs-lookup"><span data-stu-id="2fd08-162">XText Class</span></span>  
 <span data-ttu-id="2fd08-163"><xref:System.Xml.Linq.XText>představuje textový uzel.</span><span class="sxs-lookup"><span data-stu-id="2fd08-163"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="2fd08-164">Ve většině případů tuto třídu nemusíte používat.</span><span class="sxs-lookup"><span data-stu-id="2fd08-164">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="2fd08-165">Tato třída se primárně používá pro smíšený obsah.</span><span class="sxs-lookup"><span data-stu-id="2fd08-165">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fd08-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="2fd08-166">See also</span></span>

- [<span data-ttu-id="2fd08-167">Přehled programování LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2fd08-167">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
