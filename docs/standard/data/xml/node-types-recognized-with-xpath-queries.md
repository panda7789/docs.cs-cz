---
title: Rozpoznané typy uzlů s dotazy XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
ms.openlocfilehash: b9fc55b11455491406970af2a9232b277160875f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288729"
---
# <a name="node-types-recognized-with-xpath-queries"></a><span data-ttu-id="291dc-102">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="291dc-102">Node Types Recognized with XPath Queries</span></span>
<span data-ttu-id="291dc-103">Typy uzlů rozpoznané v dotazu XPath nejsou stejné typy uzlů, které se nacházejí v model DOM (Document Object Model) (DOM).</span><span class="sxs-lookup"><span data-stu-id="291dc-103">The types of nodes recognized in an XPath query are not the same node types found in the Document Object Model (DOM).</span></span>  
  
## <a name="w3c-xpath-node-types"></a><span data-ttu-id="291dc-104">Typy uzlů XPath W3C</span><span class="sxs-lookup"><span data-stu-id="291dc-104">W3C XPath Node Types</span></span>  
 <span data-ttu-id="291dc-105">Typy uzlů rozpoznané v dotazu XPath nejsou typy uzlů, které se nacházejí v model DOM (Document Object Model) (DOM).</span><span class="sxs-lookup"><span data-stu-id="291dc-105">The types of nodes recognized in an XPath query are not the types of nodes found in the Document Object Model (DOM).</span></span> <span data-ttu-id="291dc-106">Níže jsou uvedeny typy uzlů XPath reprezentované <xref:System.Xml.XPath.XPathNodeType> výčtem.</span><span class="sxs-lookup"><span data-stu-id="291dc-106">The following are the XPath node types represented by the <xref:System.Xml.XPath.XPathNodeType> enumeration.</span></span>  
  
- <xref:System.Xml.XPath.XPathNodeType.All>  
  
- <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
- <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
- <xref:System.Xml.XPath.XPathNodeType.Element>  
  
- <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
- <xref:System.Xml.XPath.XPathNodeType.Root>  
  
- <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.Text>  
  
- <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 <span data-ttu-id="291dc-107">Tyto typy uzlů jsou založeny na datovém modelu XPath, kde jsou uzly odvozeny ze sady informací XML.</span><span class="sxs-lookup"><span data-stu-id="291dc-107">These node types are based on the XPath data model, where the nodes are derived from the XML Information Set.</span></span> <span data-ttu-id="291dc-108"><xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> <xref:System.Xml.XPath.XPathNodeType.Whitespace> Typy uzlů a jsou rozšířeními od Microsoftu .NET Framework k typům základních uzlů popsaným v datovém modelu XPath.</span><span class="sxs-lookup"><span data-stu-id="291dc-108">The <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> and <xref:System.Xml.XPath.XPathNodeType.Whitespace> node types are Microsoft .NET Framework extensions to the base node types described in the XPath data model.</span></span>  
  
 <span data-ttu-id="291dc-109">Typ uzlu atributu je v datovém modelu XPath použit odlišně, než je v modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="291dc-109">The attribute node type is used differently in the XPath data model than it is in the DOM.</span></span> <span data-ttu-id="291dc-110">V datovém modelu XPath uzel elementu obsahuje sadu uzlů atributů, které se týkají, a uzel elementu je nadřazeným uzlem každého uzlu atributu.</span><span class="sxs-lookup"><span data-stu-id="291dc-110">In the XPath data model, the element node has a set of attribute nodes related to it and the element node is the parent of each attribute node.</span></span> <span data-ttu-id="291dc-111">V modelu DOM je však uzel prvku vlastníkem a nikoli nadřazeným objektem.</span><span class="sxs-lookup"><span data-stu-id="291dc-111">However, in the DOM, the element node is the owner and not the parent.</span></span> <span data-ttu-id="291dc-112">V obou modelech se uzly atributů a názvů nepovažují za podřízené uzly uzlu elementu.</span><span class="sxs-lookup"><span data-stu-id="291dc-112">In both models, attribute and namespace nodes are not considered child nodes of the element node.</span></span>  
  
 <span data-ttu-id="291dc-113">Typ uzlu oboru názvů je doplněk k datovému modelu XPath a není rozpoznaným typem uzlu modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="291dc-113">The namespace node type is an addition to the XPath data model and is not a recognized DOM node type.</span></span>  
  
 <span data-ttu-id="291dc-114">Další informace o přechodu elementů, atributů a uzlů oboru názvů naleznete v tématu [uzel nastavení navigace pomocí prvku XPathNavigator](node-set-navigation-using-xpathnavigator.md) a [atribut a uzel oboru názvů pomocí témat XPathNavigator](attribute-and-namespace-node-navigation-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="291dc-114">For more information about navigating element, attribute, and namespace nodes, see the [Node Set Navigation Using XPathNavigator](node-set-navigation-using-xpathnavigator.md) and [Attribute and Namespace Node Navigation Using XPathNavigator](attribute-and-namespace-node-navigation-using-xpathnavigator.md) topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="291dc-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="291dc-115">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="291dc-116">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="291dc-116">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="291dc-117">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="291dc-117">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="291dc-118">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="291dc-118">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="291dc-119">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="291dc-119">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="291dc-120">Dotazy a obory názvů XPath</span><span class="sxs-lookup"><span data-stu-id="291dc-120">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="291dc-121">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="291dc-121">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
