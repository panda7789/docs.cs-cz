---
title: "Výběr, Evaluating a porovnávání dat XML pomocí objektem XPathNavigator nastaveným na"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7a86fb36d367342ea0c5bc4968bdd5744bd0524e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="dca84-102">Výběr, Evaluating a porovnávání dat XML pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="dca84-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>
<span data-ttu-id="dca84-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje metody a vyberte uzly ve <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí dotaz XPath, hodnocení a podívejte se na výsledky výraz XPath a určí, zda uzel v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu odpovídá daný výraz XPath.</span><span class="sxs-lookup"><span data-stu-id="dca84-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="dca84-104">Těchto a dalších konceptech, které se vztahují k výběru, hodnocení a odpovídající uzly ve <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objekt jsou popsány v následujících tématech.</span><span class="sxs-lookup"><span data-stu-id="dca84-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dca84-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="dca84-105">In This Section</span></span>  
 [<span data-ttu-id="dca84-106">Vyberte pomocí objektem XPathNavigator nastaveným na Data XML</span><span class="sxs-lookup"><span data-stu-id="dca84-106">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="dca84-107">Popisuje sadu <xref:System.Xml.XPath.XPathNavigator> metody, které jsou použity k výběru sada uzlů v třídy <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="dca84-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="dca84-108">Vyhodnocení výrazů jazyka XPath pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="dca84-108">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="dca84-109">Popisuje <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídu sloužící k vyhodnocení výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="dca84-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="dca84-110">Odpovídající pomocí objektem XPathNavigator nastaveným na uzly</span><span class="sxs-lookup"><span data-stu-id="dca84-110">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="dca84-111">Popisuje <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metodu <xref:System.Xml.XPath.XPathNavigator> třídu sloužící k určení, jestli odpovídá uzlu výraz XPath.</span><span class="sxs-lookup"><span data-stu-id="dca84-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="dca84-112">Typy uzlů rozpoznána s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="dca84-112">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="dca84-113">Popisuje typy uzlů rozpoznán v dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="dca84-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="dca84-114">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="dca84-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 <span data-ttu-id="dca84-115">Popisuje použití obory názvů v dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="dca84-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="dca84-116">Výrazy kompilované XPath</span><span class="sxs-lookup"><span data-stu-id="dca84-116">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)  
 <span data-ttu-id="dca84-117">Popisuje <xref:System.Xml.XPath.XPathExpression> třídu, která představuje kompilovaném dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="dca84-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca84-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="dca84-118">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="dca84-119">Zpracování kódu XML dat pomocí jazyka XPath datový Model</span><span class="sxs-lookup"><span data-stu-id="dca84-119">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="dca84-120">Načítání dat XML pomocí XPathDocument a třídou XMLDocument nastavenou na</span><span class="sxs-lookup"><span data-stu-id="dca84-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="dca84-121">Přístup k datům XML pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="dca84-121">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="dca84-122">Úpravy pomocí objektem XPathNavigator nastaveným na Data XML</span><span class="sxs-lookup"><span data-stu-id="dca84-122">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="dca84-123">Ověření schématu pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="dca84-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
