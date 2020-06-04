---
title: Přehled třídy XElement
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: a0e50c8a5a14150ee09a328f4dcdd5bc88363621
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413216"
---
# <a name="xelement-class-overview-visual-basic"></a><span data-ttu-id="a70a6-102">Přehled třídy XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a70a6-102">XElement Class Overview (Visual Basic)</span></span>
<span data-ttu-id="a70a6-103"><xref:System.Xml.Linq.XElement>Třída je jednou ze základních tříd v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a70a6-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="a70a6-104">Představuje XML element.</span><span class="sxs-lookup"><span data-stu-id="a70a6-104">It represents an XML element.</span></span> <span data-ttu-id="a70a6-105">Tuto třídu můžete použít k vytváření elementů. změnit obsah elementu; Přidání, změna nebo odstranění podřízených elementů; přidejte atributy k elementu; nebo serializovat obsah elementu v textovém formuláři.</span><span class="sxs-lookup"><span data-stu-id="a70a6-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="a70a6-106">Můžete také vzájemně spolupracovat s jinými třídami v, jako například <xref:System.Xml?displayProperty=nameWithType> <xref:System.Xml.XmlReader> , <xref:System.Xml.XmlWriter> a <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="a70a6-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="a70a6-107">Funkce XElement</span><span class="sxs-lookup"><span data-stu-id="a70a6-107">XElement Functionality</span></span>  
 <span data-ttu-id="a70a6-108">Toto téma popisuje funkce poskytované <xref:System.Xml.Linq.XElement> třídou.</span><span class="sxs-lookup"><span data-stu-id="a70a6-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="a70a6-109">Sestavování stromů XML</span><span class="sxs-lookup"><span data-stu-id="a70a6-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="a70a6-110">Stromy XML můžete vytvářet různými způsoby, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="a70a6-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="a70a6-111">V kódu můžete vytvořit strom XML.</span><span class="sxs-lookup"><span data-stu-id="a70a6-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="a70a6-112">Další informace naleznete v tématu [vytváření stromů XML (Visual Basic)](creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="a70a6-112">For more information, see [Creating XML Trees (Visual Basic)](creating-xml-trees.md).</span></span>  
  
- <span data-ttu-id="a70a6-113">Můžete analyzovat XML z různých zdrojů, včetně <xref:System.IO.TextReader> textových souborů nebo webové adresy (URL).</span><span class="sxs-lookup"><span data-stu-id="a70a6-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="a70a6-114">Další informace najdete v tématu [Analýza XML (Visual Basic)](parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a70a6-114">For more information, see [Parsing XML (Visual Basic)](parsing-xml.md).</span></span>  
  
- <span data-ttu-id="a70a6-115"><xref:System.Xml.XmlReader>K naplnění stromu můžete použít.</span><span class="sxs-lookup"><span data-stu-id="a70a6-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="a70a6-116">Další informace naleznete v tématu <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="a70a6-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="a70a6-117">Máte-li modul, který může zapisovat obsah do <xref:System.Xml.XmlWriter> , můžete použít <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metodu k vytvoření zapisovače, předat zapisovači modulu a potom použít obsah, který je zapsán do objektu <xref:System.Xml.XmlWriter> k naplnění stromu XML.</span><span class="sxs-lookup"><span data-stu-id="a70a6-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="a70a6-118">Nejběžnější způsob vytvoření stromu XML je však následující:</span><span class="sxs-lookup"><span data-stu-id="a70a6-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="a70a6-119">Další velmi obvyklá technika pro vytváření stromu XML zahrnuje použití výsledků dotazu LINQ k naplnění stromu XML, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a70a6-119">Another very common technique for creating an XML tree involves using the results of a LINQ query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="a70a6-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a70a6-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="a70a6-121">Serializace stromů XML</span><span class="sxs-lookup"><span data-stu-id="a70a6-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="a70a6-122">Strom XML lze serializovat do <xref:System.IO.File> , <xref:System.IO.TextWriter> nebo <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="a70a6-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="a70a6-123">Další informace naleznete v tématu [serializace stromů XML (Visual Basic)](serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="a70a6-123">For more information, see [Serializing XML Trees (Visual Basic)](serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="a70a6-124">Načítání dat XML přes metody osy</span><span class="sxs-lookup"><span data-stu-id="a70a6-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="a70a6-125">Můžete použít metody osy k načtení atributů, podřízených prvků, následníků a nadřazených prvků.</span><span class="sxs-lookup"><span data-stu-id="a70a6-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="a70a6-126">Dotazy LINQ pracují na metodách osy a poskytují několik flexibilních a výkonných způsobů navigace ve stromu XML a zpracování.</span><span class="sxs-lookup"><span data-stu-id="a70a6-126">LINQ queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="a70a6-127">Další informace najdete v tématu [LINQ to XML osy (Visual Basic)](linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="a70a6-127">For more information, see [LINQ to XML Axes (Visual Basic)](linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="a70a6-128">Dotazování na stromy XML</span><span class="sxs-lookup"><span data-stu-id="a70a6-128">Querying XML Trees</span></span>  
 <span data-ttu-id="a70a6-129">Můžete zapisovat dotazy LINQ, které extrahují data ze stromu XML.</span><span class="sxs-lookup"><span data-stu-id="a70a6-129">You can write LINQ queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="a70a6-130">Další informace najdete v tématu [dotazování na stromy XML (Visual Basic)](querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="a70a6-130">For more information, see [Querying XML Trees (Visual Basic)](querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="a70a6-131">Úprava stromů XML</span><span class="sxs-lookup"><span data-stu-id="a70a6-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="a70a6-132">Prvek můžete upravit různými způsoby, včetně změny jeho obsahu nebo atributů.</span><span class="sxs-lookup"><span data-stu-id="a70a6-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="a70a6-133">Můžete také odebrat prvek z jeho nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="a70a6-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="a70a6-134">Další informace najdete v tématu [Úprava stromů XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a70a6-134">For more information, see [Modifying XML Trees (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a70a6-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="a70a6-135">See also</span></span>

- [<span data-ttu-id="a70a6-136">Přehled programování LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a70a6-136">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)
