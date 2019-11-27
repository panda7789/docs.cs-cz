---
title: LINQ to XML vs. DOM
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: b25993fba4d878beb881dfdc46effe5a8ab3485b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331707"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a><span data-ttu-id="22b4b-102">LINQ to XML vs. DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22b4b-102">LINQ to XML vs. DOM (Visual Basic)</span></span>
<span data-ttu-id="22b4b-103">Tato část popisuje některé klíčové rozdíly mezi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] a aktuální převládající rozhraní API pro programování XML, model DOM (Document Object Model) W3C (DOM).</span><span class="sxs-lookup"><span data-stu-id="22b4b-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="22b4b-104">Nové způsoby vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="22b4b-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="22b4b-105">Ve formátu W3C DOM sestavíte strom XML od dolní části. To znamená, že vytvoříte dokument, vytvoříte prvky a potom přidáte prvky do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="22b4b-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="22b4b-106">Následující příklad by byl typický způsob, jak vytvořit strom XML pomocí implementace modelu DOM od společnosti Microsoft <xref:System.Xml.XmlDocument>:</span><span class="sxs-lookup"><span data-stu-id="22b4b-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
Dim phone1 As XmlElement = doc.CreateElement("Phone")  
phone1.SetAttribute("Type", "Home")  
phone1.InnerText = "206-555-0144"  
Dim phone2 As XmlElement = doc.CreateElement("Phone")  
phone2.SetAttribute("Type", "Work")  
phone2.InnerText = "425-555-0145"  
Dim street1 As XmlElement = doc.CreateElement("Street1")  
street1.InnerText = "123 Main St"  
Dim city As XmlElement = doc.CreateElement("City")  
city.InnerText = "Mercer Island"  
Dim state As XmlElement = doc.CreateElement("State")  
state.InnerText = "WA"  
Dim postal As XmlElement = doc.CreateElement("Postal")  
postal.InnerText = "68042"  
Dim address As XmlElement = doc.CreateElement("Address")  
address.AppendChild(street1)  
address.AppendChild(city)  
address.AppendChild(state)  
address.AppendChild(postal)  
Dim contact As XmlElement = doc.CreateElement("Contact")  
contact.AppendChild(name)  
contact.AppendChild(phone1)  
contact.AppendChild(phone2)  
contact.AppendChild(address)  
Dim contacts As XmlElement = doc.CreateElement("Contacts")  
contacts.AppendChild(contact)  
doc.AppendChild(contacts)  
Console.WriteLine(doc.OuterXml)  
```  
  
 <span data-ttu-id="22b4b-107">Tento styl kódování vizuálně neposkytuje mnoho informací o struktuře stromu XML.</span><span class="sxs-lookup"><span data-stu-id="22b4b-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="22b4b-108">podporuje tento přístup k sestavování stromu XML, ale také podporuje alternativní přístup, *funkční konstrukce*.</span><span class="sxs-lookup"><span data-stu-id="22b4b-108">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="22b4b-109">V Visual Basic konstrukce funkčnosti používá literály XML k sestavení stromu XML.</span><span class="sxs-lookup"><span data-stu-id="22b4b-109">In Visual Basic, functional construction uses XML literals to build an XML tree.</span></span>  
  
 <span data-ttu-id="22b4b-110">Tady je postup vytvoření stejného stromu XML pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] funkční konstrukce:</span><span class="sxs-lookup"><span data-stu-id="22b4b-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="22b4b-111">Všimněte si, že odsazení kódu pro sestavení stromu XML ukazuje strukturu podkladového XML.</span><span class="sxs-lookup"><span data-stu-id="22b4b-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="22b4b-112">Další informace naleznete v tématu [vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="22b4b-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="22b4b-113">Práce přímo s prvky XML</span><span class="sxs-lookup"><span data-stu-id="22b4b-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="22b4b-114">Při programování v jazyce XML je primární fokus obvykle na prvcích XML a případně na atributy.</span><span class="sxs-lookup"><span data-stu-id="22b4b-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="22b4b-115">V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]můžete pracovat přímo s prvky a atributy XML.</span><span class="sxs-lookup"><span data-stu-id="22b4b-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="22b4b-116">K dispozici máte například následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="22b4b-116">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="22b4b-117">Vytvářejte XML elementy bez použití objektu dokumentu vůbec.</span><span class="sxs-lookup"><span data-stu-id="22b4b-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="22b4b-118">To zjednodušuje programování, pokud je třeba pracovat s fragmenty stromů XML.</span><span class="sxs-lookup"><span data-stu-id="22b4b-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="22b4b-119">Načtení `T:System.Xml.Linq.XElement` objektů přímo ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="22b4b-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="22b4b-120">Serializace objektů `T:System.Xml.Linq.XElement` do souboru nebo datového proudu.</span><span class="sxs-lookup"><span data-stu-id="22b4b-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="22b4b-121">Porovnejte je s konsorciem W3C DOM, ve kterém je dokument XML použit jako logický kontejner pro strom XML.</span><span class="sxs-lookup"><span data-stu-id="22b4b-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="22b4b-122">V modelu DOM, uzly XML, včetně elementů a atributů, musí být vytvořeny v kontextu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="22b4b-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="22b4b-123">Tady je fragment kódu pro vytvoření elementu Name v modelu DOM:</span><span class="sxs-lookup"><span data-stu-id="22b4b-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 <span data-ttu-id="22b4b-124">Chcete-li použít prvek v rámci více dokumentů, je nutné importovat uzly mezi dokumenty.</span><span class="sxs-lookup"><span data-stu-id="22b4b-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="22b4b-125">zabrání této vrstvě složitosti.</span><span class="sxs-lookup"><span data-stu-id="22b4b-125">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="22b4b-126">Při použití LINQ to XML použijete třídu <xref:System.Xml.Linq.XDocument> pouze v případě, že chcete přidat komentář nebo pokyn ke zpracování na kořenové úrovni dokumentu.</span><span class="sxs-lookup"><span data-stu-id="22b4b-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="22b4b-127">Zjednodušené zpracování názvů a oborů názvů</span><span class="sxs-lookup"><span data-stu-id="22b4b-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="22b4b-128">Zpracování názvů, oborů názvů a předpon oboru názvů je všeobecně složitou součástí programování XML.</span><span class="sxs-lookup"><span data-stu-id="22b4b-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="22b4b-129">zjednodušuje názvy a obory názvů tím, že eliminuje nutnost zabývat se předponami oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="22b4b-129">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="22b4b-130">Pokud chcete řídit předpony oboru názvů, můžete.</span><span class="sxs-lookup"><span data-stu-id="22b4b-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="22b4b-131">Ale pokud se rozhodnete, že nechcete explicitně řídit předpony oboru názvů, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] přiřadí předpony oboru názvů během serializace, pokud jsou požadovány, nebo budou serializovány pomocí výchozích oborů názvů, pokud nejsou.</span><span class="sxs-lookup"><span data-stu-id="22b4b-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="22b4b-132">Pokud jsou použity výchozí obory názvů, nebudou ve výsledném dokumentu žádné předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="22b4b-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="22b4b-133">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="22b4b-133">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="22b4b-134">Dalším problémem s modelem DOM je, že neumožňuje změnit název uzlu.</span><span class="sxs-lookup"><span data-stu-id="22b4b-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="22b4b-135">Místo toho je nutné vytvořit nový uzel a zkopírovat do něj všechny podřízené uzly a ztratit tak původní identitu uzlu.</span><span class="sxs-lookup"><span data-stu-id="22b4b-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="22b4b-136">zabrání tomuto problému tím, že vám umožní nastavit vlastnost <xref:System.Xml.Linq.XName> na uzlu.</span><span class="sxs-lookup"><span data-stu-id="22b4b-136">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="22b4b-137">Podpora statické metody pro načítání XML</span><span class="sxs-lookup"><span data-stu-id="22b4b-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="22b4b-138">umožňuje načíst XML pomocí statických metod namísto instančních metod.</span><span class="sxs-lookup"><span data-stu-id="22b4b-138">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="22b4b-139">Tím se zjednodušuje načítání a analýza.</span><span class="sxs-lookup"><span data-stu-id="22b4b-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="22b4b-140">Další informace najdete v tématu [Postup: načtení XML ze souboru (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="22b4b-140">For more information, see [How to: Load XML from a File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="22b4b-141">Odebrání podpory pro konstrukce DTD</span><span class="sxs-lookup"><span data-stu-id="22b4b-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="22b4b-142">dále zjednodušuje programování XML odebráním podpory entit a odkazů na entity.</span><span class="sxs-lookup"><span data-stu-id="22b4b-142">further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="22b4b-143">Správa entit je složitá a používá se zřídka.</span><span class="sxs-lookup"><span data-stu-id="22b4b-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="22b4b-144">Odebrání podpory zvyšuje výkon a zjednodušuje programovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="22b4b-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="22b4b-145">Po naplnění [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] stromu jsou rozbaleny všechny entity DTD.</span><span class="sxs-lookup"><span data-stu-id="22b4b-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="22b4b-146">Podpora fragmentů</span><span class="sxs-lookup"><span data-stu-id="22b4b-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="22b4b-147">neposkytuje ekvivalent pro třídu `XmlDocumentFragment`.</span><span class="sxs-lookup"><span data-stu-id="22b4b-147">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="22b4b-148">V mnoha případech ale koncept `XmlDocumentFragment` může být zpracován výsledkem dotazu, který je zadán jako <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XNode>nebo <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="22b4b-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="22b4b-149">Podpora pro XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="22b4b-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="22b4b-150">poskytuje podporu pro <xref:System.Xml.XPath.XPathNavigator> prostřednictvím rozšiřujících metod v oboru názvů <xref:System.Xml.XPath?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="22b4b-150">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="22b4b-151">Další informace najdete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="22b4b-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="22b4b-152">Podpora pro prázdné znaky a odsazení</span><span class="sxs-lookup"><span data-stu-id="22b4b-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="22b4b-153">zpracovává prázdné znaky více než DOM.</span><span class="sxs-lookup"><span data-stu-id="22b4b-153">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="22b4b-154">Běžným scénářem je čtení odsazeného XML, vytvoření stromu XML v paměti bez jakýchkoli textových uzlů s prázdnými znaky (tj. bez zachovávání prázdných znaků), provedení některých operací v XML a následné uložení XML s odsazením.</span><span class="sxs-lookup"><span data-stu-id="22b4b-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="22b4b-155">Při serializaci XML s formátováním je zachováno pouze významné prázdné znaky ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="22b4b-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="22b4b-156">Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22b4b-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="22b4b-157">Dalším běžným scénářem je číst a upravovat kód XML, který již byl záměrně odsazen.</span><span class="sxs-lookup"><span data-stu-id="22b4b-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="22b4b-158">Toto odsazení nebudete chtít nijak měnit.</span><span class="sxs-lookup"><span data-stu-id="22b4b-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="22b4b-159">V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]můžete to provést tak, že zachováte prázdné místo při načítání nebo analýze XML a zakážete formátování při serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="22b4b-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="22b4b-160">ukládá prázdné znaky jako <xref:System.Xml.Linq.XText> uzel místo typu specializovaného <xref:System.Xml.XmlNodeType.Whitespace>ho uzlu jako DOM.</span><span class="sxs-lookup"><span data-stu-id="22b4b-160">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="22b4b-161">Podpora poznámek</span><span class="sxs-lookup"><span data-stu-id="22b4b-161">Support for Annotations</span></span>  
 <span data-ttu-id="22b4b-162">prvky [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podporují rozšiřitelnou sadu poznámek.</span><span class="sxs-lookup"><span data-stu-id="22b4b-162">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] elements support an extensible set of annotations.</span></span> <span data-ttu-id="22b4b-163">To je užitečné pro sledování různých informací o prvku, například informace o schématu, informace o tom, zda je element svázán s uživatelským rozhraním, nebo jakýkoli jiný druh informací specifických pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="22b4b-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="22b4b-164">Další informace najdete v tématu [LINQ to XML poznámky](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="22b4b-164">For more information, see [LINQ to XML Annotations](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="22b4b-165">Podpora informací o schématu</span><span class="sxs-lookup"><span data-stu-id="22b4b-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="22b4b-166">poskytuje podporu pro ověřování XSD prostřednictvím rozšiřujících metod v oboru názvů <xref:System.Xml.Schema?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="22b4b-166">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="22b4b-167">Můžete ověřit, že strom XML odpovídá XSD.</span><span class="sxs-lookup"><span data-stu-id="22b4b-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="22b4b-168">Ke stromu XML můžete naplnit informační sadu po PSVI (post-Schema-Revalidace).</span><span class="sxs-lookup"><span data-stu-id="22b4b-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="22b4b-169">Další informace naleznete v tématu [How to: Validate using XSD](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span><span class="sxs-lookup"><span data-stu-id="22b4b-169">For more information, see [How to: Validate Using XSD](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22b4b-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22b4b-170">See also</span></span>

- [<span data-ttu-id="22b4b-171">Začínáme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="22b4b-171">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
