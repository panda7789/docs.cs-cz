---
title: "Typy uzlů rozpoznána s dotazy XPath"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1c1e48bbfd6388686fdb83f08668f7f0234275a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="node-types-recognized-with-xpath-queries"></a><span data-ttu-id="03238-102">Typy uzlů rozpoznána s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="03238-102">Node Types Recognized with XPath Queries</span></span>
<span data-ttu-id="03238-103">Typy uzlů rozpoznán v dotaz XPath nejsou stejné typy uzlů nalezen v objektu modelu dokumentu (DOM).</span><span class="sxs-lookup"><span data-stu-id="03238-103">The types of nodes recognized in an XPath query are not the same node types found in the Document Object Model (DOM).</span></span>  
  
## <a name="w3c-xpath-node-types"></a><span data-ttu-id="03238-104">Typy uzlů XPath W3C</span><span class="sxs-lookup"><span data-stu-id="03238-104">W3C XPath Node Types</span></span>  
 <span data-ttu-id="03238-105">Typy uzlů rozpoznán v dotaz XPath nejsou typy uzlů nalezen v objektu modelu dokumentu (DOM).</span><span class="sxs-lookup"><span data-stu-id="03238-105">The types of nodes recognized in an XPath query are not the types of nodes found in the Document Object Model (DOM).</span></span> <span data-ttu-id="03238-106">Toto jsou typy uzlů XPath reprezentována <xref:System.Xml.XPath.XPathNodeType> výčtu.</span><span class="sxs-lookup"><span data-stu-id="03238-106">The following are the XPath node types represented by the <xref:System.Xml.XPath.XPathNodeType> enumeration.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNodeType.All>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Element>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Root>  
  
-   <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Text>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 <span data-ttu-id="03238-107">Tyto typy uzlů jsou založené na XPath datový model, kde jsou uzly odvozené ze sady informace XML.</span><span class="sxs-lookup"><span data-stu-id="03238-107">These node types are based on the XPath data model, where the nodes are derived from the XML Information Set.</span></span> <span data-ttu-id="03238-108"><xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> a <xref:System.Xml.XPath.XPathNodeType.Whitespace> rozšíření rozhraní Microsoft .NET Framework pro typy základní uzlů, které jsou popsané v datovém modelu XPath jsou typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="03238-108">The <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> and <xref:System.Xml.XPath.XPathNodeType.Whitespace> node types are Microsoft .NET Framework extensions to the base node types described in the XPath data model.</span></span>  
  
 <span data-ttu-id="03238-109">Typ uzlu atribut se používá jinak v datovém modelu XPath než je v modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="03238-109">The attribute node type is used differently in the XPath data model than it is in the DOM.</span></span> <span data-ttu-id="03238-110">V datovém modelu XPath uzlu element obsahuje sadu atributů uzly s ním souvisejí a uzel elementu je nadřazená každého uzlu atributu.</span><span class="sxs-lookup"><span data-stu-id="03238-110">In the XPath data model, the element node has a set of attribute nodes related to it and the element node is the parent of each attribute node.</span></span> <span data-ttu-id="03238-111">V modelu DOM, uzlu element je však vlastníka a není nadřazený.</span><span class="sxs-lookup"><span data-stu-id="03238-111">However, in the DOM, the element node is the owner and not the parent.</span></span> <span data-ttu-id="03238-112">V obou modelech atribut a obor názvů uzly nejsou považovány za podřízené uzly uzlu elementu.</span><span class="sxs-lookup"><span data-stu-id="03238-112">In both models, attribute and namespace nodes are not considered child nodes of the element node.</span></span>  
  
 <span data-ttu-id="03238-113">Typ uzlu oboru názvů je doplňkem k XPath datový model a není rozpoznaný typ uzlu DOM.</span><span class="sxs-lookup"><span data-stu-id="03238-113">The namespace node type is an addition to the XPath data model and is not a recognized DOM node type.</span></span>  
  
 <span data-ttu-id="03238-114">Další informace o navigace element atribut a uzly oboru názvů najdete v tématu [uzlu nastavit navigační pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) a [atribut a Namespace uzlu navigace pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) témata.</span><span class="sxs-lookup"><span data-stu-id="03238-114">For more information about navigating element, attribute, and namespace nodes, see the [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) and [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03238-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="03238-115">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="03238-116">Zpracování kódu XML dat pomocí jazyka XPath datový Model</span><span class="sxs-lookup"><span data-stu-id="03238-116">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="03238-117">Vyberte pomocí objektem XPathNavigator nastaveným na Data XML</span><span class="sxs-lookup"><span data-stu-id="03238-117">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="03238-118">Vyhodnocení výrazů jazyka XPath pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="03238-118">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="03238-119">Odpovídající pomocí objektem XPathNavigator nastaveným na uzly</span><span class="sxs-lookup"><span data-stu-id="03238-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="03238-120">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="03238-120">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="03238-121">Výrazy kompilované XPath</span><span class="sxs-lookup"><span data-stu-id="03238-121">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
