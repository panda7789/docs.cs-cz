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
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="2841b-102">Vložení dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="2841b-102">Insert XML Data using XPathNavigator</span></span>
<span data-ttu-id="2841b-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které slouží k vložení uzlů na stejné úrovni, podřízeného prvku a atributu v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="2841b-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="2841b-104">Aby bylo možné tyto metody použít, musí <xref:System.Xml.XPath.XPathNavigator> být objekt upravitelný, to znamená, že <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> jeho vlastnost musí `true`být.</span><span class="sxs-lookup"><span data-stu-id="2841b-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="2841b-105"><xref:System.Xml.XPath.XPathNavigator>objekty, které mohou upravovat dokument XML, jsou vytvořeny <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodou <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="2841b-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="2841b-106"><xref:System.Xml.XPath.XPathNavigator>objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídou jsou jen pro čtení a všechny pokusy o použití metod úprav <xref:System.Xml.XPath.XPathNavigator> objektu vytvořeného <xref:System.Xml.XPath.XPathDocument> objektem mají za následek. <xref:System.NotSupportedException></span><span class="sxs-lookup"><span data-stu-id="2841b-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="2841b-107">Další informace o vytváření upravitelných <xref:System.Xml.XPath.XPathNavigator> objektů najdete v tématu [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="2841b-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="2841b-108">Vkládání uzlů</span><span class="sxs-lookup"><span data-stu-id="2841b-108">Inserting Nodes</span></span>  
 <span data-ttu-id="2841b-109"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje metody pro vložení uzlů na stejné úrovni, podřízeného prvku a atributu v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="2841b-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="2841b-110">Tyto metody umožňují vkládat uzly a atributy v různých umístěních ve vztahu k aktuální pozici <xref:System.Xml.XPath.XPathNavigator> objektu a jsou popsány v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="2841b-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="2841b-111">Vkládání uzlů na stejné úrovni</span><span class="sxs-lookup"><span data-stu-id="2841b-111">Inserting Sibling Nodes</span></span>  
 <span data-ttu-id="2841b-112"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody pro vložení uzlů na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="2841b-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="2841b-113">Tyto metody vloží uzly stejné úrovně před a za uzlem <xref:System.Xml.XPath.XPathNavigator> , na kterém je objekt aktuálně umístěný.</span><span class="sxs-lookup"><span data-stu-id="2841b-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="2841b-114">Metody <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> jsou přetížené a přijímají `string` <xref:System.Xml.XmlReader> objekt, objekt nebo <xref:System.Xml.XPath.XPathNavigator> objekt obsahující uzel na stejné úrovni, který se přidá jako parametry.</span><span class="sxs-lookup"><span data-stu-id="2841b-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="2841b-115">Obě metody také vracejí <xref:System.Xml.XmlWriter> objekt, který slouží k vložení uzlů na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="2841b-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="2841b-116">Metody <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> vkládají jeden uzel na stejné úrovni před a po uzlu, na <xref:System.Xml.XPath.XPathNavigator> kterém je objekt aktuálně umístěný, pomocí předpony oboru názvů, místního názvu, identifikátoru URI oboru názvů a hodnoty zadané jako parametry.</span><span class="sxs-lookup"><span data-stu-id="2841b-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="2841b-117">`pages` V následujícím příkladu je nový prvek vložen před `price` podřízený prvek prvního `book` prvku v `contosoBooks.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="2841b-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="2841b-118">Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="2841b-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="2841b-119">Další informace o metodách <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> naleznete v referenční dokumentaci <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="2841b-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="2841b-120">Vkládání podřízených uzlů</span><span class="sxs-lookup"><span data-stu-id="2841b-120">Inserting Child Nodes</span></span>  
 <span data-ttu-id="2841b-121"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody pro vložení podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="2841b-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="2841b-122">Tyto metody připojí a odřadí podřízené uzly na konec a začátek seznamu podřízených uzlů uzlu, na kterém je <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěn.</span><span class="sxs-lookup"><span data-stu-id="2841b-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="2841b-123">Podobně jako metody v části "vložení uzlů stejné úrovně", metody <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> přijímají `string`, <xref:System.Xml.XmlReader> objekt nebo <xref:System.Xml.XPath.XPathNavigator> objekt, který obsahuje podřízený uzel, který chcete přidat jako parametry.</span><span class="sxs-lookup"><span data-stu-id="2841b-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="2841b-124">Obě metody také vracejí <xref:System.Xml.XmlWriter> objekt, který slouží k vložení podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="2841b-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="2841b-125">Stejně jako metody v části "vložení uzlů stejné úrovně", metody <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> vkládají jeden podřízený uzel na konec a začátek seznamu podřízených uzlů uzlu, na kterém je <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný, pomocí předpony oboru názvů, místního názvu, identifikátoru URI oboru názvů a hodnoty zadané jako parametry.</span><span class="sxs-lookup"><span data-stu-id="2841b-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="2841b-126">V následujícím příkladu je nový `pages` podřízený element připojen do seznamu podřízených prvků prvního `book` prvku v `contosoBooks.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="2841b-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="2841b-127">Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="2841b-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="2841b-128">Další informace o metodách <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> naleznete v referenční dokumentaci <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="2841b-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="2841b-129">Vkládání uzlů atributů</span><span class="sxs-lookup"><span data-stu-id="2841b-129">Inserting Attribute Nodes</span></span>  
 <span data-ttu-id="2841b-130"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody pro vložení uzlů atributů.</span><span class="sxs-lookup"><span data-stu-id="2841b-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="2841b-131">Tyto metody vkládají uzly atributů v uzlu element, na <xref:System.Xml.XPath.XPathNavigator> kterém je objekt aktuálně umístěný.</span><span class="sxs-lookup"><span data-stu-id="2841b-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="2841b-132"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda vytvoří uzel atributu v uzlu element a <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na základě předpony oboru názvů, místního názvu, identifikátoru URI oboru názvů a hodnoty zadané jako parametry.</span><span class="sxs-lookup"><span data-stu-id="2841b-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="2841b-133"><xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda vrátí <xref:System.Xml.XmlWriter> objekt použitý pro vložení uzlů atributu.</span><span class="sxs-lookup"><span data-stu-id="2841b-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="2841b-134">V následujícím příkladu jsou vytvořeny nové `discount` a `currency` atributy `price` v podřízeném prvku `book` prvního prvku v `contosoBooks.xml` souboru pomocí <xref:System.Xml.XmlWriter> objektu vráceného z <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2841b-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="2841b-135">Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="2841b-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="2841b-136">Další informace o metodách <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> a <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> naleznete v <xref:System.Xml.XPath.XPathNavigator> referenční dokumentaci třídy.</span><span class="sxs-lookup"><span data-stu-id="2841b-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="2841b-137">Kopírování uzlů</span><span class="sxs-lookup"><span data-stu-id="2841b-137">Copying Nodes</span></span>  
 <span data-ttu-id="2841b-138">V některých případech může být vhodné naplnit dokument XML obsahem z jiného dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="2841b-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="2841b-139"><xref:System.Xml.XPath.XPathNavigator> Třída i <xref:System.Xml.XmlWriter> třída mohou kopírovat uzly do <xref:System.Xml.XmlDocument> objektu z existujícího <xref:System.Xml.XmlReader> objektu nebo <xref:System.Xml.XPath.XPathNavigator> objektu.</span><span class="sxs-lookup"><span data-stu-id="2841b-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="2841b-140">Metody <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> a <xref:System.Xml.XPath.XPathNavigator> třídy All mají přetížení, které mohou přijmout <xref:System.Xml.XPath.XPathNavigator> objekt nebo <xref:System.Xml.XmlReader> objekt jako parametr.</span><span class="sxs-lookup"><span data-stu-id="2841b-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="2841b-141"><xref:System.Xml.XmlWriter.WriteNode%2A> Metoda <xref:System.Xml.XmlWriter> třídy má přetížení, které může přijmout objekt <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>nebo. <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="2841b-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="2841b-142">Následující příklad zkopíruje všechny `book` prvky z jednoho dokumentu do druhého.</span><span class="sxs-lookup"><span data-stu-id="2841b-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
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
  
