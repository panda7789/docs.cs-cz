---
title: Vkládání dat XML pomocí objektem XPathNavigator nastaveným na
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f597696514f53259b4ad0f388b6474259d77bea5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579376"
---
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="987ac-102">Vkládání dat XML pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="987ac-102">Insert XML Data using XPathNavigator</span></span>
<span data-ttu-id="987ac-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, používá se k vložení na stejné úrovni, podřízený a atribut uzly v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="987ac-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="987ac-104">Chcete-li používat tyto metody <xref:System.Xml.XPath.XPathNavigator> objekt musí být upravitelné, který je jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musí být vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="987ac-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="987ac-105"><xref:System.Xml.XPath.XPathNavigator> objekty, které můžete upravit dokument XML, které jsou vytvořené pomocí <xref:System.Xml.XmlDocument.CreateNavigator%2A> metodu <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="987ac-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="987ac-106"><xref:System.Xml.XPath.XPathNavigator> objekty vytvořené <xref:System.Xml.XPath.XPathDocument> třídy jsou jen pro čtení a jakýkoli pokus o úpravu metody použijte <xref:System.Xml.XPath.XPathNavigator> objekt vytvořený <xref:System.Xml.XPath.XPathDocument> objekt výsledkem <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="987ac-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="987ac-107">Další informace o vytváření upravitelné <xref:System.Xml.XPath.XPathNavigator> objekty, najdete v části [čtení dat XML pomocí XPathDocument třídou XMLDocument nastavenou na](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="987ac-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="987ac-108">Vkládání uzlů</span><span class="sxs-lookup"><span data-stu-id="987ac-108">Inserting Nodes</span></span>  
 <span data-ttu-id="987ac-109"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje metody pro vložení na stejné úrovni, podřízený a atribut uzly v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="987ac-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="987ac-110">Tyto metody umožňují vložit uzly a atributy v různých umístěních ve vztahu k aktuální pozici <xref:System.Xml.XPath.XPathNavigator> objektu a jsou popsané v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="987ac-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="987ac-111">Vkládání uzly na stejné úrovni</span><span class="sxs-lookup"><span data-stu-id="987ac-111">Inserting Sibling Nodes</span></span>  
 <span data-ttu-id="987ac-112"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody, které vložit uzly na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="987ac-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="987ac-113">Tyto metody vložit na stejné úrovni jako uzly před a za uzel <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na.</span><span class="sxs-lookup"><span data-stu-id="987ac-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="987ac-114"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> metody jsou přetížené a přijmout `string`, <xref:System.Xml.XmlReader> objekt, nebo <xref:System.Xml.XPath.XPathNavigator> objekt, který obsahuje uzel na stejné úrovni, který chcete přidat jako parametry.</span><span class="sxs-lookup"><span data-stu-id="987ac-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="987ac-115">Obě metody se taky vrátit <xref:System.Xml.XmlWriter> objekt použitý k vložení uzly na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="987ac-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="987ac-116"><xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metody vložení na stejné úrovni jako jednoho uzlu před a po uzlu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na pomocí předponu oboru názvů, místní název, identifikátor URI oboru názvů a hodnotě zadané jako parametry.</span><span class="sxs-lookup"><span data-stu-id="987ac-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="987ac-117">V následujícím příkladu a nové `pages` element je vložen před `price` první podřízený prvek `book` element v `contosoBooks.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="987ac-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="987ac-118">V příkladu trvá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="987ac-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="987ac-119">Další informace o <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metody, najdete v článku <xref:System.Xml.XPath.XPathNavigator> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="987ac-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="987ac-120">Vkládání podřízené uzly</span><span class="sxs-lookup"><span data-stu-id="987ac-120">Inserting Child Nodes</span></span>  
 <span data-ttu-id="987ac-121"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody, které vložit podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="987ac-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="987ac-122">Tyto metody připojit a předřazení podřízených uzlů na konci a na začátek seznamu podřízené uzly uzlu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na.</span><span class="sxs-lookup"><span data-stu-id="987ac-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="987ac-123">Metody v části "Vkládání uzly na stejné úrovni", jako <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody přijímají `string`, <xref:System.Xml.XmlReader> objekt, nebo <xref:System.Xml.XPath.XPathNavigator> objekt obsahující podřízený uzel, který chcete přidat jako parametry.</span><span class="sxs-lookup"><span data-stu-id="987ac-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="987ac-124">Obě metody se taky vrátit <xref:System.Xml.XmlWriter> objekt použitý k vložení podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="987ac-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="987ac-125">Také jako metody v části "Vkládání uzly na stejné úrovni" <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metody vložit jeden podřízený uzel na konci a na začátek seznamu podřízené uzly uzlu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na pomocí Předpona oboru názvů, místní název, identifikátor URI oboru názvů a hodnotě zadané jako parametry.</span><span class="sxs-lookup"><span data-stu-id="987ac-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="987ac-126">V následujícím příkladu nový `pages` připojí se k seznamu podřízených elementů první podřízený element `book` element v `contosoBooks.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="987ac-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="987ac-127">V příkladu trvá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="987ac-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="987ac-128">Další informace o <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metody, najdete v článku <xref:System.Xml.XPath.XPathNavigator> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="987ac-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="987ac-129">Vkládání atribut uzlů</span><span class="sxs-lookup"><span data-stu-id="987ac-129">Inserting Attribute Nodes</span></span>  
 <span data-ttu-id="987ac-130"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje následující metody, které vložit atribut uzlů.</span><span class="sxs-lookup"><span data-stu-id="987ac-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="987ac-131">Tyto metody vložit atribut uzly na uzlu elementu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na.</span><span class="sxs-lookup"><span data-stu-id="987ac-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="987ac-132"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda vytvoří uzlu atributu na uzlu elementu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na pomocí předponu oboru názvů, místní název, identifikátor URI oboru názvů a hodnotě zadané jako parametry.</span><span class="sxs-lookup"><span data-stu-id="987ac-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="987ac-133"><xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda vrátí <xref:System.Xml.XmlWriter> objekt použitý k vložení atribut uzlů.</span><span class="sxs-lookup"><span data-stu-id="987ac-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="987ac-134">V následujícím příkladu, nové `discount` a `currency` atributy se vytvářejí na `price` první podřízený prvek `book` element v `contosoBooks.xml` souboru pomocí <xref:System.Xml.XmlWriter> objekt vrácený <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda.</span><span class="sxs-lookup"><span data-stu-id="987ac-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="987ac-135">V příkladu trvá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="987ac-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="987ac-136">Další informace o <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> a <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metody, najdete v článku <xref:System.Xml.XPath.XPathNavigator> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="987ac-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="987ac-137">Kopírování uzly</span><span class="sxs-lookup"><span data-stu-id="987ac-137">Copying Nodes</span></span>  
 <span data-ttu-id="987ac-138">V některých případech můžete chtít naplnit dokumentu XML se obsah z jiného dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="987ac-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="987ac-139">Obě <xref:System.Xml.XPath.XPathNavigator> – třída a <xref:System.Xml.XmlWriter> třídy můžete zkopírovat uzly, aby <xref:System.Xml.XmlDocument> objekt z existující <xref:System.Xml.XmlReader> objekt nebo <xref:System.Xml.XPath.XPathNavigator> objektu.</span><span class="sxs-lookup"><span data-stu-id="987ac-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="987ac-140"><xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> a <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> metody <xref:System.Xml.XPath.XPathNavigator> třída všechny mají přetížení, které může přijmout <xref:System.Xml.XPath.XPathNavigator> objekt nebo <xref:System.Xml.XmlReader> objekt jako parametr.</span><span class="sxs-lookup"><span data-stu-id="987ac-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="987ac-141"><xref:System.Xml.XmlWriter.WriteNode%2A> Metodu <xref:System.Xml.XmlWriter> třída má přetížení, která může přijmout <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, nebo <xref:System.Xml.XPath.XPathNavigator> objektu.</span><span class="sxs-lookup"><span data-stu-id="987ac-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="987ac-142">Následující příklad zkopíruje všechny `book` elementy z jednoho dokumentu do jiného.</span><span class="sxs-lookup"><span data-stu-id="987ac-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
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
  
