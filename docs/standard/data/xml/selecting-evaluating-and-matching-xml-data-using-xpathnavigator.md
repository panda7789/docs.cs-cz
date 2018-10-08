---
title: Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2544070bb7ea891a804edd559a5d58e08b071771
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850384"
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="50925-102">Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="50925-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>
<span data-ttu-id="50925-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje metody k výběru uzly v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí dotazu XPath, vyhodnocení a podívejte se na výsledky výrazu XPath a určí, zda uzel v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> shoduje s hodnotou výraz XPath.</span><span class="sxs-lookup"><span data-stu-id="50925-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="50925-104">Těchto a dalších konceptech, které se týkají výběr, vyhodnocení a odpovídající uzly v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu jsou popsány v následujících tématech.</span><span class="sxs-lookup"><span data-stu-id="50925-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="50925-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="50925-105">In This Section</span></span>  
 [<span data-ttu-id="50925-106">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="50925-106">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="50925-107">Popisuje sadu <xref:System.Xml.XPath.XPathNavigator> metody, které jsou použity k výběru sada uzlů v třídy <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="50925-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="50925-108">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="50925-108">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="50925-109">Popisuje <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídu sloužící k vyhodnocení výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="50925-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="50925-110">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="50925-110">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="50925-111">Popisuje <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídu sloužící k určení, pokud uzel odpovídá výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="50925-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="50925-112">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="50925-112">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="50925-113">Popisuje typy uzlů, které jsou rozpoznány ve dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="50925-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="50925-114">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="50925-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 <span data-ttu-id="50925-115">Popisuje použití oborů názvů v dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="50925-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="50925-116">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="50925-116">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)  
 <span data-ttu-id="50925-117">Popisuje <xref:System.Xml.XPath.XPathExpression> třídu, která představuje zkompilovaný dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="50925-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50925-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50925-118">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="50925-119">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="50925-119">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="50925-120">Načítání dat XML pomocí XPathDocument a XmlDocument</span><span class="sxs-lookup"><span data-stu-id="50925-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
- [<span data-ttu-id="50925-121">Přístup k datům XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="50925-121">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="50925-122">Úpravy dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="50925-122">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="50925-123">Ověření schématu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="50925-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
