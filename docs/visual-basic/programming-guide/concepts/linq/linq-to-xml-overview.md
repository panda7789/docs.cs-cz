---
title: Technologie LINQ to XML přehled (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f4ccc81f1f7b875c7388dc09cc45521c6257c00d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="linq-to-xml-overview-visual-basic"></a><span data-ttu-id="4c1a9-102">Technologie LINQ to XML přehled (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c1a9-102">LINQ to XML Overview (Visual Basic)</span></span>
<span data-ttu-id="4c1a9-103">XML byl široce přijat jako způsob formátování dat v mnoha kontexty.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="4c1a9-104">Například můžete vyhledat XML na webu, konfigurační soubory, soubory Microsoft Office Word a databází.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="4c1a9-105"> je aktuální, přepracovanou přístup k programování se souborem XML.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-105"> is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="4c1a9-106">Poskytuje možnosti úprav z objektu modelu dokumentu (DOM) v dokumentu v paměti a podporuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz výrazy.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="4c1a9-107">I když jsou tyto výrazy dotazů syntakticky liší od jazyka XPath, poskytují podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="4c1a9-108">Technologie LINQ to XML vývojáři</span><span class="sxs-lookup"><span data-stu-id="4c1a9-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="4c1a9-109"> cílem celou řadu vývojáři.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-109"> targets a variety of developers.</span></span> <span data-ttu-id="4c1a9-110">Pro průměrné vývojáře, kteří právě chce získat něco udělat [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usnadňuje XML tím, že poskytuje podobné do SQL možnosti dotazu.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="4c1a9-111">S jenom kousek studii můžete postup programátory v jazyce psát dotazy stručného a výkonné v jejich programovací jazyk podle volby.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="4c1a9-112">Můžete použít profesionální vývojáře [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] výrazně zvýšit produktivitu.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="4c1a9-113">S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mohou zapisovat menší kód, který je více výrazovou, kompaktnější a účinnější.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="4c1a9-114">Výrazy dotazů použitím z několika domén dat ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="4c1a9-115">Co je technologie LINQ to XML?</span><span class="sxs-lookup"><span data-stu-id="4c1a9-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="4c1a9-116"> je povolené LINQ, v paměti XML programovací rozhraní, které umožňuje pracovat s XML uvnitř [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-116"> is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="4c1a9-117"> jako objektu modelu dokumentu (DOM) je v tom, že přináší dokumentu XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-117"> is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="4c1a9-118">Můžete vyhledat a upravit dokumentu, a po úpravě ho můžete uložit do souboru nebo jej serializovat a poslat přes Internet.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="4c1a9-119">Ale [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se liší od DOM: poskytuje nový model objektu, který je světlejší váhy a snadnější pracovat, a který využívá funkce jazyka v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.</span></span>  
  
 <span data-ttu-id="4c1a9-120">Nejdůležitější výhod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je své integraci s [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4c1a9-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="4c1a9-121">Tato integrace umožňuje psát dotazy na dokument XML v paměti pro načtení kolekce elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="4c1a9-122">Funkce dotazu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je srovnatelná ve funkcích (i když není v syntaxi) XPath a XQuery.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="4c1a9-123">Integrace [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] v jazyce Visual Basic poskytuje silnější zadáte, kompilace kontrolu a vylepšenou podporu ladicí program.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="4c1a9-124">Další výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je schopnost používat výsledky dotazu jako parametry pro <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory umožňuje efektivní přístup pro vytváření stromů XML.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="4c1a9-125">Tuto metodu volá *funkční konstrukce*, umožňuje vývojářům snadno transformace stromy XML z jednoho obrazce do jiného.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="4c1a9-126">Například můžete mít typické XML nákupní objednávka, jak je popsáno v [ukázkový soubor XML: typické nákupní objednávka (technologie LINQ to XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348).</span><span class="sxs-lookup"><span data-stu-id="4c1a9-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348).</span></span> <span data-ttu-id="4c1a9-127">Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete spustit následující dotaz pro získání část hodnoty číslo atribut pro každý element položky v nákupní objednávka:</span><span class="sxs-lookup"><span data-stu-id="4c1a9-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 <span data-ttu-id="4c1a9-128">Například můžete seznam seřadit podle počtu část položky s hodnotou větší než 100 USD.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="4c1a9-129">Chcete-li získat tyto informace, můžete spustit následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="4c1a9-129">To obtain this information, you could run the following query:</span></span>  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 <span data-ttu-id="4c1a9-130">Kromě těchto [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] možnosti, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje vylepšené programovací rozhraní XML.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-130">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="4c1a9-131">Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete:</span><span class="sxs-lookup"><span data-stu-id="4c1a9-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
-   <span data-ttu-id="4c1a9-132">Načtení XML ze souborů nebo datových proudů.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-132">Load XML from files or streams.</span></span>  
  
-   <span data-ttu-id="4c1a9-133">Serializace XML na soubory nebo datové proudy.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-133">Serialize XML to files or streams.</span></span>  
  
-   <span data-ttu-id="4c1a9-134">Vytvoření XML od začátku pomocí funkční konstrukce.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-134">Create XML from scratch by using functional construction.</span></span>  
  
-   <span data-ttu-id="4c1a9-135">Dotaz pomocí jazyka XPath jako osy XML.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-135">Query XML using XPath-like axes.</span></span>  
  
-   <span data-ttu-id="4c1a9-136">Manipulace s stromu XML v paměti pomocí metody <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, a <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
-   <span data-ttu-id="4c1a9-137">Ověření XML stromy pomocí XSD.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-137">Validate XML trees using XSD.</span></span>  
  
-   <span data-ttu-id="4c1a9-138">Použijte kombinaci těchto funkcí k transformaci stromy XML z jednoho obrazce do jiné.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="4c1a9-139">Vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="4c1a9-139">Creating XML Trees</span></span>  
 <span data-ttu-id="4c1a9-140">IOne nejvýznamnějších výhod programování s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je, že je snadné vytvořit stromy XML.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="4c1a9-141">Například pokud chcete vytvořit malé stromu XML, můžete napsat kód následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4c1a9-141">For example, to create a small XML tree, you can write  code as follows:</span></span>  
  
```vb  
Dim contacts = _  
<Contacts>  
    <Contact>  
        <Name>Patrick Hines</Name>  
        <Phone Type="Home">206-555-0144</Phone>  
        <Phone Type="Work">425-555-0145</Phone>  
        <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
        </Address>  
    </Contact>  
</Contacts>  
```  
  
 <span data-ttu-id="4c1a9-142">Visual Basic – kompilátor překládá literálů XML do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] volání metody.</span><span class="sxs-lookup"><span data-stu-id="4c1a9-142">The Visual Basic compiler translates XML literals into [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] method calls.</span></span>  
  
 <span data-ttu-id="4c1a9-143">Další informace najdete v tématu [vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="4c1a9-143">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c1a9-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c1a9-144">See Also</span></span>  
 <xref:System.Xml.Linq>  
 [<span data-ttu-id="4c1a9-145">Začínáme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="4c1a9-145">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
 [<span data-ttu-id="4c1a9-146">Přehled technologie LINQ to XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4c1a9-146">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 [<span data-ttu-id="4c1a9-147">XML</span><span class="sxs-lookup"><span data-stu-id="4c1a9-147">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
