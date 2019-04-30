---
title: Vytváření nových uzlů v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 390ffa1dd9f2e76372b0e4fcbf2916918b64d748
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934599"
---
# <a name="create-new-nodes-in-the-dom"></a><span data-ttu-id="4345c-102">Vytváření nových uzlů v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="4345c-102">Create New Nodes in the DOM</span></span>
<span data-ttu-id="4345c-103"><xref:System.Xml.XmlDocument> Má vytvořit metodu pro všechny typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="4345c-103">The <xref:System.Xml.XmlDocument> has a create method for all of the node types.</span></span> <span data-ttu-id="4345c-104">Zadejte metodu s názvem v případě potřeby a obsah nebo jiné parametry pro ty uzly, které mají obsah (například textový uzel) a uzel se vytvoří.</span><span class="sxs-lookup"><span data-stu-id="4345c-104">Supply the method with a name when required, and content or other parameters for those nodes that have content (for example, a text node), and the node is created.</span></span> <span data-ttu-id="4345c-105">Jsou tyto metody těch, které je třeba název a několik dalších parametrů, které jsou vyplněny vytvořit příslušný uzel.</span><span class="sxs-lookup"><span data-stu-id="4345c-105">The following methods are ones that need a name and a few other parameters filled to create an appropriate node.</span></span>  
  
- <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
- <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
- <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
- <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
- <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
- <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
- <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
- <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
- <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
- <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
- <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 <span data-ttu-id="4345c-106">Jiné typy uzlů mají další požadavky než jenom poskytuje data pro parametry.</span><span class="sxs-lookup"><span data-stu-id="4345c-106">Other node types have more requirements than just providing data to parameters.</span></span>  
  
 <span data-ttu-id="4345c-107">Informace o atributech naleznete v tématu [vytváření nových atributů pro elementy v modelu DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="4345c-107">For information on attributes, see [Creating New Attributes for Elements in the DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span></span> <span data-ttu-id="4345c-108">Informace o ověření názvu elementu a atribut, naleznete v tématu [– Element XML a ověření názvu atributu při vytváření nových uzlů](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="4345c-108">For information on element and attribute name validation, see [XML Element and Attribute Name Verification when Creating New Nodes](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span></span> <span data-ttu-id="4345c-109">K vytváření odkazů na entity, naleznete v tématu [vytváření odkazů na nové Entity](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span><span class="sxs-lookup"><span data-stu-id="4345c-109">For creating entity references, see [Creating New Entity References](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span></span> <span data-ttu-id="4345c-110">Informace o vliv rozšíření odkazy na entity v oborech názvů najdete v tématu [Namespace vliv na rozšíření odkazu Entity pro nové uzly obsahující prvky a atributy](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="4345c-110">For information on how namespaces affect the expansion of entity references, see [Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span></span>  
  
 <span data-ttu-id="4345c-111">Po vytvoření nové uzly, existuje několik metod, které jsou k dispozici pro vložení do stromu.</span><span class="sxs-lookup"><span data-stu-id="4345c-111">Once new nodes are created, there are several methods available to insert them into the tree.</span></span> <span data-ttu-id="4345c-112">V tabulce jsou uvedeny metody s popisem toho, kde nového uzlu se zobrazuje v XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="4345c-112">The table lists the methods with a description of where the new node appears in the XML Document Object Model (DOM).</span></span>  
  
|<span data-ttu-id="4345c-113">Metoda</span><span class="sxs-lookup"><span data-stu-id="4345c-113">Method</span></span>|<span data-ttu-id="4345c-114">Umístění uzlů</span><span class="sxs-lookup"><span data-stu-id="4345c-114">Node placement</span></span>|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|<span data-ttu-id="4345c-115">Vložit před uzlu odkazu.</span><span class="sxs-lookup"><span data-stu-id="4345c-115">Inserted before the reference node.</span></span> <span data-ttu-id="4345c-116">Chcete-li například vložit nový uzel na pozici 5:</span><span class="sxs-lookup"><span data-stu-id="4345c-116">For example, to insert the new node in position 5:</span></span><br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> <span data-ttu-id="4345c-117">Další informace najdete v tématu <xref:System.Xml.XmlNode.InsertBefore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4345c-117">For more information, see the <xref:System.Xml.XmlNode.InsertBefore%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|<span data-ttu-id="4345c-118">Vkládá uzlu odkazu.</span><span class="sxs-lookup"><span data-stu-id="4345c-118">Inserted after the reference node.</span></span> <span data-ttu-id="4345c-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4345c-119">For example:</span></span><br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> <span data-ttu-id="4345c-120">Další informace najdete v tématu <xref:System.Xml.XmlNode.InsertAfter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4345c-120">For more information, see the <xref:System.Xml.XmlNode.InsertAfter%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|<span data-ttu-id="4345c-121">Uzel se přidá na konec seznamu podřízených uzlů pro daný uzel.</span><span class="sxs-lookup"><span data-stu-id="4345c-121">Adds the node to the end of the list of child nodes for the given node.</span></span> <span data-ttu-id="4345c-122">Pokud uzel přidáván, je <xref:System.Xml.XmlDocumentFragment>, celý obsah část dokumentu přesunou do seznamu podřízených tohoto uzlu.</span><span class="sxs-lookup"><span data-stu-id="4345c-122">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="4345c-123">Další informace najdete v tématu <xref:System.Xml.XmlNode.AppendChild%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4345c-123">For more information, see the <xref:System.Xml.XmlNode.AppendChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|<span data-ttu-id="4345c-124">Uzel se přidá na začátek seznamu podřízených uzlů daný uzel.</span><span class="sxs-lookup"><span data-stu-id="4345c-124">Adds the node to the beginning of the list of child nodes of the given node.</span></span> <span data-ttu-id="4345c-125">Pokud uzel přidáván, je <xref:System.Xml.XmlDocumentFragment>, celý obsah část dokumentu přesunou do seznamu podřízených tohoto uzlu.</span><span class="sxs-lookup"><span data-stu-id="4345c-125">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="4345c-126">Další informace najdete v tématu <xref:System.Xml.XmlNode.PrependChild%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4345c-126">For more information, see the <xref:System.Xml.XmlNode.PrependChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|<span data-ttu-id="4345c-127">Připojí <xref:System.Xml.XmlAttribute> uzlu na konec kolekce atributů spojených s elementem.</span><span class="sxs-lookup"><span data-stu-id="4345c-127">Appends an <xref:System.Xml.XmlAttribute> node to the end of the attribute collection associated with an element.</span></span> <span data-ttu-id="4345c-128">Další informace najdete v tématu <xref:System.Xml.XmlAttributeCollection.Append%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4345c-128">For more information, see the <xref:System.Xml.XmlAttributeCollection.Append%2A> method.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4345c-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4345c-129">See also</span></span>

- [<span data-ttu-id="4345c-130">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="4345c-130">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
