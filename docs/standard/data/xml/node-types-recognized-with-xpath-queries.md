---
title: Typy uzlů rozpoznána s dotazy XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 005c5f4981a7ab1889678e391a6df6e0b7b43f71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569376"
---
# <a name="node-types-recognized-with-xpath-queries"></a><span data-ttu-id="3e304-102">Typy uzlů rozpoznána s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="3e304-102">Node Types Recognized with XPath Queries</span></span>
<span data-ttu-id="3e304-103">Typy uzlů rozpoznán v dotaz XPath nejsou stejné typy uzlů nalezen v objektu modelu dokumentu (DOM).</span><span class="sxs-lookup"><span data-stu-id="3e304-103">The types of nodes recognized in an XPath query are not the same node types found in the Document Object Model (DOM).</span></span>  
  
## <a name="w3c-xpath-node-types"></a><span data-ttu-id="3e304-104">Typy uzlů XPath W3C</span><span class="sxs-lookup"><span data-stu-id="3e304-104">W3C XPath Node Types</span></span>  
 <span data-ttu-id="3e304-105">Typy uzlů rozpoznán v dotaz XPath nejsou typy uzlů nalezen v objektu modelu dokumentu (DOM).</span><span class="sxs-lookup"><span data-stu-id="3e304-105">The types of nodes recognized in an XPath query are not the types of nodes found in the Document Object Model (DOM).</span></span> <span data-ttu-id="3e304-106">Toto jsou typy uzlů XPath reprezentována <xref:System.Xml.XPath.XPathNodeType> výčtu.</span><span class="sxs-lookup"><span data-stu-id="3e304-106">The following are the XPath node types represented by the <xref:System.Xml.XPath.XPathNodeType> enumeration.</span></span>  
  
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
  
 <span data-ttu-id="3e304-107">Tyto typy uzlů jsou založené na XPath datový model, kde jsou uzly odvozené ze sady informace XML.</span><span class="sxs-lookup"><span data-stu-id="3e304-107">These node types are based on the XPath data model, where the nodes are derived from the XML Information Set.</span></span> <span data-ttu-id="3e304-108"><xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> a <xref:System.Xml.XPath.XPathNodeType.Whitespace> rozšíření rozhraní Microsoft .NET Framework pro typy základní uzlů, které jsou popsané v datovém modelu XPath jsou typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="3e304-108">The <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> and <xref:System.Xml.XPath.XPathNodeType.Whitespace> node types are Microsoft .NET Framework extensions to the base node types described in the XPath data model.</span></span>  
  
 <span data-ttu-id="3e304-109">Typ uzlu atribut se používá jinak v datovém modelu XPath než je v modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="3e304-109">The attribute node type is used differently in the XPath data model than it is in the DOM.</span></span> <span data-ttu-id="3e304-110">V datovém modelu XPath uzlu element obsahuje sadu atributů uzly s ním souvisejí a uzel elementu je nadřazená každého uzlu atributu.</span><span class="sxs-lookup"><span data-stu-id="3e304-110">In the XPath data model, the element node has a set of attribute nodes related to it and the element node is the parent of each attribute node.</span></span> <span data-ttu-id="3e304-111">V modelu DOM, uzlu element je však vlastníka a není nadřazený.</span><span class="sxs-lookup"><span data-stu-id="3e304-111">However, in the DOM, the element node is the owner and not the parent.</span></span> <span data-ttu-id="3e304-112">V obou modelech atribut a obor názvů uzly nejsou považovány za podřízené uzly uzlu elementu.</span><span class="sxs-lookup"><span data-stu-id="3e304-112">In both models, attribute and namespace nodes are not considered child nodes of the element node.</span></span>  
  
 <span data-ttu-id="3e304-113">Typ uzlu oboru názvů je doplňkem k XPath datový model a není rozpoznaný typ uzlu DOM.</span><span class="sxs-lookup"><span data-stu-id="3e304-113">The namespace node type is an addition to the XPath data model and is not a recognized DOM node type.</span></span>  
  
 <span data-ttu-id="3e304-114">Další informace o navigace element atribut a uzly oboru názvů najdete v tématu [uzlu nastavit navigační pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) a [atribut a Namespace uzlu navigace pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) témata.</span><span class="sxs-lookup"><span data-stu-id="3e304-114">For more information about navigating element, attribute, and namespace nodes, see the [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) and [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e304-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e304-115">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="3e304-116">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="3e304-116">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="3e304-117">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3e304-117">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="3e304-118">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3e304-118">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="3e304-119">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3e304-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="3e304-120">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="3e304-120">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="3e304-121">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="3e304-121">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
