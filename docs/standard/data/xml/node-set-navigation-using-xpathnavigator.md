---
title: "Uzel navigační sady pomocí objektem XPathNavigator nastaveným na"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d1bca725d20ec35ef7d6f60fce131f9d9c951650
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="c15e8-102">Uzel navigační sady pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="c15e8-102">Node Set Navigation Using XPathNavigator</span></span>
<span data-ttu-id="c15e8-103">Můžete přejít přes uzly v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu pomocí uzlu nastavit metody navigace <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="c15e8-103">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="c15e8-104">Můžete přejít přes všechny uzly nebo přes vybraná sada uzlů, které vrátí jednu z metod výběr <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="c15e8-104">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="c15e8-105">Element uzlu sady navigace</span><span class="sxs-lookup"><span data-stu-id="c15e8-105">Element Node Set Navigation</span></span>  
 <span data-ttu-id="c15e8-106"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje několik metod používaných k přejděte uzly elementu.</span><span class="sxs-lookup"><span data-stu-id="c15e8-106">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="c15e8-107">Následující tabulka uvádí metody navigace, která je k dispozici a jak se přesouvají; popis nezahrnuje metody použité k přejděte uzly atribut a obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c15e8-107">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="c15e8-108">Další informace o výběru uzlů v <xref:System.Xml.XPath.XPathNavigator> objektu, najdete v části [zvolíte, Evaluating a porovnávání dat XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="c15e8-108">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="c15e8-109">Další informace o navigace uzly atribut a obor názvů najdete v tématu [atribut a Namespace uzlu navigace pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="c15e8-109">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="c15e8-110">Metoda</span><span class="sxs-lookup"><span data-stu-id="c15e8-110">Method</span></span>|<span data-ttu-id="c15e8-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c15e8-111">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="c15e8-112">Přesune <xref:System.Xml.XPath.XPathNavigator> na stejné pozici <xref:System.Xml.XPath.XPathNavigator> zadaný.</span><span class="sxs-lookup"><span data-stu-id="c15e8-112">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="c15e8-113">Přesune <xref:System.Xml.XPath.XPathNavigator> na aktuálním uzlu podřízený uzel.</span><span class="sxs-lookup"><span data-stu-id="c15e8-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="c15e8-114">Přesune <xref:System.Xml.XPath.XPathNavigator> na první uzel na stejné úrovni aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="c15e8-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="c15e8-115">Přesune <xref:System.Xml.XPath.XPathNavigator> na první podřízený uzel aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="c15e8-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="c15e8-116">Přesune <xref:System.Xml.XPath.XPathNavigator> na zadaný prvek v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="c15e8-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="c15e8-117">Přesune <xref:System.Xml.XPath.XPathNavigator> na uzlu, který má atribut typu `ID` s hodnotou, která odpovídá danou <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c15e8-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="c15e8-118">Přesune <xref:System.Xml.XPath.XPathNavigator> na další uzel na stejné úrovni jako aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="c15e8-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="c15e8-119">Přesune <xref:System.Xml.XPath.XPathNavigator> na nadřazený uzel aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="c15e8-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="c15e8-120">Přesune <xref:System.Xml.XPath.XPathNavigator> předchozí uzel na stejné úrovni jako aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="c15e8-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="c15e8-121">Přesune <xref:System.Xml.XPath.XPathNavigator> do kořenového uzlu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c15e8-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="c15e8-122">Komentáře a zpracování instrukcí uzlu navigace</span><span class="sxs-lookup"><span data-stu-id="c15e8-122">Comments and Processing Instruction Node Navigation</span></span>  
 <span data-ttu-id="c15e8-123">Následující <xref:System.Xml.XPath.XPathNavigator> metody třídy jsou platné pro přechod komentáře nebo zpracování pokyny z jiných uzlů v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c15e8-123">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="c15e8-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="c15e8-124">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="c15e8-125">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="c15e8-125">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="c15e8-126">Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c15e8-126">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="c15e8-127">Extrahování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c15e8-127">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="c15e8-128">Přístup k datům XML silného typu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c15e8-128">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
