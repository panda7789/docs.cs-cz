---
title: XElement – Přehled třídyC#()
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: e742741f56f3e39f93b9f1d6be30a54a4ede67f3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590891"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="c012c-102">XElement – Přehled třídyC#()</span><span class="sxs-lookup"><span data-stu-id="c012c-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="c012c-103">Třída je jednou ze základních tříd v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c012c-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="c012c-104">Představuje XML element.</span><span class="sxs-lookup"><span data-stu-id="c012c-104">It represents an XML element.</span></span> <span data-ttu-id="c012c-105">Tuto třídu můžete použít k vytváření elementů. změnit obsah elementu; Přidání, změna nebo odstranění podřízených elementů; přidejte atributy k elementu; nebo serializovat obsah elementu v textovém formuláři.</span><span class="sxs-lookup"><span data-stu-id="c012c-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="c012c-106">Můžete také vzájemně spolupracovat s jinými třídami <xref:System.Xml?displayProperty=nameWithType>v, <xref:System.Xml.XmlReader>jako například <xref:System.Xml.XmlWriter>, a <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="c012c-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
<span data-ttu-id="c012c-107">Toto téma popisuje funkce poskytované <xref:System.Xml.Linq.XElement> třídou.</span><span class="sxs-lookup"><span data-stu-id="c012c-107">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
## <a name="constructing-xml-trees"></a><span data-ttu-id="c012c-108">Sestavování stromů XML</span><span class="sxs-lookup"><span data-stu-id="c012c-108">Constructing XML Trees</span></span>  
 <span data-ttu-id="c012c-109">Stromy XML můžete vytvářet různými způsoby, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="c012c-109">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="c012c-110">V kódu můžete vytvořit strom XML.</span><span class="sxs-lookup"><span data-stu-id="c012c-110">You can construct an XML tree in code.</span></span> <span data-ttu-id="c012c-111">Další informace naleznete v tématu [CREATING XML TreesC#()](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c012c-111">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
- <span data-ttu-id="c012c-112">Můžete analyzovat XML z různých zdrojů, včetně <xref:System.IO.TextReader>textových souborů nebo webové adresy (URL).</span><span class="sxs-lookup"><span data-stu-id="c012c-112">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="c012c-113">Další informace najdete v tématu [Analýza XML (C#)](./how-to-parse-a-string.md).</span><span class="sxs-lookup"><span data-stu-id="c012c-113">For more information, see [Parsing XML (C#)](./how-to-parse-a-string.md).</span></span>  
  
- <span data-ttu-id="c012c-114"><xref:System.Xml.XmlReader> K naplnění stromu můžete použít.</span><span class="sxs-lookup"><span data-stu-id="c012c-114">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="c012c-115">Další informace naleznete v tématu <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="c012c-115">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="c012c-116">Máte-li modul, který může zapisovat obsah do, <xref:System.Xml.XmlWriter>můžete <xref:System.Xml.Linq.XContainer.CreateWriter%2A> použít metodu k vytvoření zapisovače, předat zapisovači modulu a potom použít obsah <xref:System.Xml.XmlWriter> , který je zapsán do objektu k naplnění stromu XML.</span><span class="sxs-lookup"><span data-stu-id="c012c-116">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="c012c-117">Nejběžnější způsob vytvoření stromu XML je však následující:</span><span class="sxs-lookup"><span data-stu-id="c012c-117">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="c012c-118">Další velmi běžné postupy pro vytváření stromu XML zahrnuje použití výsledků [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu k naplnění stromu XML, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c012c-118">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="c012c-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c012c-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a><span data-ttu-id="c012c-120">Serializace stromů XML</span><span class="sxs-lookup"><span data-stu-id="c012c-120">Serializing XML Trees</span></span>  
 <span data-ttu-id="c012c-121">Strom XML lze serializovat do <xref:System.IO.File> <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="c012c-121">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="c012c-122">Další informace naleznete v tématu [serializace stromů XML (C#)](./preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="c012c-122">For more information, see [Serializing XML Trees (C#)](./preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="c012c-123">Načítání dat XML přes metody osy</span><span class="sxs-lookup"><span data-stu-id="c012c-123">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="c012c-124">Můžete použít metody osy k načtení atributů, podřízených prvků, následníků a nadřazených prvků.</span><span class="sxs-lookup"><span data-stu-id="c012c-124">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="c012c-125">dotazy fungují na metodách osy a poskytují několik flexibilních a výkonných způsobů navigace ve stromu XML a zpracování.</span><span class="sxs-lookup"><span data-stu-id="c012c-125">queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="c012c-126">Další informace najdete v tématu [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c012c-126">For more information, see [LINQ to XML Axes (C#)](./linq-to-xml-axes-overview.md).</span></span>  
  
## <a name="querying-xml-trees"></a><span data-ttu-id="c012c-127">Dotazování na stromy XML</span><span class="sxs-lookup"><span data-stu-id="c012c-127">Querying XML Trees</span></span>  
 <span data-ttu-id="c012c-128">Můžete zapisovat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, které extrahují data ze stromu XML.</span><span class="sxs-lookup"><span data-stu-id="c012c-128">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="c012c-129">Další informace najdete v tématu [dotazování na stromy XMLC#()](./how-to-find-an-element-with-a-specific-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="c012c-129">For more information, see [Querying XML Trees (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span></span>  
  
## <a name="modifying-xml-trees"></a><span data-ttu-id="c012c-130">Úprava stromů XML</span><span class="sxs-lookup"><span data-stu-id="c012c-130">Modifying XML Trees</span></span>  
 <span data-ttu-id="c012c-131">Prvek můžete upravit různými způsoby, včetně změny jeho obsahu nebo atributů.</span><span class="sxs-lookup"><span data-stu-id="c012c-131">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="c012c-132">Můžete také odebrat prvek z jeho nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="c012c-132">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="c012c-133">Další informace najdete v tématu [Úprava stromů XML (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c012c-133">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c012c-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c012c-134">See also</span></span>

- [<span data-ttu-id="c012c-135">Přehled programování LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c012c-135">LINQ to XML Programming Overview (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