## <a name="inserting-values"></a><span data-ttu-id="987ac-143">Vložení hodnoty</span><span class="sxs-lookup"><span data-stu-id="987ac-143">Inserting Values</span></span>  
 <span data-ttu-id="987ac-144"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> a <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody vložit hodnoty pro uzel do <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="987ac-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="987ac-145">Vkládání bez typu hodnoty</span><span class="sxs-lookup"><span data-stu-id="987ac-145">Inserting Untyped Values</span></span>  
 <span data-ttu-id="987ac-146"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jednoduše vloží netypové `string` hodnota předaná jako parametr jako hodnotu uzlu <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na.</span><span class="sxs-lookup"><span data-stu-id="987ac-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="987ac-147">Hodnota je vložen bez jakéhokoli typu nebo bez ověření, že nová hodnota je platná podle typu uzlu, pokud je k dispozici informace o schématu.</span><span class="sxs-lookup"><span data-stu-id="987ac-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="987ac-148">V následujícím příkladu <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda se používá k aktualizaci všech `price` elementů v `contosoBooks.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="987ac-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="987ac-149">V příkladu trvá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="987ac-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="987ac-150">Vkládání zadávaných hodnot</span><span class="sxs-lookup"><span data-stu-id="987ac-150">Inserting Typed Values</span></span>  
 <span data-ttu-id="987ac-151">Pokud je typ uzlu schématu XML W3C jednoduchý typ, nová hodnota vložená <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metoda bude zkontrolován omezující vlastnosti pro jednoduchý typ. předtím, než je hodnota nastavená.</span><span class="sxs-lookup"><span data-stu-id="987ac-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="987ac-152">Pokud nová hodnota není platná podle typu uzlu (například nastavení hodnotu `-1` u elementu, jehož typ je `xs:positiveInteger`), výsledkem výjimka.</span><span class="sxs-lookup"><span data-stu-id="987ac-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="987ac-153">V následujícím příkladu se pokusí změnit hodnotu `price` element první `book` element v `contosoBooks.xml` do souboru <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="987ac-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="987ac-154">Vzhledem k tomu, že typ schématu XML `price` element je definován jako `xs:decimal` v `contosoBooks.xsd` soubory, to vede k výjimce.</span><span class="sxs-lookup"><span data-stu-id="987ac-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="987ac-155">V příkladu trvá `contosoBooks.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="987ac-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="987ac-156">Tento příklad také trvá `contosoBooks.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="987ac-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="987ac-157">InnerXml a OuterXml vlastnosti</span><span class="sxs-lookup"><span data-stu-id="987ac-157">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="987ac-158"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třída změnit kód XML uzlů <xref:System.Xml.XPath.XPathNavigator> objektu je aktuálně nastavený na.</span><span class="sxs-lookup"><span data-stu-id="987ac-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="987ac-159"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Změny vlastností kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný na s Analyzovaná obsah daného XML `string`.</span><span class="sxs-lookup"><span data-stu-id="987ac-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="987ac-160">Podobně <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> změny vlastností kód XML podřízených uzlů <xref:System.Xml.XPath.XPathNavigator> objekt aktuálně umístěný na i aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="987ac-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="987ac-161">Kromě metod popsaných v tomto tématu <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti slouží k vložení uzlů a hodnoty v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="987ac-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="987ac-162">Další informace o používání <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> a <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> vlastnosti, které chcete vložit uzly a hodnoty, najdete v článku [upravit Data XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="987ac-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="987ac-163">Namespace XML: lang konflikty a</span><span class="sxs-lookup"><span data-stu-id="987ac-163">Namespace and xml:lang Conflicts</span></span>  
 <span data-ttu-id="987ac-164">Některé konflikty související do oboru názvů a `xml:lang` deklarace může dojít při vkládání dat XML pomocí <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídu, která trvat <xref:System.Xml.XmlReader>objektů jako parametry.</span><span class="sxs-lookup"><span data-stu-id="987ac-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="987ac-165">Níže jsou uvedeny možné obor názvů konfliktů.</span><span class="sxs-lookup"><span data-stu-id="987ac-165">The following are the possible namespace conflicts.</span></span>  
  
-   <span data-ttu-id="987ac-166">Pokud dojde oboru názvů v oboru v rámci <xref:System.Xml.XmlReader> objektu kontextu, kde předponu pro obor názvů URI mapování není součástí <xref:System.Xml.XPath.XPathNavigator> objektu kontextu novou deklaraci oboru názvů se přidá do nově vloženou uzlu.</span><span class="sxs-lookup"><span data-stu-id="987ac-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
-   <span data-ttu-id="987ac-167">Pokud stejný identifikátor URI oboru názvů je v oboru jak <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu, ale s jinou předponu k němu mapována v obou kontextech, přidá se do nově vloženou uzlu, s předponou novou deklaraci oboru názvů a identifikátor URI, které jsou převzaty z oboru názvů <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="987ac-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
-   <span data-ttu-id="987ac-168">Pokud stejnou předponu oboru názvů je v oboru jak <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu nově vloženou uzel má jiný identifikátor URI oboru názvů k němu mapována v obou kontextech, se přidá novou deklaraci oboru názvů, ale které znovu deklaruje, že předpona s oborem názvů URI převzaty z <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="987ac-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
-   <span data-ttu-id="987ac-169">Pokud předponu, jakož i identifikátor URI oboru názvů v obou <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> objektu kontextu je stejný, bez novou deklaraci oboru názvů se přidá do nově vloženou uzlu.</span><span class="sxs-lookup"><span data-stu-id="987ac-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="987ac-170">Výše uvedený popis platí také pro deklarace oboru názvů s prázdné `string` jako předpona (například výchozí deklaraci oboru názvů).</span><span class="sxs-lookup"><span data-stu-id="987ac-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="987ac-171">Toto jsou možné `xml:lang` je v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="987ac-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
-   <span data-ttu-id="987ac-172">Pokud dojde `xml:lang` atribut v oboru v rámci <xref:System.Xml.XmlReader> kontextu objektu, ale ne v <xref:System.Xml.XPath.XPathNavigator> kontextu objektu, `xml:lang` atribut, jehož hodnota je převzat ze <xref:System.Xml.XmlReader> objekt přidá do nově vloženou uzlu.</span><span class="sxs-lookup"><span data-stu-id="987ac-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
-   <span data-ttu-id="987ac-173">Pokud dojde `xml:lang` atribut v oboru v obou <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> kontextu objektu, ale každý má jinou hodnotu, `xml:lang` atribut, jehož hodnota je převzat ze <xref:System.Xml.XmlReader> objekt přidá do nově vloženou uzlu.</span><span class="sxs-lookup"><span data-stu-id="987ac-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
-   <span data-ttu-id="987ac-174">Pokud dojde `xml:lang` atribut v oboru v obou <xref:System.Xml.XmlReader> objektu kontextu a <xref:System.Xml.XPath.XPathNavigator> kontextu objektu, ale každý se stejnou hodnotou, nové `xml:lang` atribut je přidaný na nově vloženou uzlu.</span><span class="sxs-lookup"><span data-stu-id="987ac-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
-   <span data-ttu-id="987ac-175">Pokud dojde `xml:lang` atribut v oboru v rámci <xref:System.Xml.XPath.XPathNavigator> kontextu objektu, ale žádné existující v <xref:System.Xml.XmlReader> objektu kontextu, ne `xml:lang` přidání atributu do nově vloženou uzlu.</span><span class="sxs-lookup"><span data-stu-id="987ac-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="987ac-176">Vkládání uzly s XmlWriter</span><span class="sxs-lookup"><span data-stu-id="987ac-176">Inserting Nodes with XmlWriter</span></span>  
 <span data-ttu-id="987ac-177">Jsou přetížené metody použité k vložení na stejné úrovni, podřízený a atribut uzlů, které jsou popsané v části "Vkládání uzlů a hodnoty".</span><span class="sxs-lookup"><span data-stu-id="987ac-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="987ac-178"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> a <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy vrátit <xref:System.Xml.XmlWriter> objekt použitý k vložení uzlů.</span><span class="sxs-lookup"><span data-stu-id="987ac-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="987ac-179">Nepodporované XmlWriter metody</span><span class="sxs-lookup"><span data-stu-id="987ac-179">Unsupported XmlWriter Methods</span></span>  
 <span data-ttu-id="987ac-180">Ne všechny metody použité k zápisu informací do dokumentu XML pomocí <xref:System.Xml.XmlWriter> třída podporuje <xref:System.Xml.XPath.XPathNavigator> třída kvůli rozdílu mezi XPath datového modelu a modelu objektu dokumentu (DOM).</span><span class="sxs-lookup"><span data-stu-id="987ac-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="987ac-181">V následující tabulce jsou popsány <xref:System.Xml.XmlWriter> metody, které nepodporují třídy <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="987ac-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="987ac-182">Metoda</span><span class="sxs-lookup"><span data-stu-id="987ac-182">Method</span></span>|<span data-ttu-id="987ac-183">Popis</span><span class="sxs-lookup"><span data-stu-id="987ac-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="987ac-184">Vyvolá <xref:System.NotSupportedException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="987ac-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="987ac-185">Ignorovat na kořenové úrovni a generuje <xref:System.NotSupportedException> výjimka, pokud je volána na jiné úrovni v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="987ac-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="987ac-186">Považuje za volání <xref:System.Xml.XmlWriter.WriteString%2A> metodu ekvivalentní znak nebo znaky.</span><span class="sxs-lookup"><span data-stu-id="987ac-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="987ac-187">Považuje za volání <xref:System.Xml.XmlWriter.WriteString%2A> metodu ekvivalentní znak nebo znaky.</span><span class="sxs-lookup"><span data-stu-id="987ac-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="987ac-188">Považuje za volání <xref:System.Xml.XmlWriter.WriteString%2A> metodu ekvivalentní znak nebo znaky.</span><span class="sxs-lookup"><span data-stu-id="987ac-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="987ac-189">Další informace o <xref:System.Xml.XmlWriter> naleznete <xref:System.Xml.XmlWriter> třídy referenční dokumentaci k nástroji.</span><span class="sxs-lookup"><span data-stu-id="987ac-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="987ac-190">Více objektů XmlWriter</span><span class="sxs-lookup"><span data-stu-id="987ac-190">Multiple XmlWriter Objects</span></span>  
 <span data-ttu-id="987ac-191">Je možné, že více <xref:System.Xml.XPath.XPathNavigator> objekty odkazující na různé části XML dokumentů s jeden nebo více otevřete <xref:System.Xml.XmlWriter> objekty.</span><span class="sxs-lookup"><span data-stu-id="987ac-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="987ac-192">Více <xref:System.Xml.XmlWriter> jsou povoleny a podporován ve scénářích jednovláknové objekty.</span><span class="sxs-lookup"><span data-stu-id="987ac-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="987ac-193">Toto jsou důležité poznámky ke zvážení při použití více <xref:System.Xml.XmlWriter> objekty.</span><span class="sxs-lookup"><span data-stu-id="987ac-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
-   <span data-ttu-id="987ac-194">Fragmenty kódu XML zapsaných správcem <xref:System.Xml.XmlWriter> objekty jsou přidány do souboru XML dokumentů, kdy <xref:System.Xml.XmlWriter.Close%2A> metoda jednotlivých <xref:System.Xml.XmlWriter> objektu se říká.</span><span class="sxs-lookup"><span data-stu-id="987ac-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="987ac-195">Dokud nebude tento bod <xref:System.Xml.XmlWriter> objektu je zápis fragment odpojené.</span><span class="sxs-lookup"><span data-stu-id="987ac-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="987ac-196">Pokud se provádí operace v dokumentu XML žádné fragmenty zapisovaný podle <xref:System.Xml.XmlWriter> objektu před <xref:System.Xml.XmlWriter.Close%2A> byla volána, neovlivní.</span><span class="sxs-lookup"><span data-stu-id="987ac-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
-   <span data-ttu-id="987ac-197">Pokud dojde otevření <xref:System.Xml.XmlWriter> je odstraněn objekt na konkrétní podstrom XML a že podstrom, <xref:System.Xml.XmlWriter> objekt může přesto přidat do dílčí stromu.</span><span class="sxs-lookup"><span data-stu-id="987ac-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="987ac-198">Podstrom jednoduše stane fragment odstraněné.</span><span class="sxs-lookup"><span data-stu-id="987ac-198">The subtree simply becomes a deleted fragment.</span></span>  
  
-   <span data-ttu-id="987ac-199">Pokud je to více <xref:System.Xml.XmlWriter> objektů jsou otevřené na stejném místě v dokumentu XML, budou přidány do dokumentu XML v pořadí, ve kterém <xref:System.Xml.XmlWriter> objekty zavřou, není v pořadí, ve kterém byly otevřeny.</span><span class="sxs-lookup"><span data-stu-id="987ac-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="987ac-200">Následující příklad vytvoří <xref:System.Xml.XmlDocument> objektu, vytvoří <xref:System.Xml.XPath.XPathNavigator> objekt a používá <xref:System.Xml.XmlWriter> objekt vrácený <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metodu pro vytvoření strukturu první seznam v `books.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="987ac-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="987ac-201">Příklad pak uloží jej jako `book.xml` souboru.</span><span class="sxs-lookup"><span data-stu-id="987ac-201">The example then saves it as the `book.xml` file.</span></span>  
  
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
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="987ac-202">Uložení dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="987ac-202">Saving an XML Document</span></span>  
 <span data-ttu-id="987ac-203">Ukládají se změny provedené v <xref:System.Xml.XmlDocument> objektu jako výsledek metody popsané v tomto tématu se provádí pomocí metody <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="987ac-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="987ac-204">Další informace o ukládání změny <xref:System.Xml.XmlDocument> objektu, najdete v části [ukládání a zápis dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="987ac-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="987ac-205">Viz také</span><span class="sxs-lookup"><span data-stu-id="987ac-205">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="987ac-206">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="987ac-206">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="987ac-207">Změna dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="987ac-207">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="987ac-208">Odebrání dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="987ac-208">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
