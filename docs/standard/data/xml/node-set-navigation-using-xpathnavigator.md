---
title: Navigace v sadě uzlů pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
ms.openlocfilehash: 91115af03b635d7660721fac5ce8bd749953e4ff
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710567"
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="3c0c9-102">Navigace v sadě uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3c0c9-102">Node Set Navigation Using XPathNavigator</span></span>
<span data-ttu-id="3c0c9-103">Můžete procházet uzly v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu pomocí uzlu, který je navigačními metodami třídy <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-103">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="3c0c9-104">Můžete přecházet přes všechny uzly nebo přes vybranou sadu uzlů vrácenou jednou z metod výběru třídy <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-104">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="3c0c9-105">Uzel elementu – nastavení navigace</span><span class="sxs-lookup"><span data-stu-id="3c0c9-105">Element Node Set Navigation</span></span>  
 <span data-ttu-id="3c0c9-106">Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje několik metod, které slouží k procházení uzlů prvků.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-106">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="3c0c9-107">V následující tabulce jsou uvedeny dostupné metody navigace a popis jejich přesunu; nezahrnuje metody používané pro navigaci v uzlech atributu a oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-107">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="3c0c9-108">Další informace o výběru uzlů v objektu <xref:System.Xml.XPath.XPathNavigator> najdete v tématu [výběr, vyhodnocení a porovnání dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="3c0c9-108">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="3c0c9-109">Další informace o navigaci v uzlech atributů a oboru názvů naleznete v tématu [navigace pomocí atributů a uzlu oboru názvů pomocí XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="3c0c9-109">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="3c0c9-110">Metoda</span><span class="sxs-lookup"><span data-stu-id="3c0c9-110">Method</span></span>|<span data-ttu-id="3c0c9-111">Popis</span><span class="sxs-lookup"><span data-stu-id="3c0c9-111">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="3c0c9-112">Přesune <xref:System.Xml.XPath.XPathNavigator> do stejné pozice <xref:System.Xml.XPath.XPathNavigator> zadaného.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-112">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="3c0c9-113">Přesune <xref:System.Xml.XPath.XPathNavigator> do podřízeného uzlu aktuálního uzlu.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="3c0c9-114">Přesune <xref:System.Xml.XPath.XPathNavigator> na první uzel na stejné úrovni jako aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="3c0c9-115">Přesune <xref:System.Xml.XPath.XPathNavigator> do prvního podřízeného uzlu aktuálního uzlu.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="3c0c9-116">Přesune <xref:System.Xml.XPath.XPathNavigator> na zadaný element v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="3c0c9-117">Přesune <xref:System.Xml.XPath.XPathNavigator> na uzel, který má atribut typu `ID` s hodnotou, která odpovídá danému <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="3c0c9-118">Přesune <xref:System.Xml.XPath.XPathNavigator> na další uzel na stejné úrovni jako aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="3c0c9-119">Přesune <xref:System.Xml.XPath.XPathNavigator> do nadřazeného uzlu aktuálního uzlu.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="3c0c9-120">Přesune <xref:System.Xml.XPath.XPathNavigator> na předchozí uzel na stejné úrovni jako aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="3c0c9-121">Přesune <xref:System.Xml.XPath.XPathNavigator> do kořenového uzlu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="3c0c9-122">Komentáře a zpracování – navigace uzlu instrukcí</span><span class="sxs-lookup"><span data-stu-id="3c0c9-122">Comments and Processing Instruction Node Navigation</span></span>  
 <span data-ttu-id="3c0c9-123">Následující metody třídy <xref:System.Xml.XPath.XPathNavigator> jsou platné pro přesun na komentáře nebo pokyny pro zpracování z jiných uzlů v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="3c0c9-123">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="3c0c9-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c0c9-124">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="3c0c9-125">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="3c0c9-125">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="3c0c9-126">Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3c0c9-126">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="3c0c9-127">Extrahování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3c0c9-127">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="3c0c9-128">Přístup k datům XML silného typu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3c0c9-128">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
