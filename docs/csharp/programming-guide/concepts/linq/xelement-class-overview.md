---
title: Přehled třídy XElement (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 6a93dd4bdaf16fddff800b08b0f3146ecb63f9b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167891"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="47969-102">Přehled třídy XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="47969-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="47969-103">Třída <xref:System.Xml.Linq.XElement> je jednou ze základních [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]tříd v .</span><span class="sxs-lookup"><span data-stu-id="47969-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="47969-104">Představuje element XML.</span><span class="sxs-lookup"><span data-stu-id="47969-104">It represents an XML element.</span></span> <span data-ttu-id="47969-105">Tuto třídu můžete použít k vytvoření prvků; změnit obsah prvku; přidání, změna nebo odstranění podřízených prvků; přidat atributy k prvku; nebo serializovat obsah prvku v textové podobě.</span><span class="sxs-lookup"><span data-stu-id="47969-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="47969-106">Můžete také spolupracovat s jinými třídami <xref:System.Xml?displayProperty=nameWithType>v , například <xref:System.Xml.XmlReader>v , <xref:System.Xml.XmlWriter>a <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="47969-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
<span data-ttu-id="47969-107">Toto téma popisuje funkce poskytované <xref:System.Xml.Linq.XElement> třídou.</span><span class="sxs-lookup"><span data-stu-id="47969-107">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
## <a name="constructing-xml-trees"></a><span data-ttu-id="47969-108">Vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="47969-108">Constructing XML Trees</span></span>  
 <span data-ttu-id="47969-109">Stromy XML můžete vytvářet různými způsoby, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="47969-109">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="47969-110">Můžete vytvořit strom XML v kódu.</span><span class="sxs-lookup"><span data-stu-id="47969-110">You can construct an XML tree in code.</span></span> <span data-ttu-id="47969-111">Další informace naleznete [v tématu Creating XML Trees (C#)](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="47969-111">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
- <span data-ttu-id="47969-112">Xml můžete analyzovat z různých zdrojů, včetně textových <xref:System.IO.TextReader>souborů nebo webové adresy (URL).</span><span class="sxs-lookup"><span data-stu-id="47969-112">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="47969-113">Další informace naleznete [v tématu Analýza XML (C#)](./how-to-parse-a-string.md).</span><span class="sxs-lookup"><span data-stu-id="47969-113">For more information, see [Parsing XML (C#)](./how-to-parse-a-string.md).</span></span>  
  
- <span data-ttu-id="47969-114">Můžete použít <xref:System.Xml.XmlReader> k naplnění stromu.</span><span class="sxs-lookup"><span data-stu-id="47969-114">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="47969-115">Další informace naleznete v tématu <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="47969-115">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="47969-116">Pokud máte modul, který může <xref:System.Xml.XmlWriter>psát obsah do <xref:System.Xml.Linq.XContainer.CreateWriter%2A> , můžete použít metodu k vytvoření zapisovače, předat <xref:System.Xml.XmlWriter> zapisovatele do modulu a potom použít obsah, který je zapsán do stromu XML.</span><span class="sxs-lookup"><span data-stu-id="47969-116">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="47969-117">Nejběžnější způsob vytvoření stromu XML je však následující:</span><span class="sxs-lookup"><span data-stu-id="47969-117">However, the most common way to create an XML tree is as follows:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="47969-118">Další velmi běžná technika pro vytvoření stromu XML zahrnuje použití výsledků dotazu LINQ k naplnění stromu XML, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="47969-118">Another very common technique for creating an XML tree involves using the results of a LINQ query to populate an XML tree, as shown in the following example:</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 <span data-ttu-id="47969-119">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="47969-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a><span data-ttu-id="47969-120">Serializace stromů XML</span><span class="sxs-lookup"><span data-stu-id="47969-120">Serializing XML Trees</span></span>  
 <span data-ttu-id="47969-121">Strom XML můžete serializovat do <xref:System.IO.File>, <xref:System.IO.TextWriter>a <xref:System.Xml.XmlWriter>nebo .</span><span class="sxs-lookup"><span data-stu-id="47969-121">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="47969-122">Další informace naleznete [v tématu Serializing XML Trees (C#)](./preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="47969-122">For more information, see [Serializing XML Trees (C#)](./preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="47969-123">Načítání dat XML pomocí metod osy</span><span class="sxs-lookup"><span data-stu-id="47969-123">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="47969-124">Metody osy můžete použít k načtení atributů, podřízených prvků, potomků prvků a prvků nadřazených prvků.</span><span class="sxs-lookup"><span data-stu-id="47969-124">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="47969-125">Linq dotazy pracují na metodách osy a poskytují několik flexibilních a účinných způsobů procházení a zpracování stromu XML.</span><span class="sxs-lookup"><span data-stu-id="47969-125">LINQ queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="47969-126">Další informace naleznete v tématu [LINQ to XML Axes (C#)](./linq-to-xml-axes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="47969-126">For more information, see [LINQ to XML Axes (C#)](./linq-to-xml-axes-overview.md).</span></span>  
  
## <a name="querying-xml-trees"></a><span data-ttu-id="47969-127">Dotazování na stromy XML</span><span class="sxs-lookup"><span data-stu-id="47969-127">Querying XML Trees</span></span>  
 <span data-ttu-id="47969-128">Můžete psát dotazy LINQ, které extrahují data ze stromu XML.</span><span class="sxs-lookup"><span data-stu-id="47969-128">You can write LINQ queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="47969-129">Další informace naleznete v [tématu Querying XML Trees (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="47969-129">For more information, see [Querying XML Trees (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span></span>  
  
## <a name="modifying-xml-trees"></a><span data-ttu-id="47969-130">Úprava mezistromy XML</span><span class="sxs-lookup"><span data-stu-id="47969-130">Modifying XML Trees</span></span>  
 <span data-ttu-id="47969-131">Prvek můžete upravit různými způsoby, včetně změny jeho obsahu nebo atributů.</span><span class="sxs-lookup"><span data-stu-id="47969-131">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="47969-132">Můžete také odebrat prvek z jeho nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="47969-132">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="47969-133">Další informace naleznete [v tématu Úprava stromů XML (LINQ na XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="47969-133">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47969-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="47969-134">See also</span></span>

- [<span data-ttu-id="47969-135">Přehled programování LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="47969-135">LINQ to XML Programming Overview (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
