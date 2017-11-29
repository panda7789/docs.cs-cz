---
title: Technologie LINQ to XML vs. Model DOM (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18c36130-d598-40b7-9007-828232252978
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1f89d3ded61daf16d4a59ccabb4d58625cae4a58
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a><span data-ttu-id="381b1-102">Technologie LINQ to XML vs. Model DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="381b1-102">LINQ to XML vs. DOM (Visual Basic)</span></span>
<span data-ttu-id="381b1-103">Tato část popisuje některé hlavní rozdíly mezi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] a aktuální převládá XML programovací rozhraní API, W3C Model DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="381b1-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="381b1-104">Nové způsoby, jak vytvořit stromy XML</span><span class="sxs-lookup"><span data-stu-id="381b1-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="381b1-105">V modelu DOM W3C sestavení strom XML zdola nahoru; To znamená vytvoření dokumentu, můžete vytvořit elementy a poté přidejte elementy v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="381b1-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="381b1-106">Například následující by typické způsob, jak vytvořit strom XML pomocí implementace Microsoft DOM, <xref:System.Xml.XmlDocument>:</span><span class="sxs-lookup"><span data-stu-id="381b1-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="381b1-107">Tento styl kódování neposkytuje vizuálně velkého množství informací o struktuře stromu XML.</span><span class="sxs-lookup"><span data-stu-id="381b1-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="381b1-108">podporuje tento přístup k vytváření strom XML, ale také podporuje alternativní způsob, *funkční konstrukce*.</span><span class="sxs-lookup"><span data-stu-id="381b1-108"> supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="381b1-109">V jazyce Visual Basic používá funkční konstrukce XML – literály Sestavit strom XML.</span><span class="sxs-lookup"><span data-stu-id="381b1-109">In Visual Basic, functional construction uses XML literals to build an XML tree.</span></span>  
  
 <span data-ttu-id="381b1-110">Zde je, jak by vytvořit stejném stromu pro XML pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] funkční konstrukce:</span><span class="sxs-lookup"><span data-stu-id="381b1-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="381b1-111">Všimněte si, že odsazení kódu k vytvoření stromu XML ukazuje strukturu základní XML.</span><span class="sxs-lookup"><span data-stu-id="381b1-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="381b1-112">Další informace najdete v tématu [vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="381b1-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="381b1-113">Práce přímo se elementy XML</span><span class="sxs-lookup"><span data-stu-id="381b1-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="381b1-114">Když budete programu s XML, hlavním cílem je obvykle na elementy XML a případně na atributy.</span><span class="sxs-lookup"><span data-stu-id="381b1-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="381b1-115">V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], může spolupracovat přímo s XML elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="381b1-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="381b1-116">Například můžete provést následující:</span><span class="sxs-lookup"><span data-stu-id="381b1-116">For example, you can do the following:</span></span>  
  
-   <span data-ttu-id="381b1-117">Vytvořte elementů XML pomocí objektu dokumentu vůbec.</span><span class="sxs-lookup"><span data-stu-id="381b1-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="381b1-118">Tato funkce zjednodušuje programování při práci s fragmenty stromy XML.</span><span class="sxs-lookup"><span data-stu-id="381b1-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
-   <span data-ttu-id="381b1-119">Zatížení `T:System.Xml.Linq.XElement` objekty přímo ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="381b1-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
-   <span data-ttu-id="381b1-120">Serializovat `T:System.Xml.Linq.XElement` objekty do souboru nebo datový proud.</span><span class="sxs-lookup"><span data-stu-id="381b1-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="381b1-121">Výsledky porovnejte s DOM W3C, ve kterém se používá v dokumentu XML jako logický kontejner pro stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="381b1-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="381b1-122">V modelu DOM musí být vytvořený z uzlů XML, včetně elementů a atributů, v rámci dokument XML.</span><span class="sxs-lookup"><span data-stu-id="381b1-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="381b1-123">Zde je fragment kódu, chcete-li vytvořit název elementu v modelu DOM:</span><span class="sxs-lookup"><span data-stu-id="381b1-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 <span data-ttu-id="381b1-124">Pokud chcete použít element napříč více dokumentů, je nutné naimportovat uzly na dokumentech.</span><span class="sxs-lookup"><span data-stu-id="381b1-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="381b1-125">zabraňuje tuto vrstvu složitost.</span><span class="sxs-lookup"><span data-stu-id="381b1-125"> avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="381b1-126">Při použití technologie LINQ to XML, můžete použít <xref:System.Xml.Linq.XDocument> třídy pouze v případě, že chcete přidat instrukcí komentářů nebo zpracování na kořenové úrovni dokumentu.</span><span class="sxs-lookup"><span data-stu-id="381b1-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="381b1-127">Zjednodušená zpracování názvy a obory názvů</span><span class="sxs-lookup"><span data-stu-id="381b1-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="381b1-128">Zpracování názvy, obory názvů a předpony oboru názvů je obecně komplexní součástí programování XML.</span><span class="sxs-lookup"><span data-stu-id="381b1-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="381b1-129">zjednodušuje názvy a obory názvů odstraněním požadavek jak nakládat s předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="381b1-129"> simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="381b1-130">Pokud chcete řídit předpony oboru názvů, můžete.</span><span class="sxs-lookup"><span data-stu-id="381b1-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="381b1-131">Ale pokud se rozhodnete řídit není explicitně předpony oboru názvů [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] přidělí předpony oboru názvů během serializace, pokud jsou požadované, nebo se serializovat pomocí výchozí obory názvů, pokud nejsou.</span><span class="sxs-lookup"><span data-stu-id="381b1-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="381b1-132">Pokud se používají výchozí obory názvů, budou ve výsledném dokumentu existovat žádné předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="381b1-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="381b1-133">Další informace najdete v tématu [práci s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="381b1-133">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="381b1-134">Dalším problémem s modelu DOM je, že ji neumožňuje změnit název uzlu.</span><span class="sxs-lookup"><span data-stu-id="381b1-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="381b1-135">Místo toho budete muset vytvořit nový uzel a zkopírujte všechny podřízené uzly, došlo ke ztrátě identitě původní uzel.</span><span class="sxs-lookup"><span data-stu-id="381b1-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="381b1-136">tomuto problému se vyhnete tím, že vám nastavit <xref:System.Xml.Linq.XName> vlastnost na uzlu.</span><span class="sxs-lookup"><span data-stu-id="381b1-136"> avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="381b1-137">Podpora statickou metodu pro načítání dat XML</span><span class="sxs-lookup"><span data-stu-id="381b1-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="381b1-138">umožňuje načíst XML pomocí statické metody, namísto metody instance.</span><span class="sxs-lookup"><span data-stu-id="381b1-138"> lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="381b1-139">Tato funkce zjednodušuje načítání a analýzu.</span><span class="sxs-lookup"><span data-stu-id="381b1-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="381b1-140">Další informace najdete v tématu [postupy: načtení XML ze souboru (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="381b1-140">For more information, see [How to: Load XML from a File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="381b1-141">Odebrání podpory pro DTD konstrukce</span><span class="sxs-lookup"><span data-stu-id="381b1-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="381b1-142">Další zjednodušuje programování odebráním podporu pro entity a odkazy na entity XML.</span><span class="sxs-lookup"><span data-stu-id="381b1-142"> further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="381b1-143">Správa entit je složitý a je používána zřídka.</span><span class="sxs-lookup"><span data-stu-id="381b1-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="381b1-144">Odebrání jejich podpora zvyšuje výkon a zjednodušuje programovací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="381b1-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="381b1-145">Když [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] stromu je vyplněný, jsou všechny entity DTD rozšířit.</span><span class="sxs-lookup"><span data-stu-id="381b1-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="381b1-146">Podpora pro fragmenty</span><span class="sxs-lookup"><span data-stu-id="381b1-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="381b1-147">neposkytuje ekvivalentní pro `XmlDocumentFragment` třídy.</span><span class="sxs-lookup"><span data-stu-id="381b1-147"> does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="381b1-148">V mnoha případech ale `XmlDocumentFragment` koncept může zpracovávat výsledek dotazu, který je zadán jako <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XNode>, nebo <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="381b1-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="381b1-149">Podpora pro objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="381b1-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="381b1-150">poskytuje podporu pro <xref:System.Xml.XPath.XPathNavigator> prostřednictvím metody rozšíření v <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="381b1-150"> provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="381b1-151">Další informace naleznete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="381b1-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="381b1-152">Podpora pro mezer a odsazení</span><span class="sxs-lookup"><span data-stu-id="381b1-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="381b1-153">zpracovává mezer jednodušeji než modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="381b1-153"> handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="381b1-154">Běžný scénář je číst zobrazují odsazené XML, vytvořte ve stromu v paměti XML bez mezer text uzlů (tedy ne zachování mezer), provádění některých operací na soubor XML a potom uložte soubor XML s odsazení.</span><span class="sxs-lookup"><span data-stu-id="381b1-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="381b1-155">Při serializaci XML s formátování se zachová jenom významné mezer ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="381b1-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="381b1-156">Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="381b1-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="381b1-157">Další z typických možností je číst a upravovat kód XML, který je už záměrně zobrazují odsazené.</span><span class="sxs-lookup"><span data-stu-id="381b1-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="381b1-158">Možná chcete změnit toto odsazení žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="381b1-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="381b1-159">V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete to udělat zachování mezer při načtení nebo analyzovat soubor XML a zakázání formátování při serializaci XML.</span><span class="sxs-lookup"><span data-stu-id="381b1-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="381b1-160">ukládá mezer jako <xref:System.Xml.Linq.XText> uzlu, místo nutnosti specializované <xref:System.Xml.XmlNodeType.Whitespace> typ uzlu jako modelu DOM nemá.</span><span class="sxs-lookup"><span data-stu-id="381b1-160"> stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="381b1-161">Podpora pro poznámky</span><span class="sxs-lookup"><span data-stu-id="381b1-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="381b1-162">elementy podporovat rozšiřitelnou sadu poznámky.</span><span class="sxs-lookup"><span data-stu-id="381b1-162"> elements support an extensible set of annotations.</span></span> <span data-ttu-id="381b1-163">To je užitečné pro sledování různé informace o elementu, například informace o schématu, informace o tom, jestli je vázána element uživatelského rozhraní nebo všechny ostatní informace druh specifické pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="381b1-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="381b1-164">Další informace najdete v tématu [technologie LINQ to XML poznámky](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span><span class="sxs-lookup"><span data-stu-id="381b1-164">For more information, see [LINQ to XML Annotations](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="381b1-165">Podpora pro informace o schématu</span><span class="sxs-lookup"><span data-stu-id="381b1-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="381b1-166">poskytuje podporu pro ověření XSD prostřednictvím metody rozšíření v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="381b1-166"> provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="381b1-167">Můžete ověřit, že ve stromu XML v souladu se XSD.</span><span class="sxs-lookup"><span data-stu-id="381b1-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="381b1-168">Jej můžete naplnit stromu XML s informační sadu po schema ověření (PSVI).</span><span class="sxs-lookup"><span data-stu-id="381b1-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="381b1-169">Další informace najdete v tématu [postupy: ověření pomocí XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) a <xref:System.Xml.Schema.Extensions>.</span><span class="sxs-lookup"><span data-stu-id="381b1-169">For more information, see [How to: Validate Using XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="381b1-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="381b1-170">See Also</span></span>  
 [<span data-ttu-id="381b1-171">Začínáme (technologie LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="381b1-171">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
