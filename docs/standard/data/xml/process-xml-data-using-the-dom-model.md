---
title: Zpracování dat XML pomocí modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d34d22d8329f0bc26c1e29653137211bf300d324
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647824"
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="dd969-102">Zpracování dat XML pomocí modelu DOM</span><span class="sxs-lookup"><span data-stu-id="dd969-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="dd969-103">XML Document Object Model (DOM) zpracovává XML data jako standardní sadu objektů a slouží ke zpracování dat XML v paměti.</span><span class="sxs-lookup"><span data-stu-id="dd969-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="dd969-104">`System.Xml` Obor názvů poskytuje programový reprezentace XML dokumenty, fragmentů, uzly nebo sad uzlů.</span><span class="sxs-lookup"><span data-stu-id="dd969-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="dd969-105">Je založen na základní úrovni 1 modelu DOM World Wide Web Consortium (W3C) a doporučení modelu DOM úroveň 2 jádra.</span><span class="sxs-lookup"><span data-stu-id="dd969-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="dd969-106"><xref:System.Xml.XmlDocument> Třída představuje dokument XML.</span><span class="sxs-lookup"><span data-stu-id="dd969-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="dd969-107">Obsahuje členy pro načtení a vytvoření všechny ostatní objekty jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="dd969-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="dd969-108">Použití <xref:System.Xml.XmlDocument>a jeho souvisejících tříd, můžete vytvořit dokumentů XML, načtení a přístup k datům a upravovat data, a uložit změny.</span><span class="sxs-lookup"><span data-stu-id="dd969-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd969-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="dd969-109">In This Section</span></span>  
  
- [<span data-ttu-id="dd969-110">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="dd969-110">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)  
  
- [<span data-ttu-id="dd969-111">Typy uzlů XML</span><span class="sxs-lookup"><span data-stu-id="dd969-111">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
  
- [<span data-ttu-id="dd969-112">Hierarchie modelu DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="dd969-112">XML Document Object Model (DOM) Hierarchy</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)  
  
- [<span data-ttu-id="dd969-113">Mapování hierarchie objektů na data XML</span><span class="sxs-lookup"><span data-stu-id="dd969-113">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)  
  
- [<span data-ttu-id="dd969-114">Vytváření dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="dd969-114">XML Document Creation</span></span>](../../../../docs/standard/data/xml/xml-document-creation.md)  
  
- [<span data-ttu-id="dd969-115">Čtení dokumentu XML do modelu DOM</span><span class="sxs-lookup"><span data-stu-id="dd969-115">Reading an XML Document into the DOM</span></span>](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)  
  
- [<span data-ttu-id="dd969-116">Vkládání uzlů do dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="dd969-116">Inserting Nodes into an XML Document</span></span>](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md)  
  
- [<span data-ttu-id="dd969-117">Odebrání uzlů, obsahu a hodnot z dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="dd969-117">Removing Nodes, Content, and Values from an XML Document</span></span>](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)  
  
- [<span data-ttu-id="dd969-118">Úprava uzlů, obsahu a hodnot v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="dd969-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)  
  
- [<span data-ttu-id="dd969-119">Ověřování dokumentu XML v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="dd969-119">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
  
- [<span data-ttu-id="dd969-120">Ukládání a zápis dokumentu</span><span class="sxs-lookup"><span data-stu-id="dd969-120">Saving and Writing a Document</span></span>](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)  
  
- [<span data-ttu-id="dd969-121">Výběr uzlů pomocí navigace XPath</span><span class="sxs-lookup"><span data-stu-id="dd969-121">Select Nodes Using XPath Navigation</span></span>](../../../../docs/standard/data/xml/select-nodes-using-xpath-navigation.md)  
  
- [<span data-ttu-id="dd969-122">Překlad externích prostředků</span><span class="sxs-lookup"><span data-stu-id="dd969-122">Resolving External Resources</span></span>](../../../../docs/standard/data/xml/resolving-external-resources.md)  
  
- [<span data-ttu-id="dd969-123">Porovnání objektů pomocí XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="dd969-123">Object Comparison Using XmlNameTable</span></span>](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)  
  
- [<span data-ttu-id="dd969-124">Kolekce uzlů v NamedNodeMaps a NodeLists</span><span class="sxs-lookup"><span data-stu-id="dd969-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)  
  
- [<span data-ttu-id="dd969-125">Dynamické aktualizace pro NodeLists a NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="dd969-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](../../../../docs/standard/data/xml/dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
- [<span data-ttu-id="dd969-126">Podpora oboru názvů v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="dd969-126">Namespace Support in the DOM</span></span>](../../../../docs/standard/data/xml/namespace-support-in-the-dom.md)  
  
- [<span data-ttu-id="dd969-127">Zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs</span><span class="sxs-lookup"><span data-stu-id="dd969-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
- [<span data-ttu-id="dd969-128">Rozšíření modelu DOM</span><span class="sxs-lookup"><span data-stu-id="dd969-128">Extending the DOM</span></span>](../../../../docs/standard/data/xml/extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="dd969-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="dd969-129">Related Sections</span></span>  
 [<span data-ttu-id="dd969-130">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="dd969-130">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="dd969-131">Popisuje použití zpracování XML <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="dd969-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
