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
ms.openlocfilehash: 9ac0135227599d6a72813bcf57b209705545da66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="e685b-102">Uzel navigační sady pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="e685b-102">Node Set Navigation Using XPathNavigator</span></span>
<span data-ttu-id="e685b-103">Můžete přejít přes uzly v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu pomocí uzlu nastavit metody navigace <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="e685b-103">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="e685b-104">Můžete přejít přes všechny uzly nebo přes vybraná sada uzlů, které vrátí jednu z metod výběr <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="e685b-104">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="e685b-105">Element uzlu sady navigace</span><span class="sxs-lookup"><span data-stu-id="e685b-105">Element Node Set Navigation</span></span>  
 <span data-ttu-id="e685b-106"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje několik metod používaných k přejděte uzly elementu.</span><span class="sxs-lookup"><span data-stu-id="e685b-106">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="e685b-107">Následující tabulka uvádí metody navigace, která je k dispozici a jak se přesouvají; popis nezahrnuje metody použité k přejděte uzly atribut a obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e685b-107">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="e685b-108">Další informace o výběru uzlů v <xref:System.Xml.XPath.XPathNavigator> objektu, najdete v části [zvolíte, Evaluating a porovnávání dat XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="e685b-108">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="e685b-109">Další informace o navigace uzly atribut a obor názvů najdete v tématu [atribut a Namespace uzlu navigace pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="e685b-109">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="e685b-110">Metoda</span><span class="sxs-lookup"><span data-stu-id="e685b-110">Method</span></span>|<span data-ttu-id="e685b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="e685b-111">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="e685b-112">Přesune <xref:System.Xml.XPath.XPathNavigator> na stejné pozici <xref:System.Xml.XPath.XPathNavigator> zadaný.</span><span class="sxs-lookup"><span data-stu-id="e685b-112">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="e685b-113">Přesune <xref:System.Xml.XPath.XPathNavigator> na aktuálním uzlu podřízený uzel.</span><span class="sxs-lookup"><span data-stu-id="e685b-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="e685b-114">Přesune <xref:System.Xml.XPath.XPathNavigator> na první uzel na stejné úrovni aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="e685b-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="e685b-115">Přesune <xref:System.Xml.XPath.XPathNavigator> na první podřízený uzel aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="e685b-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="e685b-116">Přesune <xref:System.Xml.XPath.XPathNavigator> na zadaný prvek v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="e685b-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="e685b-117">Přesune <xref:System.Xml.XPath.XPathNavigator> na uzlu, který má atribut typu `ID` s hodnotou, která odpovídá danou <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="e685b-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="e685b-118">Přesune <xref:System.Xml.XPath.XPathNavigator> na další uzel na stejné úrovni jako aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="e685b-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="e685b-119">Přesune <xref:System.Xml.XPath.XPathNavigator> na nadřazený uzel aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="e685b-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="e685b-120">Přesune <xref:System.Xml.XPath.XPathNavigator> předchozí uzel na stejné úrovni jako aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="e685b-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="e685b-121">Přesune <xref:System.Xml.XPath.XPathNavigator> do kořenového uzlu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="e685b-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="e685b-122">Komentáře a zpracování instrukcí uzlu navigace</span><span class="sxs-lookup"><span data-stu-id="e685b-122">Comments and Processing Instruction Node Navigation</span></span>  
 <span data-ttu-id="e685b-123">Následující <xref:System.Xml.XPath.XPathNavigator> metody třídy jsou platné pro přechod komentáře nebo zpracování pokyny z jiných uzlů v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="e685b-123">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="e685b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="e685b-124">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="e685b-125">Zpracování kódu XML dat pomocí jazyka XPath datový Model</span><span class="sxs-lookup"><span data-stu-id="e685b-125">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="e685b-126">Atribut a Namespace uzlu navigace pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="e685b-126">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="e685b-127">Extrahovat pomocí objektem XPathNavigator nastaveným na Data XML</span><span class="sxs-lookup"><span data-stu-id="e685b-127">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="e685b-128">Přístup k důrazně zadali pomocí objektem XPathNavigator nastaveným na Data XML</span><span class="sxs-lookup"><span data-stu-id="e685b-128">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
