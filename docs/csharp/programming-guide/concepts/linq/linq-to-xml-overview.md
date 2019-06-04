---
title: Přehled LINQ to XML (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: a9435027a7487af96227fdc7a0eae6f511d82b23
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484344"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="b4637-102">Přehled LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b4637-102">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="b4637-103">Technologie LINQ to XML poskytuje programovací rozhraní v paměti XML, které využívá rozhraní .NET Language-Integrated Query (LINQ).</span><span class="sxs-lookup"><span data-stu-id="b4637-103">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="b4637-104">LINQ to XML použije funkce .NET a je srovnatelná se aktualizované, přepracovaný programovací rozhraní XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="b4637-104">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span> 
 
<span data-ttu-id="b4637-105">XML je široce přijat jako způsob, jak formátování dat v mnoha kontextech.</span><span class="sxs-lookup"><span data-stu-id="b4637-105">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="b4637-106">Například můžete vyhledat XML na webu, konfigurační soubory, soubory Microsoft Office Word a databázích.</span><span class="sxs-lookup"><span data-stu-id="b4637-106">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="b4637-107">je aktuální, přepracovaný přístup k programování v jazyce XML.</span><span class="sxs-lookup"><span data-stu-id="b4637-107">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="b4637-108">Poskytuje možnosti úprav Document Object Model (DOM) dokumentu v paměti a podporuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="b4637-108">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="b4637-109">I když tyto výrazy dotazu představují syntakticky liší od jazyka XPath, poskytují podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="b4637-109">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="b4637-110">Technologie LINQ to XML vývojáře</span><span class="sxs-lookup"><span data-stu-id="b4637-110">LINQ to XML Developers</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="b4637-111">cílí na širokou škálu vývojáři.</span><span class="sxs-lookup"><span data-stu-id="b4637-111">targets a variety of developers.</span></span> <span data-ttu-id="b4637-112">Průměrná vývojář, který právě chce získat něco udělat [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usnadňuje XML pomocí prostředí dotazu, který je podobný SQL.</span><span class="sxs-lookup"><span data-stu-id="b4637-112">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="b4637-113">S jen trochu studii můžete další programátorům v jejich programovací jazyk podle vlastní volby psát stručné a výkonné dotazy.</span><span class="sxs-lookup"><span data-stu-id="b4637-113">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="b4637-114">Profesionální vývojáři mohou použít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] výrazně zvýšit svou produktivitu.</span><span class="sxs-lookup"><span data-stu-id="b4637-114">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="b4637-115">S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], zapisují menší kód, který je více výrazovými možnostmi, kompaktnějším a výkonnější.</span><span class="sxs-lookup"><span data-stu-id="b4637-115">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="b4637-116">Použitím – výrazy dotazů z několika domén dat ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="b4637-116">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="b4637-117">Co je LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="b4637-117">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="b4637-118">je povolené LINQ, v paměti XML programovací rozhraní, která umožňuje pracovat s jazykem XML z v rámci rozhraní .NET Framework programovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="b4637-118">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="b4637-119">je třeba Document Object Model (DOM) přináší dokumentu XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="b4637-119">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="b4637-120">Můžete zadávat dotazy a úpravě dokumentu a po úpravě ho můžete uložit do souboru nebo ho serializovat a odešle je prostřednictvím Internetu.</span><span class="sxs-lookup"><span data-stu-id="b4637-120">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="b4637-121">Nicméně [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se liší od modelu DOM: Poskytuje nové objektový model, který je světlejší váha a snadněji pracovat, a, která využívá funkcí jazyka v C#.</span><span class="sxs-lookup"><span data-stu-id="b4637-121">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="b4637-122">Nejdůležitější výhod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je své integraci s [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4637-122">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="b4637-123">Tato integrace umožňuje psát dotazy v dokumentu XML v paměti k načtení kolekce elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="b4637-123">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="b4637-124">Funkce dotazu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je srovnatelné funkci (i když nejsou v syntaxi) na XPath a XQuery.</span><span class="sxs-lookup"><span data-stu-id="b4637-124">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="b4637-125">Integrace [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] v jazyce C# poskytuje silnější typy, kompilace kontrolu a vylepšená podpora ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="b4637-125">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="b4637-126">Další výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je schopnost používat výsledky dotazu jako parametry pro <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory objektu umožňuje efektivní přístup k vytváření stromů XML.</span><span class="sxs-lookup"><span data-stu-id="b4637-126">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="b4637-127">Tomuto přístupu se říká *funkční konstrukce*, umožňuje vývojářům snadno transformace stromů XML z jednoho obrazce na jiný.</span><span class="sxs-lookup"><span data-stu-id="b4637-127">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="b4637-128">Například můžete mít typické XML nákupní objednávka, jak je popsáno v [ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="b4637-128">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="b4637-129">S použitím [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete spustit následující dotaz pro získání část hodnoty číselné atribut pro každý prvek položky v nákupní objednávky:</span><span class="sxs-lookup"><span data-stu-id="b4637-129">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="b4637-130">To může být přepsán ve formuláři syntaxe metody:</span><span class="sxs-lookup"><span data-stu-id="b4637-130">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="b4637-131">Další příklad můžete seznam seřazený podle čísel položky s hodnotou větší než 100 USD.</span><span class="sxs-lookup"><span data-stu-id="b4637-131">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="b4637-132">Pro získání těchto informací, můžete spustit následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="b4637-132">To obtain this information, you could run the following query:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

<span data-ttu-id="b4637-133">Znovu to může být přepsán ve formuláři syntaxe metody:</span><span class="sxs-lookup"><span data-stu-id="b4637-133">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="b4637-134">Kromě těchto [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] možnosti [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje vylepšené programovací rozhraní XML.</span><span class="sxs-lookup"><span data-stu-id="b4637-134">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="b4637-135">Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete:</span><span class="sxs-lookup"><span data-stu-id="b4637-135">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="b4637-136">Načtení XML ze [soubory](how-to-load-xml-from-a-file.md) nebo [datové proudy](how-to-stream-xml-fragments-from-an-xmlreader.md).</span><span class="sxs-lookup"><span data-stu-id="b4637-136">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="b4637-137">Serializace XML pro soubory nebo datové proudy.</span><span class="sxs-lookup"><span data-stu-id="b4637-137">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="b4637-138">Vytvoření XML od začátku pomocí funkční konstrukce.</span><span class="sxs-lookup"><span data-stu-id="b4637-138">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="b4637-139">Dotaz XML pomocí XPath jako osy.</span><span class="sxs-lookup"><span data-stu-id="b4637-139">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="b4637-140">Manipulace s stromu XML v paměti pomocí metody <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, a <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="b4637-140">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="b4637-141">Ověření pomocí XSD stromů XML.</span><span class="sxs-lookup"><span data-stu-id="b4637-141">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="b4637-142">Pomocí kombinace těchto funkcí transformace stromů XML z jednoho obrazce do jiné.</span><span class="sxs-lookup"><span data-stu-id="b4637-142">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="b4637-143">Vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="b4637-143">Creating XML Trees</span></span>

<span data-ttu-id="b4637-144">Jednou z nejvýznamnějších výhod programování s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je, že je snadné vytváření stromů XML.</span><span class="sxs-lookup"><span data-stu-id="b4637-144">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="b4637-145">Například k vytvoření malé stromu XML, můžete napsat kód následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b4637-145">For example, to create a small XML tree, you can write code as follows:</span></span>

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

<span data-ttu-id="b4637-146">Další informace najdete v tématu [vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b4637-146">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4637-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4637-147">See also</span></span>

- [<span data-ttu-id="b4637-148">Referenční informace (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b4637-148">Reference (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/reference-linq-to-xml.md)
- [<span data-ttu-id="b4637-149">Technologie LINQ to XML versus DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="b4637-149">LINQ to XML vs. DOM (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="b4637-150">Technologie LINQ to XML versus jiné technologie XML</span><span class="sxs-lookup"><span data-stu-id="b4637-150">LINQ to XML vs. Other XML Technologies</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
