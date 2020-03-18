---
title: LinQ na XML Přehled (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 334788a50832b8fe42ecc9a3272dd71f2f2af4ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168412"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="dbab5-102">LinQ na XML Přehled (C#)</span><span class="sxs-lookup"><span data-stu-id="dbab5-102">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="dbab5-103">LINQ na XML poskytuje programovací rozhraní XML v paměti, které využívá rozhraní LINQ (Language-Integrated Query) .NET.NET to XML provides a in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span><span class="sxs-lookup"><span data-stu-id="dbab5-103">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="dbab5-104">LINQ to XML používá možnosti rozhraní .NET a je srovnatelný s aktualizovaným přepracovaným programovacím rozhraním XML objektového modelu dokumentu (DOM).</span><span class="sxs-lookup"><span data-stu-id="dbab5-104">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span>

<span data-ttu-id="dbab5-105">Jazyk XML byl široce přijat jako způsob formátování dat v mnoha kontextech.</span><span class="sxs-lookup"><span data-stu-id="dbab5-105">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="dbab5-106">Xml můžete například najít na webu, v konfiguračních souborech, v souborech aplikace Microsoft Office Word a v databázích.</span><span class="sxs-lookup"><span data-stu-id="dbab5-106">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="dbab5-107">je aktuální, přepracovaný přístup k programování pomocí XML.</span><span class="sxs-lookup"><span data-stu-id="dbab5-107">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="dbab5-108">Poskytuje možnosti úpravy dokumentu v paměti modelu DOCUMENT Object Model (DOM) a podporuje výrazy dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="dbab5-108">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span> <span data-ttu-id="dbab5-109">Přestože tyto výrazy dotazu jsou syntakticky odlišné od XPath, poskytují podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="dbab5-109">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="dbab5-110">LINQ vývojářům XML</span><span class="sxs-lookup"><span data-stu-id="dbab5-110">LINQ to XML Developers</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="dbab5-111">zaměřuje na různé vývojáře.</span><span class="sxs-lookup"><span data-stu-id="dbab5-111">targets a variety of developers.</span></span> <span data-ttu-id="dbab5-112">Pro průměrného vývojáře, který chce [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jen něco udělat, usnadňuje XML tím, že poskytuje prostředí dotazu, které je podobné SQL.</span><span class="sxs-lookup"><span data-stu-id="dbab5-112">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="dbab5-113">S trochou studia se programátoři mohou naučit psát stručné a výkonné dotazy ve svém programovacím jazyce.</span><span class="sxs-lookup"><span data-stu-id="dbab5-113">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="dbab5-114">Profesionální vývojáři [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] mohou využít k výraznému zvýšení jejich produktivity.</span><span class="sxs-lookup"><span data-stu-id="dbab5-114">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="dbab5-115">S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mohou psát méně kódu, který je výraznější, kompaktnější a výkonnější.</span><span class="sxs-lookup"><span data-stu-id="dbab5-115">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="dbab5-116">Mohou používat výrazy dotazu z více datových domén současně.</span><span class="sxs-lookup"><span data-stu-id="dbab5-116">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="dbab5-117">Co je LINQ na XML?</span><span class="sxs-lookup"><span data-stu-id="dbab5-117">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="dbab5-118">je programovací rozhraní XML s podporou linq v paměti, které umožňuje pracovat s jazykem XML z programovacích jazyků rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dbab5-118">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="dbab5-119">je jako document object model (DOM) v tom, že přináší dokument XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="dbab5-119">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="dbab5-120">Dokument můžete dotazovat a upravovat a po jeho úpravě jej můžete uložit do souboru nebo jej serializovat a odeslat přes Internet.</span><span class="sxs-lookup"><span data-stu-id="dbab5-120">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="dbab5-121">Liší [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se však od modelu DOM: Poskytuje nový objektový model, který je lehčí a snadněji se s ním pracuje a který využívá funkce jazyka v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="dbab5-121">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="dbab5-122">Nejdůležitější výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je jeho integrace s jazykem integrovaný dotaz (LINQ).</span><span class="sxs-lookup"><span data-stu-id="dbab5-122">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="dbab5-123">Tato integrace umožňuje psát dotazy na dokument XML v paměti k načtení kolekcí prvků a atributů.</span><span class="sxs-lookup"><span data-stu-id="dbab5-123">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="dbab5-124">Možnost dotazu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je srovnatelná ve funkčnosti (i když ne v syntaxi) s XPath a XQuery.</span><span class="sxs-lookup"><span data-stu-id="dbab5-124">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="dbab5-125">Integrace LINQ v C# poskytuje silnější psaní, kontrolu v době kompilace a vylepšenou podporu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="dbab5-125">The integration of LINQ in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="dbab5-126">Další výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je možnost použít výsledky dotazu <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> jako parametry a konstruktory objektů umožňuje výkonný přístup k vytváření stromů XML.</span><span class="sxs-lookup"><span data-stu-id="dbab5-126">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="dbab5-127">Tento přístup, nazývaný *funkční konstrukce*, umožňuje vývojářům snadno transformovat stromy XML z jednoho obrazce do druhého.</span><span class="sxs-lookup"><span data-stu-id="dbab5-127">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="dbab5-128">Můžete mít například typickou nákupní objednávku XML popsanou v [ukázkovém souboru XML: Typická nákupní objednávka (LINQ to XML).](sample-xml-file-typical-purchase-order-linq-to-xml-1.md)</span><span class="sxs-lookup"><span data-stu-id="dbab5-128">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="dbab5-129">Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]aplikace můžete spustit následující dotaz a získat hodnotu atributu číslo dílu pro každý prvek položky v nákupní objednávce:</span><span class="sxs-lookup"><span data-stu-id="dbab5-129">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="dbab5-130">To lze přepsat ve formě syntaxe metody:</span><span class="sxs-lookup"><span data-stu-id="dbab5-130">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="dbab5-131">Jako další příklad můžete chtít seznam položek s hodnotou větší než 100 Kč seřazený podle čísla dílu.</span><span class="sxs-lookup"><span data-stu-id="dbab5-131">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="dbab5-132">Chcete-li získat tyto informace, můžete spustit následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="dbab5-132">To obtain this information, you could run the following query:</span></span>

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

<span data-ttu-id="dbab5-133">Opět platí, že to to může být přepsána ve formě syntaxe metody:</span><span class="sxs-lookup"><span data-stu-id="dbab5-133">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="dbab5-134">Kromě těchto funkcí LINQ [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje vylepšené programovací rozhraní XML.</span><span class="sxs-lookup"><span data-stu-id="dbab5-134">In addition to these LINQ capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="dbab5-135">Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]aplikace můžete:</span><span class="sxs-lookup"><span data-stu-id="dbab5-135">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="dbab5-136">Načtěte XML ze [souborů](how-to-load-xml-from-a-file.md) nebo [datových proudů](how-to-stream-xml-fragments-from-an-xmlreader.md).</span><span class="sxs-lookup"><span data-stu-id="dbab5-136">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="dbab5-137">Serialize XML na soubory nebo datové proudy.</span><span class="sxs-lookup"><span data-stu-id="dbab5-137">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="dbab5-138">Vytvořte XML od začátku pomocí funkční konstrukce.</span><span class="sxs-lookup"><span data-stu-id="dbab5-138">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="dbab5-139">Dotaz XML pomocí xpath-jako osy.</span><span class="sxs-lookup"><span data-stu-id="dbab5-139">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="dbab5-140">Manipulujte se stromem XML v paměti <xref:System.Xml.Linq.XContainer.Add%2A> <xref:System.Xml.Linq.XNode.Remove%2A>pomocí <xref:System.Xml.Linq.XNode.ReplaceWith%2A>metod, jako jsou například , , a <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="dbab5-140">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="dbab5-141">Ověřte stromy XML pomocí xsd.</span><span class="sxs-lookup"><span data-stu-id="dbab5-141">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="dbab5-142">Pomocí kombinace těchto funkcí můžete transformovat stromy XML z jednoho obrazce do druhého.</span><span class="sxs-lookup"><span data-stu-id="dbab5-142">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="dbab5-143">Vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="dbab5-143">Creating XML Trees</span></span>

<span data-ttu-id="dbab5-144">Jednou z nejvýznamnějších výhod programování [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s je, že je snadné vytvářet xml stromy.</span><span class="sxs-lookup"><span data-stu-id="dbab5-144">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="dbab5-145">Chcete-li například vytvořit malý strom XML, můžete napsat kód následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="dbab5-145">For example, to create a small XML tree, you can write code as follows:</span></span>

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

<span data-ttu-id="dbab5-146">Další informace naleznete [v tématu Creating XML Trees (C#)](./creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="dbab5-146">For more information, see [Creating XML Trees (C#)](./creating-xml-trees-linq-to-xml-2.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dbab5-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="dbab5-147">See also</span></span>

- [<span data-ttu-id="dbab5-148">Referenční informace (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="dbab5-148">Reference (LINQ to XML)</span></span>](./reference-linq-to-xml.md)
- [<span data-ttu-id="dbab5-149">LINQ na XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="dbab5-149">LINQ to XML vs. DOM (C#)</span></span>](./linq-to-xml-vs-dom.md)
- [<span data-ttu-id="dbab5-150">LINQ na XML vs. jiné technologie XML</span><span class="sxs-lookup"><span data-stu-id="dbab5-150">LINQ to XML vs. Other XML Technologies</span></span>](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
