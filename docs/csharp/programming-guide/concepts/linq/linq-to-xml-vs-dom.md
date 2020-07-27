---
title: LINQ to XML vs. DOM (C#)
description: Přečtěte si o některých klíčových rozdílech mezi LINQ to XML a rozhraním API pro programování XML W3C model DOM (Document Object Model) (DOM).
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: f5fc3fd7869079d47d7c9031e3668afeed7a117b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165342"
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="c0ee7-103">LINQ to XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="c0ee7-103">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="c0ee7-104">Tato část popisuje některé klíčové rozdíly mezi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] a aktuální převládající rozhraní API pro programování XML, model DOM (Document Object Model) W3C (DOM).</span><span class="sxs-lookup"><span data-stu-id="c0ee7-104">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="c0ee7-105">Nové způsoby vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="c0ee7-105">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="c0ee7-106">Ve formátu W3C DOM sestavíte strom XML od dolní části. To znamená, že vytvoříte dokument, vytvoříte prvky a potom přidáte prvky do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-106">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="c0ee7-107">Následující příklad by byl typický způsob, jak vytvořit strom XML pomocí implementace modelu DOM od společnosti Microsoft <xref:System.Xml.XmlDocument> :</span><span class="sxs-lookup"><span data-stu-id="c0ee7-107">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="c0ee7-108">Tento styl kódování vizuálně neposkytuje mnoho informací o struktuře stromu XML.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-108">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c0ee7-109">podporuje tento přístup k sestavení stromu XML, ale také podporuje alternativní přístup, *funkční konstrukci*.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-109">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="c0ee7-110">Funkční konstrukce používá <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> konstruktory a k sestavení stromu XML.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-110">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="c0ee7-111">Tady je postup vytvoření stejného stromu XML pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] funkční konstrukce:</span><span class="sxs-lookup"><span data-stu-id="c0ee7-111">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="c0ee7-112">Všimněte si, že odsazení kódu pro sestavení stromu XML ukazuje strukturu podkladového XML.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-112">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="c0ee7-113">Další informace naleznete v tématu [vytváření stromů XML (C#)](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c0ee7-113">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="c0ee7-114">Práce přímo s prvky XML</span><span class="sxs-lookup"><span data-stu-id="c0ee7-114">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="c0ee7-115">Při programování v jazyce XML je primární fokus obvykle na prvcích XML a případně na atributy.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-115">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="c0ee7-116">V aplikaci [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete pracovat přímo s prvky a atributy XML.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-116">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="c0ee7-117">Můžete například provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="c0ee7-117">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="c0ee7-118">Vytvářejte XML elementy bez použití objektu dokumentu vůbec.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-118">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="c0ee7-119">To zjednodušuje programování, pokud je třeba pracovat s fragmenty stromů XML.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-119">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="c0ee7-120">Načíst `T:System.Xml.Linq.XElement` objekty přímo ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-120">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="c0ee7-121">Serializace `T:System.Xml.Linq.XElement` objektů do souboru nebo datového proudu.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-121">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="c0ee7-122">Porovnejte je s konsorciem W3C DOM, ve kterém je dokument XML použit jako logický kontejner pro strom XML.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-122">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="c0ee7-123">V modelu DOM, uzly XML, včetně elementů a atributů, musí být vytvořeny v kontextu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-123">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="c0ee7-124">Tady je fragment kódu pro vytvoření elementu Name v modelu DOM:</span><span class="sxs-lookup"><span data-stu-id="c0ee7-124">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="c0ee7-125">Chcete-li použít prvek v rámci více dokumentů, je nutné importovat uzly mezi dokumenty.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-125">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c0ee7-126">zabrání této vrstvě složitosti.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-126">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="c0ee7-127">Při použití LINQ to XML použijte <xref:System.Xml.Linq.XDocument> třídu pouze v případě, že chcete přidat komentář nebo pokyn ke zpracování na kořenové úrovni dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-127">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="c0ee7-128">Zjednodušené zpracování názvů a oborů názvů</span><span class="sxs-lookup"><span data-stu-id="c0ee7-128">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="c0ee7-129">Zpracování názvů, oborů názvů a předpon oboru názvů je všeobecně složitou součástí programování XML.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-129">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c0ee7-130">zjednodušuje názvy a obory názvů tím, že eliminuje nutnost zabývat se předponami oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-130">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="c0ee7-131">Pokud chcete řídit předpony oboru názvů, můžete.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-131">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="c0ee7-132">Ale pokud se rozhodnete, že nechcete explicitně řídit předpony oboru názvů, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] přiřadí předpony oboru názvů během serializace, pokud jsou požadovány, nebo budou serializovány pomocí výchozích oborů názvů, pokud nejsou.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-132">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="c0ee7-133">Pokud jsou použity výchozí obory názvů, nebudou ve výsledném dokumentu žádné předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-133">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="c0ee7-134">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c0ee7-134">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="c0ee7-135">Dalším problémem s modelem DOM je, že neumožňuje změnit název uzlu.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-135">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="c0ee7-136">Místo toho je nutné vytvořit nový uzel a zkopírovat do něj všechny podřízené uzly a ztratit tak původní identitu uzlu.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-136">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c0ee7-137">tomuto problému se vyhnete tím, že vám umožní nastavit <xref:System.Xml.Linq.XName> vlastnost na uzlu.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-137">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="c0ee7-138">Podpora statické metody pro načítání XML</span><span class="sxs-lookup"><span data-stu-id="c0ee7-138">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c0ee7-139">umožňuje načíst XML pomocí statických metod namísto instančních metod.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-139">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="c0ee7-140">Tím se zjednodušuje načítání a analýza.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-140">This simplifies loading and parsing.</span></span> <span data-ttu-id="c0ee7-141">Další informace naleznete v tématu [jak načíst XML ze souboru (C#)](./how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="c0ee7-141">For more information, see [How to load XML from a file (C#)](./how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="c0ee7-142">Odebrání podpory pro konstrukce DTD</span><span class="sxs-lookup"><span data-stu-id="c0ee7-142">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c0ee7-143">dále zjednodušuje programování XML odebráním podpory entit a odkazů na entity.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-143">further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="c0ee7-144">Správa entit je složitá a používá se zřídka.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-144">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="c0ee7-145">Odebrání podpory zvyšuje výkon a zjednodušuje programovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-145">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="c0ee7-146">Po [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] naplnění stromu se rozšíří všechny entity DTD.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-146">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="c0ee7-147">Podpora fragmentů</span><span class="sxs-lookup"><span data-stu-id="c0ee7-147">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c0ee7-148">neposkytuje ekvivalent pro `XmlDocumentFragment` třídu.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-148">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="c0ee7-149">V mnoha případech však `XmlDocumentFragment` koncept může být zpracován výsledkem dotazu, který je zadán jako <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XNode> nebo <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="c0ee7-149">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="c0ee7-150">Podpora pro XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c0ee7-150">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c0ee7-151">poskytuje podporu pro <xref:System.Xml.XPath.XPathNavigator> metody rozšíření v <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-151">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c0ee7-152">Další informace naleznete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-152">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="c0ee7-153">Podpora pro prázdné znaky a odsazení</span><span class="sxs-lookup"><span data-stu-id="c0ee7-153">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c0ee7-154">zpracovává prázdné znaky více než DOM.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-154">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="c0ee7-155">Běžným scénářem je čtení odsazeného XML, vytvoření stromu XML v paměti bez jakýchkoli textových uzlů s prázdnými znaky (tj. bez zachovávání prázdných znaků), provedení některých operací v XML a následné uložení XML s odsazením.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-155">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="c0ee7-156">Při serializaci XML s formátováním je zachováno pouze významné prázdné znaky ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-156">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="c0ee7-157">Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c0ee7-157">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="c0ee7-158">Dalším běžným scénářem je číst a upravovat kód XML, který již byl záměrně odsazen.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-158">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="c0ee7-159">Toto odsazení nebudete chtít nijak měnit.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-159">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="c0ee7-160">V můžete [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to provést tak, že zachováte prázdné místo při načítání nebo analýze XML a zakážete formátování při serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-160">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c0ee7-161">ukládá prázdné znaky jako <xref:System.Xml.Linq.XText> uzel namísto typu specializovaného <xref:System.Xml.XmlNodeType.Whitespace> uzlu jako Dom.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-161">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="c0ee7-162">Podpora poznámek</span><span class="sxs-lookup"><span data-stu-id="c0ee7-162">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c0ee7-163">prvky podporují rozšiřitelnou sadu poznámek.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-163">elements support an extensible set of annotations.</span></span> <span data-ttu-id="c0ee7-164">To je užitečné pro sledování různých informací o prvku, například informace o schématu, informace o tom, zda je element svázán s uživatelským rozhraním, nebo jakýkoli jiný druh informací specifických pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-164">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="c0ee7-165">Další informace najdete v tématu [LINQ to XML poznámky](./linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="c0ee7-165">For more information, see [LINQ to XML Annotations](./linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="c0ee7-166">Podpora informací o schématu</span><span class="sxs-lookup"><span data-stu-id="c0ee7-166">Support for Schema Information</span></span>  
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c0ee7-167">poskytuje podporu pro ověřování XSD prostřednictvím metod rozšíření v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-167">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c0ee7-168">Můžete ověřit, že strom XML odpovídá XSD.</span><span class="sxs-lookup"><span data-stu-id="c0ee7-168">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="c0ee7-169">Ke stromu XML můžete naplnit informační sadu po PSVI (post-Schema-Revalidace).</span><span class="sxs-lookup"><span data-stu-id="c0ee7-169">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="c0ee7-170">Další informace naleznete v tématu [Jak ověřit pomocí XSD](./how-to-validate-using-xsd-linq-to-xml.md) a <xref:System.Xml.Schema.Extensions> .</span><span class="sxs-lookup"><span data-stu-id="c0ee7-170">For more information, see [How to validate using XSD](./how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c0ee7-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0ee7-171">See also</span></span>

- [<span data-ttu-id="c0ee7-172">Začínáme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c0ee7-172">Getting Started (LINQ to XML)</span></span>](./linq-to-xml-overview.md)
