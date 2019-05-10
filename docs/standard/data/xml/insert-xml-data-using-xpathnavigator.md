---
title: Vložení dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a941c99e1d22a71dc6d94e73f5402716f41e3a81
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647917"
---
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="3a1ca-102">Vložení dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3a1ca-102">Insert XML Data using XPathNavigator</span></span>
<span data-ttu-id="3a1ca-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod pro vložení na stejné úrovni, podřízený a atribut uzly v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="3a1ca-104">Chcete-li používat tyto metody <xref:System.Xml.XPath.XPathNavigator> objekt musí být upravitelné, to znamená, jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="3a1ca-105"><xref:System.Xml.XPath.XPathNavigator> objekty, které můžete upravit dokument XML jsou vytvářeny <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="3a1ca-106"><xref:System.Xml.XPath.XPathNavigator> objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídy jsou jen pro čtení a žádný pokus o použití metod pro posunutí úprav <xref:System.Xml.XPath.XPathNavigator> objekt vytvořený pomocí <xref:System.Xml.XPath.XPathDocument> výsledkem objektu <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="3a1ca-107">Další informace o vytváření upravitelné <xref:System.Xml.XPath.XPathNavigator> objekty, najdete [čtení dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="3a1ca-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="3a1ca-108">Vkládání uzlů</span><span class="sxs-lookup"><span data-stu-id="3a1ca-108">Inserting Nodes</span></span>  
 <span data-ttu-id="3a1ca-109"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje metody pro vložení na stejné úrovni, podřízený a atribut uzly v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="3a1ca-110">Tyto metody umožňují vkládání uzlů a atributy v různých umístěních ve vztahu k aktuální pozici <xref:System.Xml.XPath.XPathNavigator> objektů a jsou popsané v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="3a1ca-111">Vkládání uzlů na stejné úrovni</span><span class="sxs-lookup"><span data-stu-id="3a1ca-111">Inserting Sibling Nodes</span></span>  
 <span data-ttu-id="3a1ca-112"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody, chcete-li vložit uzlů na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="3a1ca-113">Tyto metody vložit na stejné úrovni uzly před a za uzel <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="3a1ca-114"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> metody jsou přetížené a přijmout `string`, <xref:System.Xml.XmlReader> objektu, nebo <xref:System.Xml.XPath.XPathNavigator> objekt, který obsahuje uzel na stejné úrovni jako parametry.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="3a1ca-115">Obě metody také vrátit <xref:System.Xml.XmlWriter> objekt používaný pro vkládání uzlů na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="3a1ca-116"><xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metody vložit jeden na stejné úrovni uzlu před a za uzel <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na použití předponu oboru názvů, místní název, identifikátor URI oboru názvů a hodnotě zadané jako parametry.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="3a1ca-117">V následujícím příkladu nový `pages` prvek se vloží před `price` první podřízený prvek `book` prvek `contosoBooks.xml` soubor.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="3a1ca-118">V příkladu přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="3a1ca-119">Další informace o <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metody, naleznete v tématu <xref:System.Xml.XPath.XPathNavigator> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="3a1ca-120">Vkládání podřízené uzly</span><span class="sxs-lookup"><span data-stu-id="3a1ca-120">Inserting Child Nodes</span></span>  
 <span data-ttu-id="3a1ca-121"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody, chcete-li vložit podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="3a1ca-122">Tyto metody připojení a předřaďte podřízených uzlů na konci a na začátek seznamu podřízené uzly uzlu <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="3a1ca-123">Metody v části "Vkládání uzlů na stejné úrovni", jako jsou <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody přijímají `string`, <xref:System.Xml.XmlReader> objektu, nebo <xref:System.Xml.XPath.XPathNavigator> objekt, který obsahuje podřízený uzel, který chcete přidat jako parametry.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="3a1ca-124">Obě metody také vrátit <xref:System.Xml.XmlWriter> objekt použitý k vložení podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="3a1ca-125">Také, jako jsou metody v části "Vkládání uzlů na stejné úrovni" <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metody vložit jeden podřízený uzel na konci a na začátek seznamu podřízené uzly uzlu <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na použití Předpona oboru názvů, místní název, identifikátor URI oboru názvů a hodnotě zadané jako parametry.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="3a1ca-126">V následujícím příkladu nový `pages` podřízený element je připojen k seznamu podřízených elementů prvního `book` prvek `contosoBooks.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="3a1ca-127">V příkladu přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="3a1ca-128">Další informace o <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metody, naleznete v tématu <xref:System.Xml.XPath.XPathNavigator> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="3a1ca-129">Vkládání uzlů atributů</span><span class="sxs-lookup"><span data-stu-id="3a1ca-129">Inserting Attribute Nodes</span></span>  
 <span data-ttu-id="3a1ca-130"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody, chcete-li vložit uzlů atributů.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="3a1ca-131">Tyto metody vložení, atribut uzlů na uzlu elementu <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="3a1ca-132"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda vytvoří uzel atributu na uzlu elementu <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na použití předponu oboru názvů, místní název, identifikátor URI oboru názvů a hodnotě zadané jako parametry.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="3a1ca-133"><xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Vrátí metoda <xref:System.Xml.XmlWriter> objekt používaný pro vkládání uzlů atributů.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="3a1ca-134">V následujícím příkladu, nové `discount` a `currency` atributy vytvořené na `price` podřízený element prvního `book` element v `contosoBooks.xml` soubor pomocí <xref:System.Xml.XmlWriter> objekt vrácený z <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="3a1ca-135">V příkladu přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="3a1ca-136">Další informace o <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> a <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metody, naleznete v tématu <xref:System.Xml.XPath.XPathNavigator> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="3a1ca-137">Kopírování uzly</span><span class="sxs-lookup"><span data-stu-id="3a1ca-137">Copying Nodes</span></span>  
 <span data-ttu-id="3a1ca-138">V některých případech můžete chtít naplnit dokument XML s obsahem z jiného dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="3a1ca-139">Obě <xref:System.Xml.XPath.XPathNavigator> třídy a <xref:System.Xml.XmlWriter> třídy můžete kopírovat uzly <xref:System.Xml.XmlDocument> objekt z existující <xref:System.Xml.XmlReader> objektu nebo <xref:System.Xml.XPath.XPathNavigator> objektu.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="3a1ca-140"><xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy všechny mají přetížení, která může přijmout <xref:System.Xml.XPath.XPathNavigator> objektu nebo <xref:System.Xml.XmlReader> objektu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="3a1ca-141"><xref:System.Xml.XmlWriter.WriteNode%2A> Metodu <xref:System.Xml.XmlWriter> třída nemá přetížení, která může přijmout <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, nebo <xref:System.Xml.XPath.XPathNavigator> objektu.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="3a1ca-142">Následující příklad zkopíruje všechny `book` prvky z jednoho dokumentu do jiného.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
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
  
## <a name="inserting-values"></a><span data-ttu-id="3a1ca-143">Vkládání hodnot</span><span class="sxs-lookup"><span data-stu-id="3a1ca-143">Inserting Values</span></span>  
 <span data-ttu-id="3a1ca-144"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody pro vložení hodnoty do uzlu <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="3a1ca-145">Vkládání Netypové hodnoty</span><span class="sxs-lookup"><span data-stu-id="3a1ca-145">Inserting Untyped Values</span></span>  
 <span data-ttu-id="3a1ca-146"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` předanou jako parametr jako hodnotu uzlu <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="3a1ca-147">Hodnota je vložen bez jakéhokoli typu nebo bez ověření, že nová hodnota je platná pro typ uzlu, pokud je k dispozici informace o schématu.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="3a1ca-148">V následujícím příkladu <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda se používá k aktualizaci všech `price` prvků v `contosoBooks.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="3a1ca-149">V příkladu přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="3a1ca-150">Vkládání zadaných hodnot</span><span class="sxs-lookup"><span data-stu-id="3a1ca-150">Inserting Typed Values</span></span>  
 <span data-ttu-id="3a1ca-151">Pokud je typ uzlu W3C XML schématu jednoduché zadejte, nová hodnota vkládat stisknutím <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda je porovnávána s omezující vlastnosti pro jednoduchý typ. předtím, než je hodnota nastavena.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="3a1ca-152">Pokud je nová hodnota není platná pro typ uzlu (například nastavíte hodnotu `-1` na element, jehož typ je `xs:positiveInteger`), je výsledkem výjimky.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="3a1ca-153">V následujícím příkladu se pokusí změnit hodnotu `price` prvek první `book` prvek `contosoBooks.xml` do souboru <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="3a1ca-154">Protože typ schématu XML `price` element je definován jako `xs:decimal` v `contosoBooks.xsd` souborů, v důsledku výjimky.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="3a1ca-155">V příkladu přebírá `contosoBooks.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="3a1ca-156">Tento příklad využívá taky `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="3a1ca-157">InnerXml a OuterXml vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3a1ca-157">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="3a1ca-158"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy změnit kód XML uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="3a1ca-159"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Vlastnost se změní kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na s analyzovaný obsah XML daného `string`.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="3a1ca-160">Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnost se změní kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt je aktuálně umístěn na i samotný uzel aktuální.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="3a1ca-161">Kromě metod popsaných v tomto tématu <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti slouží k vložení uzly a hodnoty v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="3a1ca-162">Další informace o používání <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti, které chcete vložit uzly a hodnoty, najdete v článku [upravit dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="3a1ca-163">Namespace a XML: lang – konflikty</span><span class="sxs-lookup"><span data-stu-id="3a1ca-163">Namespace and xml:lang Conflicts</span></span>  
 <span data-ttu-id="3a1ca-164">Některé konflikty související se obor názvů a `xml:lang` deklarace může dojít při vkládání dat XML pomocí <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy, které využívají <xref:System.Xml.XmlReader>objektů jako parametry.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="3a1ca-165">Tady jsou možné obor názvů konflikty.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-165">The following are the possible namespace conflicts.</span></span>  
  
- <span data-ttu-id="3a1ca-166">Pokud je obor názvů v obor v rámci <xref:System.Xml.XmlReader> objektu kontextu, kde není v předponu pro obor názvů identifikátoru URI mapování <xref:System.Xml.XPath.XPathNavigator> kontext objektu na nově vložený uzel se přidá nová deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="3a1ca-167">Pokud stejný obor názvů identifikátoru URI je v oboru v rámci i <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu, ale má jinou předponu k němu mapována v obou kontextech, přidá novou deklaraci oboru názvů na nově vložený uzel s předponou a z identifikátoru URI oboru názvů <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="3a1ca-168">Pokud stejnou předponu oboru názvů je v oboru v rámci i <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu nově vložený uzel má jiný obor názvů identifikátoru URI k němu mapována v obou kontextech, se přidá nová deklarace oboru názvů, ale které znovu deklaruje tuto předponu oboru názvů identifikátoru URI na základě <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="3a1ca-169">Pokud předponu, stejně jako obor názvů URI v obou <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu je stejný, bez nové deklarace oboru názvů se přidá na nově vložený uzel.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a1ca-170">Výše uvedený popis platí také pro deklarace oboru názvů s prázdnou `string` jako předpona (například výchozí deklaraci oboru názvů).</span><span class="sxs-lookup"><span data-stu-id="3a1ca-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="3a1ca-171">Toto jsou možné `xml:lang` je v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
- <span data-ttu-id="3a1ca-172">Pokud dojde `xml:lang` atribut v oboru v rámci <xref:System.Xml.XmlReader> objektu kontextu, ale ne v <xref:System.Xml.XPath.XPathNavigator> kontext objektu `xml:lang` atribut, jehož hodnota je převzata z <xref:System.Xml.XmlReader> je objekt přidán na nově vložený uzel.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="3a1ca-173">Pokud dojde `xml:lang` atribut v oboru v obou <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu, ale každý má jinou hodnotu, `xml:lang` atribut, jehož hodnota je převzata z <xref:System.Xml.XmlReader> objekt je přidat do nově vložený uzel.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="3a1ca-174">Pokud dojde `xml:lang` atribut v oboru v obou <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu, ale každý se stejnou hodnotou, nové `xml:lang` přidat atribut na nově vložený uzel.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
- <span data-ttu-id="3a1ca-175">Pokud dojde `xml:lang` atribut v oboru v rámci <xref:System.Xml.XPath.XPathNavigator> objektu kontextu, ale žádné existující v <xref:System.Xml.XmlReader> objektu kontextu, ne `xml:lang` přidat atribut na nově vložený uzel.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="3a1ca-176">Vkládání uzlů s XmlWriter</span><span class="sxs-lookup"><span data-stu-id="3a1ca-176">Inserting Nodes with XmlWriter</span></span>  
 <span data-ttu-id="3a1ca-177">Jsou přetížené metody použité k vložení na stejné úrovni, podřízený a atribut uzly, které jsou popsané v části "Vkládání uzlů a hodnoty".</span><span class="sxs-lookup"><span data-stu-id="3a1ca-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="3a1ca-178"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> a <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy vrátit <xref:System.Xml.XmlWriter> objekt použitý k vložení uzlů.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="3a1ca-179">Nepodporovaný objekt XmlWriter metody</span><span class="sxs-lookup"><span data-stu-id="3a1ca-179">Unsupported XmlWriter Methods</span></span>  
 <span data-ttu-id="3a1ca-180">Některé z metod používaných pro zápis do dokumentu XML pomocí informací <xref:System.Xml.XmlWriter> třídy jsou podporovány <xref:System.Xml.XPath.XPathNavigator> třídy kvůli rozdílu mezi modelu dat XPath a Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="3a1ca-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="3a1ca-181">V následující tabulce jsou popsány <xref:System.Xml.XmlWriter> metody, které nepodporují třídy <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="3a1ca-182">Metoda</span><span class="sxs-lookup"><span data-stu-id="3a1ca-182">Method</span></span>|<span data-ttu-id="3a1ca-183">Popis</span><span class="sxs-lookup"><span data-stu-id="3a1ca-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="3a1ca-184">Vyvolá výjimku <xref:System.NotSupportedException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="3a1ca-185">Na kořenové úrovni a vyvolá výjimku Ignorovat <xref:System.NotSupportedException> výjimky-li volána na jiné úrovni v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="3a1ca-186">Považováno za volání <xref:System.Xml.XmlWriter.WriteString%2A> metodu pro odpovídající znak nebo znaky.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="3a1ca-187">Považováno za volání <xref:System.Xml.XmlWriter.WriteString%2A> metodu pro odpovídající znak nebo znaky.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="3a1ca-188">Považováno za volání <xref:System.Xml.XmlWriter.WriteString%2A> metodu pro odpovídající znak nebo znaky.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="3a1ca-189">Další informace o <xref:System.Xml.XmlWriter> najdete v tématu <xref:System.Xml.XmlWriter> třídy referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="3a1ca-190">Více objektů XmlWriter</span><span class="sxs-lookup"><span data-stu-id="3a1ca-190">Multiple XmlWriter Objects</span></span>  
 <span data-ttu-id="3a1ca-191">Je možné mít více <xref:System.Xml.XPath.XPathNavigator> objekty odkazující na různé části XML dokument otevřít jeden nebo více <xref:System.Xml.XmlWriter> objekty.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="3a1ca-192">Více <xref:System.Xml.XmlWriter> objekty jsou povolené a podporován ve scénářích s jedním vláknem.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="3a1ca-193">Tady jsou důležité poznámky ke zvážení při použití více <xref:System.Xml.XmlWriter> objekty.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
- <span data-ttu-id="3a1ca-194">Fragmenty XML autorem <xref:System.Xml.XmlWriter> objekty jsou přidány do souboru XML dokumentů, kdy <xref:System.Xml.XmlWriter.Close%2A> metoda jednotlivých <xref:System.Xml.XmlWriter> objekt, se nazývá.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="3a1ca-195">Do tohoto bodu <xref:System.Xml.XmlWriter> objekt zapisuje odpojené fragment.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="3a1ca-196">Pokud se operace provádí v dokumentu XML, jakékoli fragmenty jsou zapsána pomocí <xref:System.Xml.XmlWriter> objektu před <xref:System.Xml.XmlWriter.Close%2A> byla volána, nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
- <span data-ttu-id="3a1ca-197">Pokud není otevřený <xref:System.Xml.XmlWriter> odstranění objektu na konkrétní podstrom XML a že podstrom <xref:System.Xml.XmlWriter> objekt může přesto přidat do dílčí stromu.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="3a1ca-198">Podstrom jednoduše stane odstraněné fragment.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-198">The subtree simply becomes a deleted fragment.</span></span>  
  
- <span data-ttu-id="3a1ca-199">Pokud je položek víc <xref:System.Xml.XmlWriter> objektů jsou otevřené na stejné místo v dokumentu XML, jsou přidány do dokumentu XML v pořadí, ve kterém <xref:System.Xml.XmlWriter> objektů jsou uzavřeny, ne v pořadí, v jakém byly otevřeny.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="3a1ca-200">Následující příklad vytvoří <xref:System.Xml.XmlDocument> objektu, vytvoří <xref:System.Xml.XPath.XPathNavigator> a pak použije <xref:System.Xml.XmlWriter> objekt vrácený <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metodu pro vytvoření struktury první adresáře v `books.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="3a1ca-201">Jako příklad pak uloží `book.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-201">The example then saves it as the `book.xml` file.</span></span>  
  
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
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="3a1ca-202">Uložení dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="3a1ca-202">Saving an XML Document</span></span>  
 <span data-ttu-id="3a1ca-203">Ukládají se změny provedené <xref:System.Xml.XmlDocument> objekt výsledku z metod popsaných v tomto tématu se provádí pomocí metody <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="3a1ca-204">Další informace o uložení změny <xref:System.Xml.XmlDocument> objektu, najdete v článku [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="3a1ca-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a1ca-205">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a1ca-205">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="3a1ca-206">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="3a1ca-206">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="3a1ca-207">Změna dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3a1ca-207">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="3a1ca-208">Odebrání dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3a1ca-208">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
