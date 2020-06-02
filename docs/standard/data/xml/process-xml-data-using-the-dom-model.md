---
title: Zpracování dat XML pomocí modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
ms.openlocfilehash: 242554cc948ef16972ffd26d5464dae2727ed339
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290834"
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="eb4b5-102">Zpracování dat XML pomocí modelu DOM</span><span class="sxs-lookup"><span data-stu-id="eb4b5-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="eb4b5-103">XML model DOM (Document Object Model) (DOM) zpracovává data XML jako standardní sadu objektů a slouží ke zpracování dat XML v paměti.</span><span class="sxs-lookup"><span data-stu-id="eb4b5-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="eb4b5-104">`System.Xml`Obor názvů poskytuje programovou reprezentaci dokumentů XML, fragmentů, uzlů nebo sad uzlů.</span><span class="sxs-lookup"><span data-stu-id="eb4b5-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="eb4b5-105">Vychází z konsorcium World Wide Web (W3C) DOM úrovně 1 Core a DOM – základní doporučení úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="eb4b5-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="eb4b5-106"><xref:System.Xml.XmlDocument>Třída představuje dokument XML.</span><span class="sxs-lookup"><span data-stu-id="eb4b5-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="eb4b5-107">Obsahuje členy pro načtení a vytvoření všech ostatních objektů XML.</span><span class="sxs-lookup"><span data-stu-id="eb4b5-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="eb4b5-108">Pomocí <xref:System.Xml.XmlDocument> a souvisejících tříd můžete vytvářet dokumenty XML, načítat a přistupovat k datům, upravovat data a ukládat změny.</span><span class="sxs-lookup"><span data-stu-id="eb4b5-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb4b5-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="eb4b5-109">In This Section</span></span>  
  
- [<span data-ttu-id="eb4b5-110">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="eb4b5-110">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)  
  
- [<span data-ttu-id="eb4b5-111">Typy uzlů XML</span><span class="sxs-lookup"><span data-stu-id="eb4b5-111">Types of XML Nodes</span></span>](types-of-xml-nodes.md)  
  
- [<span data-ttu-id="eb4b5-112">Hierarchie modelu DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="eb4b5-112">XML Document Object Model (DOM) Hierarchy</span></span>](xml-document-object-model-dom-hierarchy.md)  
  
- [<span data-ttu-id="eb4b5-113">Mapování hierarchie objektů na data XML</span><span class="sxs-lookup"><span data-stu-id="eb4b5-113">Mapping the Object Hierarchy to XML Data</span></span>](mapping-the-object-hierarchy-to-xml-data.md)  
  
- [<span data-ttu-id="eb4b5-114">Vytváření dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="eb4b5-114">XML Document Creation</span></span>](xml-document-creation.md)  
  
- [<span data-ttu-id="eb4b5-115">Načtení dokumentu XML do modelu DOM</span><span class="sxs-lookup"><span data-stu-id="eb4b5-115">Reading an XML Document into the DOM</span></span>](reading-an-xml-document-into-the-dom.md)  
  
- [<span data-ttu-id="eb4b5-116">Vkládání uzlů do dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="eb4b5-116">Inserting Nodes into an XML Document</span></span>](inserting-nodes-into-an-xml-document.md)  
  
- [<span data-ttu-id="eb4b5-117">Odebrání uzlů, obsahu a hodnot z dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="eb4b5-117">Removing Nodes, Content, and Values from an XML Document</span></span>](removing-nodes-content-and-values-from-an-xml-document.md)  
  
- [<span data-ttu-id="eb4b5-118">Úprava uzlů, obsahu a hodnot v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="eb4b5-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](modifying-nodes-content-and-values-in-an-xml-document.md)  
  
- [<span data-ttu-id="eb4b5-119">Ověřování dokumentu XML v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="eb4b5-119">Validating an XML Document in the DOM</span></span>](validating-an-xml-document-in-the-dom.md)  
  
- [<span data-ttu-id="eb4b5-120">Ukládání a zápis dokumentu</span><span class="sxs-lookup"><span data-stu-id="eb4b5-120">Saving and Writing a Document</span></span>](saving-and-writing-a-document.md)  
  
- [<span data-ttu-id="eb4b5-121">Výběr uzlů pomocí navigace XPath</span><span class="sxs-lookup"><span data-stu-id="eb4b5-121">Select Nodes Using XPath Navigation</span></span>](select-nodes-using-xpath-navigation.md)  
  
- [<span data-ttu-id="eb4b5-122">Překlad externích prostředků</span><span class="sxs-lookup"><span data-stu-id="eb4b5-122">Resolving External Resources</span></span>](resolving-external-resources.md)  
  
- [<span data-ttu-id="eb4b5-123">Porovnání objektů pomocí XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="eb4b5-123">Object Comparison Using XmlNameTable</span></span>](object-comparison-using-xmlnametable.md)  
  
- [<span data-ttu-id="eb4b5-124">Kolekce uzlů v NamedNodeMaps a NodeLists</span><span class="sxs-lookup"><span data-stu-id="eb4b5-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](node-collections-in-namednodemaps-and-nodelists.md)  
  
- [<span data-ttu-id="eb4b5-125">Dynamické aktualizace pro NodeLists a NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="eb4b5-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
- [<span data-ttu-id="eb4b5-126">Podpora oboru názvů v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="eb4b5-126">Namespace Support in the DOM</span></span>](namespace-support-in-the-dom.md)  
  
- [<span data-ttu-id="eb4b5-127">Zpracování událostí v dokumentu XML pomocí XmlNodeChangedEventArgs</span><span class="sxs-lookup"><span data-stu-id="eb4b5-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
- [<span data-ttu-id="eb4b5-128">Rozšíření modelu DOM</span><span class="sxs-lookup"><span data-stu-id="eb4b5-128">Extending the DOM</span></span>](extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="eb4b5-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="eb4b5-129">Related Sections</span></span>  
 [<span data-ttu-id="eb4b5-130">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="eb4b5-130">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="eb4b5-131">Popisuje zpracování XML pomocí <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="eb4b5-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
