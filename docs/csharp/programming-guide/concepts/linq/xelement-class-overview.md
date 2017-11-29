---
title: "Přehled třídy XElement (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bd3ffed4f164ac9edc5e46719f516363220c8d63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="cb561-102">Přehled třídy XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="cb561-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="cb561-103"><xref:System.Xml.Linq.XElement> Třída je jedné ze základních tříd v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb561-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="cb561-104">Reprezentuje element, XML.</span><span class="sxs-lookup"><span data-stu-id="cb561-104">It represents an XML element.</span></span> <span data-ttu-id="cb561-105">Tuto třídu můžete použít k vytváření prvků; Změňte obsah elementu; přidat, změnit nebo odstranit podřízené elementy; Přidání atributů do elementu; nebo serializovat obsah elementu v textové podobě.</span><span class="sxs-lookup"><span data-stu-id="cb561-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="cb561-106">Také můžete spolupracovat s jiné třídy v <xref:System.Xml?displayProperty=nameWithType>, jako například <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, a <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="cb561-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="cb561-107">Funkce XElement</span><span class="sxs-lookup"><span data-stu-id="cb561-107">XElement Functionality</span></span>  
 <span data-ttu-id="cb561-108">Toto téma popisuje funkce poskytované službou <xref:System.Xml.Linq.XElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="cb561-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="cb561-109">Vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="cb561-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="cb561-110">Můžete vytvořit stromy XML v mnoha různými způsoby, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="cb561-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
-   <span data-ttu-id="cb561-111">Můžete vytvořit strom XML v kódu.</span><span class="sxs-lookup"><span data-stu-id="cb561-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="cb561-112">Další informace najdete v tématu [vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="cb561-112">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
-   <span data-ttu-id="cb561-113">Můžete analyzovat soubor XML z různých zdrojů, včetně <xref:System.IO.TextReader>, textové soubory nebo webovou adresu (URL).</span><span class="sxs-lookup"><span data-stu-id="cb561-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="cb561-114">Další informace najdete v tématu [analýze XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cb561-114">For more information, see [Parsing XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
-   <span data-ttu-id="cb561-115">Můžete použít <xref:System.Xml.XmlReader> k naplnění stromu.</span><span class="sxs-lookup"><span data-stu-id="cb561-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="cb561-116">Další informace naleznete v tématu <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb561-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
-   <span data-ttu-id="cb561-117">Pokud máte modul, který může zapisovat obsah tak, aby <xref:System.Xml.XmlWriter>, můžete použít <xref:System.Xml.Linq.XContainer.CreateWriter%2A> metodu pro vytvoření zapisovač, zapisovač předat modul a potom používat obsah, který je zapsán do <xref:System.Xml.XmlWriter> k naplnění stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="cb561-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="cb561-118">Však většiny běžných způsob, jak vytvořit strom XML je následující:</span><span class="sxs-lookup"><span data-stu-id="cb561-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="cb561-119">Jiné velmi běžné technika pro vytvoření strom XML, která využívá výsledky [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz k naplnění strom XML, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cb561-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="cb561-120">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cb561-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="cb561-121">Serializace XML stromů</span><span class="sxs-lookup"><span data-stu-id="cb561-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="cb561-122">Může serializovat XML stromu <xref:System.IO.File>, <xref:System.IO.TextWriter>, nebo <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="cb561-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="cb561-123">Další informace najdete v tématu [serializace XML stromů (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="cb561-123">For more information, see [Serializing XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="cb561-124">Načítání dat XML pomocí metody osy</span><span class="sxs-lookup"><span data-stu-id="cb561-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="cb561-125">Metody osy můžete načíst atributy, podřízené elementy, následnickým elementům a nadřazenými prvky.</span><span class="sxs-lookup"><span data-stu-id="cb561-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="cb561-126">dotazy na ose metody pracovat a zadejte několik způsobů pružnější a výkonnější procházení a zpracovat strom XML.</span><span class="sxs-lookup"><span data-stu-id="cb561-126"> queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="cb561-127">Další informace najdete v tématu [technologie LINQ to XML osy (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="cb561-127">For more information, see [LINQ to XML Axes (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="cb561-128">Dotazování stromy XML</span><span class="sxs-lookup"><span data-stu-id="cb561-128">Querying XML Trees</span></span>  
 <span data-ttu-id="cb561-129">Můžete napsat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, které extrahovat data z strom XML.</span><span class="sxs-lookup"><span data-stu-id="cb561-129">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="cb561-130">Další informace najdete v tématu [dotazování stromy XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="cb561-130">For more information, see [Querying XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="cb561-131">Úprava stromy XML</span><span class="sxs-lookup"><span data-stu-id="cb561-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="cb561-132">Element v mnoha různými způsoby, včetně změny jeho obsah nebo atributy, můžete upravit.</span><span class="sxs-lookup"><span data-stu-id="cb561-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="cb561-133">Můžete také odebrat element z jeho nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="cb561-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="cb561-134">Další informace najdete v tématu [úpravy stromů XML (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cb561-134">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb561-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb561-135">See Also</span></span>  
 [<span data-ttu-id="cb561-136">Technologie LINQ to XML přehled programování (C#)</span><span class="sxs-lookup"><span data-stu-id="cb561-136">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
