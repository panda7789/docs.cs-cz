---
title: Zpracování dat XML pomocí modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
ms.openlocfilehash: 01ef4bef57b8a2e3e13f28a98adb21b111f3f4ed
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710450"
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="57a15-102">Zpracování dat XML pomocí modelu DOM</span><span class="sxs-lookup"><span data-stu-id="57a15-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="57a15-103">XML model DOM (Document Object Model) (DOM) zpracovává data XML jako standardní sadu objektů a slouží ke zpracování dat XML v paměti.</span><span class="sxs-lookup"><span data-stu-id="57a15-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="57a15-104">Obor názvů `System.Xml` poskytuje programové znázornění dokumentů XML, fragmentů, uzlů nebo sad uzlů.</span><span class="sxs-lookup"><span data-stu-id="57a15-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="57a15-105">Vychází z konsorcium World Wide Web (W3C) DOM úrovně 1 Core a DOM – základní doporučení úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="57a15-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="57a15-106">Třída <xref:System.Xml.XmlDocument> představuje dokument XML.</span><span class="sxs-lookup"><span data-stu-id="57a15-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="57a15-107">Obsahuje členy pro načtení a vytvoření všech ostatních objektů XML.</span><span class="sxs-lookup"><span data-stu-id="57a15-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="57a15-108">Pomocí <xref:System.Xml.XmlDocument>a souvisejících tříd můžete vytvářet dokumenty XML, načítat a přistupovat k datům, upravovat data a ukládat změny.</span><span class="sxs-lookup"><span data-stu-id="57a15-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57a15-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="57a15-109">In This Section</span></span>  
  
- [<span data-ttu-id="57a15-110">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="57a15-110">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)  
  
- [<span data-ttu-id="57a15-111">Typy uzlů XML</span><span class="sxs-lookup"><span data-stu-id="57a15-111">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
  
- [<span data-ttu-id="57a15-112">Hierarchie modelu DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="57a15-112">XML Document Object Model (DOM) Hierarchy</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)  
  
- [<span data-ttu-id="57a15-113">Mapování hierarchie objektů na data XML</span><span class="sxs-lookup"><span data-stu-id="57a15-113">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)  
  
- [<span data-ttu-id="57a15-114">Vytváření dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="57a15-114">XML Document Creation</span></span>](../../../../docs/standard/data/xml/xml-document-creation.md)  
  
- [<span data-ttu-id="57a15-115">Čtení dokumentu XML do modelu DOM</span><span class="sxs-lookup"><span data-stu-id="57a15-115">Reading an XML Document into the DOM</span></span>](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)  
  
- [<span data-ttu-id="57a15-116">Vkládání uzlů do dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="57a15-116">Inserting Nodes into an XML Document</span></span>](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md)  
  
- [<span data-ttu-id="57a15-117">Odebrání uzlů, obsahu a hodnot z dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="57a15-117">Removing Nodes, Content, and Values from an XML Document</span></span>](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)  
  
- [<span data-ttu-id="57a15-118">Úprava uzlů, obsahu a hodnot v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="57a15-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)  
  
- [<span data-ttu-id="57a15-119">Ověřování dokumentu XML v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="57a15-119">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
  
- [<span data-ttu-id="57a15-120">Ukládání a zápis dokumentu</span><span class="sxs-lookup"><span data-stu-id="57a15-120">Saving and Writing a Document</span></span>](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)  
  
- [<span data-ttu-id="57a15-121">Výběr uzlů pomocí navigace XPath</span><span class="sxs-lookup"><span data-stu-id="57a15-121">Select Nodes Using XPath Navigation</span></span>](../../../../docs/standard/data/xml/select-nodes-using-xpath-navigation.md)  
  
- [<span data-ttu-id="57a15-122">Překlad externích prostředků</span><span class="sxs-lookup"><span data-stu-id="57a15-122">Resolving External Resources</span></span>](../../../../docs/standard/data/xml/resolving-external-resources.md)  
  
- [<span data-ttu-id="57a15-123">Porovnání objektů pomocí XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="57a15-123">Object Comparison Using XmlNameTable</span></span>](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)  
  
- [<span data-ttu-id="57a15-124">Kolekce uzlů v NamedNodeMaps a NodeLists</span><span class="sxs-lookup"><span data-stu-id="57a15-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)  
  
- [<span data-ttu-id="57a15-125">Dynamické aktualizace pro NodeLists a NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="57a15-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](../../../../docs/standard/data/xml/dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
- [<span data-ttu-id="57a15-126">Podpora oboru názvů v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="57a15-126">Namespace Support in the DOM</span></span>](../../../../docs/standard/data/xml/namespace-support-in-the-dom.md)  
  
- [<span data-ttu-id="57a15-127">Zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs</span><span class="sxs-lookup"><span data-stu-id="57a15-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
- [<span data-ttu-id="57a15-128">Rozšíření modelu DOM</span><span class="sxs-lookup"><span data-stu-id="57a15-128">Extending the DOM</span></span>](../../../../docs/standard/data/xml/extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="57a15-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="57a15-129">Related Sections</span></span>  
 [<span data-ttu-id="57a15-130">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="57a15-130">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="57a15-131">Popisuje zpracování XML pomocí třídy <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="57a15-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
