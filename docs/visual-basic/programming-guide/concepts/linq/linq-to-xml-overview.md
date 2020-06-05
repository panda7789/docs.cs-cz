---
title: Přehled LINQ to XML
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: afdec54ac05bb4a631de7fdb599123ffe964c443
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368735"
---
# <a name="linq-to-xml-overview-visual-basic"></a><span data-ttu-id="fca7c-102">Přehled LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fca7c-102">LINQ to XML Overview (Visual Basic)</span></span>
<span data-ttu-id="fca7c-103">Soubor XML byl široce přijat jako způsob, jak formátovat data v mnoha kontextech.</span><span class="sxs-lookup"><span data-stu-id="fca7c-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="fca7c-104">Můžete například najít XML na webu, v konfiguračních souborech, v systém Microsoft Office soubory aplikace Word a v databázích.</span><span class="sxs-lookup"><span data-stu-id="fca7c-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fca7c-105">je aktuální, přenavržený přístup k programování s XML.</span><span class="sxs-lookup"><span data-stu-id="fca7c-105">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="fca7c-106">Poskytuje funkce pro úpravy dokumentu v paměti model DOM (Document Object Model) (DOM) a podporuje výrazy dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="fca7c-106">It provides the in-memory document-modification capabilities of the Document Object Model (DOM) and supports LINQ query expressions.</span></span> <span data-ttu-id="fca7c-107">I když tyto výrazy dotazu jsou syntakticky odlišné od XPath, poskytují podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="fca7c-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="fca7c-108">LINQ to XML vývojáři</span><span class="sxs-lookup"><span data-stu-id="fca7c-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fca7c-109">cílí na celou řadu vývojářů.</span><span class="sxs-lookup"><span data-stu-id="fca7c-109">targets a variety of developers.</span></span> <span data-ttu-id="fca7c-110">Pro průměrného vývojáře, který chce jenom udělat něco udělat, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usnadňuje XML práci s dotazy, která je podobná SQL.</span><span class="sxs-lookup"><span data-stu-id="fca7c-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="fca7c-111">S pouhou bitovou studiem se programátoři můžou naučit psát stručné a výkonné dotazy v programovacím jazyce, který si vyberete.</span><span class="sxs-lookup"><span data-stu-id="fca7c-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="fca7c-112">Profesionální vývojáři mohou využít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] k výraznému zvýšení produktivity.</span><span class="sxs-lookup"><span data-stu-id="fca7c-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="fca7c-113">Pomocí nástroje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] mohou napsat méně kódu, který je více expresější, kompaktnější a výkonnější.</span><span class="sxs-lookup"><span data-stu-id="fca7c-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="fca7c-114">Můžou používat výrazy dotazů z více domén dat současně.</span><span class="sxs-lookup"><span data-stu-id="fca7c-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="fca7c-115">Co je LINQ to XML?</span><span class="sxs-lookup"><span data-stu-id="fca7c-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fca7c-116">je programovací rozhraní XML v paměti, které umožňuje pracovat s XML v rámci .NET Framework programovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="fca7c-116">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fca7c-117">je podobně jako model DOM (Document Object Model) (DOM) v tom, že převede dokument XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="fca7c-117">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="fca7c-118">Můžete provést dotazování a úpravy dokumentu a až ho upravíte, můžete ho uložit do souboru nebo ho serializovat a poslat přes Internet.</span><span class="sxs-lookup"><span data-stu-id="fca7c-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="fca7c-119">Ale [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] liší se od modelu DOM: poskytuje nový objektový model, který je nevýznamný a usnadňuje práci s a který využívá funkce jazyka v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fca7c-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.</span></span>  
  
 <span data-ttu-id="fca7c-120">Nejdůležitější výhodou je, že [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je její integrace s LINQ (Language-Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="fca7c-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="fca7c-121">Tato integrace umožňuje zapisovat dotazy v dokumentu XML v paměti pro načtení kolekcí prvků a atributů.</span><span class="sxs-lookup"><span data-stu-id="fca7c-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="fca7c-122">Funkce dotazu pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je srovnatelná s funkcemi (i když není v syntaxi) do XPath a XQuery.</span><span class="sxs-lookup"><span data-stu-id="fca7c-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="fca7c-123">Integrace LINQ v Visual Basic poskytuje silnější psaní, kontrolu doby kompilace a vylepšenou podporu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="fca7c-123">The integration of LINQ in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="fca7c-124">Další výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je možnost použít výsledky dotazu jako parametry <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory objektů umožňují účinný přístup k vytváření stromů XML.</span><span class="sxs-lookup"><span data-stu-id="fca7c-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="fca7c-125">Tento přístup s názvem *funkční konstrukce*umožňuje vývojářům snadno transformovat stromy XML z jednoho obrazce na druhý.</span><span class="sxs-lookup"><span data-stu-id="fca7c-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="fca7c-126">Například můžete mít typické nákupní objednávky XML, jak je popsáno v [ukázkovém souboru XML: typická nákupní objednávka (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fca7c-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span> <span data-ttu-id="fca7c-127">Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete spustit následující dotaz pro získání hodnoty atributu číslo součásti pro každý prvek položky v nákupní objednávce:</span><span class="sxs-lookup"><span data-stu-id="fca7c-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 <span data-ttu-id="fca7c-128">Jako další příklad můžete chtít seznam, který je seřazen podle čísla součásti, u položek s hodnotou větší než $100.</span><span class="sxs-lookup"><span data-stu-id="fca7c-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="fca7c-129">Chcete-li získat tyto informace, můžete spustit následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="fca7c-129">To obtain this information, you could run the following query:</span></span>  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 <span data-ttu-id="fca7c-130">Kromě těchto možností LINQ [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje vylepšené programovací rozhraní XML.</span><span class="sxs-lookup"><span data-stu-id="fca7c-130">In addition to these LINQ capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="fca7c-131">Pomocí nástroje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete:</span><span class="sxs-lookup"><span data-stu-id="fca7c-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
- <span data-ttu-id="fca7c-132">Načte XML ze souborů nebo datových proudů.</span><span class="sxs-lookup"><span data-stu-id="fca7c-132">Load XML from files or streams.</span></span>  
  
- <span data-ttu-id="fca7c-133">Serializace XML do souborů nebo datových proudů.</span><span class="sxs-lookup"><span data-stu-id="fca7c-133">Serialize XML to files or streams.</span></span>  
  
- <span data-ttu-id="fca7c-134">Vytvořte XML od začátku pomocí funkční konstrukce.</span><span class="sxs-lookup"><span data-stu-id="fca7c-134">Create XML from scratch by using functional construction.</span></span>  
  
- <span data-ttu-id="fca7c-135">Dotazování XML pomocí osy jako XPath</span><span class="sxs-lookup"><span data-stu-id="fca7c-135">Query XML using XPath-like axes.</span></span>  
  
- <span data-ttu-id="fca7c-136">Manipulace se stromovou strukturou XML v paměti pomocí metod, jako <xref:System.Xml.Linq.XContainer.Add%2A> jsou,, <xref:System.Xml.Linq.XNode.Remove%2A> <xref:System.Xml.Linq.XNode.ReplaceWith%2A> a <xref:System.Xml.Linq.XElement.SetValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="fca7c-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
- <span data-ttu-id="fca7c-137">Ověří stromy XML pomocí XSD.</span><span class="sxs-lookup"><span data-stu-id="fca7c-137">Validate XML trees using XSD.</span></span>  
  
- <span data-ttu-id="fca7c-138">Použijte kombinaci těchto funkcí pro transformaci stromů XML z jednoho obrazce do jiného.</span><span class="sxs-lookup"><span data-stu-id="fca7c-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="fca7c-139">Vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="fca7c-139">Creating XML Trees</span></span>  
 <span data-ttu-id="fca7c-140">IOne s nejvýznamnějšími výhodami programování [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je, že je snadné vytvořit stromy XML.</span><span class="sxs-lookup"><span data-stu-id="fca7c-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="fca7c-141">Například pro vytvoření malého stromu XML můžete napsat kód následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fca7c-141">For example, to create a small XML tree, you can write  code as follows:</span></span>  
  
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
  
 <span data-ttu-id="fca7c-142">Kompilátor Visual Basic překládá literály XML do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] volání metody.</span><span class="sxs-lookup"><span data-stu-id="fca7c-142">The Visual Basic compiler translates XML literals into [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] method calls.</span></span>  
  
 <span data-ttu-id="fca7c-143">Další informace naleznete v tématu [vytváření stromů XML (Visual Basic)](creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="fca7c-143">For more information, see [Creating XML Trees (Visual Basic)](creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fca7c-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="fca7c-144">See also</span></span>

- <xref:System.Xml.Linq>
- [<span data-ttu-id="fca7c-145">Začínáme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="fca7c-145">Getting Started (LINQ to XML)</span></span>](getting-started-linq-to-xml.md)
- [<span data-ttu-id="fca7c-146">Přehled technologie LINQ to XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fca7c-146">Overview of LINQ to XML in Visual Basic</span></span>](../../language-features/xml/overview-of-linq-to-xml.md)
- [<span data-ttu-id="fca7c-147">XML</span><span class="sxs-lookup"><span data-stu-id="fca7c-147">XML</span></span>](../../language-features/xml/index.md)
