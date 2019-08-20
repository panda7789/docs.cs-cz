---
title: Přehled tříd LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 55be666fc0db0becb12ec8b525e7fc443536e1df
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591882"
---
# <a name="linq-to-xml-classes-overview-c"></a><span data-ttu-id="16a99-102">Přehled tříd LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="16a99-102">LINQ to XML Classes Overview (C#)</span></span>
<span data-ttu-id="16a99-103">Toto téma poskytuje seznam [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tříd <xref:System.Xml.Linq> v oboru názvů a stručný popis každého z nich.</span><span class="sxs-lookup"><span data-stu-id="16a99-103">This topic provides a list of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="16a99-104">Třídy LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="16a99-104">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="16a99-105">XAttribute – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-105">XAttribute Class</span></span>  
 <span data-ttu-id="16a99-106"><xref:System.Xml.Linq.XAttribute>představuje atribut XML.</span><span class="sxs-lookup"><span data-stu-id="16a99-106"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="16a99-107">Podrobné informace a příklady naleznete v tématu [XAttribute Class Overview (C#)](./xattribute-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16a99-107">For detailed information and examples, see [XAttribute Class Overview (C#)](./xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="16a99-108">XCData – Třída</span><span class="sxs-lookup"><span data-stu-id="16a99-108">XCData Class</span></span>  
 <span data-ttu-id="16a99-109"><xref:System.Xml.Linq.XCData>představuje textový uzel CDATA.</span><span class="sxs-lookup"><span data-stu-id="16a99-109"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="16a99-110">XComment – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-110">XComment Class</span></span>  
 <span data-ttu-id="16a99-111"><xref:System.Xml.Linq.XComment>představuje komentář XML.</span><span class="sxs-lookup"><span data-stu-id="16a99-111"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="16a99-112">XContainer – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-112">XContainer Class</span></span>  
 <span data-ttu-id="16a99-113"><xref:System.Xml.Linq.XContainer>je abstraktní základní třída pro všechny uzly, které mohou mít podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="16a99-113"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="16a99-114">Následující třídy jsou odvozeny z <xref:System.Xml.Linq.XContainer> třídy:</span><span class="sxs-lookup"><span data-stu-id="16a99-114">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="16a99-115">XDeclaration – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-115">XDeclaration Class</span></span>  
 <span data-ttu-id="16a99-116"><xref:System.Xml.Linq.XDeclaration>představuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="16a99-116"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="16a99-117">Deklarace XML se používá k deklaraci verze XML a kódování dokumentu.</span><span class="sxs-lookup"><span data-stu-id="16a99-117">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="16a99-118">Kromě toho deklarace XML určuje, zda je dokument XML samostatný.</span><span class="sxs-lookup"><span data-stu-id="16a99-118">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="16a99-119">Pokud je dokument samostatný, neexistují žádná deklarace externích značek, ani externí deklarace DTD, nebo externí parametr entity, na kterou se odkazuje z vnitřní podmnožiny.</span><span class="sxs-lookup"><span data-stu-id="16a99-119">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="16a99-120">XDocument – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-120">XDocument Class</span></span>  
 <span data-ttu-id="16a99-121"><xref:System.Xml.Linq.XDocument>představuje dokument XML.</span><span class="sxs-lookup"><span data-stu-id="16a99-121"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="16a99-122">Podrobné informace a příklady naleznete v tématu [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16a99-122">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="16a99-123">XDocumentType – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-123">XDocumentType Class</span></span>  
 <span data-ttu-id="16a99-124"><xref:System.Xml.Linq.XDocumentType>představuje definici typu dokumentu XML (DTD).</span><span class="sxs-lookup"><span data-stu-id="16a99-124"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="16a99-125">XElement – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-125">XElement Class</span></span>  
 <span data-ttu-id="16a99-126"><xref:System.Xml.Linq.XElement>představuje XML element.</span><span class="sxs-lookup"><span data-stu-id="16a99-126"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="16a99-127">Podrobné informace a příklady naleznete v tématu [XElement Class Overview (C#)](./xelement-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16a99-127">For detailed information and examples, see [XElement Class Overview (C#)](./xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="16a99-128">XName – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-128">XName Class</span></span>  
 <span data-ttu-id="16a99-129"><xref:System.Xml.Linq.XName>představuje názvy elementů (<xref:System.Xml.Linq.XElement>) a atributů (<xref:System.Xml.Linq.XAttribute>).</span><span class="sxs-lookup"><span data-stu-id="16a99-129"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="16a99-130">Podrobné informace a příklady naleznete v tématu [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16a99-130">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="16a99-131">je navržena tak, aby co nejjednodušší názvy XML.</span><span class="sxs-lookup"><span data-stu-id="16a99-131">is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="16a99-132">V důsledku jejich složitosti se názvy XML často považují za pokročilé téma v XML.</span><span class="sxs-lookup"><span data-stu-id="16a99-132">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="16a99-133">Pravděpodobně, Tato složitost nepochází z oborů názvů, které vývojáři pravidelně používají při programování, ale z prefixů oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="16a99-133">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="16a99-134">Předpony oboru názvů mohou být užitečné ke zmenšování klávesových úhozů vyžadovaných při zadávání XML nebo ke snazšímu čtení XML.</span><span class="sxs-lookup"><span data-stu-id="16a99-134">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="16a99-135">Předpony jsou však často pouze zástupci pro použití plného oboru názvů XML a ve většině případů nejsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="16a99-135">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="16a99-136">zjednodušuje názvy XML tím, že překládá všechny předpony na jejich odpovídající obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="16a99-136">simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="16a99-137">Předpony jsou k dispozici, pokud jsou požadovány, <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> prostřednictvím metody.</span><span class="sxs-lookup"><span data-stu-id="16a99-137">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="16a99-138">V případě potřeby je možné řídit předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="16a99-138">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="16a99-139">V některých případech, pokud pracujete s jinými systémy XML, jako jsou XSLT nebo XAML, je nutné řídit předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="16a99-139">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="16a99-140">Například pokud máte výraz XPath, který používá předpony oboru názvů a je vložen do šablony stylů XSLT, je nutné zajistit, aby byl dokument XML serializován s předponami oboru názvů, které odpovídají hodnotám používaným ve výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="16a99-140">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="16a99-141">XNamespace – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-141">XNamespace Class</span></span>  
 <span data-ttu-id="16a99-142"><xref:System.Xml.Linq.XNamespace>představuje obor názvů pro <xref:System.Xml.Linq.XElement> nebo. <xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="16a99-142"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="16a99-143">Obory názvů jsou součástí <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="16a99-143">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="16a99-144">XNode – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-144">XNode Class</span></span>  
 <span data-ttu-id="16a99-145"><xref:System.Xml.Linq.XNode>je abstraktní třída, která představuje uzly stromu XML.</span><span class="sxs-lookup"><span data-stu-id="16a99-145"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="16a99-146">Následující třídy jsou odvozeny z <xref:System.Xml.Linq.XNode> třídy:</span><span class="sxs-lookup"><span data-stu-id="16a99-146">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="16a99-147">XNodeDocumentOrderComparer – Třída</span><span class="sxs-lookup"><span data-stu-id="16a99-147">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="16a99-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer>poskytuje funkce pro porovnání uzlů pro jejich pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="16a99-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="16a99-149">XNodeEqualityComparer – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-149">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="16a99-150"><xref:System.Xml.Linq.XNodeEqualityComparer>poskytuje funkce pro porovnání uzlů pro rovnost hodnot.</span><span class="sxs-lookup"><span data-stu-id="16a99-150"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="16a99-151">XObject – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-151">XObject Class</span></span>  
 <span data-ttu-id="16a99-152"><xref:System.Xml.Linq.XObject>je abstraktní základní třída <xref:System.Xml.Linq.XNode> a. <xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="16a99-152"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="16a99-153">Poskytuje funkce pro anotace a události.</span><span class="sxs-lookup"><span data-stu-id="16a99-153">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="16a99-154">XObjectChange – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-154">XObjectChange Class</span></span>  
 <span data-ttu-id="16a99-155"><xref:System.Xml.Linq.XObjectChange>Určuje typ události při vyvolání události pro <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="16a99-155"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="16a99-156">XObjectChangeEventArgs – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-156">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="16a99-157"><xref:System.Xml.Linq.XObjectChangeEventArgs>poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> události a <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="16a99-157"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="16a99-158">XProcessingInstruction – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-158">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="16a99-159"><xref:System.Xml.Linq.XProcessingInstruction>představuje instrukci pro zpracování XML.</span><span class="sxs-lookup"><span data-stu-id="16a99-159"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="16a99-160">Instrukce pro zpracování sděluje informace aplikaci, která zpracovává XML.</span><span class="sxs-lookup"><span data-stu-id="16a99-160">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="16a99-161">XText – třída</span><span class="sxs-lookup"><span data-stu-id="16a99-161">XText Class</span></span>  
 <span data-ttu-id="16a99-162"><xref:System.Xml.Linq.XText>představuje textový uzel.</span><span class="sxs-lookup"><span data-stu-id="16a99-162"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="16a99-163">Ve většině případů tuto třídu nemusíte používat.</span><span class="sxs-lookup"><span data-stu-id="16a99-163">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="16a99-164">Tato třída se primárně používá pro smíšený obsah.</span><span class="sxs-lookup"><span data-stu-id="16a99-164">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16a99-165">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16a99-165">See also</span></span>

- [<span data-ttu-id="16a99-166">Přehled programování LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="16a99-166">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
