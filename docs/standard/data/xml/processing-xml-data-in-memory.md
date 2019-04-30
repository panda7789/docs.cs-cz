---
title: Zpracování dat XML v paměti
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f1a4587838180896b52bb79d447ed7ede3e22d1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770419"
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="b44ff-102">Zpracování dat XML v paměti</span><span class="sxs-lookup"><span data-stu-id="b44ff-102">Processing XML Data In-Memory</span></span>
<span data-ttu-id="b44ff-103">Rozhraní Microsoft .NET Framework zahrnuje tři modely pro zpracování dat XML: <xref:System.Xml.XmlDocument> třídy, <xref:System.Xml.XPath.XPathDocument> třídy, a [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b44ff-103">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b44ff-104"><xref:System.Xml.XmlDocument> Třída implementuje úroveň 1 jádro W3C dokumentu objektu model (DOM) a modelu DOM základní úrovně 2 doporučení.</span><span class="sxs-lookup"><span data-stu-id="b44ff-104">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="b44ff-105">(Mezipaměť) v paměti je v modelu DOM stromu reprezentace dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="b44ff-105">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="b44ff-106">S <xref:System.Xml.XmlDocument> a jeho souvisejících tříd, můžete vytvořit dokumentů XML, načtení a přístup k datům a upravovat data, a uložit změny.</span><span class="sxs-lookup"><span data-stu-id="b44ff-106">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="b44ff-107"><xref:System.Xml.XPath.XPathDocument> Třída je úložiště dat jen pro čtení, v paměti, která je založena na modelu dat XPath.</span><span class="sxs-lookup"><span data-stu-id="b44ff-107">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="b44ff-108"><xref:System.Xml.XPath.XPathNavigator> Třídy nabízí několik možností úprav a možností navigace pomocí modelu kurzoru nad dokumenty XML obsažených v jen pro čtení <xref:System.Xml.XPath.XPathDocument> třídy i na <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="b44ff-108">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="b44ff-109">[Technologie LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) je model zavedena v rozhraní .NET Framework verze 3.5 pro zpracování dat XML.</span><span class="sxs-lookup"><span data-stu-id="b44ff-109">[LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) is a model introduced in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="b44ff-110">Je modelu v paměti, který využívá [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="b44ff-110">It's an in-memory model that leverages [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).</span></span> <span data-ttu-id="b44ff-111">Rozšiřuje syntaxi jazyka LINQ C# a Visual Basic a poskytují nové možnosti dotazu.</span><span class="sxs-lookup"><span data-stu-id="b44ff-111">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b44ff-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b44ff-112">In This Section</span></span>  
 [<span data-ttu-id="b44ff-113">Zpracování dat XML pomocí modelu DOM</span><span class="sxs-lookup"><span data-stu-id="b44ff-113">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="b44ff-114">Popisuje použití <xref:System.Xml.XmlDocument>a její související třídy pro zpracování dat XML.</span><span class="sxs-lookup"><span data-stu-id="b44ff-114">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="b44ff-115">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="b44ff-115">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="b44ff-116">Popisuje použití <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, a <xref:System.Xml.XPath.XPathNavigator> třídy pro zpracování dat XML.</span><span class="sxs-lookup"><span data-stu-id="b44ff-116">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="b44ff-117">Zpracování dat XML pomocí LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="b44ff-117">Process XML Data Using LINQ to XML</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="b44ff-118">Poskytuje stručný přehled technologie LINQ to XML a poskytuje odkazy na LINQ to XML dokumentace.</span><span class="sxs-lookup"><span data-stu-id="b44ff-118">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b44ff-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b44ff-119">Related Sections</span></span>  
 [<span data-ttu-id="b44ff-120">Dokumenty a data XML</span><span class="sxs-lookup"><span data-stu-id="b44ff-120">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
