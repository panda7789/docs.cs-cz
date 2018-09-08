---
title: Přehled LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: 962fddcfec04259425c1094f07adf0e3966dfab0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185084"
---
# <a name="linq-to-xml-overview-visual-basic"></a><span data-ttu-id="5f21d-102">Přehled LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f21d-102">LINQ to XML Overview (Visual Basic)</span></span>
<span data-ttu-id="5f21d-103">XML je široce přijat jako způsob, jak formátování dat v mnoha kontextech.</span><span class="sxs-lookup"><span data-stu-id="5f21d-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="5f21d-104">Například můžete vyhledat XML na webu, konfigurační soubory, soubory Microsoft Office Word a databázích.</span><span class="sxs-lookup"><span data-stu-id="5f21d-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5f21d-105"> je aktuální, přepracovaný přístup k programování v jazyce XML.</span><span class="sxs-lookup"><span data-stu-id="5f21d-105"> is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="5f21d-106">Poskytuje možnosti úprav Document Object Model (DOM) dokumentu v paměti a podporuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="5f21d-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="5f21d-107">I když tyto výrazy dotazu představují syntakticky liší od jazyka XPath, poskytují podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="5f21d-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="5f21d-108">Technologie LINQ to XML vývojáře</span><span class="sxs-lookup"><span data-stu-id="5f21d-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5f21d-109"> cílí na širokou škálu vývojáři.</span><span class="sxs-lookup"><span data-stu-id="5f21d-109"> targets a variety of developers.</span></span> <span data-ttu-id="5f21d-110">Průměrná vývojář, který právě chce získat něco udělat [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] usnadňuje XML pomocí prostředí dotazu, který je podobný SQL.</span><span class="sxs-lookup"><span data-stu-id="5f21d-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="5f21d-111">S jen trochu studii můžete další programátorům v jejich programovací jazyk podle vlastní volby psát stručné a výkonné dotazy.</span><span class="sxs-lookup"><span data-stu-id="5f21d-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="5f21d-112">Profesionální vývojáři mohou použít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] výrazně zvýšit svou produktivitu.</span><span class="sxs-lookup"><span data-stu-id="5f21d-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="5f21d-113">S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], zapisují menší kód, který je více výrazovými možnostmi, kompaktnějším a výkonnější.</span><span class="sxs-lookup"><span data-stu-id="5f21d-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="5f21d-114">Použitím – výrazy dotazů z několika domén dat ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="5f21d-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="5f21d-115">Co je LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="5f21d-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5f21d-116"> je povolené LINQ, v paměti XML programovací rozhraní, která umožňuje pracovat s jazykem XML z v rámci [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programovacích jazyků.</span><span class="sxs-lookup"><span data-stu-id="5f21d-116"> is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5f21d-117"> je třeba Document Object Model (DOM) přináší dokumentu XML do paměti.</span><span class="sxs-lookup"><span data-stu-id="5f21d-117"> is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="5f21d-118">Můžete zadávat dotazy a úpravě dokumentu a po úpravě ho můžete uložit do souboru nebo ho serializovat a odešle je prostřednictvím Internetu.</span><span class="sxs-lookup"><span data-stu-id="5f21d-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="5f21d-119">Nicméně [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se liší od modelu DOM: poskytuje nové objektový model, který je světlejší váha a snadněji pracovat, a, který využívá funkce jazyka v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5f21d-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.</span></span>  
  
 <span data-ttu-id="5f21d-120">Nejdůležitější výhod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je své integraci s [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5f21d-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="5f21d-121">Tato integrace umožňuje psát dotazy v dokumentu XML v paměti k načtení kolekce elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="5f21d-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="5f21d-122">Funkce dotazu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je srovnatelné funkci (i když nejsou v syntaxi) na XPath a XQuery.</span><span class="sxs-lookup"><span data-stu-id="5f21d-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="5f21d-123">Integrace [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] v jazyce Visual Basic nabízí silnější typy, kompilace kontrolu a vylepšená podpora ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="5f21d-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="5f21d-124">Další výhodou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je schopnost používat výsledky dotazu jako parametry pro <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory objektu umožňuje efektivní přístup k vytváření stromů XML.</span><span class="sxs-lookup"><span data-stu-id="5f21d-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="5f21d-125">Tomuto přístupu se říká *funkční konstrukce*, umožňuje vývojářům snadno transformace stromů XML z jednoho obrazce na jiný.</span><span class="sxs-lookup"><span data-stu-id="5f21d-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="5f21d-126">Například můžete mít typické XML nákupní objednávka, jak je popsáno v [ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5f21d-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span> <span data-ttu-id="5f21d-127">S použitím [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete spustit následující dotaz pro získání část hodnoty číselné atribut pro každý prvek položky v nákupní objednávky:</span><span class="sxs-lookup"><span data-stu-id="5f21d-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 <span data-ttu-id="5f21d-128">Další příklad můžete seznam seřazený podle čísel položky s hodnotou větší než 100 USD.</span><span class="sxs-lookup"><span data-stu-id="5f21d-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="5f21d-129">Pro získání těchto informací, můžete spustit následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="5f21d-129">To obtain this information, you could run the following query:</span></span>  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 <span data-ttu-id="5f21d-130">Kromě těchto [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] možnosti [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje vylepšené programovací rozhraní XML.</span><span class="sxs-lookup"><span data-stu-id="5f21d-130">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="5f21d-131">Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete:</span><span class="sxs-lookup"><span data-stu-id="5f21d-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
-   <span data-ttu-id="5f21d-132">Načtení XML ze souborů nebo datových proudů.</span><span class="sxs-lookup"><span data-stu-id="5f21d-132">Load XML from files or streams.</span></span>  
  
-   <span data-ttu-id="5f21d-133">Serializace XML pro soubory nebo datové proudy.</span><span class="sxs-lookup"><span data-stu-id="5f21d-133">Serialize XML to files or streams.</span></span>  
  
-   <span data-ttu-id="5f21d-134">Vytvoření XML od začátku pomocí funkční konstrukce.</span><span class="sxs-lookup"><span data-stu-id="5f21d-134">Create XML from scratch by using functional construction.</span></span>  
  
-   <span data-ttu-id="5f21d-135">Dotaz XML pomocí XPath jako osy.</span><span class="sxs-lookup"><span data-stu-id="5f21d-135">Query XML using XPath-like axes.</span></span>  
  
-   <span data-ttu-id="5f21d-136">Manipulace s stromu XML v paměti pomocí metody <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, a <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="5f21d-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
-   <span data-ttu-id="5f21d-137">Ověření pomocí XSD stromů XML.</span><span class="sxs-lookup"><span data-stu-id="5f21d-137">Validate XML trees using XSD.</span></span>  
  
-   <span data-ttu-id="5f21d-138">Pomocí kombinace těchto funkcí transformace stromů XML z jednoho obrazce do jiné.</span><span class="sxs-lookup"><span data-stu-id="5f21d-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="5f21d-139">Vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="5f21d-139">Creating XML Trees</span></span>  
 <span data-ttu-id="5f21d-140">IOne nejvýznamnější výhody programování s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je, že je snadné vytváření stromů XML.</span><span class="sxs-lookup"><span data-stu-id="5f21d-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="5f21d-141">Například k vytvoření malé stromu XML, můžete napsat kód následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5f21d-141">For example, to create a small XML tree, you can write  code as follows:</span></span>  
  
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
  
 <span data-ttu-id="5f21d-142">Kompilátor jazyka Visual Basic přeloží literály XML do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] volání metody.</span><span class="sxs-lookup"><span data-stu-id="5f21d-142">The Visual Basic compiler translates XML literals into [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] method calls.</span></span>  
  
 <span data-ttu-id="5f21d-143">Další informace najdete v tématu [vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="5f21d-143">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f21d-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f21d-144">See also</span></span>

- <xref:System.Xml.Linq>  
- [<span data-ttu-id="5f21d-145">Začínáme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5f21d-145">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
- [<span data-ttu-id="5f21d-146">Přehled technologie LINQ to XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5f21d-146">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
- [<span data-ttu-id="5f21d-147">XML</span><span class="sxs-lookup"><span data-stu-id="5f21d-147">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
