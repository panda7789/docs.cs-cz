---
title: Navigace v sadě uzlů pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58adf0251fdc7427f493e8bf9947c081bfccd2a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698814"
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="782cc-102">Navigace v sadě uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="782cc-102">Node Set Navigation Using XPathNavigator</span></span>
<span data-ttu-id="782cc-103">Můžete přejít přes uzly v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu pomocí uzel nastavení metody navigace <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="782cc-103">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="782cc-104">Můžete přejít přes všechny uzly nebo vybrané sady uzlů, které vrátí jednu z metod výběr <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="782cc-104">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="782cc-105">Navigace v sadě uzlů – element</span><span class="sxs-lookup"><span data-stu-id="782cc-105">Element Node Set Navigation</span></span>  
 <span data-ttu-id="782cc-106"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje několik metod pro pohyb mezi uzly element.</span><span class="sxs-lookup"><span data-stu-id="782cc-106">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="782cc-107">V následující tabulce jsou uvedeny navigační metody, které jsou k dispozici a jak přecházejí; popis To nezahrnuje metody použít pro účely navigace uzly atributu a oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="782cc-107">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="782cc-108">Další informace o výběru uzlů v <xref:System.Xml.XPath.XPathNavigator> objektu, najdete v článku [výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="782cc-108">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="782cc-109">Další informace o procházení atributu a oboru názvů uzlů najdete v tématu [atribut a Namespace uzlu navigace pomocí XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="782cc-109">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="782cc-110">Metoda</span><span class="sxs-lookup"><span data-stu-id="782cc-110">Method</span></span>|<span data-ttu-id="782cc-111">Popis</span><span class="sxs-lookup"><span data-stu-id="782cc-111">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="782cc-112">Přesune <xref:System.Xml.XPath.XPathNavigator> na stejné pozici <xref:System.Xml.XPath.XPathNavigator> zadané.</span><span class="sxs-lookup"><span data-stu-id="782cc-112">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="782cc-113">Přesune <xref:System.Xml.XPath.XPathNavigator> na podřízený uzel pro aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="782cc-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="782cc-114">Přesune <xref:System.Xml.XPath.XPathNavigator> do prvního uzlu na stejné úrovni pro aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="782cc-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="782cc-115">Přesune <xref:System.Xml.XPath.XPathNavigator> na první podřízený uzel pro aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="782cc-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="782cc-116">Přesune <xref:System.Xml.XPath.XPathNavigator> pro zadaný element v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="782cc-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="782cc-117">Přesune <xref:System.Xml.XPath.XPathNavigator> k uzlu, který má atribut typu `ID` s hodnotou, která odpovídá daný <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="782cc-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="782cc-118">Přesune <xref:System.Xml.XPath.XPathNavigator> k dalšímu uzlu na stejné úrovni pro aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="782cc-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="782cc-119">Přesune <xref:System.Xml.XPath.XPathNavigator> na nadřazený uzel pro aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="782cc-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="782cc-120">Přesune <xref:System.Xml.XPath.XPathNavigator> do předchozího uzlu na stejné úrovni pro aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="782cc-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="782cc-121">Přesune <xref:System.Xml.XPath.XPathNavigator> pro kořenový uzel dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="782cc-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="782cc-122">Komentáře a navigační uzel zpracování instrukcí</span><span class="sxs-lookup"><span data-stu-id="782cc-122">Comments and Processing Instruction Node Navigation</span></span>  
 <span data-ttu-id="782cc-123">Následující <xref:System.Xml.XPath.XPathNavigator> metody třídy jsou platné pro přesun do komentáře nebo zpracování pokyny z jiných uzlů v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="782cc-123">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="782cc-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="782cc-124">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="782cc-125">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="782cc-125">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="782cc-126">Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="782cc-126">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="782cc-127">Extrahování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="782cc-127">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="782cc-128">Přístup k datům XML silného typu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="782cc-128">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
