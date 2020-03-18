---
title: Úprava stromu XML v paměti vs. funkční konstrukce (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 55eb95585bdd5d2c52175cacae2e6d049bd06f69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484554"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a><span data-ttu-id="001fa-102">Úprava stromu XML v paměti vs. funkční konstrukce (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="001fa-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>
<span data-ttu-id="001fa-103">Změna stromu XML na místě je tradiční přístup ke změně tvaru dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="001fa-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="001fa-104">Typická aplikace načte dokument do úložiště dat, jako je například DOM nebo [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; používá programovací rozhraní k vkládání uzlů, odstraňování uzlů nebo změně obsahu uzlů; a potom uloží XML do souboru nebo jej odešle v síti.</span><span class="sxs-lookup"><span data-stu-id="001fa-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="001fa-105">umožňuje jiný přístup, který je užitečný v mnoha scénářích: *funkční konstrukce*.</span><span class="sxs-lookup"><span data-stu-id="001fa-105">enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="001fa-106">Funkční konstrukce považuje úpravy dat za problém transformace, nikoli jako podrobnou manipulaci s úložištěm dat.</span><span class="sxs-lookup"><span data-stu-id="001fa-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="001fa-107">Pokud můžete vzít reprezentaci dat a efektivně je transformovat z jednoho formuláře do druhého, výsledek je stejný, jako kdybyste vzali jedno úložiště dat a nějakým způsobem s ním manipulovali, aby se vzal jiný tvar.</span><span class="sxs-lookup"><span data-stu-id="001fa-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="001fa-108">Klíčem k přístupu funkce konstrukce je předat výsledky <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> dotazů a konstruktory.</span><span class="sxs-lookup"><span data-stu-id="001fa-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="001fa-109">V mnoha případech můžete napsat transformační kód ve zlomku času, který by trvalo manipulovat úložiště dat a že kód je robustnější a snadněji udržovat.</span><span class="sxs-lookup"><span data-stu-id="001fa-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="001fa-110">V těchto případech i v případě, že transformační přístup může trvat více výpočetní výkon, je efektivnější způsob, jak upravit data.</span><span class="sxs-lookup"><span data-stu-id="001fa-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="001fa-111">Pokud vývojář je obeznámen s funkční přístup, výsledný kód v mnoha případech je srozumitelnější.</span><span class="sxs-lookup"><span data-stu-id="001fa-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="001fa-112">Je snadné najít kód, který upravuje každou část stromu.</span><span class="sxs-lookup"><span data-stu-id="001fa-112">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="001fa-113">Přístup, kde můžete upravit strom XML na místě je známější mnoho programátorů DOM, zatímco kód napsaný pomocí funkční ho přístupu může vypadat neznámé vývojáři, který ještě nerozumí, že přístup.</span><span class="sxs-lookup"><span data-stu-id="001fa-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="001fa-114">Pokud máte provést pouze malé změny velké stromu XML, přístup, kde upravit strom na místě v mnoha případech bude trvat méně času procesoru.</span><span class="sxs-lookup"><span data-stu-id="001fa-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="001fa-115">Toto téma obsahuje příklad, který je implementován s oběma přístupy.</span><span class="sxs-lookup"><span data-stu-id="001fa-115">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="001fa-116">Transformace atributů na prvky</span><span class="sxs-lookup"><span data-stu-id="001fa-116">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="001fa-117">V tomto příkladu předpokládejme, že chcete upravit následující jednoduchý dokument XML tak, aby se atributy staly elementy.</span><span class="sxs-lookup"><span data-stu-id="001fa-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="001fa-118">Toto téma nejprve představuje tradiční přístup změny na místě.</span><span class="sxs-lookup"><span data-stu-id="001fa-118">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="001fa-119">To pak ukazuje funkční stavební přístup.</span><span class="sxs-lookup"><span data-stu-id="001fa-119">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="001fa-120">Úprava stromu XML</span><span class="sxs-lookup"><span data-stu-id="001fa-120">Modifying the XML Tree</span></span>  
 <span data-ttu-id="001fa-121">Můžete napsat nějaký procedurální kód pro vytvoření prvků z atributů a potom odstranit atributy takto:</span><span class="sxs-lookup"><span data-stu-id="001fa-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="001fa-122">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="001fa-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="001fa-123">Přístup k funkční konstrukci</span><span class="sxs-lookup"><span data-stu-id="001fa-123">Functional Construction Approach</span></span>  
 <span data-ttu-id="001fa-124">Naproti tomu funkční přístup se skládá z kódu k vytvoření nového stromu, vychystávání a výběr u prvků a atributů ze zdrojového stromu a jejich transformace podle potřeby, jak jsou přidány do nového stromu.</span><span class="sxs-lookup"><span data-stu-id="001fa-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="001fa-125">Funkční přístup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="001fa-125">The functional approach looks like the following:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="001fa-126">Tento příklad vyvezuje stejný XML jako první příklad.</span><span class="sxs-lookup"><span data-stu-id="001fa-126">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="001fa-127">Všimněte si však, že můžete skutečně zobrazit výslednou strukturu nového XML ve funkčním přístupu.</span><span class="sxs-lookup"><span data-stu-id="001fa-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="001fa-128">Můžete vidět vytvoření `Root` prvku, kód, který vytáhne `Child1` prvek ze zdrojového stromu a kód, který transformuje atributy ze zdrojového stromu na prvky v novém stromu.</span><span class="sxs-lookup"><span data-stu-id="001fa-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="001fa-129">Funkční příklad v tomto případě není o nic kratší než první příklad a není to opravdu jednodušší.</span><span class="sxs-lookup"><span data-stu-id="001fa-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="001fa-130">Pokud však máte mnoho změn, které chcete provést ve stromu XML, nefunkční přístup se stane poměrně složitým a poněkud tupým.</span><span class="sxs-lookup"><span data-stu-id="001fa-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="001fa-131">Naproti tomu při použití funkčního přístupu stále tvoříte pouze požadovaný xml, vkládání dotazů a výrazů podle potřeby, chcete-li získat požadovaný obsah.</span><span class="sxs-lookup"><span data-stu-id="001fa-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="001fa-132">Funkční přístup poskytuje kód, který je snadněji udržovat.</span><span class="sxs-lookup"><span data-stu-id="001fa-132">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="001fa-133">Všimněte si, že v tomto případě by funkční přístup pravděpodobně neprovedl tak dobře, jako přístup manipulace se stromem.</span><span class="sxs-lookup"><span data-stu-id="001fa-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="001fa-134">Hlavním problémem je, že funkční přístup vytváří více krátkodobých objektů.</span><span class="sxs-lookup"><span data-stu-id="001fa-134">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="001fa-135">Kompromis je však efektivní, pokud použití funkčního přístupu umožňuje větší produktivitu programátorů.</span><span class="sxs-lookup"><span data-stu-id="001fa-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="001fa-136">Jedná se o velmi jednoduchý příklad, ale slouží k zobrazení rozdílu ve filozofii mezi těmito dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="001fa-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="001fa-137">Funkční přístup přináší vyšší nárůst produktivity při transformaci větších dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="001fa-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  