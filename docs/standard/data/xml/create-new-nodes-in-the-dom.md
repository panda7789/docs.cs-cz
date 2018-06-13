---
title: Vytvořit nové uzly v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bbc8d6c1055afc1a0799522f341551d04bab4ace
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569301"
---
# <a name="create-new-nodes-in-the-dom"></a><span data-ttu-id="e615e-102">Vytvořit nové uzly v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="e615e-102">Create New Nodes in the DOM</span></span>
<span data-ttu-id="e615e-103"><xref:System.Xml.XmlDocument> Má metodu create pro všechny typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="e615e-103">The <xref:System.Xml.XmlDocument> has a create method for all of the node types.</span></span> <span data-ttu-id="e615e-104">Zadejte metodu s názvem vyžádání a obsah nebo jiné parametry pro uzly, u kterých se obsah (například textový uzel) a uzlu je vytvořena.</span><span class="sxs-lookup"><span data-stu-id="e615e-104">Supply the method with a name when required, and content or other parameters for those nodes that have content (for example, a text node), and the node is created.</span></span> <span data-ttu-id="e615e-105">Tyto metody jsou ty, které je třeba název a několik dalších parametrů, které jsou vyplněna můžete vytvořit příslušný uzel.</span><span class="sxs-lookup"><span data-stu-id="e615e-105">The following methods are ones that need a name and a few other parameters filled to create an appropriate node.</span></span>  
  
-   <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 <span data-ttu-id="e615e-106">Ostatní typy uzlů mají další požadavky než právě poskytuje data na parametry.</span><span class="sxs-lookup"><span data-stu-id="e615e-106">Other node types have more requirements than just providing data to parameters.</span></span>  
  
 <span data-ttu-id="e615e-107">Informace o atributech, najdete v části [vytváření nové atributy pro elementy v modelu DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="e615e-107">For information on attributes, see [Creating New Attributes for Elements in the DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span></span> <span data-ttu-id="e615e-108">Informace o ověření názvu elementu a atributu v tématu [– Element XML a ověření názvu atributu při vytváření nových uzlů](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="e615e-108">For information on element and attribute name validation, see [XML Element and Attribute Name Verification when Creating New Nodes](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span></span> <span data-ttu-id="e615e-109">Vytváření odkazy na entity, najdete v části [vytváření nové odkazy na Entity](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span><span class="sxs-lookup"><span data-stu-id="e615e-109">For creating entity references, see [Creating New Entity References](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span></span> <span data-ttu-id="e615e-110">Informace o vlivu rozšíření odkazy na entity obory názvů, v tématu [Namespace vlivu na Entity odkaz na rozšíření pro nové uzly obsahující elementy a atributy](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="e615e-110">For information on how namespaces affect the expansion of entity references, see [Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span></span>  
  
 <span data-ttu-id="e615e-111">Po vytvoření nové uzly jsou existuje několik metod, které jsou k dispozici pro vložte je do stromu.</span><span class="sxs-lookup"><span data-stu-id="e615e-111">Once new nodes are created, there are several methods available to insert them into the tree.</span></span> <span data-ttu-id="e615e-112">Tabulka uvádí metody popisem toho, kde se nový uzel objeví v XML dokumentu objektu modelu (DOM).</span><span class="sxs-lookup"><span data-stu-id="e615e-112">The table lists the methods with a description of where the new node appears in the XML Document Object Model (DOM).</span></span>  
  
|<span data-ttu-id="e615e-113">Metoda</span><span class="sxs-lookup"><span data-stu-id="e615e-113">Method</span></span>|<span data-ttu-id="e615e-114">Umístění uzlu</span><span class="sxs-lookup"><span data-stu-id="e615e-114">Node placement</span></span>|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|<span data-ttu-id="e615e-115">Vložit před uzlu odkazu.</span><span class="sxs-lookup"><span data-stu-id="e615e-115">Inserted before the reference node.</span></span> <span data-ttu-id="e615e-116">Chcete-li například vložit nový uzel v pozici 5:</span><span class="sxs-lookup"><span data-stu-id="e615e-116">For example, to insert the new node in position 5:</span></span><br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> <span data-ttu-id="e615e-117">Další informace najdete v tématu <xref:System.Xml.XmlNode.InsertBefore%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e615e-117">For more information, see the <xref:System.Xml.XmlNode.InsertBefore%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|<span data-ttu-id="e615e-118">Vložit po uzlu odkazu.</span><span class="sxs-lookup"><span data-stu-id="e615e-118">Inserted after the reference node.</span></span> <span data-ttu-id="e615e-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e615e-119">For example:</span></span><br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> <span data-ttu-id="e615e-120">Další informace najdete v tématu <xref:System.Xml.XmlNode.InsertAfter%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e615e-120">For more information, see the <xref:System.Xml.XmlNode.InsertAfter%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|<span data-ttu-id="e615e-121">Přidá na konec seznamu podřízené uzly pro daný uzel uzlu.</span><span class="sxs-lookup"><span data-stu-id="e615e-121">Adds the node to the end of the list of child nodes for the given node.</span></span> <span data-ttu-id="e615e-122">Pokud uzel, který chcete přidat je <xref:System.Xml.XmlDocumentFragment>, celý obsah dokumentu fragment přesunou do seznamu podřízené tohoto uzlu.</span><span class="sxs-lookup"><span data-stu-id="e615e-122">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="e615e-123">Další informace najdete v tématu <xref:System.Xml.XmlNode.AppendChild%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e615e-123">For more information, see the <xref:System.Xml.XmlNode.AppendChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|<span data-ttu-id="e615e-124">Přidá na začátek seznamu podřízené uzly uzlu daného uzlu.</span><span class="sxs-lookup"><span data-stu-id="e615e-124">Adds the node to the beginning of the list of child nodes of the given node.</span></span> <span data-ttu-id="e615e-125">Pokud uzel, který chcete přidat je <xref:System.Xml.XmlDocumentFragment>, celý obsah dokumentu fragment přesunou do seznamu podřízené tohoto uzlu.</span><span class="sxs-lookup"><span data-stu-id="e615e-125">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="e615e-126">Další informace najdete v tématu <xref:System.Xml.XmlNode.PrependChild%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e615e-126">For more information, see the <xref:System.Xml.XmlNode.PrependChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|<span data-ttu-id="e615e-127">Připojí <xref:System.Xml.XmlAttribute> uzlu na konec kolekce atributů, které jsou spojené s elementem.</span><span class="sxs-lookup"><span data-stu-id="e615e-127">Appends an <xref:System.Xml.XmlAttribute> node to the end of the attribute collection associated with an element.</span></span> <span data-ttu-id="e615e-128">Další informace najdete v tématu <xref:System.Xml.XmlAttributeCollection.Append%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e615e-128">For more information, see the <xref:System.Xml.XmlAttributeCollection.Append%2A> method.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e615e-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="e615e-129">See Also</span></span>  
 [<span data-ttu-id="e615e-130">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="e615e-130">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
