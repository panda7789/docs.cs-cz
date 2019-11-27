---
title: Úprava struktury XML v paměti vs. konstrukce funkčnosti (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: d91c4ebf-6549-43cc-9961-26d4a82f722b
ms.openlocfilehash: 15c38cdf7ce860b34d8d3e9d59b8f06d80f6edd8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344441"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="3c958-102">Úprava struktury XML v paměti vs. konstrukce funkčnosti (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c958-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="3c958-103">Úprava stromu XML na místě je tradiční přístup ke změně tvaru dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="3c958-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="3c958-104">Typická aplikace načte dokument do úložiště dat, jako je DOM nebo [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; používá programovací rozhraní pro vkládání uzlů, odstraňování uzlů nebo změnu obsahu uzlů. a pak soubor XML uloží do souboru nebo ho přenáší přes síť.</span><span class="sxs-lookup"><span data-stu-id="3c958-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="3c958-105">umožňuje další přístup, který je užitečný v mnoha scénářích *: konstrukce funkcí*.</span><span class="sxs-lookup"><span data-stu-id="3c958-105">enables another approach that is useful in many scenarios *: functional construction*.</span></span> <span data-ttu-id="3c958-106">Funkční konstrukce zpracovává změny dat jako problém transformace, nikoli jako podrobnou manipulaci s úložištěm dat.</span><span class="sxs-lookup"><span data-stu-id="3c958-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="3c958-107">Pokud můžete podniknout data a efektivně je transformovat z jednoho formuláře na jiný, výsledek je stejný jako v případě, že jste si pořídili jedno úložiště dat a manipulujete ho nějakým způsobem, aby byl jiný tvar.</span><span class="sxs-lookup"><span data-stu-id="3c958-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="3c958-108">Klíč k přístupu k funkcím konstrukce je předat výsledky dotazů do <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement> konstruktory.</span><span class="sxs-lookup"><span data-stu-id="3c958-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="3c958-109">V mnoha případech můžete napsat transformační kód za zlomek času, který by trval při manipulaci s úložištěm dat, a tento kód je robustnější a snazší ho udržovat.</span><span class="sxs-lookup"><span data-stu-id="3c958-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="3c958-110">V těchto případech i v případě, že transformační přístup může trvat více výpočetní výkon, je efektivnější způsob, jak data upravovat.</span><span class="sxs-lookup"><span data-stu-id="3c958-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="3c958-111">Pokud je vývojář obeznámen s funkcí přístupu, výsledný kód v mnoha případech je snazší pochopit.</span><span class="sxs-lookup"><span data-stu-id="3c958-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="3c958-112">Je snadné najít kód, který upraví jednotlivé části stromu.</span><span class="sxs-lookup"><span data-stu-id="3c958-112">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="3c958-113">Přístup, při kterém upravíte strom XML na místě, je více známý pro mnoho programátorů modelu DOM, zatímco kód napsaný pomocí funkčního přístupu může vypadat neznámým vývojářům, kteří tento přístup ještě neznají.</span><span class="sxs-lookup"><span data-stu-id="3c958-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="3c958-114">Pokud je třeba udělat pouze malou úpravu velkého stromu XML, přístup, který upravujete stromovou strukturu v mnoha případech, bude trvat méně času procesoru.</span><span class="sxs-lookup"><span data-stu-id="3c958-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="3c958-115">Toto téma poskytuje příklad, který je implementován pomocí obou přístupů.</span><span class="sxs-lookup"><span data-stu-id="3c958-115">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="3c958-116">Transformace atributů na elementy</span><span class="sxs-lookup"><span data-stu-id="3c958-116">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="3c958-117">V tomto příkladu Předpokládejme, že chcete upravit následující jednoduchý dokument XML, aby se atributy staly elementy.</span><span class="sxs-lookup"><span data-stu-id="3c958-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="3c958-118">V tomto tématu se nejdřív prezentuje tradiční místní modifikace.</span><span class="sxs-lookup"><span data-stu-id="3c958-118">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="3c958-119">Pak zobrazuje přístup k konstrukci funkčnosti.</span><span class="sxs-lookup"><span data-stu-id="3c958-119">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="3c958-120">Úprava stromu XML</span><span class="sxs-lookup"><span data-stu-id="3c958-120">Modifying the XML Tree</span></span>  
 <span data-ttu-id="3c958-121">Můžete napsat nějaký procedurální kód pro vytvoření prvků z atributů a poté odstranit atributy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3c958-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
For Each att As XAttribute In root.Attributes()  
    root.Add(New XElement(att.Name, att.Value))  
Next  
root.Attributes().Remove()  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="3c958-122">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3c958-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="3c958-123">Přístup k konstrukci funkčnosti</span><span class="sxs-lookup"><span data-stu-id="3c958-123">Functional Construction Approach</span></span>  
 <span data-ttu-id="3c958-124">Naproti tomu funkční přístup se skládá z kódu pro vytvoření nové stromové struktury, výběru a výběru prvků a atributů ze zdrojového stromu a jejich transformaci podle potřeby, jak jsou přidány do nového stromu.</span><span class="sxs-lookup"><span data-stu-id="3c958-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="3c958-125">Funkční přístup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="3c958-125">The functional approach looks like the following:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim newTree As XElement = _  
    <Root>  
        <%= root.<Child1> %>  
        <%= From att In root.Attributes() _  
            Select New XElement(att.Name, att.Value) %>  
    </Root>  
Console.WriteLine(newTree)  
```  
  
 <span data-ttu-id="3c958-126">Tento příklad vytvoří výstup stejného XML jako první příklad.</span><span class="sxs-lookup"><span data-stu-id="3c958-126">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="3c958-127">Všimněte si však, že ve skutečnosti vidíte výslednou strukturu nového XML v rámci funkčního přístupu.</span><span class="sxs-lookup"><span data-stu-id="3c958-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="3c958-128">Můžete zobrazit vytvoření prvku `Root`, kód, který přebírá `Child1` prvek ze zdrojového stromu a kód, který transformuje atributy ze zdrojového stromu na prvky v novém stromu.</span><span class="sxs-lookup"><span data-stu-id="3c958-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="3c958-129">Funkční příklad v tomto případě není kratší než první příklad a není skutečně jednodušší.</span><span class="sxs-lookup"><span data-stu-id="3c958-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="3c958-130">Nicméně pokud máte mnoho změn ve stromu XML, nefunkční přístup se stane poměrně složitým a trochu obtuse.</span><span class="sxs-lookup"><span data-stu-id="3c958-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="3c958-131">Naopak pokud používáte funkční přístup, stále stačí vytvořit požadovaný kód XML, vložit dotazy a výrazy podle potřeby a vyžádat si požadovaný obsah.</span><span class="sxs-lookup"><span data-stu-id="3c958-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="3c958-132">Funkční přístup poskytuje kód, který je snazší udržovat.</span><span class="sxs-lookup"><span data-stu-id="3c958-132">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="3c958-133">Všimněte si, že v takovém případě funkční přístup pravděpodobně nepracuje úplně stejně jako přístup ke stromové manipulaci.</span><span class="sxs-lookup"><span data-stu-id="3c958-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="3c958-134">Hlavním problémem je to, že funkční přístup vytváří krátkodobé objekty pro dlouhodobé vyzkoušení.</span><span class="sxs-lookup"><span data-stu-id="3c958-134">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="3c958-135">Kompromis je ale platný, pokud použití funkčního přístupu umožňuje větší produktivitu programátorů.</span><span class="sxs-lookup"><span data-stu-id="3c958-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="3c958-136">Toto je velmi jednoduchý příklad, ale slouží k zobrazení rozdílu v filozofie mezi dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="3c958-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="3c958-137">Funkční přístup poskytuje větší produktivitu při transformaci větších dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="3c958-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c958-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c958-138">See also</span></span>

- [<span data-ttu-id="3c958-139">Úprava stromů XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c958-139">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
