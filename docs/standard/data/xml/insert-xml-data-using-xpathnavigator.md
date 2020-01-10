---
title: Vložení dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
ms.openlocfilehash: 68c003467d837fe79d5e275968e47fa5dc3490cc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710723"
---
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="4a3a4-102">Vložení dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4a3a4-102">Insert XML Data using XPathNavigator</span></span>
<span data-ttu-id="4a3a4-103">Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje sadu metod, které slouží k vložení uzlů na stejné úrovni, podřízeného prvku a atributu v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="4a3a4-104">Aby bylo možné použít tyto metody, objekt <xref:System.Xml.XPath.XPathNavigator> musí být upravitelný, to znamená, že jeho vlastnost <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být `true`.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="4a3a4-105"><xref:System.Xml.XPath.XPathNavigator> objektů, které mohou upravovat dokument XML, jsou vytvořeny metodou <xref:System.Xml.XmlDocument.CreateNavigator%2A> třídy <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="4a3a4-106"><xref:System.Xml.XPath.XPathNavigator> objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídou jsou jen pro čtení a všechny pokusy o použití metod úprav objektu <xref:System.Xml.XPath.XPathNavigator> vytvořeného objektem <xref:System.Xml.XPath.XPathDocument> mají za následek <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="4a3a4-107">Další informace o vytváření upravitelných <xref:System.Xml.XPath.XPathNavigator> objektů naleznete v tématu [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="4a3a4-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="4a3a4-108">Vkládání uzlů</span><span class="sxs-lookup"><span data-stu-id="4a3a4-108">Inserting Nodes</span></span>  
 <span data-ttu-id="4a3a4-109">Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje metody pro vložení uzlů na stejné úrovni, podřízeného prvku a atributu v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="4a3a4-110">Tyto metody umožňují vkládat uzly a atributy v různých umístěních ve vztahu k aktuální pozici objektu <xref:System.Xml.XPath.XPathNavigator> a jsou popsány v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="4a3a4-111">Vkládání uzlů na stejné úrovni</span><span class="sxs-lookup"><span data-stu-id="4a3a4-111">Inserting Sibling Nodes</span></span>  
 <span data-ttu-id="4a3a4-112">Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje následující metody pro vložení uzlů na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="4a3a4-113">Tyto metody vloží uzly stejné úrovně před a po uzlu, na kterém je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěný.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="4a3a4-114">Metody <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> jsou přetížené a přijímají objekt `string`, <xref:System.Xml.XmlReader> nebo objekt <xref:System.Xml.XPath.XPathNavigator> obsahující uzel na stejné úrovni, který se přidá jako parametry.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="4a3a4-115">Obě metody také vracejí objekt <xref:System.Xml.XmlWriter>, který slouží k vložení uzlů na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="4a3a4-116">Metody <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> vloží jeden uzel na stejné úrovni před a po uzlu, na kterém je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěný, pomocí předpony oboru názvů, místního názvu, identifikátoru URI oboru názvů a hodnoty zadané jako parametry.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="4a3a4-117">V následujícím příkladu je vložen nový prvek `pages` před `price` podřízený prvek prvního `book` elementu v souboru `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="4a3a4-118">Příklad přebírá soubor `contosoBooks.xml` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="4a3a4-119">Další informace o <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metod naleznete v dokumentaci třídy <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="4a3a4-120">Vkládání podřízených uzlů</span><span class="sxs-lookup"><span data-stu-id="4a3a4-120">Inserting Child Nodes</span></span>  
 <span data-ttu-id="4a3a4-121">Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje následující metody pro vložení podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="4a3a4-122">Tyto metody připojí a odřadí podřízené uzly na konec a začátek seznamu podřízených uzlů uzlu, na kterém je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěný.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="4a3a4-123">Podobně jako metody v části "vložení uzlů na stejné úrovni" metody <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> přijímají `string`, objekt <xref:System.Xml.XmlReader> nebo objekt <xref:System.Xml.XPath.XPathNavigator> obsahující podřízený uzel, který chcete přidat jako parametry.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="4a3a4-124">Obě metody také vracejí objekt <xref:System.Xml.XmlWriter>, který se používá pro vložení podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="4a3a4-125">Podobně jako metody v části "vložení uzlů na stejné úrovni" metody <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> vloží jeden podřízený uzel na konec a začátek seznamu podřízených uzlů uzlu, na kterém je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěný, na základě předpony oboru názvů, místního názvu, identifikátoru URI oboru názvů a hodnoty zadané jako parametry.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="4a3a4-126">V následujícím příkladu je nový `pages` podřízený element připojen k seznamu podřízených prvků prvního prvku `book` v souboru `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="4a3a4-127">Příklad přebírá soubor `contosoBooks.xml` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="4a3a4-128">Další informace o <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metod naleznete v dokumentaci třídy <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="4a3a4-129">Vkládání uzlů atributů</span><span class="sxs-lookup"><span data-stu-id="4a3a4-129">Inserting Attribute Nodes</span></span>  
 <span data-ttu-id="4a3a4-130">Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje následující metody pro vkládání uzlů atributů.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="4a3a4-131">Tyto metody vkládají uzly atributů na uzel elementu, kde je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěný.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="4a3a4-132">Metoda <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> vytvoří uzel atributu v uzlu element. objekt <xref:System.Xml.XPath.XPathNavigator> je aktuálně umístěn na základě předpony oboru názvů, místního názvu, identifikátoru URI oboru názvů a hodnoty zadané jako parametry.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="4a3a4-133">Metoda <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> vrátí objekt <xref:System.Xml.XmlWriter>, který se používá pro vložení uzlů atributu.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="4a3a4-134">V následujícím příkladu jsou vytvořeny nové `discount` a `currency` atributy v `price` podřízený prvek prvního `book` prvku v souboru `contosoBooks.xml` pomocí objektu <xref:System.Xml.XmlWriter> vráceného z metody <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="4a3a4-135">Příklad přebírá soubor `contosoBooks.xml` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="4a3a4-136">Další informace o metodách <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> a <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> naleznete v dokumentaci třídy <xref:System.Xml.XPath.XPathNavigator> reference.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="4a3a4-137">Kopírování uzlů</span><span class="sxs-lookup"><span data-stu-id="4a3a4-137">Copying Nodes</span></span>  
 <span data-ttu-id="4a3a4-138">V některých případech může být vhodné naplnit dokument XML obsahem z jiného dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="4a3a4-139">Třída <xref:System.Xml.XPath.XPathNavigator> i třída <xref:System.Xml.XmlWriter> mohou kopírovat uzly do objektu <xref:System.Xml.XmlDocument> z existujícího objektu <xref:System.Xml.XmlReader> nebo objektu <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="4a3a4-140"><xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> metody třídy <xref:System.Xml.XPath.XPathNavigator> mají přetížení, které mohou přijmout objekt <xref:System.Xml.XPath.XPathNavigator> nebo objekt <xref:System.Xml.XmlReader> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="4a3a4-141">Metoda <xref:System.Xml.XmlWriter.WriteNode%2A> třídy <xref:System.Xml.XmlWriter> má přetížení, které může přijmout objekt <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>nebo <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="4a3a4-142">Následující příklad zkopíruje všechny prvky `book` z jednoho dokumentu do druhého.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
  
Dim newBooks As XPathDocument = New XPathDocument("newBooks.xml")  
Dim newBooksNavigator As XPathNavigator = newBooks.CreateNavigator()  
  
Dim nav As XPathNavigator  
For Each nav in newBooksNavigator.SelectDescendants("book", "", false)  
    navigator.AppendChild(nav)  
Next  
  
document.Save("newBooks.xml");  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
  
XPathDocument newBooks = new XPathDocument("newBooks.xml");  
XPathNavigator newBooksNavigator = newBooks.CreateNavigator();  
  
foreach (XPathNavigator nav in newBooksNavigator.SelectDescendants("book", "", false))  
{  
    navigator.AppendChild(nav);  
}  
  
document.Save("newBooks.xml");  
```  
  
## <a name="inserting-values"></a><span data-ttu-id="4a3a4-143">Vkládání hodnot</span><span class="sxs-lookup"><span data-stu-id="4a3a4-143">Inserting Values</span></span>  
 <span data-ttu-id="4a3a4-144">Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> pro vkládání hodnot pro uzel do objektu <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="4a3a4-145">Vkládání netypových hodnot</span><span class="sxs-lookup"><span data-stu-id="4a3a4-145">Inserting Untyped Values</span></span>  
 <span data-ttu-id="4a3a4-146">Metoda <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> jednoduše vloží Netypový `string` hodnotu předanou jako parametr jako hodnotu uzlu, na kterém je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěný.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="4a3a4-147">Hodnota je vložena bez jakéhokoli typu nebo bez ověření, že nová hodnota je platná podle typu uzlu, pokud jsou k dispozici informace o schématu.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="4a3a4-148">V následujícím příkladu je použita metoda <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> k aktualizaci všech prvků `price` v souboru `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="4a3a4-149">Příklad přebírá soubor `contosoBooks.xml` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="4a3a4-150">Vkládání zadaných hodnot</span><span class="sxs-lookup"><span data-stu-id="4a3a4-150">Inserting Typed Values</span></span>  
 <span data-ttu-id="4a3a4-151">Pokud je typ uzlu jednoduchý typ schématu W3C XML, je nová hodnota vložená metodou <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> zkontrolována proti omezující vlastnosti jednoduchého typu před nastavením hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="4a3a4-152">Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnoty `-1` u elementu, jehož typ je `xs:positiveInteger`), výsledkem bude výjimka.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="4a3a4-153">Následující příklad se pokusí změnit hodnotu prvku `price` prvního prvku `book` v souboru `contosoBooks.xml` na <xref:System.DateTime>ou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="4a3a4-154">Vzhledem k tomu, že typ schématu XML prvku `price` je definován jako `xs:decimal` v souborech `contosoBooks.xsd`, výsledkem je výjimka.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 <span data-ttu-id="4a3a4-155">Příklad přebírá soubor `contosoBooks.xml` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="4a3a4-156">Příklad také přebírá `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="4a3a4-157">Vlastnosti InnerXml a OuterXml</span><span class="sxs-lookup"><span data-stu-id="4a3a4-157">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="4a3a4-158">Vlastnosti <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> třídy <xref:System.Xml.XPath.XPathNavigator> mění kód XML uzlů, na kterých je objekt <xref:System.Xml.XPath.XPathNavigator> aktuálně umístěn.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="4a3a4-159">Vlastnost <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> změní kód XML podřízených uzlů, na kterých je aktuálně umístěn <xref:System.Xml.XPath.XPathNavigator> objekt, který obsahuje analyzovaný obsah daného XML `string`.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="4a3a4-160">Podobně vlastnost <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> mění kód XML podřízených uzlů, na kterých je aktuálně umístěn <xref:System.Xml.XPath.XPathNavigator> objekt a také na samotném aktuálním uzlu.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="4a3a4-161">Kromě metod popsaných v tomto tématu, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastností lze použít k vložení uzlů a hodnot do dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="4a3a4-162">Další informace o použití <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastností pro vkládání uzlů a hodnot naleznete v tématu [Úprava dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="4a3a4-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="4a3a4-163">Namespaces and XML: lang – konflikty</span><span class="sxs-lookup"><span data-stu-id="4a3a4-163">Namespace and xml:lang Conflicts</span></span>  
 <span data-ttu-id="4a3a4-164">Při vkládání dat XML pomocí <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>ch metod třídy <xref:System.Xml.XPath.XPathNavigator>, které jako parametry přebírají <xref:System.Xml.XmlReader> objekty, může dojít k určitým konfliktům souvisejícím s oborem oboru názvů a `xml:lang` deklarací.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="4a3a4-165">Níže jsou uvedené možné konflikty oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-165">The following are the possible namespace conflicts.</span></span>  
  
- <span data-ttu-id="4a3a4-166">Pokud je obor názvů v oboru v kontextu <xref:System.Xml.XmlReader>ho objektu, kde předpona na mapování identifikátoru URI oboru názvů není v kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, je do nově vloženého uzlu přidána deklarace nového oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="4a3a4-167">Pokud je stejný identifikátor URI oboru názvů v rámci kontextu objektu <xref:System.Xml.XmlReader> a kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, ale v obou kontextech je namapovaný jiný prefix, nová deklarace oboru názvů je přidána do nově vloženého uzlu s předponou a identifikátorem URI oboru názvů provedenými z objektu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="4a3a4-168">Je-li stejná předpona oboru názvů v rámci kontextu objektu <xref:System.Xml.XmlReader> a kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, ale má v obou kontextech namapován jiný identifikátor URI oboru názvů, nová deklarace oboru názvů je přidána do nově vloženého uzlu, který znovu deklaruje tuto předponu s identifikátorem URI oboru názvů provedeným z objektu <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="4a3a4-169">Pokud je předpona i identifikátor URI oboru názvů jak v kontextu objektu <xref:System.Xml.XmlReader>, tak v kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, do nově vloženého uzlu není přidána žádná nová deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a3a4-170">Výše uvedený popis platí také pro deklarace oboru názvů s prázdným `string` jako předponu (například výchozí deklarace oboru názvů).</span><span class="sxs-lookup"><span data-stu-id="4a3a4-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="4a3a4-171">Níže jsou uvedené možné konflikty `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
- <span data-ttu-id="4a3a4-172">Pokud je atribut `xml:lang` v oboru v rámci kontextu <xref:System.Xml.XmlReader> objektu, ale ne v kontextu objektu <xref:System.Xml.XPath.XPathNavigator>, atribut `xml:lang`, jehož hodnota je předávána z objektu <xref:System.Xml.XmlReader>, je přidán do nově vloženého uzlu.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="4a3a4-173">Pokud existuje atribut `xml:lang` v oboru v kontextu <xref:System.Xml.XmlReader> objektu a kontextu objektu <xref:System.Xml.XPath.XPathNavigator>, ale každá má jinou hodnotu, atribut `xml:lang`, jehož hodnota je předávána z objektu <xref:System.Xml.XmlReader>, je přidána do nově vloženého uzlu.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="4a3a4-174">Pokud existuje atribut `xml:lang` v oboru v kontextu <xref:System.Xml.XmlReader> objektu a kontextu objektu <xref:System.Xml.XPath.XPathNavigator>, ale každý se stejnou hodnotou, není do nově vloženého uzlu přidán žádný nový atribut `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
- <span data-ttu-id="4a3a4-175">Pokud v kontextu <xref:System.Xml.XPath.XPathNavigator> objektu existuje atribut `xml:lang` v oboru, ale žádná existující v kontextu objektu <xref:System.Xml.XmlReader>, není do nově vloženého uzlu přidána žádná `xml:lang` atributu.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="4a3a4-176">Vkládání uzlů pomocí XmlWriter</span><span class="sxs-lookup"><span data-stu-id="4a3a4-176">Inserting Nodes with XmlWriter</span></span>  
 <span data-ttu-id="4a3a4-177">Metody použité pro vložení uzlů na stejné úrovni, podřízené a atributy popsané v části vkládání uzlů a hodnot jsou přetíženy.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="4a3a4-178">Metody <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> a <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> třídy <xref:System.Xml.XPath.XPathNavigator> vrátí objekt <xref:System.Xml.XmlWriter>, který se používá pro vkládání uzlů.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="4a3a4-179">Nepodporované metody XmlWriter</span><span class="sxs-lookup"><span data-stu-id="4a3a4-179">Unsupported XmlWriter Methods</span></span>  
 <span data-ttu-id="4a3a4-180">Ne všechny metody, které jsou použity pro zápis informací do dokumentu XML pomocí třídy <xref:System.Xml.XmlWriter>, jsou podporovány třídou <xref:System.Xml.XPath.XPathNavigator> z důvodu rozdílu mezi datovým modelem XPath a model DOM (Document Object Model) (DOM).</span><span class="sxs-lookup"><span data-stu-id="4a3a4-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="4a3a4-181">Následující tabulka popisuje metody třídy <xref:System.Xml.XmlWriter>, které nejsou podporovány třídou <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="4a3a4-182">Metoda</span><span class="sxs-lookup"><span data-stu-id="4a3a4-182">Method</span></span>|<span data-ttu-id="4a3a4-183">Popis</span><span class="sxs-lookup"><span data-stu-id="4a3a4-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="4a3a4-184">Vyvolá výjimku <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="4a3a4-185">Ignoruje se na kořenové úrovni a vyvolá výjimku <xref:System.NotSupportedException>, pokud je volána na jakékoli jiné úrovni dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="4a3a4-186">Je považována za volání metody <xref:System.Xml.XmlWriter.WriteString%2A> pro ekvivalentní znak nebo znaky.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="4a3a4-187">Je považována za volání metody <xref:System.Xml.XmlWriter.WriteString%2A> pro ekvivalentní znak nebo znaky.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="4a3a4-188">Je považována za volání metody <xref:System.Xml.XmlWriter.WriteString%2A> pro ekvivalentní znak nebo znaky.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="4a3a4-189">Další informace o třídě <xref:System.Xml.XmlWriter> naleznete v referenční dokumentaci třídy <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="4a3a4-190">Více objektů XmlWriter</span><span class="sxs-lookup"><span data-stu-id="4a3a4-190">Multiple XmlWriter Objects</span></span>  
 <span data-ttu-id="4a3a4-191">Je možné mít více <xref:System.Xml.XPath.XPathNavigator> objektů odkazujících na různé části dokumentu XML s jedním nebo více otevřenými objekty <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="4a3a4-192">Ve scénářích s jedním vláknem je povoleno a podporováno více objektů <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="4a3a4-193">V následujícím seznamu jsou důležité poznámky, které je potřeba vzít v úvahu při používání více <xref:System.Xml.XmlWriter> objektů.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
- <span data-ttu-id="4a3a4-194">Fragmenty XML napsané <xref:System.Xml.XmlWriter> objekty jsou přidány do dokumentu XML při volání metody <xref:System.Xml.XmlWriter.Close%2A> každého objektu <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="4a3a4-195">Až do tohoto okamžiku, objekt <xref:System.Xml.XmlWriter> zapisuje odpojený fragment.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="4a3a4-196">Pokud je operace provedena v dokumentu XML, nebudou ovlivněny všechny fragmenty, které jsou zapsány objektem <xref:System.Xml.XmlWriter> před voláním <xref:System.Xml.XmlWriter.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
- <span data-ttu-id="4a3a4-197">Pokud je otevřený objekt <xref:System.Xml.XmlWriter> v konkrétním podstromu XML a tento podstrom je odstraněn, může být objekt <xref:System.Xml.XmlWriter> stále přidán do podstromu.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="4a3a4-198">Podstrom se jednoduše odstraněný fragmentem.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-198">The subtree simply becomes a deleted fragment.</span></span>  
  
- <span data-ttu-id="4a3a4-199">Pokud je v dokumentu XML otevřeno více objektů <xref:System.Xml.XmlWriter>, jsou přidány do dokumentu XML v pořadí, ve kterém byly objekty <xref:System.Xml.XmlWriter> uzavřeny, nikoli v pořadí, ve kterém byly otevřeny.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="4a3a4-200">Následující příklad vytvoří objekt <xref:System.Xml.XmlDocument>, vytvoří objekt <xref:System.Xml.XPath.XPathNavigator> a poté pomocí objektu <xref:System.Xml.XmlWriter> vráceného metodou <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> vytvoří strukturu první knihy v souboru `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="4a3a4-201">Příklad ho uloží jako soubor `book.xml`.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-201">The example then saves it as the `book.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Using writer As XmlWriter = navigator.PrependChild()  
  
    writer.WriteStartElement("bookstore")  
    writer.WriteStartElement("book")  
    writer.WriteAttributeString("genre", "autobiography")  
    writer.WriteAttributeString("publicationdate", "1981-03-22")  
    writer.WriteAttributeString("ISBN", "1-861003-11-0")  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin")  
    writer.WriteStartElement("author")  
    writer.WriteElementString("first-name", "Benjamin")  
    writer.WriteElementString("last-name", "Franklin")  
    writer.WriteElementString("price", "8.99")  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
  
