---
title: Zpracování dat XML pomocí modelu dat XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da8b623d3a73ca8791a0619c67b0ed3bd42447d3
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46699037"
---
# <a name="process-xml-data-using-the-xpath-data-model"></a><span data-ttu-id="c6bdd-102">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="c6bdd-102">Process XML Data Using the XPath Data Model</span></span>
<span data-ttu-id="c6bdd-103"><xref:System.Xml?displayProperty=nameWithType> Obor názvů poskytuje programový reprezentace XML dokumenty, fragmentů, uzly nebo sad uzlů v paměti, pomocí <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="c6bdd-103">The <xref:System.Xml?displayProperty=nameWithType> namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets in-memory, using the <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> classes.</span></span>  
  
 <span data-ttu-id="c6bdd-104"><xref:System.Xml.XPath.XPathDocument> Třída poskytuje rychlé, jen pro čtení, v paměti reprezentace dokumentu XML pomocí modelu dat XPath.</span><span class="sxs-lookup"><span data-stu-id="c6bdd-104">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="c6bdd-105"><xref:System.Xml.XmlDocument> Třída poskytuje reprezentaci upravovat v paměti implementace základní úrovně 1 W3C Document Object Model (DOM) a základní modelu DOM úrovně 2 dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c6bdd-105">The <xref:System.Xml.XmlDocument> class provides an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="c6bdd-106">Implementovat obě třídy <xref:System.Xml.XPath.IXPathNavigable> rozhraní a vrátit se <xref:System.Xml.XPath.XPathNavigator> objekt použitý k výběru, vyhodnocení, přejděte a v některých případech může upravovat podkladová data XML.</span><span class="sxs-lookup"><span data-stu-id="c6bdd-106">Both classes implement the <xref:System.Xml.XPath.IXPathNavigable> interface and return an <xref:System.Xml.XPath.XPathNavigator> object used to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="c6bdd-107">Následující části popisují funkce <xref:System.Xml.XPath.XPathNavigator> třídy podle třídy, která vrátí jej.</span><span class="sxs-lookup"><span data-stu-id="c6bdd-107">The following sections describe the functionality of the <xref:System.Xml.XPath.XPathNavigator> class based on the class that returns it.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6bdd-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c6bdd-108">In This Section</span></span>  
 [<span data-ttu-id="c6bdd-109">Načítání dat XML pomocí XPathDocument a XmlDocument</span><span class="sxs-lookup"><span data-stu-id="c6bdd-109">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 <span data-ttu-id="c6bdd-110">Popisuje, jak vytvořit jen pro čtení <xref:System.Xml.XPath.XPathDocument> třída objektu určeného ke čtení dokumentu XML a jak vytvářet upravitelné <xref:System.Xml.XmlDocument> objektu třídy číst a upravovat dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c6bdd-110">Describes how to create a read-only <xref:System.Xml.XPath.XPathDocument> class object to read an XML document and how to create an editable <xref:System.Xml.XmlDocument> class object to read and edit an XML document.</span></span> <span data-ttu-id="c6bdd-111">Toto téma také popisuje, jak návratový <xref:System.Xml.XPath.XPathNavigator> objekt z každé třídě k procházení a úpravy dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c6bdd-111">This topic also describes how return an <xref:System.Xml.XPath.XPathNavigator> object from each class to navigate and edit an XML document.</span></span>  
  
 [<span data-ttu-id="c6bdd-112">Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c6bdd-112">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="c6bdd-113">Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třídu sloužící k výběru uzly v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí dotazu XPath, vyhodnocení a podívejte se na výsledky výrazu XPath a určit, pokud uzel v dokumentu XML odpovídá dané XPath výraz.</span><span class="sxs-lookup"><span data-stu-id="c6bdd-113">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an XML document matches a given XPath expression.</span></span>  
  
 [<span data-ttu-id="c6bdd-114">Přístup k datům XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c6bdd-114">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="c6bdd-115">Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třídu použít k procházení uzly, extrahování dat XML a přístup k datům silného typu XML v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="c6bdd-115">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="c6bdd-116">Úpravy dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c6bdd-116">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="c6bdd-117">Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třídu sloužící k vložení, úpravu a odebrání uzlů a hodnot z dokumentu XML, který je součástí <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="c6bdd-117">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="c6bdd-118">Ověření schématu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c6bdd-118">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="c6bdd-119">Popisuje, jak ověřit obsah XML obsažených v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="c6bdd-119">Describes the ways to validate the XML content contained in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6bdd-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6bdd-120">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="c6bdd-121">Zpracování dat XML pomocí modelu DOM</span><span class="sxs-lookup"><span data-stu-id="c6bdd-121">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
