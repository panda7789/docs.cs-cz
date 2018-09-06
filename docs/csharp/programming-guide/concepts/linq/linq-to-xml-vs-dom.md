---
title: LINQ to XML versus. MODELU DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: d838b99505eb9808ab66ef442895ad24a2658726
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857242"
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="7488f-102">LINQ to XML versus. MODELU DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="7488f-102">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="7488f-103">Tato část popisuje některé hlavní rozdíly mezi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] a aktuální převládající XML programování rozhraní API, W3C Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="7488f-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="7488f-104">Nové způsoby, jak vytvořit stromů XML</span><span class="sxs-lookup"><span data-stu-id="7488f-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="7488f-105">V modelu DOM W3C při vytváření stromu XML zdola; To znamená vytvořte dokument, vytvořit prvky a potom přidat prvky v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7488f-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="7488f-106">Například následující by typické způsob, jak vytvořit stromu XML pomocí modelu DOM, implementace Microsoft <xref:System.Xml.XmlDocument>:</span><span class="sxs-lookup"><span data-stu-id="7488f-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="7488f-107">Tento styl psaní kódu vizuálně neposkytuje mnoho informací o struktuře stromu XML.</span><span class="sxs-lookup"><span data-stu-id="7488f-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7488f-108"> podporuje tento přístup k sestavením stromu XML, ale také podporuje alternativním přístupem \*funkční konstrukce\*.</span><span class="sxs-lookup"><span data-stu-id="7488f-108"> supports this approach to constructing an XML tree, but also supports an alternative approach, \*functional construction\*.</span></span> <span data-ttu-id="7488f-109">Funkční konstrukce používá <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory k sestavení stromu XML.</span><span class="sxs-lookup"><span data-stu-id="7488f-109">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="7488f-110">Zde je, jak je vytvořit stejném stromu XML pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] funkční konstrukce:</span><span class="sxs-lookup"><span data-stu-id="7488f-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="7488f-111">Všimněte si, že odsazení kódu k sestavení kompletních stromu XML ukazuje strukturu základní XML.</span><span class="sxs-lookup"><span data-stu-id="7488f-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="7488f-112">Další informace najdete v tématu [vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="7488f-112">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="7488f-113">Práce přímo se elementů XML</span><span class="sxs-lookup"><span data-stu-id="7488f-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="7488f-114">Když je program s XML, hlavním cílem je obvykle na prvky XML a případně na atributy.</span><span class="sxs-lookup"><span data-stu-id="7488f-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="7488f-115">V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], může spolupracovat přímo s XML elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="7488f-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="7488f-116">Například můžete provést následující:</span><span class="sxs-lookup"><span data-stu-id="7488f-116">For example, you can do the following:</span></span>  
  
