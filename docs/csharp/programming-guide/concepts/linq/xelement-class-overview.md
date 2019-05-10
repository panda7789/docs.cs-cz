---
title: Přehled třídy XElement (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: cddb36ac6401c20478a1254fe3d63afe5bd13099
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595765"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="70804-102">Přehled třídy XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="70804-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="70804-103"><xref:System.Xml.Linq.XElement> Třídy je jedním ze základních tříd v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70804-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="70804-104">Reprezentuje XML element.</span><span class="sxs-lookup"><span data-stu-id="70804-104">It represents an XML element.</span></span> <span data-ttu-id="70804-105">Tato třída slouží k vytváření prvků; Změňte obsah elementu; Přidání, změna nebo odstranění podřízené elementy; přidat atributy pro element. nebo serializace obsah prvek v textové podobě.</span><span class="sxs-lookup"><span data-stu-id="70804-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="70804-106">Můžete také spolupracovat s jinými třídami v <xref:System.Xml?displayProperty=nameWithType>, jako například <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, a <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="70804-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="70804-107">Funkce XElement</span><span class="sxs-lookup"><span data-stu-id="70804-107">XElement Functionality</span></span>  
 <span data-ttu-id="70804-108">Toto téma popisuje funkce poskytované službou <xref:System.Xml.Linq.XElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="70804-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="70804-109">Vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="70804-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="70804-110">Můžete sestavit stromů XML v celou řadu způsobů, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="70804-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="70804-111">Můžete vytvořit stromu XML v kódu.</span><span class="sxs-lookup"><span data-stu-id="70804-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="70804-112">Další informace najdete v tématu [vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="70804-112">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
- <span data-ttu-id="70804-113">Můžete analyzovat soubor XML z různých zdrojů, včetně <xref:System.IO.TextReader>, textové soubory nebo webovou adresu (URL).</span><span class="sxs-lookup"><span data-stu-id="70804-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="70804-114">Další informace najdete v tématu [analýza kódu XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="70804-114">For more information, see [Parsing XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
- <span data-ttu-id="70804-115">Můžete použít <xref:System.Xml.XmlReader> k naplnění stromu.</span><span class="sxs-lookup"><span data-stu-id="70804-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="70804-116">Další informace naleznete v tématu <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="70804-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="70804-117">Pokud máte modul, který může zapisovat obsah tak, aby <xref:System.Xml.XmlWriter>, můžete použít <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metodu pro vytvoření zapisovač, předat modul pro zápis do modulu a pak použít obsah, který je zapsán do <xref:System.Xml.XmlWriter> k naplnění stromu XML.</span><span class="sxs-lookup"><span data-stu-id="70804-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="70804-118">Nejběžnější způsob, jak vytvořit stromu XML je však následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="70804-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="70804-119">Zahrnuje jiného velmi běžná technika pro vytvoření stromu XML pomocí výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu k naplnění stromu XML, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="70804-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="70804-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="70804-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="70804-121">Serializace stromů XML</span><span class="sxs-lookup"><span data-stu-id="70804-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="70804-122">Může serializovat stromu XML <xref:System.IO.File>, <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="70804-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="70804-123">Další informace najdete v tématu [serializace stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="70804-123">For more information, see [Serializing XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="70804-124">Načítání dat XML pomocí metody osy</span><span class="sxs-lookup"><span data-stu-id="70804-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="70804-125">Načíst atributy, podřízené prvky, následnickým elementům a nadřazených elementů můžete použít metody osy.</span><span class="sxs-lookup"><span data-stu-id="70804-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="70804-126">dotazy pracovat na metody osy a poskytují několik pružnější a výkonnější způsobů, jak procházet a zpracování stromu XML.</span><span class="sxs-lookup"><span data-stu-id="70804-126">queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="70804-127">Další informace najdete v tématu [osy LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="70804-127">For more information, see [LINQ to XML Axes (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="70804-128">Dotazování na stromy XML</span><span class="sxs-lookup"><span data-stu-id="70804-128">Querying XML Trees</span></span>  
 <span data-ttu-id="70804-129">Můžete napsat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, které extrahují data z stromu XML.</span><span class="sxs-lookup"><span data-stu-id="70804-129">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="70804-130">Další informace najdete v tématu [dotazování na stromy XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="70804-130">For more information, see [Querying XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="70804-131">Změna stromů XML</span><span class="sxs-lookup"><span data-stu-id="70804-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="70804-132">Můžete upravovat prvek v celou řadu způsobů, včetně změny jeho obsahu nebo atributů.</span><span class="sxs-lookup"><span data-stu-id="70804-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="70804-133">Můžete také odebrat element ze svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="70804-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="70804-134">Další informace najdete v tématu [změna stromů XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="70804-134">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70804-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70804-135">See also</span></span>

- [<span data-ttu-id="70804-136">Přehled LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="70804-136">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
