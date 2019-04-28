---
title: Změna stromu XML v paměti vs. Funkční konstrukce (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 1dea6a687f041c3464f582d3339f76713828f244
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667590"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a><span data-ttu-id="d4436-102">Změna stromu XML v paměti vs. Funkční konstrukce (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d4436-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>
<span data-ttu-id="d4436-103">Změna stromu XML v místě je tradiční přístup na měnící tvar dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="d4436-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="d4436-104">Typická aplikace načte dokument do úložiště dat, jako je například modelu DOM nebo [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; používá programovací rozhraní pro vložení uzlů, odstraňovat uzly nebo změnit obsah uzlů a pak uloží do souboru XML nebo přenáší přes síť.</span><span class="sxs-lookup"><span data-stu-id="d4436-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d4436-105">umožňuje další možností, které jsou užitečné v mnoha scénářích: *funkční konstrukce*.</span><span class="sxs-lookup"><span data-stu-id="d4436-105">enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="d4436-106">Funkční konstrukce zpracovává změny dat, jako problém transformace, nikoli jako podrobné manipulaci s úložištěm dat.</span><span class="sxs-lookup"><span data-stu-id="d4436-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="d4436-107">Pokud můžete vzít vyjádření data a transformovali je efektivní z jednoho formuláře do jiného, výsledek je stejný, jako by trvalo jednoho úložiště dat a manipulovat nějakým způsobem provést jiný tvar.</span><span class="sxs-lookup"><span data-stu-id="d4436-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="d4436-108">Klíč k přístupu funkční konstrukce je předat výsledky dotazů pro <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement> konstruktory.</span><span class="sxs-lookup"><span data-stu-id="d4436-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="d4436-109">V mnoha případech můžete napsat kód transformace, jehož za zlomek času, který by to obnášelo k práci s úložišti dat a tento kód je robustní a jednodušší správu.</span><span class="sxs-lookup"><span data-stu-id="d4436-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="d4436-110">V těchto případech i v případě, že transformace, jehož přístupu může trvat více výpočetního výkonu, je efektivnější způsob, jak upravovat data.</span><span class="sxs-lookup"><span data-stu-id="d4436-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="d4436-111">Pokud vývojář zkušenosti s funkční přístup, je výsledný kód v mnoha případech lze snáze pochopit.</span><span class="sxs-lookup"><span data-stu-id="d4436-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="d4436-112">Je snadné kód, který upravuje jednotlivých součástí stromu.</span><span class="sxs-lookup"><span data-stu-id="d4436-112">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="d4436-113">Místo, kde upravíte XML stromu místní přístup je více do hloubky na mnoho programátorů modelu DOM, zatímco kód napsané s využitím funkční přístup může být nevypadá to povědomě pro vývojáře, kteří ještě nerozumí tento přístup.</span><span class="sxs-lookup"><span data-stu-id="d4436-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="d4436-114">Pokud je nutné provést pouze malé změny do velké stromu XML, přístup místo, kde upravíte stromu je v mnoha případech bude trvat méně času procesoru.</span><span class="sxs-lookup"><span data-stu-id="d4436-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="d4436-115">V tomto tématu poskytuje příklad, který implementuje pomocí obou metod.</span><span class="sxs-lookup"><span data-stu-id="d4436-115">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="d4436-116">Transformace atributů na prvky</span><span class="sxs-lookup"><span data-stu-id="d4436-116">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="d4436-117">V tomto příkladu předpokládejme, že chcete změnit následující jednoduchý dokument XML tak, aby atributy stát elementů.</span><span class="sxs-lookup"><span data-stu-id="d4436-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="d4436-118">Toto téma představuje první přístup tradiční místní úpravy.</span><span class="sxs-lookup"><span data-stu-id="d4436-118">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="d4436-119">Potom zobrazí funkční konstrukce přístup.</span><span class="sxs-lookup"><span data-stu-id="d4436-119">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="d4436-120">Změna stromu XML</span><span class="sxs-lookup"><span data-stu-id="d4436-120">Modifying the XML Tree</span></span>  
 <span data-ttu-id="d4436-121">Můžete napsat kód procedury k vytváření prvků z atributů a atributů, odstraňte následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d4436-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="d4436-122">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d4436-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="d4436-123">Funkční konstrukce přístup</span><span class="sxs-lookup"><span data-stu-id="d4436-123">Functional Construction Approach</span></span>  
 <span data-ttu-id="d4436-124">Naopak funkční přístup se skládá z kódu k vytvoření nové větve, výběru a Výběr elementů a atributů ze stromu zdrojového kódu a transformují je podle potřeby, jako jsou přidány do nového stromu.</span><span class="sxs-lookup"><span data-stu-id="d4436-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="d4436-125">Funkční přístup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="d4436-125">The functional approach looks like the following:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="d4436-126">V tomto příkladu vrátí stejné XML jako v prvním příkladu.</span><span class="sxs-lookup"><span data-stu-id="d4436-126">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="d4436-127">Všimněte si však, že vidíte ve skutečnosti výsledný struktura nový kód XML v funkční přístup.</span><span class="sxs-lookup"><span data-stu-id="d4436-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="d4436-128">Můžete zobrazit vytvořením `Root` elementu, kód, který si vyžádá `Child1` element ze stromu zdrojového kódu a kód, který transformuje atributy ze stromu zdrojového kódu na prvky do nového stromu.</span><span class="sxs-lookup"><span data-stu-id="d4436-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="d4436-129">Funkční příklad v tomto případě není žádná kratší než v prvním příkladu, a není ve skutečnosti jednodušší.</span><span class="sxs-lookup"><span data-stu-id="d4436-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="d4436-130">Nicméně pokud máte mnoho změn tak, aby stromu XML nefunkční přístup se stanou poměrně složité a trochu obtuse.</span><span class="sxs-lookup"><span data-stu-id="d4436-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="d4436-131">Naopak při použití funkční přístup, stále pouze formulář požadované XML vkládat dotazy a výrazy podle potřeby, aby se načetla požadovaný obsah.</span><span class="sxs-lookup"><span data-stu-id="d4436-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="d4436-132">Funkční přístup poskytuje kód, který je snazší Údržba.</span><span class="sxs-lookup"><span data-stu-id="d4436-132">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="d4436-133">Všimněte si, že v tomto případě funkční přístup pravděpodobně nebude provádět úplně stejně přístup zpracování stromu.</span><span class="sxs-lookup"><span data-stu-id="d4436-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="d4436-134">Hlavní problém je, že vytvoří funkční přístup více krátký povahy objekty.</span><span class="sxs-lookup"><span data-stu-id="d4436-134">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="d4436-135">Výměnou za to však je efektivní jeden, pokud pomocí funkční přístup umožňuje vyšší produktivita programátorů.</span><span class="sxs-lookup"><span data-stu-id="d4436-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="d4436-136">To je velmi jednoduchý příklad, ale funguje zobrazíte filozofie rozdíl mezi dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="d4436-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="d4436-137">Funkční přístup poskytuje větší zvýšení produktivity pro transformaci větší dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="d4436-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4436-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4436-138">See also</span></span>

- [<span data-ttu-id="d4436-139">Změna stromů XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d4436-139">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
