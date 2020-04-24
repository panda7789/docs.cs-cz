---
title: Vytváření nových uzlů v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
ms.openlocfilehash: f48990286405baee347becef87d0511cd42e9e77
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710996"
---
# <a name="create-new-nodes-in-the-dom"></a><span data-ttu-id="fb616-102">Vytváření nových uzlů v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="fb616-102">Create New Nodes in the DOM</span></span>
<span data-ttu-id="fb616-103"><xref:System.Xml.XmlDocument> Obsahuje metodu create pro všechny typy uzlů.</span><span class="sxs-lookup"><span data-stu-id="fb616-103">The <xref:System.Xml.XmlDocument> has a create method for all of the node types.</span></span> <span data-ttu-id="fb616-104">Poskytněte metodu s názvem v případě potřeby a obsah nebo jiné parametry pro tyto uzly, které mají obsah (například textový uzel) a uzel je vytvořen.</span><span class="sxs-lookup"><span data-stu-id="fb616-104">Supply the method with a name when required, and content or other parameters for those nodes that have content (for example, a text node), and the node is created.</span></span> <span data-ttu-id="fb616-105">Níže jsou uvedené metody, které vyžadují název a několik dalších parametrů, které mají vytvořit vhodný uzel.</span><span class="sxs-lookup"><span data-stu-id="fb616-105">The following methods are ones that need a name and a few other parameters filled to create an appropriate node.</span></span>  
  
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
  
 <span data-ttu-id="fb616-106">Jiné typy uzlů mají více požadavků, než stačí poskytnout data parametrům.</span><span class="sxs-lookup"><span data-stu-id="fb616-106">Other node types have more requirements than just providing data to parameters.</span></span>  
  
 <span data-ttu-id="fb616-107">Informace o atributech naleznete v tématu [vytváření nových atributů pro prvky v modelu DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="fb616-107">For information on attributes, see [Creating New Attributes for Elements in the DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span></span> <span data-ttu-id="fb616-108">Informace o ověřování prvků a názvů atributů naleznete v tématu [ověření názvu elementu XML a atributů při vytváření nových uzlů](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="fb616-108">For information on element and attribute name validation, see [XML Element and Attribute Name Verification when Creating New Nodes](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span></span> <span data-ttu-id="fb616-109">Informace o vytváření odkazů na entity najdete v tématu [vytváření nových odkazů na entity](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span><span class="sxs-lookup"><span data-stu-id="fb616-109">For creating entity references, see [Creating New Entity References](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span></span> <span data-ttu-id="fb616-110">Informace o tom, jak obory názvů ovlivňují rozšiřování odkazů na entity, najdete v tématu věnovaném [oboru názvů vliv na rozšíření odkazu na entity pro nové uzly obsahující prvky a atributy](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="fb616-110">For information on how namespaces affect the expansion of entity references, see [Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span></span>  
  
 <span data-ttu-id="fb616-111">Po vytvoření nových uzlů je k dispozici několik metod, které jsou k dispozici pro jejich vložení do stromu.</span><span class="sxs-lookup"><span data-stu-id="fb616-111">Once new nodes are created, there are several methods available to insert them into the tree.</span></span> <span data-ttu-id="fb616-112">V tabulce jsou uvedeny metody s popisem, kde se nový uzel zobrazuje v souboru XML model DOM (Document Object Model) (DOM).</span><span class="sxs-lookup"><span data-stu-id="fb616-112">The table lists the methods with a description of where the new node appears in the XML Document Object Model (DOM).</span></span>  
  
|<span data-ttu-id="fb616-113">Metoda</span><span class="sxs-lookup"><span data-stu-id="fb616-113">Method</span></span>|<span data-ttu-id="fb616-114">Umístění uzlu</span><span class="sxs-lookup"><span data-stu-id="fb616-114">Node placement</span></span>|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|<span data-ttu-id="fb616-115">Vloženo před referenční uzel.</span><span class="sxs-lookup"><span data-stu-id="fb616-115">Inserted before the reference node.</span></span> <span data-ttu-id="fb616-116">Například pro vložení nového uzlu na pozici 5:</span><span class="sxs-lookup"><span data-stu-id="fb616-116">For example, to insert the new node in position 5:</span></span><br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> <span data-ttu-id="fb616-117">Další informace naleznete v <xref:System.Xml.XmlNode.InsertBefore%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="fb616-117">For more information, see the <xref:System.Xml.XmlNode.InsertBefore%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|<span data-ttu-id="fb616-118">Vloženo za referenční uzel.</span><span class="sxs-lookup"><span data-stu-id="fb616-118">Inserted after the reference node.</span></span> <span data-ttu-id="fb616-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fb616-119">For example:</span></span><br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> <span data-ttu-id="fb616-120">Další informace naleznete v <xref:System.Xml.XmlNode.InsertAfter%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="fb616-120">For more information, see the <xref:System.Xml.XmlNode.InsertAfter%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|<span data-ttu-id="fb616-121">Přidá uzel na konec seznamu podřízených uzlů pro daný uzel.</span><span class="sxs-lookup"><span data-stu-id="fb616-121">Adds the node to the end of the list of child nodes for the given node.</span></span> <span data-ttu-id="fb616-122">Pokud je přidaný uzel objekt <xref:System.Xml.XmlDocumentFragment>, je celý obsah fragmentu dokumentu přesunut do podřízeného seznamu tohoto uzlu.</span><span class="sxs-lookup"><span data-stu-id="fb616-122">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="fb616-123">Další informace naleznete v <xref:System.Xml.XmlNode.AppendChild%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="fb616-123">For more information, see the <xref:System.Xml.XmlNode.AppendChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|<span data-ttu-id="fb616-124">Přidá uzel na začátek seznamu podřízených uzlů daného uzlu.</span><span class="sxs-lookup"><span data-stu-id="fb616-124">Adds the node to the beginning of the list of child nodes of the given node.</span></span> <span data-ttu-id="fb616-125">Pokud je přidaný uzel objekt <xref:System.Xml.XmlDocumentFragment>, je celý obsah fragmentu dokumentu přesunut do podřízeného seznamu tohoto uzlu.</span><span class="sxs-lookup"><span data-stu-id="fb616-125">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="fb616-126">Další informace naleznete v <xref:System.Xml.XmlNode.PrependChild%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="fb616-126">For more information, see the <xref:System.Xml.XmlNode.PrependChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|<span data-ttu-id="fb616-127">Připojí <xref:System.Xml.XmlAttribute> uzel na konec kolekce atributů přidružené k elementu.</span><span class="sxs-lookup"><span data-stu-id="fb616-127">Appends an <xref:System.Xml.XmlAttribute> node to the end of the attribute collection associated with an element.</span></span> <span data-ttu-id="fb616-128">Další informace naleznete v <xref:System.Xml.XmlAttributeCollection.Append%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="fb616-128">For more information, see the <xref:System.Xml.XmlAttributeCollection.Append%2A> method.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb616-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb616-129">See also</span></span>

- [<span data-ttu-id="fb616-130">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="fb616-130">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
