---
title: "Zpracování dat XML pomocí modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 06c8b2e130dbecaca4c08684d030c8dcef1cd5a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="ddbab-102">Zpracování dat XML pomocí modelu DOM</span><span class="sxs-lookup"><span data-stu-id="ddbab-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="ddbab-103">XML modelu DOM (Document Object) zpracovává XML data jako standardní sadu objektů a slouží k procesu data XML v paměti.</span><span class="sxs-lookup"><span data-stu-id="ddbab-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="ddbab-104">`System.Xml` Obor názvů obsahuje programový reprezentace XML dokumenty, fragmenty, uzly nebo sad uzlů.</span><span class="sxs-lookup"><span data-stu-id="ddbab-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="ddbab-105">Je založena na základní úroveň 1 DOM World Wide Web Consortium (W3C) a doporučení DOM úroveň 2 jádra.</span><span class="sxs-lookup"><span data-stu-id="ddbab-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="ddbab-106"><xref:System.Xml.XmlDocument> Třída reprezentuje dokument XML.</span><span class="sxs-lookup"><span data-stu-id="ddbab-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="ddbab-107">Pro načítání a vytvoření všechny ostatní objekty XML obsahuje členy.</span><span class="sxs-lookup"><span data-stu-id="ddbab-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="ddbab-108">Pomocí <xref:System.Xml.XmlDocument>a jeho souvisejících tříd, můžete vytvořit dokumentů XML, spouštění a přístup k datům, upravovat data a uložit změny.</span><span class="sxs-lookup"><span data-stu-id="ddbab-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ddbab-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ddbab-109">In This Section</span></span>  
  
-   [<span data-ttu-id="ddbab-110">XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="ddbab-110">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)  
  
-   [<span data-ttu-id="ddbab-111">Typy uzlů XML</span><span class="sxs-lookup"><span data-stu-id="ddbab-111">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
  
-   [<span data-ttu-id="ddbab-112">Hierarchie modelu (DOM) objekt dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="ddbab-112">XML Document Object Model (DOM) Hierarchy</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)  
  
-   [<span data-ttu-id="ddbab-113">Mapování hierarchie objektů na XML Data</span><span class="sxs-lookup"><span data-stu-id="ddbab-113">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)  
  
-   [<span data-ttu-id="ddbab-114">Vytváření dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="ddbab-114">XML Document Creation</span></span>](../../../../docs/standard/data/xml/xml-document-creation.md)  
  
-   [<span data-ttu-id="ddbab-115">Čtení dokumentu XML do modelu DOM</span><span class="sxs-lookup"><span data-stu-id="ddbab-115">Reading an XML Document into the DOM</span></span>](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)  
  
-   [<span data-ttu-id="ddbab-116">Vkládání uzlů do dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="ddbab-116">Inserting Nodes into an XML Document</span></span>](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md)  
  
-   [<span data-ttu-id="ddbab-117">Odebírání uzlů, obsah a hodnoty z dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="ddbab-117">Removing Nodes, Content, and Values from an XML Document</span></span>](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)  
  
-   [<span data-ttu-id="ddbab-118">Úprava uzlů, obsah a hodnoty v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="ddbab-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)  
  
-   [<span data-ttu-id="ddbab-119">Ověřování dokumentu XML v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="ddbab-119">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
  
-   [<span data-ttu-id="ddbab-120">Ukládání a zápis dokumentu</span><span class="sxs-lookup"><span data-stu-id="ddbab-120">Saving and Writing a Document</span></span>](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)  
  
-   [<span data-ttu-id="ddbab-121">Vyberte uzel pomocí jazyka XPath navigace</span><span class="sxs-lookup"><span data-stu-id="ddbab-121">Select Nodes Using XPath Navigation</span></span>](../../../../docs/standard/data/xml/select-nodes-using-xpath-navigation.md)  
  
-   [<span data-ttu-id="ddbab-122">Řešení externí zdroje</span><span class="sxs-lookup"><span data-stu-id="ddbab-122">Resolving External Resources</span></span>](../../../../docs/standard/data/xml/resolving-external-resources.md)  
  
-   [<span data-ttu-id="ddbab-123">Objekt porovnání pomocí XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="ddbab-123">Object Comparison Using XmlNameTable</span></span>](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)  
  
-   [<span data-ttu-id="ddbab-124">Uzel kolekce v NamedNodeMaps a NodeLists</span><span class="sxs-lookup"><span data-stu-id="ddbab-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)  
  
-   [<span data-ttu-id="ddbab-125">Dynamické aktualizace NodeLists a NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="ddbab-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](../../../../docs/standard/data/xml/dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
-   [<span data-ttu-id="ddbab-126">Podpora Namespace v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="ddbab-126">Namespace Support in the DOM</span></span>](../../../../docs/standard/data/xml/namespace-support-in-the-dom.md)  
  
-   [<span data-ttu-id="ddbab-127">Zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs</span><span class="sxs-lookup"><span data-stu-id="ddbab-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
-   [<span data-ttu-id="ddbab-128">Rozšíření modelu DOM</span><span class="sxs-lookup"><span data-stu-id="ddbab-128">Extending the DOM</span></span>](../../../../docs/standard/data/xml/extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="ddbab-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ddbab-129">Related Sections</span></span>  
 [<span data-ttu-id="ddbab-130">Zpracování kódu XML dat pomocí jazyka XPath datový Model</span><span class="sxs-lookup"><span data-stu-id="ddbab-130">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="ddbab-131">Popisuje použití zpracování XML <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="ddbab-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
