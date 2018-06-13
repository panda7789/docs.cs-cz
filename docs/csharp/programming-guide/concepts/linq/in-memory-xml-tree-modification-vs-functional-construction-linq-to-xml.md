---
title: Změna stromové struktury v paměti XML vs. Funkční konstrukce (technologie LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 3e6d86ac11f10d7dbb3d270410415fb23acb2e01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333733"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a><span data-ttu-id="40a81-102">Změna stromové struktury v paměti XML vs. Funkční konstrukce (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="40a81-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>
<span data-ttu-id="40a81-103">Úprava strom XML na místě je tradiční přístup k změna tvaru dokument XML.</span><span class="sxs-lookup"><span data-stu-id="40a81-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="40a81-104">Typická aplikace dokumentu načte do úložiště dat, jako je například DOM nebo [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; používá programovací rozhraní vložení uzlů, odstranit uzly nebo změnit obsah uzly; a potom uloží do souboru XML nebo přenáší přes síť.</span><span class="sxs-lookup"><span data-stu-id="40a81-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="40a81-105"> Umožňuje jiná možnost, která je užitečné v mnoha scénářích *: funkční konstrukce*.</span><span class="sxs-lookup"><span data-stu-id="40a81-105"> enables another approach that is useful in many scenarios *: functional construction*.</span></span> <span data-ttu-id="40a81-106">Funkční konstrukce zpracovává změny dat, jako problém transformace, nikoli jako podrobné manipulaci data Store.</span><span class="sxs-lookup"><span data-stu-id="40a81-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="40a81-107">Pokud může trvat znázornění dat a transformují je efektivně z jednoho formátu do druhého, výsledek je stejný, jako kdyby trvalo jedno úložiště dat a s nimi manipulovat nějakým způsobem provést další obrazec.</span><span class="sxs-lookup"><span data-stu-id="40a81-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="40a81-108">Klíč k funkční konstrukce přístup, je předat výsledky dotazů pro <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement> konstruktory.</span><span class="sxs-lookup"><span data-stu-id="40a81-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="40a81-109">V mnoha případech můžete napsat kód transformational za zlomek času, které by byly třeba k manipulaci s úložiště dat, a tento kód je robustnější a snadněji provádět údržbu.</span><span class="sxs-lookup"><span data-stu-id="40a81-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="40a81-110">V těchto případech i když transformational přístup může trvat další výpočetní výkon, je efektivnější způsob, jak upravovat data.</span><span class="sxs-lookup"><span data-stu-id="40a81-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="40a81-111">Pokud znáte funkční přístup vývojář se výsledný kód v mnoha případech je srozumitelnější.</span><span class="sxs-lookup"><span data-stu-id="40a81-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="40a81-112">Je snadno najít kód, který upravuje jednotlivých součástí stromu.</span><span class="sxs-lookup"><span data-stu-id="40a81-112">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="40a81-113">Přístup, kde můžete upravit XML stromu místní je známější mnoho DOM programátorům, zatímco kód napsaný funkční přístup může vypadat neznámého vývojáře, kteří ještě nerozumí tento přístup.</span><span class="sxs-lookup"><span data-stu-id="40a81-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="40a81-114">Pokud je nutné provést pouze malé změny na velké strom XML, přístup, kde můžete upravit stromu zavedené v mnoha případech bude trvat méně času procesoru.</span><span class="sxs-lookup"><span data-stu-id="40a81-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="40a81-115">Toto téma poskytuje příklad, který implementuje pomocí obou přístupů.</span><span class="sxs-lookup"><span data-stu-id="40a81-115">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="40a81-116">Transformace atributy do elementů</span><span class="sxs-lookup"><span data-stu-id="40a81-116">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="40a81-117">Například předpokládejme, že chcete upravit následující jednoduché dokumentu XML tak, aby atributy stát elementy.</span><span class="sxs-lookup"><span data-stu-id="40a81-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="40a81-118">Toto téma představuje první přístup úpravu tradičním na místě.</span><span class="sxs-lookup"><span data-stu-id="40a81-118">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="40a81-119">Poté zobrazí funkční konstrukce přístup.</span><span class="sxs-lookup"><span data-stu-id="40a81-119">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="40a81-120">Úprava stromu XML</span><span class="sxs-lookup"><span data-stu-id="40a81-120">Modifying the XML Tree</span></span>  
 <span data-ttu-id="40a81-121">Můžete napsat kód procedurální k vytváření prvků z atributů a pak odstraňte atributy, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="40a81-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="40a81-122">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="40a81-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="40a81-123">Funkční konstrukce přístup</span><span class="sxs-lookup"><span data-stu-id="40a81-123">Functional Construction Approach</span></span>  
 <span data-ttu-id="40a81-124">Naopak funkční přístup se skládá z kódu a vytvořit novou větev, výběr a Výběr elementů a atributů ze stromu zdroj a je vhodné, když jsou přidávány do stromu nové transformace.</span><span class="sxs-lookup"><span data-stu-id="40a81-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="40a81-125">Funkční přístup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="40a81-125">The functional approach looks like the following:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="40a81-126">Tento příklad výstupu stejné XML jako v prvním příkladu.</span><span class="sxs-lookup"><span data-stu-id="40a81-126">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="40a81-127">Všimněte si však, že ve skutečnosti najdete v části výsledné strukturu nový kód XML v funkční přístup.</span><span class="sxs-lookup"><span data-stu-id="40a81-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="40a81-128">Uvidíte vytvoření `Root` element, kód, který žádá o `Child1` element ze stromu zdroje a kód, který transformuje atributy ze stromu zdroje na elementy ve stromové struktuře nové.</span><span class="sxs-lookup"><span data-stu-id="40a81-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="40a81-129">Funkční příklad v tomto případě není žádná kratší než v prvním příkladu, a není skutečně jednodušší.</span><span class="sxs-lookup"><span data-stu-id="40a81-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="40a81-130">Ale pokud máte mnoho změn, aby na strom XML, není funkční přístup se stane poměrně složitá a poněkud obtuse.</span><span class="sxs-lookup"><span data-stu-id="40a81-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="40a81-131">Naproti tomu při použití funkční přístup, stále jenom formuláře požadované XML, vkládání dotazy a výrazy podle potřeby, požadovaný obsah stáhnout.</span><span class="sxs-lookup"><span data-stu-id="40a81-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="40a81-132">Funkční způsob vypočítá kód, který je snazší správa.</span><span class="sxs-lookup"><span data-stu-id="40a81-132">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="40a81-133">Všimněte si, že v tomto případě funkční přístup pravděpodobně nebude provádět poměrně a také způsob zpracování stromu.</span><span class="sxs-lookup"><span data-stu-id="40a81-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="40a81-134">Hlavní problém je, že funkční přístup vytváří více krátké povahy objektů.</span><span class="sxs-lookup"><span data-stu-id="40a81-134">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="40a81-135">Kompromis je však efektivní jeden Pokud funkční přístup umožňuje vyšší produktivita programátory.</span><span class="sxs-lookup"><span data-stu-id="40a81-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="40a81-136">To je velmi jednoduchý příklad, ale funguje na tento rozdíl v filosofie mezi dva přístupy.</span><span class="sxs-lookup"><span data-stu-id="40a81-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="40a81-137">Funkční způsob vypočítá větší zvýšení produktivity pro převod větší dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="40a81-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40a81-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="40a81-138">See Also</span></span>  
 [<span data-ttu-id="40a81-139">Úprava XML stromů (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="40a81-139">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