-   <span data-ttu-id="7488f-117">Vytvořte prvky XML bez použití objektu dokumentu vůbec.</span><span class="sxs-lookup"><span data-stu-id="7488f-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="7488f-118">Tato funkce usnadňuje programování v případě, že máte pro práci s fragmenty stromů XML.</span><span class="sxs-lookup"><span data-stu-id="7488f-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
-   <span data-ttu-id="7488f-119">Zatížení `T:System.Xml.Linq.XElement` objekty přímo ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="7488f-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
-   <span data-ttu-id="7488f-120">Serializace `T:System.Xml.Linq.XElement` objektů do souboru nebo datový proud.</span><span class="sxs-lookup"><span data-stu-id="7488f-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="7488f-121">Porovnejte W3C v modelu DOM, ve kterém se používá dokumentu XML jako logický kontejner pro stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="7488f-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="7488f-122">V modelu DOM z uzlů XML, včetně elementů a atributů, musí být vytvořeny v rámci dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="7488f-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="7488f-123">Tady je fragment kódu pro vytvoření názvu elementu v modelu DOM:</span><span class="sxs-lookup"><span data-stu-id="7488f-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="7488f-124">Pokud chcete použít prvek napříč více dokumentů, je nutné naimportovat uzly v dokumentech.</span><span class="sxs-lookup"><span data-stu-id="7488f-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7488f-125"> Tato vrstva složitost se vyhnete.</span><span class="sxs-lookup"><span data-stu-id="7488f-125"> avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="7488f-126">Při použití technologie LINQ to XML, je použít <xref:System.Xml.Linq.XDocument> třídy pouze v případě, že chcete přidat komentář nebo zpracování instrukcí na kořenové úrovni dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7488f-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="7488f-127">Zjednodušená zpracování názvy a obory názvů</span><span class="sxs-lookup"><span data-stu-id="7488f-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="7488f-128">Zpracování názvy oborů názvů a předpony oboru názvů je obecně komplexní součástí XML programování.</span><span class="sxs-lookup"><span data-stu-id="7488f-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7488f-129"> zjednodušuje názvy a obory názvů tím, že eliminuje požadavek na řešení předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7488f-129"> simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="7488f-130">Pokud chcete řídit předpony oboru názvů, můžete.</span><span class="sxs-lookup"><span data-stu-id="7488f-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="7488f-131">Ale pokud se rozhodnete řízení předpon názvového prostoru, není explicitně [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] přiřadí předpony oboru názvů při serializaci, pokud jsou požadované, nebo se serializace pomocí výchozích názvových prostorů, pokud nejsou.</span><span class="sxs-lookup"><span data-stu-id="7488f-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="7488f-132">Pokud se používají výchozí obory názvů, nebudou bez předpony oboru názvů ve výsledném dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7488f-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="7488f-133">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="7488f-133">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="7488f-134">Dalším problémem modelu DOM se, že neumožní můžete změnit název uzlu.</span><span class="sxs-lookup"><span data-stu-id="7488f-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="7488f-135">Místo toho budete muset vytvořit nový uzel a zkopírujte všechny podřízené uzly, ztráty původní uzel identitu.</span><span class="sxs-lookup"><span data-stu-id="7488f-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7488f-136"> tomuto problému se vyhnete tím, že vám umožní nastavit <xref:System.Xml.Linq.XName> vlastnost uzlu.</span><span class="sxs-lookup"><span data-stu-id="7488f-136"> avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="7488f-137">Podpora statické metody pro načítání dat XML</span><span class="sxs-lookup"><span data-stu-id="7488f-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7488f-138"> umožňuje načíst XML pomocí statické metody, namísto metody instance.</span><span class="sxs-lookup"><span data-stu-id="7488f-138"> lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="7488f-139">To zjednodušuje, načítání a analýzu.</span><span class="sxs-lookup"><span data-stu-id="7488f-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="7488f-140">Další informace najdete v tématu [postupy: načtení XML ze souboru (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="7488f-140">For more information, see [How to: Load XML from a File (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="7488f-141">Odebrání podpory pro DTD konstrukce</span><span class="sxs-lookup"><span data-stu-id="7488f-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7488f-142"> Další zjednodušuje programování tak, že odeberete podporu pro entity a odkazy na entity XML.</span><span class="sxs-lookup"><span data-stu-id="7488f-142"> further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="7488f-143">Správa entit je složitá a zřídka se používá.</span><span class="sxs-lookup"><span data-stu-id="7488f-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="7488f-144">Odebírá se jejich podpora zvyšuje výkon a zjednodušuje programovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7488f-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="7488f-145">Když [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] naplnění stromu, jsou rozbaleny všechny entity DTD.</span><span class="sxs-lookup"><span data-stu-id="7488f-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="7488f-146">Podpora pro fragmenty</span><span class="sxs-lookup"><span data-stu-id="7488f-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7488f-147"> nenabízí ekvivalent pro `XmlDocumentFragment` třídy.</span><span class="sxs-lookup"><span data-stu-id="7488f-147"> does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="7488f-148">V mnoha případech se však `XmlDocumentFragment` koncept zpracovat výsledek dotazu, který je zadán jako <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XNode>, nebo <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="7488f-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="7488f-149">Podpora pro objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="7488f-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7488f-150"> poskytuje podporu pro <xref:System.Xml.XPath.XPathNavigator> prostřednictvím metody rozšíření v <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7488f-150"> provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="7488f-151">Další informace naleznete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7488f-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="7488f-152">Podpora pro prázdné znaky a odsazení</span><span class="sxs-lookup"><span data-stu-id="7488f-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7488f-153"> zpracovává prázdných jednodušeji než modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="7488f-153"> handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="7488f-154">Běžný scénář, kdy je pro čtení odsazený XML, vytvoření stromu XML v paměti bez ostatní uzly text prázdné znaky (tedy ne zachování prázdné znaky), provádění některých operací na XML a pak uložte soubor XML s odsazením.</span><span class="sxs-lookup"><span data-stu-id="7488f-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="7488f-155">Při serializaci XML s formátováním je zachována pouze významný prázdný znak ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="7488f-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="7488f-156">Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7488f-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="7488f-157">Další z typických možností je číst a upravovat kód XML, který již byl záměrně odsazeny.</span><span class="sxs-lookup"><span data-stu-id="7488f-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="7488f-158">Nebudete chtít změnit tento odsazení žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="7488f-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="7488f-159">V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete to provést tak, že zachování prázdných znaků při načtení nebo analyzovat kód XML a zakázání formátování při serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="7488f-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7488f-160"> ukládá prázdný znak jako <xref:System.Xml.Linq.XText> uzlu, namísto nutnosti specializovaný <xref:System.Xml.XmlNodeType.Whitespace> typ uzlu, jako v modelu DOM nemá.</span><span class="sxs-lookup"><span data-stu-id="7488f-160"> stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="7488f-161">Podporu pro poznámky</span><span class="sxs-lookup"><span data-stu-id="7488f-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7488f-162"> prvky podporují rozšiřitelnou sadu poznámky.</span><span class="sxs-lookup"><span data-stu-id="7488f-162"> elements support an extensible set of annotations.</span></span> <span data-ttu-id="7488f-163">To je užitečné pro sledování různé informace o elementu, jako je například informace o schématu, informace o tom, zda elementu je vázán na uživatelské rozhraní nebo nějakých jiných informací druh specifické pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7488f-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="7488f-164">Další informace najdete v tématu [LINQ to XML poznámky](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="7488f-164">For more information, see [LINQ to XML Annotations](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="7488f-165">Podpora pro informace o schématu</span><span class="sxs-lookup"><span data-stu-id="7488f-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7488f-166"> poskytuje podporu pro ověření XSD prostřednictvím metody rozšíření v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7488f-166"> provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="7488f-167">Můžete ověřit, že stromu XML v souladu s XSD.</span><span class="sxs-lookup"><span data-stu-id="7488f-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="7488f-168">Můžete naplnit stromu XML pomocí informační sadu po ověření (PSVI).</span><span class="sxs-lookup"><span data-stu-id="7488f-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="7488f-169">Další informace najdete v tématu [postupy: ověření pomocí XSD](../../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) a <xref:System.Xml.Schema.Extensions>.</span><span class="sxs-lookup"><span data-stu-id="7488f-169">For more information, see [How to: Validate Using XSD](../../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7488f-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="7488f-170">See Also</span></span>

- [<span data-ttu-id="7488f-171">Začínáme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7488f-171">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
