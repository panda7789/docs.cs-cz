---
title: LINQ na XML vs. DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 92d0da494829d57517d52fe93a3cbcf1398fdbe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168386"
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="ccdf6-102">LINQ na XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="ccdf6-102">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="ccdf6-103">Tato část popisuje některé klíčové [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozdíly mezi a aktuální převládající XML programovací rozhraní API, W3C document object model (DOM).</span><span class="sxs-lookup"><span data-stu-id="ccdf6-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="ccdf6-104">Nové způsoby vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="ccdf6-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="ccdf6-105">V W3C DOM vytvoříte strom XML zdola nahoru; to znamená, že vytvoříte dokument, vytvoříte prvky a potom přidáte prvky do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="ccdf6-106">Například následující by typický způsob, jak vytvořit strom XML pomocí implementace <xref:System.Xml.XmlDocument>Microsoft DOM, :</span><span class="sxs-lookup"><span data-stu-id="ccdf6-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
XmlElement phone1 = doc.CreateElement("Phone");  
phone1.SetAttribute("Type", "Home");  
phone1.InnerText = "206-555-0144";
XmlElement phone2 = doc.CreateElement("Phone");  
phone2.SetAttribute("Type", "Work");  
phone2.InnerText = "425-555-0145";
XmlElement street1 = doc.CreateElement("Street1");
street1.InnerText = "123 Main St";  
XmlElement city = doc.CreateElement("City");  
city.InnerText = "Mercer Island";  
XmlElement state = doc.CreateElement("State");  
state.InnerText = "WA";  
XmlElement postal = doc.CreateElement("Postal");  
postal.InnerText = "68042";  
XmlElement address = doc.CreateElement("Address");  
address.AppendChild(street1);  
address.AppendChild(city);  
address.AppendChild(state);  
address.AppendChild(postal);  
XmlElement contact = doc.CreateElement("Contact");  
contact.AppendChild(name);  
contact.AppendChild(phone1);  
contact.AppendChild(phone2);  
contact.AppendChild(address);  
XmlElement contacts = doc.CreateElement("Contacts");  
contacts.AppendChild(contact);  
doc.AppendChild(contacts);  
```  
  
 <span data-ttu-id="ccdf6-107">Tento styl kódování vizuálně neposkytuje mnoho informací o struktuře stromu XML.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ccdf6-108">podporuje tento přístup k vytváření stromu XML, ale také podporuje alternativní přístup, *funkční konstrukce*.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-108">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="ccdf6-109">Funkční konstrukce <xref:System.Xml.Linq.XElement> používá <xref:System.Xml.Linq.XAttribute> konstruktory a k vytvoření stromu XML.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-109">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="ccdf6-110">Zde je, jak byste vytvořit stejný [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] strom XML pomocí funkční konstrukce:</span><span class="sxs-lookup"><span data-stu-id="ccdf6-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="ccdf6-111">Všimněte si, že odsazení kódu pro vytvoření stromu XML ukazuje strukturu podkladového XML.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="ccdf6-112">Další informace naleznete [v tématu Creating XML Trees (C#)](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ccdf6-112">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="ccdf6-113">Práce přímo s elementy XML</span><span class="sxs-lookup"><span data-stu-id="ccdf6-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="ccdf6-114">Při programování pomocí jazyka XML je primární zaměření obvykle na elementy XML a možná i na atributy.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="ccdf6-115">V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]aplikaci můžete pracovat přímo s prvky a atributy XML.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="ccdf6-116">Můžete například provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="ccdf6-116">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="ccdf6-117">Vytvořte elementy XML bez použití objektu dokumentu vůbec.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="ccdf6-118">To zjednodušuje programování, když budete muset pracovat s fragmenty stromů XML.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="ccdf6-119">Načtěte `T:System.Xml.Linq.XElement` objekty přímo ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="ccdf6-120">Serialize `T:System.Xml.Linq.XElement` objektů do souboru nebo datového proudu.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="ccdf6-121">Porovnejte to s W3C DOM, ve kterém je dokument XML použit jako logický kontejner pro strom XML.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="ccdf6-122">V dom uzly XML, včetně prvků a atributů, musí být vytvořeny v kontextu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="ccdf6-123">Zde je fragment kódu k vytvoření elementu názvu v DOM:</span><span class="sxs-lookup"><span data-stu-id="ccdf6-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="ccdf6-124">Pokud chcete použít prvek ve více dokumentech, musíte importovat uzly mezi dokumenty.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ccdf6-125">této vrstvě složitosti.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-125">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="ccdf6-126">Při použití LINQ do XML, použijte třídu pouze v <xref:System.Xml.Linq.XDocument> případě, že chcete přidat komentář nebo instrukce pro zpracování na kořenové úrovni dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="ccdf6-127">Zjednodušené zpracování názvů a oborů názvů</span><span class="sxs-lookup"><span data-stu-id="ccdf6-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="ccdf6-128">Zpracování názvů, oborů názvů a předpon oboru názvů je obecně složitou součástí programování XML.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ccdf6-129">zjednodušuje názvy a obory názvů tím, že eliminuje požadavek na řešení předpon oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-129">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="ccdf6-130">Pokud chcete řídit předpony oboru názvů, můžete.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="ccdf6-131">Pokud se však rozhodnete explicitně neřídit předpony oboru názvů, přiřadí předpony oboru názvů během serializace, pokud jsou požadovány, nebo serializuje pomocí výchozích oborů názvů, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pokud nejsou.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="ccdf6-132">Pokud jsou použity výchozí obory názvů, nebudou ve výsledném dokumentu žádné předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="ccdf6-133">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ccdf6-133">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ccdf6-134">Dalším problémem s DOM je, že neumožňuje změnit název uzlu.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="ccdf6-135">Místo toho budete muset vytvořit nový uzel a zkopírovat všechny podřízené uzly do něj, ztrácí původní uzel identity.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ccdf6-136">zabraňuje tomuto problému tím, <xref:System.Xml.Linq.XName> že umožňuje nastavit vlastnost na uzlu.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-136">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="ccdf6-137">Podpora statické metody pro načítání XML</span><span class="sxs-lookup"><span data-stu-id="ccdf6-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ccdf6-138">umožňuje načíst XML pomocí statických metod namísto metod instance.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-138">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="ccdf6-139">To zjednodušuje načítání a analýzu.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="ccdf6-140">Další informace naleznete v tématu [Jak načíst XML ze souboru (C#)](./how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="ccdf6-140">For more information, see [How to load XML from a file (C#)](./how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="ccdf6-141">Odstranění podpory pro DTD konstrukce</span><span class="sxs-lookup"><span data-stu-id="ccdf6-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ccdf6-142">dále zjednodušuje programování XML odebráním podpory pro entity a odkazy na entity.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-142">further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="ccdf6-143">Správa subjektů je složitá a používá se jen zřídka.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="ccdf6-144">Odebrání jejich podpory zvyšuje výkon a zjednodušuje programovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="ccdf6-145">Při [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] naplnění stromu jsou rozbaleny všechny entity DTD.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="ccdf6-146">Podpora fragmentů</span><span class="sxs-lookup"><span data-stu-id="ccdf6-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ccdf6-147">neposkytuje ekvivalent pro `XmlDocumentFragment` třídu.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-147">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="ccdf6-148">V mnoha případech však `XmlDocumentFragment` koncept může být zpracován a výsledkem <xref:System.Collections.Generic.IEnumerable%601> dotazu, který je zadán jako <xref:System.Xml.Linq.XNode>, nebo <xref:System.Collections.Generic.IEnumerable%601> . <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="ccdf6-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="ccdf6-149">Podpora pro XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ccdf6-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ccdf6-150">poskytuje podporu <xref:System.Xml.XPath.XPathNavigator> pro metody <xref:System.Xml.XPath?displayProperty=nameWithType> rozšíření v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-150">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ccdf6-151">Další informace naleznete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="ccdf6-152">Podpora prázdného místa a odsazení</span><span class="sxs-lookup"><span data-stu-id="ccdf6-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ccdf6-153">zpracovává prázdné místo jednodušeji než dom.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-153">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="ccdf6-154">Běžným scénářem je čtení odsazeného xml, vytvoření stromu XML v paměti bez uzly prázdného textu (to znamená nezachování prázdného místa), provedení některých operací v xml a následné uložení XML s odsazením.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="ccdf6-155">Při serializaci xml s formátováním se zachová pouze významné prázdné místo ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="ccdf6-156">Toto je výchozí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]chování pro aplikace .</span><span class="sxs-lookup"><span data-stu-id="ccdf6-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="ccdf6-157">Dalším běžným scénářem je čtení a úprava xml, který již byl záměrně odsazen.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="ccdf6-158">Možná nebudete chtít změnit toto odsazení v žádném případě.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="ccdf6-159">V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]aplikace to lze provést tak, že při načtení nebo analyzovat xml načtete nebo analyzujete prázdné místo a při serializaci xml ukázníte formátování.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ccdf6-160">ukládá prázdné místo <xref:System.Xml.Linq.XText> jako uzel, namísto <xref:System.Xml.XmlNodeType.Whitespace> specializovaného typu uzlu, jako to dělá DOM.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-160">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="ccdf6-161">Podpora pro poznámky</span><span class="sxs-lookup"><span data-stu-id="ccdf6-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ccdf6-162">prvky podporují rozšiřitelnou sadu anotací.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-162">elements support an extensible set of annotations.</span></span> <span data-ttu-id="ccdf6-163">To je užitečné pro sledování různé informace o prvku, jako jsou informace o schématu, informace o tom, zda je prvek vázán na ui nebo jakýkoli jiný druh informací specifických pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="ccdf6-164">Další informace naleznete v tématu [LINQ to XML Anotations](./linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="ccdf6-164">For more information, see [LINQ to XML Annotations](./linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="ccdf6-165">Podpora informací o schématu</span><span class="sxs-lookup"><span data-stu-id="ccdf6-165">Support for Schema Information</span></span>  
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ccdf6-166">poskytuje podporu pro ověření XSD <xref:System.Xml.Schema?displayProperty=nameWithType> prostřednictvím rozšiřujících metod v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-166">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ccdf6-167">Můžete ověřit, zda strom XML vyhovuje xsd.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="ccdf6-168">Strom XML můžete naplnit informační sadou psvi po ověření schématu.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="ccdf6-169">Další informace naleznete v [tématu Jak ověřit pomocí XSD](./how-to-validate-using-xsd-linq-to-xml.md) a <xref:System.Xml.Schema.Extensions>.</span><span class="sxs-lookup"><span data-stu-id="ccdf6-169">For more information, see [How to validate using XSD](./how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ccdf6-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccdf6-170">See also</span></span>

- [<span data-ttu-id="ccdf6-171">Začínáme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ccdf6-171">Getting Started (LINQ to XML)</span></span>](./linq-to-xml-overview.md)
