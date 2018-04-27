---
title: Zpracování dat XML v paměti
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
caps.latest.revision: 2
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1c451e4015e37c118f475ec1e7c099566e28767f
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="718bf-102">Zpracování dat XML v paměti</span><span class="sxs-lookup"><span data-stu-id="718bf-102">Processing XML Data In-Memory</span></span>
<span data-ttu-id="718bf-103">Rozhraní Microsoft .NET Framework zahrnuje tři modely pro zpracování dat XML: <xref:System.Xml.XmlDocument> třídy, <xref:System.Xml.XPath.XPathDocument> třída, a [technologie LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span><span class="sxs-lookup"><span data-stu-id="718bf-103">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span>  
  
 <span data-ttu-id="718bf-104"><xref:System.Xml.XmlDocument> Třída implementuje základní úroveň 1 W3C dokumentu objektu modelu (DOM) a modelu DOM základní úroveň 2 doporučení.</span><span class="sxs-lookup"><span data-stu-id="718bf-104">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="718bf-105">Je modelu DOM v paměti (mezipaměť) stromu reprezentace dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="718bf-105">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="718bf-106">Pomocí <xref:System.Xml.XmlDocument> a související třídy, můžete vytvořit dokumentů XML, spouštění a přístup k datům, upravovat data a uložit změny.</span><span class="sxs-lookup"><span data-stu-id="718bf-106">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="718bf-107"><xref:System.Xml.XPath.XPathDocument> Třída je jen pro čtení, v paměti datové úložiště, které je založená na datovém modelu XPath.</span><span class="sxs-lookup"><span data-stu-id="718bf-107">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="718bf-108"><xref:System.Xml.XPath.XPathNavigator> Třída nabízí několik možností úprav a navigační možnosti použití modelu kurzoru nad dokumentů XML obsažených v jen pro čtení <xref:System.Xml.XPath.XPathDocument> třídy a taky <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="718bf-108">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="718bf-109">[Technologie LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) je nový model v rozhraní .NET Framework verze 3.5 pro zpracování dat XML.</span><span class="sxs-lookup"><span data-stu-id="718bf-109">[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="718bf-110">Je model v paměti, která využívá [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span><span class="sxs-lookup"><span data-stu-id="718bf-110">It is an in-memory model that leverages [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span></span> <span data-ttu-id="718bf-111">LINQ rozšiřuje na syntaxi jazyka C# a Visual Basic zajistit nové možnosti dotazu.</span><span class="sxs-lookup"><span data-stu-id="718bf-111">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="718bf-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="718bf-112">In This Section</span></span>  
 [<span data-ttu-id="718bf-113">Zpracování dat XML pomocí modelu DOM</span><span class="sxs-lookup"><span data-stu-id="718bf-113">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="718bf-114">Popisuje použití <xref:System.Xml.XmlDocument>a jeho souvisejících tříd zpracovat XML data.</span><span class="sxs-lookup"><span data-stu-id="718bf-114">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="718bf-115">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="718bf-115">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="718bf-116">Popisuje použití <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, a <xref:System.Xml.XPath.XPathNavigator> třídy zpracovat XML data.</span><span class="sxs-lookup"><span data-stu-id="718bf-116">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="718bf-117">Zpracování dat XML pomocí LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="718bf-117">Process XML Data Using LINQ to XML</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="718bf-118">Poskytuje stručný přehled technologie LINQ to XML a poskytuje odkazy na LINQ to XML dokumentace.</span><span class="sxs-lookup"><span data-stu-id="718bf-118">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="718bf-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="718bf-119">Related Sections</span></span>  
 [<span data-ttu-id="718bf-120">Dokumenty a data XML</span><span class="sxs-lookup"><span data-stu-id="718bf-120">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
