---
title: Přehled třídy XElement (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: 7fbe1cc484ea3482bc455c161783bd7a4513d0bd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830706"
---
# <a name="xelement-class-overview-visual-basic"></a><span data-ttu-id="0c6fd-102">Přehled třídy XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c6fd-102">XElement Class Overview (Visual Basic)</span></span>
<span data-ttu-id="0c6fd-103"><xref:System.Xml.Linq.XElement> Třídy je jedním ze základních tříd v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0c6fd-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="0c6fd-104">Reprezentuje XML element.</span><span class="sxs-lookup"><span data-stu-id="0c6fd-104">It represents an XML element.</span></span> <span data-ttu-id="0c6fd-105">Tato třída slouží k vytváření prvků; Změňte obsah elementu; Přidání, změna nebo odstranění podřízené elementy; přidat atributy pro element. nebo serializace obsah prvek v textové podobě.</span><span class="sxs-lookup"><span data-stu-id="0c6fd-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="0c6fd-106">Můžete také spolupracovat s jinými třídami v <xref:System.Xml?displayProperty=nameWithType>, jako například <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, a <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="0c6fd-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="0c6fd-107">Funkce XElement</span><span class="sxs-lookup"><span data-stu-id="0c6fd-107">XElement Functionality</span></span>  
 <span data-ttu-id="0c6fd-108">Toto téma popisuje funkce poskytované službou <xref:System.Xml.Linq.XElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="0c6fd-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="0c6fd-109">Vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="0c6fd-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="0c6fd-110">Můžete sestavit stromů XML v celou řadu způsobů, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="0c6fd-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
-   <span data-ttu-id="0c6fd-111">Můžete vytvořit stromu XML v kódu.</span><span class="sxs-lookup"><span data-stu-id="0c6fd-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="0c6fd-112">Další informace najdete v tématu [vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="0c6fd-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
-   <span data-ttu-id="0c6fd-113">Můžete analyzovat soubor XML z různých zdrojů, včetně <xref:System.IO.TextReader>, textové soubory nebo webovou adresu (URL).</span><span class="sxs-lookup"><span data-stu-id="0c6fd-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="0c6fd-114">Další informace najdete v tématu [analýza kódu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0c6fd-114">For more information, see [Parsing XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
-   <span data-ttu-id="0c6fd-115">Můžete použít <xref:System.Xml.XmlReader> k naplnění stromu.</span><span class="sxs-lookup"><span data-stu-id="0c6fd-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="0c6fd-116">Další informace naleznete v tématu <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="0c6fd-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
-   <span data-ttu-id="0c6fd-117">Pokud máte modul, který může zapisovat obsah tak, aby <xref:System.Xml.XmlWriter>, můžete použít <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metodu pro vytvoření zapisovač, předat modul pro zápis do modulu a pak použít obsah, který je zapsán do <xref:System.Xml.XmlWriter> k naplnění stromu XML.</span><span class="sxs-lookup"><span data-stu-id="0c6fd-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="0c6fd-118">Nejběžnější způsob, jak vytvořit stromu XML je však následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0c6fd-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 <span data-ttu-id="0c6fd-119">Zahrnuje jiného velmi běžná technika pro vytvoření stromu XML pomocí výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu k naplnění stromu XML, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0c6fd-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="0c6fd-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0c6fd-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="0c6fd-121">Serializace stromů XML</span><span class="sxs-lookup"><span data-stu-id="0c6fd-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="0c6fd-122">Může serializovat stromu XML <xref:System.IO.File>, <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="0c6fd-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="0c6fd-123">Další informace najdete v tématu [serializace stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="0c6fd-123">For more information, see [Serializing XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="0c6fd-124">Načítání dat XML pomocí metody osy</span><span class="sxs-lookup"><span data-stu-id="0c6fd-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="0c6fd-125">Načíst atributy, podřízené prvky, následnickým elementům a nadřazených elementů můžete použít metody osy.</span><span class="sxs-lookup"><span data-stu-id="0c6fd-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="0c6fd-126">dotazy pracovat na metody osy a poskytují několik pružnější a výkonnější způsobů, jak procházet a zpracování stromu XML.</span><span class="sxs-lookup"><span data-stu-id="0c6fd-126">queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="0c6fd-127">Další informace najdete v tématu [osy LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="0c6fd-127">For more information, see [LINQ to XML Axes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="0c6fd-128">Dotazování na stromy XML</span><span class="sxs-lookup"><span data-stu-id="0c6fd-128">Querying XML Trees</span></span>  
 <span data-ttu-id="0c6fd-129">Můžete napsat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, které extrahují data z stromu XML.</span><span class="sxs-lookup"><span data-stu-id="0c6fd-129">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="0c6fd-130">Další informace najdete v tématu [dotazování na stromy XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="0c6fd-130">For more information, see [Querying XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="0c6fd-131">Změna stromů XML</span><span class="sxs-lookup"><span data-stu-id="0c6fd-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="0c6fd-132">Můžete upravovat prvek v celou řadu způsobů, včetně změny jeho obsahu nebo atributů.</span><span class="sxs-lookup"><span data-stu-id="0c6fd-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="0c6fd-133">Můžete také odebrat element ze svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="0c6fd-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="0c6fd-134">Další informace najdete v tématu [změna stromů XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0c6fd-134">For more information, see [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c6fd-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c6fd-135">See also</span></span>

- [<span data-ttu-id="0c6fd-136">Přehled LINQ to XML programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c6fd-136">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