End Using  
  
document.Save("book.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
XPathNavigator navigator = document.CreateNavigator();  
  
using (XmlWriter writer = navigator.PrependChild())  
{  
    writer.WriteStartElement("bookstore");  
    writer.WriteStartElement("book");  
    writer.WriteAttributeString("genre", "autobiography");  
    writer.WriteAttributeString("publicationdate", "1981-03-22");  
    writer.WriteAttributeString("ISBN", "1-861003-11-0");  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin");  
    writer.WriteStartElement("author");  
    writer.WriteElementString("first-name", "Benjamin");  
    writer.WriteElementString("last-name", "Franklin");  
    writer.WriteElementString("price", "8.99");  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
}  
document.Save("book.xml");  
```  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="4a3a4-202">Uložení dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="4a3a4-202">Saving an XML Document</span></span>  
 <span data-ttu-id="4a3a4-203">Uložení změn provedených v objektu <xref:System.Xml.XmlDocument> jako výsledek metod popsaných v tomto tématu se provádí pomocí metod <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="4a3a4-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="4a3a4-204">Další informace o uložení změn provedených v objektu <xref:System.Xml.XmlDocument> naleznete v tématu [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="4a3a4-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a3a4-205">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a3a4-205">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="4a3a4-206">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="4a3a4-206">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="4a3a4-207">Změna dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4a3a4-207">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="4a3a4-208">Odebrání dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4a3a4-208">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
