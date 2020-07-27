---
title: Přehled LINQ to XML (C#)
description: LINQ to XML využívá rozhraní .NET LINQ Framework k poskytnutí možností úprav dokumentů v paměti a výrazů dotazů s funkcemi jako XPath.
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: d2e4cf4e63d1a6ed7c1f0c163c12bb422b55ba11
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165358"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="1d8d6-103">Přehled LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="1d8d6-103">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="1d8d6-104">LINQ to XML poskytuje rozhraní pro programování XML v paměti, které využívá architekturu LINQ (Integrated Query) jazyka .NET.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-104">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="1d8d6-105">LINQ to XML využívá možnosti rozhraní .NET a je porovnatelný z aktualizovaného a přepracovaného programovacího rozhraní XML model DOM (Document Object Model) (DOM).</span><span class="sxs-lookup"><span data-stu-id="1d8d6-105">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span>

<span data-ttu-id="1d8d6-106">Soubor XML byl široce přijat jako způsob, jak formátovat data v mnoha kontextech.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-106">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="1d8d6-107">Můžete například najít XML na webu, v konfiguračních souborech, v systém Microsoft Office soubory aplikace Word a v databázích.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-107">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1d8d6-108">je aktuální, přenavržený přístup k programování s XML.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-108">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="1d8d6-109">Poskytuje funkce pro úpravy dokumentů v paměti model DOM (Document Object Model) (DOM) a podporuje výrazy dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-109">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span> <span data-ttu-id="1d8d6-110">I když tyto výrazy dotazu jsou syntakticky odlišné od XPath, poskytují podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-110">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="1d8d6-111">LINQ to XML vývojáři</span><span class="sxs-lookup"><span data-stu-id="1d8d6-111">LINQ to XML Developers</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1d8d6-112">cílí na celou řadu vývojářů.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-112">targets a variety of developers.</span></span> <span data-ttu-id="1d8d6-113">Pro průměrného vývojáře, který chce jenom udělat něco udělat, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usnadňuje XML práci s dotazy, která je podobná SQL.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-113">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="1d8d6-114">S pouhou bitovou studiem se programátoři můžou naučit psát stručné a výkonné dotazy v programovacím jazyce, který si vyberete.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-114">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="1d8d6-115">Profesionální vývojáři mohou využít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] k výraznému zvýšení produktivity.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-115">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="1d8d6-116">Pomocí nástroje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] mohou napsat méně kódu, který je více expresější, kompaktnější a výkonnější.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-116">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="1d8d6-117">Můžou používat výrazy dotazů z více domén dat současně.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-117">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="1d8d6-118">Co je LINQ to XML?</span><span class="sxs-lookup"><span data-stu-id="1d8d6-118">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1d8d6-119">je programovací rozhraní XML v paměti, které umožňuje pracovat s XML v programovacích jazycích .NET.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-119">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET programming languages.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1d8d6-120">je podobně jako model DOM (Document Object Model) (DOM) v tom, že převede dokument XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-120">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="1d8d6-121">Můžete provést dotazování a úpravy dokumentu a až ho upravíte, můžete ho uložit do souboru nebo ho serializovat a poslat přes Internet.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-121">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="1d8d6-122">Nicméně [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se liší od modelu DOM: poskytuje nový objektový model, který je světlejší o váhu a usnadňuje práci s a který využívá funkce jazyka v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-122">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="1d8d6-123">Nejdůležitější výhodou je, že [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je její integrace s LINQ (Language-Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="1d8d6-123">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="1d8d6-124">Tato integrace umožňuje zapisovat dotazy v dokumentu XML v paměti pro načtení kolekcí prvků a atributů.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-124">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="1d8d6-125">Funkce dotazu pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je srovnatelná s funkcemi (i když není v syntaxi) do XPath a XQuery.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-125">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="1d8d6-126">Integrace LINQ v jazyce C# nabízí silnější psaní, kontrolu doby kompilace a vylepšenou podporu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-126">The integration of LINQ in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="1d8d6-127">Další výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je možnost použít výsledky dotazu jako parametry <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory objektů umožňují účinný přístup k vytváření stromů XML.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-127">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="1d8d6-128">Tento přístup s názvem *funkční konstrukce*umožňuje vývojářům snadno transformovat stromy XML z jednoho obrazce na druhý.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-128">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="1d8d6-129">Například můžete mít typické nákupní objednávky XML, jak je popsáno v [ukázkovém souboru XML: typická nákupní objednávka (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="1d8d6-129">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="1d8d6-130">Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete spustit následující dotaz pro získání hodnoty atributu číslo součásti pro každý prvek položky v nákupní objednávce:</span><span class="sxs-lookup"><span data-stu-id="1d8d6-130">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="1d8d6-131">Toto lze přepsat ve formě syntaxe metody:</span><span class="sxs-lookup"><span data-stu-id="1d8d6-131">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="1d8d6-132">Jako další příklad můžete chtít seznam, který je seřazen podle čísla součásti, u položek s hodnotou větší než $100.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-132">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="1d8d6-133">Chcete-li získat tyto informace, můžete spustit následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="1d8d6-133">To obtain this information, you could run the following query:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

<span data-ttu-id="1d8d6-134">Tuto akci lze znovu zapsat ve formě syntaxe metody:</span><span class="sxs-lookup"><span data-stu-id="1d8d6-134">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="1d8d6-135">Kromě těchto možností LINQ [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje vylepšené programovací rozhraní XML.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-135">In addition to these LINQ capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="1d8d6-136">Pomocí nástroje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete:</span><span class="sxs-lookup"><span data-stu-id="1d8d6-136">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="1d8d6-137">Načte XML ze [souborů](how-to-load-xml-from-a-file.md) nebo [datových proudů](how-to-stream-xml-fragments-from-an-xmlreader.md).</span><span class="sxs-lookup"><span data-stu-id="1d8d6-137">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="1d8d6-138">Serializace XML do souborů nebo datových proudů.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-138">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="1d8d6-139">Vytvořte XML od začátku pomocí funkční konstrukce.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-139">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="1d8d6-140">Dotazování XML pomocí osy jako XPath</span><span class="sxs-lookup"><span data-stu-id="1d8d6-140">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="1d8d6-141">Manipulace se stromovou strukturou XML v paměti pomocí metod, jako <xref:System.Xml.Linq.XContainer.Add%2A> jsou,, <xref:System.Xml.Linq.XNode.Remove%2A> <xref:System.Xml.Linq.XNode.ReplaceWith%2A> a <xref:System.Xml.Linq.XElement.SetValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="1d8d6-141">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="1d8d6-142">Ověří stromy XML pomocí XSD.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-142">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="1d8d6-143">Použijte kombinaci těchto funkcí pro transformaci stromů XML z jednoho obrazce do jiného.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-143">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="1d8d6-144">Vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="1d8d6-144">Creating XML Trees</span></span>

<span data-ttu-id="1d8d6-145">Jednou z nejvýznamnějších výhod programování [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je, že je snadné vytvořit stromy XML.</span><span class="sxs-lookup"><span data-stu-id="1d8d6-145">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="1d8d6-146">Například pro vytvoření malého stromu XML můžete napsat kód následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="1d8d6-146">For example, to create a small XML tree, you can write code as follows:</span></span>

```csharp
XElement contacts =
new XElement("Contacts",
    new XElement("Contact",
        new XElement("Name", "Patrick Hines"),
        new XElement("Phone", "206-555-0144",
            new XAttribute("Type", "Home")),
        new XElement("phone", "425-555-0145",
            new XAttribute("Type", "Work")),
        new XElement("Address",
            new XElement("Street1", "123 Main St"),
            new XElement("City", "Mercer Island"),
            new XElement("State", "WA"),
            new XElement("Postal", "68042")
        )
    )
);
```

<span data-ttu-id="1d8d6-147">Další informace naleznete v tématu [vytváření stromů XML (C#)](./creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="1d8d6-147">For more information, see [Creating XML Trees (C#)](./creating-xml-trees-linq-to-xml-2.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d8d6-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d8d6-148">See also</span></span>

- [<span data-ttu-id="1d8d6-149">Referenční informace (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="1d8d6-149">Reference (LINQ to XML)</span></span>](./reference-linq-to-xml.md)
- [<span data-ttu-id="1d8d6-150">LINQ to XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="1d8d6-150">LINQ to XML vs. DOM (C#)</span></span>](./linq-to-xml-vs-dom.md)
- [<span data-ttu-id="1d8d6-151">Technologie LINQ to XML vs. jiné technologie XML</span><span class="sxs-lookup"><span data-stu-id="1d8d6-151">LINQ to XML vs. Other XML Technologies</span></span>](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
