---
title: LinQ na XML třídy Přehled (C#)
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 55be666fc0db0becb12ec8b525e7fc443536e1df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591882"
---
# <a name="linq-to-xml-classes-overview-c"></a><span data-ttu-id="1e5d5-102">LinQ na XML třídy Přehled (C#)</span><span class="sxs-lookup"><span data-stu-id="1e5d5-102">LINQ to XML Classes Overview (C#)</span></span>
<span data-ttu-id="1e5d5-103">Toto téma obsahuje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] seznam tříd <xref:System.Xml.Linq> v oboru názvů a krátký popis každého z nich.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-103">This topic provides a list of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="1e5d5-104">Linq na xml třídy</span><span class="sxs-lookup"><span data-stu-id="1e5d5-104">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="1e5d5-105">Třída XAttribute</span><span class="sxs-lookup"><span data-stu-id="1e5d5-105">XAttribute Class</span></span>  
 <span data-ttu-id="1e5d5-106"><xref:System.Xml.Linq.XAttribute>představuje atribut XML.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-106"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="1e5d5-107">Podrobné informace a příklady naleznete v [tématu Přehled třídy XAttribute (C#)](./xattribute-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1e5d5-107">For detailed information and examples, see [XAttribute Class Overview (C#)](./xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="1e5d5-108">Třída XCData</span><span class="sxs-lookup"><span data-stu-id="1e5d5-108">XCData Class</span></span>  
 <span data-ttu-id="1e5d5-109"><xref:System.Xml.Linq.XCData>představuje textový uzel CDATA.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-109"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="1e5d5-110">Třída XComment</span><span class="sxs-lookup"><span data-stu-id="1e5d5-110">XComment Class</span></span>  
 <span data-ttu-id="1e5d5-111"><xref:System.Xml.Linq.XComment>představuje komentář XML.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-111"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="1e5d5-112">Třída XContainer</span><span class="sxs-lookup"><span data-stu-id="1e5d5-112">XContainer Class</span></span>  
 <span data-ttu-id="1e5d5-113"><xref:System.Xml.Linq.XContainer>je abstraktní základní třída pro všechny uzly, které mohou mít podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-113"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="1e5d5-114">Následující třídy jsou <xref:System.Xml.Linq.XContainer> odvozeny z třídy:</span><span class="sxs-lookup"><span data-stu-id="1e5d5-114">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="1e5d5-115">Třída XDeclaration</span><span class="sxs-lookup"><span data-stu-id="1e5d5-115">XDeclaration Class</span></span>  
 <span data-ttu-id="1e5d5-116"><xref:System.Xml.Linq.XDeclaration>představuje deklaraci XML.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-116"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="1e5d5-117">Deklarace XML se používá k deklarování verze XML a kódování dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-117">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="1e5d5-118">Deklarace XML navíc určuje, zda je dokument XML samostatný.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-118">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="1e5d5-119">Pokud je dokument samostatný, neexistují žádné externí deklarace značek, a to buď v externím DTD, nebo v entitě externího parametru, na kterou odkazuje z vnitřní podmnožiny.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-119">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="1e5d5-120">Třída XDocument</span><span class="sxs-lookup"><span data-stu-id="1e5d5-120">XDocument Class</span></span>  
 <span data-ttu-id="1e5d5-121"><xref:System.Xml.Linq.XDocument>představuje dokument XML.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-121"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="1e5d5-122">Podrobné informace a příklady naleznete v [tématu Přehled třídxdocument (C#)](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1e5d5-122">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="1e5d5-123">Třída XDocumentType</span><span class="sxs-lookup"><span data-stu-id="1e5d5-123">XDocumentType Class</span></span>  
 <span data-ttu-id="1e5d5-124"><xref:System.Xml.Linq.XDocumentType>představuje definici typu dokumentu XML (DTD).</span><span class="sxs-lookup"><span data-stu-id="1e5d5-124"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="1e5d5-125">Třída XElement</span><span class="sxs-lookup"><span data-stu-id="1e5d5-125">XElement Class</span></span>  
 <span data-ttu-id="1e5d5-126"><xref:System.Xml.Linq.XElement>představuje element XML.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-126"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="1e5d5-127">Podrobné informace a příklady naleznete v [tématu Přehled třídy XElement (C#)](./xelement-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1e5d5-127">For detailed information and examples, see [XElement Class Overview (C#)](./xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="1e5d5-128">Třída XName</span><span class="sxs-lookup"><span data-stu-id="1e5d5-128">XName Class</span></span>  
 <span data-ttu-id="1e5d5-129"><xref:System.Xml.Linq.XName>představuje názvy<xref:System.Xml.Linq.XElement>prvků ( )<xref:System.Xml.Linq.XAttribute>a atributy ( ).</span><span class="sxs-lookup"><span data-stu-id="1e5d5-129"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="1e5d5-130">Podrobné informace a příklady naleznete v [tématu Přehled třídxdocument (C#)](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1e5d5-130">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1e5d5-131">je navržen tak, aby názvy XML byly co nejjednodušší.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-131">is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="1e5d5-132">Vzhledem ke své složitosti jsou názvy XML často považovány za pokročilé téma ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-132">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="1e5d5-133">Pravděpodobně tato složitost nepochází z oborů názvů, které vývojáři pravidelně používají v programování, ale z předpon oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-133">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="1e5d5-134">Předpony oboru názvů mohou být užitečné ke snížení úhozů požadovaných při zadávání XML nebo k usnadnění čtení jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-134">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="1e5d5-135">Předpony jsou však často pouze zástupce pro použití úplného oboru názvů XML a ve většině případů nejsou vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-135">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1e5d5-136">zjednodušuje názvy XML překladem všech předpon do odpovídajícího oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-136">simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="1e5d5-137">Předpony jsou k dispozici, pokud <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> jsou požadovány, prostřednictvím metody.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-137">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="1e5d5-138">V případě potřeby je možné řídit předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-138">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="1e5d5-139">V některých případech, pokud pracujete s jinými systémy XML, jako je například XSLT nebo XAML, je třeba řídit předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-139">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="1e5d5-140">Pokud například máte výraz XPath, který používá předpony oboru názvů a je vložen do šablony stylů XSLT, musíte se ujistit, že dokument XML je serializován s předčíslími oboru názvů, které odpovídají těm, které jsou použity ve výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-140">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="1e5d5-141">Třída XNamespace</span><span class="sxs-lookup"><span data-stu-id="1e5d5-141">XNamespace Class</span></span>  
 <span data-ttu-id="1e5d5-142"><xref:System.Xml.Linq.XNamespace>představuje obor názvů <xref:System.Xml.Linq.XElement> pro <xref:System.Xml.Linq.XAttribute>nebo .</span><span class="sxs-lookup"><span data-stu-id="1e5d5-142"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="1e5d5-143">Obory názvů jsou <xref:System.Xml.Linq.XName>součástí aplikace .</span><span class="sxs-lookup"><span data-stu-id="1e5d5-143">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="1e5d5-144">Třída XNode</span><span class="sxs-lookup"><span data-stu-id="1e5d5-144">XNode Class</span></span>  
 <span data-ttu-id="1e5d5-145"><xref:System.Xml.Linq.XNode>je abstraktní třída, která představuje uzly stromu XML.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-145"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="1e5d5-146">Následující třídy jsou <xref:System.Xml.Linq.XNode> odvozeny z třídy:</span><span class="sxs-lookup"><span data-stu-id="1e5d5-146">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="1e5d5-147">Třída XNodeDocumentOrderComparer</span><span class="sxs-lookup"><span data-stu-id="1e5d5-147">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="1e5d5-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer>poskytuje funkce pro porovnání uzlů pro jejich pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="1e5d5-149">Třída XNodeEqualityComparer</span><span class="sxs-lookup"><span data-stu-id="1e5d5-149">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="1e5d5-150"><xref:System.Xml.Linq.XNodeEqualityComparer>poskytuje funkce pro porovnání uzlů pro rovnost hodnot.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-150"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="1e5d5-151">Třída XObject</span><span class="sxs-lookup"><span data-stu-id="1e5d5-151">XObject Class</span></span>  
 <span data-ttu-id="1e5d5-152"><xref:System.Xml.Linq.XObject>je abstraktní základní <xref:System.Xml.Linq.XNode> třída <xref:System.Xml.Linq.XAttribute>a .</span><span class="sxs-lookup"><span data-stu-id="1e5d5-152"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="1e5d5-153">Poskytuje funkce poznámky a události.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-153">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="1e5d5-154">Třída XObjectChange</span><span class="sxs-lookup"><span data-stu-id="1e5d5-154">XObjectChange Class</span></span>  
 <span data-ttu-id="1e5d5-155"><xref:System.Xml.Linq.XObjectChange>určuje typ události, když je událost <xref:System.Xml.Linq.XObject>vyvolána pro .</span><span class="sxs-lookup"><span data-stu-id="1e5d5-155"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="1e5d5-156">Třída XObjectChangeEventArgs</span><span class="sxs-lookup"><span data-stu-id="1e5d5-156">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="1e5d5-157"><xref:System.Xml.Linq.XObjectChangeEventArgs>poskytuje data <xref:System.Xml.Linq.XObject.Changing> pro <xref:System.Xml.Linq.XObject.Changed> události a.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-157"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="1e5d5-158">Třída XProcessingInstruction</span><span class="sxs-lookup"><span data-stu-id="1e5d5-158">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="1e5d5-159"><xref:System.Xml.Linq.XProcessingInstruction>představuje instrukce zpracování XML.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-159"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="1e5d5-160">Instrukce zpracování sděluje informace aplikaci, která zpracovává XML.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-160">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="1e5d5-161">Třída XText</span><span class="sxs-lookup"><span data-stu-id="1e5d5-161">XText Class</span></span>  
 <span data-ttu-id="1e5d5-162"><xref:System.Xml.Linq.XText>představuje textový uzel.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-162"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="1e5d5-163">Ve většině případů není třeba používat tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-163">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="1e5d5-164">Tato třída se používá především pro smíšený obsah.</span><span class="sxs-lookup"><span data-stu-id="1e5d5-164">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5d5-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e5d5-165">See also</span></span>

- [<span data-ttu-id="1e5d5-166">Přehled programování LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="1e5d5-166">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
