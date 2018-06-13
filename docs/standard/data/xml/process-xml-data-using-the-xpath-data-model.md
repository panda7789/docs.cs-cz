---
title: Zpracování kódu XML dat pomocí jazyka XPath datový Model
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ae129d0be4afb91aedb050ff4b90aff1ce058976
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569949"
---
# <a name="process-xml-data-using-the-xpath-data-model"></a><span data-ttu-id="42485-102">Zpracování kódu XML dat pomocí jazyka XPath datový Model</span><span class="sxs-lookup"><span data-stu-id="42485-102">Process XML Data Using the XPath Data Model</span></span>
<span data-ttu-id="42485-103"><xref:System.Xml?displayProperty=nameWithType> Obor názvů poskytuje programovací reprezentace XML dokumenty, fragmenty, uzly nebo sad uzlů v paměti, pomocí <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="42485-103">The <xref:System.Xml?displayProperty=nameWithType> namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets in-memory, using the <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> classes.</span></span>  
  
 <span data-ttu-id="42485-104"><xref:System.Xml.XPath.XPathDocument> Třída poskytuje rychlé, jen pro čtení, v paměti reprezentace dokumentu XML pomocí modelu dat XPath.</span><span class="sxs-lookup"><span data-stu-id="42485-104">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="42485-105"><xref:System.Xml.XmlDocument> Třída poskytuje reprezentaci upravovat v paměti dokumentu XML, které implementují základní úroveň 1 W3C Model Document Object (DOM) a základní DOM Level 2.</span><span class="sxs-lookup"><span data-stu-id="42485-105">The <xref:System.Xml.XmlDocument> class provides an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="42485-106">Obě třídy implementovat <xref:System.Xml.XPath.IXPathNavigable> rozhraní a vrátit <xref:System.Xml.XPath.XPathNavigator> objekt použitý k výběru, vyhodnotit, přejděte a v některých případech upravit základní data XML.</span><span class="sxs-lookup"><span data-stu-id="42485-106">Both classes implement the <xref:System.Xml.XPath.IXPathNavigable> interface and return an <xref:System.Xml.XPath.XPathNavigator> object used to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="42485-107">Následující části popisují funkce <xref:System.Xml.XPath.XPathNavigator> třída založena na třídu, která vrátí ji.</span><span class="sxs-lookup"><span data-stu-id="42485-107">The following sections describe the functionality of the <xref:System.Xml.XPath.XPathNavigator> class based on the class that returns it.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42485-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="42485-108">In This Section</span></span>  
 [<span data-ttu-id="42485-109">Načítání dat XML pomocí XPathDocument a XmlDocument</span><span class="sxs-lookup"><span data-stu-id="42485-109">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 <span data-ttu-id="42485-110">Popisuje postup vytvoření jen pro čtení <xref:System.Xml.XPath.XPathDocument> třída objektu určeného ke čtení dokumentu XML a jak vytvořit upravitelné <xref:System.Xml.XmlDocument> objektu třídy číst a upravovat dokument XML.</span><span class="sxs-lookup"><span data-stu-id="42485-110">Describes how to create a read-only <xref:System.Xml.XPath.XPathDocument> class object to read an XML document and how to create an editable <xref:System.Xml.XmlDocument> class object to read and edit an XML document.</span></span> <span data-ttu-id="42485-111">Toto téma také popisuje, jak návratový <xref:System.Xml.XPath.XPathNavigator> objekt z každé třídě přejděte a upravit dokument XML.</span><span class="sxs-lookup"><span data-stu-id="42485-111">This topic also describes how return an <xref:System.Xml.XPath.XPathNavigator> object from each class to navigate and edit an XML document.</span></span>  
  
 [<span data-ttu-id="42485-112">Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="42485-112">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="42485-113">Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třída používaná k vyberte uzly ve <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí dotaz XPath, hodnocení a podívejte se na výsledky výraz XPath a určit, jestli uzlu v dokumentu XML odpovídá dané XPath výraz.</span><span class="sxs-lookup"><span data-stu-id="42485-113">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an XML document matches a given XPath expression.</span></span>  
  
 [<span data-ttu-id="42485-114">Přístup k datům XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="42485-114">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="42485-115">Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třída používaná přejděte uzly, extrahovat XML data a přístup k datům silného typu XML v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="42485-115">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="42485-116">Úpravy dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="42485-116">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="42485-117">Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třída používaná vložit, upravovat a odebírat uzly a hodnoty z dokumentu XML, který je součástí <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="42485-117">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="42485-118">Ověření schématu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="42485-118">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="42485-119">Popisuje, jak ověřit obsah XML, které jsou součástí <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="42485-119">Describes the ways to validate the XML content contained in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42485-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="42485-120">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="42485-121">Zpracování dat XML pomocí modelu DOM</span><span class="sxs-lookup"><span data-stu-id="42485-121">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