## <a name="inserting-values"></a><span data-ttu-id="2841b-143">Vkládání hodnot</span><span class="sxs-lookup"><span data-stu-id="2841b-143">Inserting Values</span></span>  
 <span data-ttu-id="2841b-144"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> pro vkládání hodnot pro uzel do <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="2841b-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="2841b-145">Vkládání netypových hodnot</span><span class="sxs-lookup"><span data-stu-id="2841b-145">Inserting Untyped Values</span></span>  
 <span data-ttu-id="2841b-146"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` hodnoty předané jako parametr jako hodnotu uzlu, na kterém <xref:System.Xml.XPath.XPathNavigator> je objekt aktuálně umístěn.</span><span class="sxs-lookup"><span data-stu-id="2841b-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="2841b-147">Hodnota je vložena bez jakéhokoli typu nebo bez ověření, že nová hodnota je platná podle typu uzlu, pokud jsou k dispozici informace o schématu.</span><span class="sxs-lookup"><span data-stu-id="2841b-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="2841b-148">V následujícím příkladu je <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda použita k aktualizaci všech `price` prvků v `contosoBooks.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="2841b-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="2841b-149">Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="2841b-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="2841b-150">Vkládání zadaných hodnot</span><span class="sxs-lookup"><span data-stu-id="2841b-150">Inserting Typed Values</span></span>  
 <span data-ttu-id="2841b-151">Pokud je typ uzlu jednoduchý typ schématu W3C XML, je nová hodnota vložená <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodou zkontrolována proti omezující vlastnosti jednoduchého typu před nastavením hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2841b-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="2841b-152">Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnoty `-1` na elementu, jehož typ je `xs:positiveInteger`), výsledkem je výjimka.</span><span class="sxs-lookup"><span data-stu-id="2841b-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="2841b-153">Následující příklad `price` se pokusí změnit hodnotu prvku prvního `book` prvku v `contosoBooks.xml` souboru na <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2841b-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="2841b-154">Vzhledem k tomu, že typ schématu `price` XML elementu je definován `xs:decimal` jako v `contosoBooks.xsd` souborech, výsledkem je výjimka.</span><span class="sxs-lookup"><span data-stu-id="2841b-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="2841b-155">Tento příklad přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="2841b-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="2841b-156">Příklad také přebírá `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="2841b-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="2841b-157">Vlastnosti InnerXml a OuterXml</span><span class="sxs-lookup"><span data-stu-id="2841b-157">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="2841b-158">Vlastnosti <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator> třídy <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> a třídy mění kód XML uzlů, na kterých je objekt aktuálně umístěn.</span><span class="sxs-lookup"><span data-stu-id="2841b-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="2841b-159"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Vlastnost změní kód XML podřízených uzlů, na kterých je <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěn, s analyzovaným obsahem daného XML `string`.</span><span class="sxs-lookup"><span data-stu-id="2841b-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="2841b-160">Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost mění kód XML podřízených uzlů, na kterých je <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěn, i v samotném aktuálním uzlu.</span><span class="sxs-lookup"><span data-stu-id="2841b-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="2841b-161">Kromě metod popsaných v tomto tématu lze vlastnosti <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> použít k vložení uzlů a hodnot v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="2841b-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="2841b-162">Další informace o použití vlastností <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> k vložení uzlů a hodnot naleznete v tématu [Úprava dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="2841b-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="2841b-163">Namespaces and XML: lang – konflikty</span><span class="sxs-lookup"><span data-stu-id="2841b-163">Namespace and xml:lang Conflicts</span></span>  
 <span data-ttu-id="2841b-164">Některé konflikty související s rozsahem oboru názvů a `xml:lang` deklarace mohou nastat při vkládání dat XML pomocí metod <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator> třídy, které přebírají <xref:System.Xml.XmlReader> objekty jako parametry.</span><span class="sxs-lookup"><span data-stu-id="2841b-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="2841b-165">Níže jsou uvedené možné konflikty oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2841b-165">The following are the possible namespace conflicts.</span></span>  
  
- <span data-ttu-id="2841b-166">Pokud v kontextu <xref:System.Xml.XmlReader> objektu existuje obor názvů v oboru, kde předpona na mapování identifikátoru URI oboru názvů není v kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, je přidána nová deklarace oboru názvů do nově vloženého uzlu.</span><span class="sxs-lookup"><span data-stu-id="2841b-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="2841b-167">Pokud je stejný identifikátor URI oboru názvů v rámci kontextu <xref:System.Xml.XmlReader> objektu i kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, ale má v obou kontextech mapována jiná předpona, nová deklarace oboru názvů je přidána do nově vloženého uzlu s předponou a identifikátorem URI oboru názvů provedeným z <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="2841b-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="2841b-168">Pokud je stejná předpona oboru názvů v rámci kontextu <xref:System.Xml.XmlReader> objektu i kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, ale má v obou KONTEXTECH mapován jiný identifikátor URI oboru názvů, nová deklarace oboru názvů je přidána do nově vloženého uzlu, který znovu deklaruje tuto předponu s identifikátorem URI oboru názvů provedeným z <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="2841b-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="2841b-169">Pokud je předpona a také identifikátor URI oboru názvů v kontextu <xref:System.Xml.XmlReader> objektu i kontext <xref:System.Xml.XPath.XPathNavigator> objektu stejný, není do nově vloženého uzlu přidána žádná nová deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2841b-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2841b-170">Výše uvedený popis platí také pro deklarace oboru názvů s prázdným `string` argumentem jako předponu (například výchozí deklarace oboru názvů).</span><span class="sxs-lookup"><span data-stu-id="2841b-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="2841b-171">Níže jsou uvedené možné `xml:lang` konflikty.</span><span class="sxs-lookup"><span data-stu-id="2841b-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
- <span data-ttu-id="2841b-172">Pokud `xml:lang` existuje atribut v oboru v kontextu <xref:System.Xml.XmlReader> objektu, ale ne v kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, je `xml:lang` atribut, jehož hodnota je převedena z <xref:System.Xml.XmlReader> objektu, přidán do nově vloženého uzlu.</span><span class="sxs-lookup"><span data-stu-id="2841b-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="2841b-173">Pokud `xml:lang` existuje atribut v oboru v kontextu <xref:System.Xml.XmlReader> objektu i kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, ale každý má jinou hodnotu, `xml:lang` atribut, jehož hodnota je převedena z <xref:System.Xml.XmlReader> objektu, je přidán do nově vloženého uzlu.</span><span class="sxs-lookup"><span data-stu-id="2841b-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="2841b-174">Pokud existuje `xml:lang` atribut v oboru v kontextu <xref:System.Xml.XmlReader> objektu i kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, ale každý se stejnou hodnotou, není do nově vloženého uzlu přidán žádný nový `xml:lang` atribut.</span><span class="sxs-lookup"><span data-stu-id="2841b-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
- <span data-ttu-id="2841b-175">Pokud existuje `xml:lang` atribut v oboru v kontextu <xref:System.Xml.XPath.XPathNavigator> objektu, ale žádný existující v kontextu <xref:System.Xml.XmlReader> objektu, není do nově vloženého uzlu přidán žádný `xml:lang` atribut.</span><span class="sxs-lookup"><span data-stu-id="2841b-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="2841b-176">Vkládání uzlů pomocí XmlWriter</span><span class="sxs-lookup"><span data-stu-id="2841b-176">Inserting Nodes with XmlWriter</span></span>  
 <span data-ttu-id="2841b-177">Metody použité pro vložení uzlů na stejné úrovni, podřízené a atributy popsané v části vkládání uzlů a hodnot jsou přetíženy.</span><span class="sxs-lookup"><span data-stu-id="2841b-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="2841b-178">Metody <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> a <xref:System.Xml.XPath.XPathNavigator> třídy vracejí <xref:System.Xml.XmlWriter> objekt, který se používá pro vkládání uzlů.</span><span class="sxs-lookup"><span data-stu-id="2841b-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="2841b-179">Nepodporované metody XmlWriter</span><span class="sxs-lookup"><span data-stu-id="2841b-179">Unsupported XmlWriter Methods</span></span>  
 <span data-ttu-id="2841b-180">Ne všechny metody použité pro zápis informací do dokumentu XML pomocí <xref:System.Xml.XmlWriter> třídy jsou podporovány <xref:System.Xml.XPath.XPathNavigator> třídou z důvodu rozdílu mezi datovým modelem XPath a model DOM (Document Object Model) (DOM).</span><span class="sxs-lookup"><span data-stu-id="2841b-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="2841b-181">Následující tabulka popisuje metody <xref:System.Xml.XmlWriter> třídy, které <xref:System.Xml.XPath.XPathNavigator> Třída nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="2841b-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="2841b-182">Metoda</span><span class="sxs-lookup"><span data-stu-id="2841b-182">Method</span></span>|<span data-ttu-id="2841b-183">Popis</span><span class="sxs-lookup"><span data-stu-id="2841b-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="2841b-184">Vyvolá <xref:System.NotSupportedException> výjimku.</span><span class="sxs-lookup"><span data-stu-id="2841b-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="2841b-185">Ignoruje se na kořenové úrovni a vyvolá <xref:System.NotSupportedException> výjimku, pokud je volána na jakékoli jiné úrovni dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="2841b-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="2841b-186">Považuje se za volání <xref:System.Xml.XmlWriter.WriteString%2A> metody pro ekvivalentní znak nebo znaky.</span><span class="sxs-lookup"><span data-stu-id="2841b-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="2841b-187">Považuje se za volání <xref:System.Xml.XmlWriter.WriteString%2A> metody pro ekvivalentní znak nebo znaky.</span><span class="sxs-lookup"><span data-stu-id="2841b-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="2841b-188">Považuje se za volání <xref:System.Xml.XmlWriter.WriteString%2A> metody pro ekvivalentní znak nebo znaky.</span><span class="sxs-lookup"><span data-stu-id="2841b-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="2841b-189">Další informace o <xref:System.Xml.XmlWriter> třídě naleznete v <xref:System.Xml.XmlWriter> referenční dokumentaci třídy.</span><span class="sxs-lookup"><span data-stu-id="2841b-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="2841b-190">Více objektů XmlWriter</span><span class="sxs-lookup"><span data-stu-id="2841b-190">Multiple XmlWriter Objects</span></span>  
 <span data-ttu-id="2841b-191">Je možné mít více <xref:System.Xml.XPath.XPathNavigator> objektů odkazujících na různé části dokumentu XML s jedním nebo více otevřenými <xref:System.Xml.XmlWriter> objekty.</span><span class="sxs-lookup"><span data-stu-id="2841b-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="2841b-192">Ve <xref:System.Xml.XmlWriter> scénářích s jedním vláknem je povoleno a podporováno více objektů.</span><span class="sxs-lookup"><span data-stu-id="2841b-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="2841b-193">V následujícím seznamu jsou důležité poznámky, které je potřeba <xref:System.Xml.XmlWriter> vzít v úvahu při použití více objektů.</span><span class="sxs-lookup"><span data-stu-id="2841b-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
- <span data-ttu-id="2841b-194">Fragmenty XML napsané <xref:System.Xml.XmlWriter> objekty jsou přidány do dokumentu XML, pokud <xref:System.Xml.XmlWriter.Close%2A> je volána metoda <xref:System.Xml.XmlWriter> každého objektu.</span><span class="sxs-lookup"><span data-stu-id="2841b-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="2841b-195">Do tohoto okamžiku <xref:System.Xml.XmlWriter> objekt zapisuje odpojený fragment.</span><span class="sxs-lookup"><span data-stu-id="2841b-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="2841b-196">Pokud je operace provedena v dokumentu XML, nebudou ovlivněny všechny fragmenty, které <xref:System.Xml.XmlWriter> jsou zapsány <xref:System.Xml.XmlWriter.Close%2A> objektem před voláním.</span><span class="sxs-lookup"><span data-stu-id="2841b-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
- <span data-ttu-id="2841b-197">Pokud je otevřený <xref:System.Xml.XmlWriter> objekt v konkrétním podstromu XML a tento podstrom je odstraněn, <xref:System.Xml.XmlWriter> objekt může být stále přidán do podstromu.</span><span class="sxs-lookup"><span data-stu-id="2841b-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="2841b-198">Podstrom se jednoduše odstraněný fragmentem.</span><span class="sxs-lookup"><span data-stu-id="2841b-198">The subtree simply becomes a deleted fragment.</span></span>  
  
- <span data-ttu-id="2841b-199">Pokud je <xref:System.Xml.XmlWriter> otevřeno více objektů ve stejném okamžiku v dokumentu XML, jsou přidány do dokumentu XML v pořadí, ve kterém byly <xref:System.Xml.XmlWriter> objekty uzavřeny, nikoli v pořadí, v jakém byly otevřeny.</span><span class="sxs-lookup"><span data-stu-id="2841b-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="2841b-200">Následující příklad vytvoří <xref:System.Xml.XmlDocument> objekt, vytvoří <xref:System.Xml.XPath.XPathNavigator> objekt a poté pomocí <xref:System.Xml.XmlWriter> objektu vráceného <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metodou vytvoří strukturu první knihy v `books.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="2841b-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="2841b-201">Příklad ho uloží jako `book.xml` soubor.</span><span class="sxs-lookup"><span data-stu-id="2841b-201">The example then saves it as the `book.xml` file.</span></span>  
  
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
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="2841b-202">Uložení dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="2841b-202">Saving an XML Document</span></span>  
 <span data-ttu-id="2841b-203">Uložení změn provedených v <xref:System.Xml.XmlDocument> objektu jako výsledek metod popsaných v tomto tématu se provádí pomocí metod <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="2841b-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="2841b-204">Další informace o ukládání změn provedených v <xref:System.Xml.XmlDocument> objektu naleznete v tématu [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="2841b-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2841b-205">Viz také</span><span class="sxs-lookup"><span data-stu-id="2841b-205">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="2841b-206">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="2841b-206">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="2841b-207">Změna dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="2841b-207">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="2841b-208">Odebrání dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="2841b-208">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
