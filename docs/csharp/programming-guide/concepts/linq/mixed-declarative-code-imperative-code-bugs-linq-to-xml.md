---
title: Smíšené deklarativní chyby kódu imperativní kód (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 76a9bb5abf6ce2700a2a0698ebc109f65e2b7eb1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168346"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a><span data-ttu-id="6c8a9-102">Smíšené deklarativní chyby kódu/imperativního kódu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6c8a9-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="6c8a9-103">obsahuje různé metody, které umožňují přímo upravit strom XML.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-103">contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="6c8a9-104">Můžete přidávat prvky, odstraňovat prvky, měnit obsah prvku, přidávat atributy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="6c8a9-105">Toto programovací rozhraní je popsáno [v úpravě stromů XML (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6c8a9-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span> <span data-ttu-id="6c8a9-106">Pokud iterace prostřednictvím jedné z os, jako je například <xref:System.Xml.Linq.XContainer.Elements%2A>, a upravujete strom XML při iterace přes osu, můžete skončit s některé podivné chyby.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="6c8a9-107">Tento problém je někdy známý jako "Halloween problém".</span><span class="sxs-lookup"><span data-stu-id="6c8a9-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="6c8a9-108">Definice problému</span><span class="sxs-lookup"><span data-stu-id="6c8a9-108">Definition of the Problem</span></span>  
 <span data-ttu-id="6c8a9-109">Při psaní některého kódu pomocí LINQ, který iteruje prostřednictvím kolekce, píšete kód v deklarativním stylu.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="6c8a9-110">Je to více podobně jako popis toho, *co* chcete, spíše to, *jak* chcete, aby si to udělat.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="6c8a9-111">Pokud napíšete kód, který 1) získá první prvek, 2) testuje pro některé podmínky, 3) upraví jej a 4) vloží zpět do seznamu, pak by to bylo nutné kód.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="6c8a9-112">Říkáte počítači, *jak* dělat to, co chcete udělat.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="6c8a9-113">Míchání těchto stylů kódu ve stejné operaci je to, co vede k problémům.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="6c8a9-114">Zvažte použití těchto zdrojů:</span><span class="sxs-lookup"><span data-stu-id="6c8a9-114">Consider the following:</span></span>  
  
 <span data-ttu-id="6c8a9-115">Předpokládejme, že máte propojený seznam se třemi položkami (a, b a c):</span><span class="sxs-lookup"><span data-stu-id="6c8a9-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="6c8a9-116">Nyní předpokládejme, že chcete procházet propojený seznam a přidat tři nové položky (a', b' a c').</span><span class="sxs-lookup"><span data-stu-id="6c8a9-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="6c8a9-117">Chcete, aby výsledný propojený seznam vypadal takto:</span><span class="sxs-lookup"><span data-stu-id="6c8a9-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="6c8a9-118">Takže napíšete kód, který itetuje prostřednictvím seznamu a pro každou položku přidá novou položku hned za ním.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="6c8a9-119">Co se stane, je, `a` že váš `a'` kód nejprve zobrazí prvek a vložit za něj.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="6c8a9-120">Nyní se váš kód přesune do dalšího uzlu v `a'`seznamu, což je nyní!</span><span class="sxs-lookup"><span data-stu-id="6c8a9-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="6c8a9-121">To šťastně přidá novou položku `a''`do seznamu, .</span><span class="sxs-lookup"><span data-stu-id="6c8a9-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="6c8a9-122">Jak byste to vyřešili ve skutečném světě?</span><span class="sxs-lookup"><span data-stu-id="6c8a9-122">How would you solve this in the real world?</span></span> <span data-ttu-id="6c8a9-123">No, můžete vytvořit kopii původního propojeného seznamu, a vytvořit zcela nový seznam.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="6c8a9-124">Nebo pokud píšete čistě imperativní kód, můžete najít první položku, přidat novou položku a potom dvakrát postoupit v propojeném seznamu a posunit se přes prvek, který jste právě přidali.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="6c8a9-125">Přidání při iterace</span><span class="sxs-lookup"><span data-stu-id="6c8a9-125">Adding While Iterating</span></span>  
 <span data-ttu-id="6c8a9-126">Předpokládejme například, že chcete napsat nějaký kód, který pro každý prvek ve stromu chcete vytvořit duplicitní prvek:</span><span class="sxs-lookup"><span data-stu-id="6c8a9-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 <span data-ttu-id="6c8a9-127">Tento kód přejde do nekonečné smyčky.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="6c8a9-128">Příkaz `foreach` iterates přes `Elements()` osu, přidání `doc` nových prvků do prvku.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="6c8a9-129">To skončí iterace i prostřednictvím prvků, které právě přidal.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="6c8a9-130">A protože přiděluje nové objekty s každou iteraci smyčky, nakonec spotřebuje všechny dostupné paměti.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="6c8a9-131">Tento problém můžete vyřešit vytažením <xref:System.Linq.Enumerable.ToList%2A> kolekce do paměti pomocí standardního operátoru dotazu, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6c8a9-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    root.Add(new XElement(e.Name, (string)e));  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="6c8a9-132">Nyní kód funguje.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-132">Now the code works.</span></span> <span data-ttu-id="6c8a9-133">Výsledný strom XML je následující:</span><span class="sxs-lookup"><span data-stu-id="6c8a9-133">The resulting XML tree is the following:</span></span>  
  
```xml  
<Root>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="6c8a9-134">Odstranění při iterace</span><span class="sxs-lookup"><span data-stu-id="6c8a9-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="6c8a9-135">Pokud chcete odstranit všechny uzly na určité úrovni, můžete být v pokušení napsat kód, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="6c8a9-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="6c8a9-136">To však nedělá to, co chcete.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-136">However, this does not do what you want.</span></span> <span data-ttu-id="6c8a9-137">V takovém případě po odebrání první prvek, A, je odebrán ze stromu XML obsažené v kořenovém adresáři a kód v Elements metoda, která dělá iterace nelze najít další prvek.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="6c8a9-138">Předchozí kód vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6c8a9-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="6c8a9-139">Řešením je opět <xref:System.Linq.Enumerable.ToList%2A> volat k zhmotnění kolekce, a to následovně:</span><span class="sxs-lookup"><span data-stu-id="6c8a9-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="6c8a9-140">Výsledkem je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6c8a9-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="6c8a9-141">Alternativně můžete eliminovat iterace úplně <xref:System.Xml.Linq.XElement.RemoveAll%2A> voláním na nadřazený prvek:</span><span class="sxs-lookup"><span data-stu-id="6c8a9-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="6c8a9-142">Proč to linq nemůže automaticky zpracovat?</span><span class="sxs-lookup"><span data-stu-id="6c8a9-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="6c8a9-143">Jedním z přístupů by bylo vždy přinést vše do paměti namísto toho, aby opožděné hodnocení.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="6c8a9-144">Nicméně, to by bylo velmi drahé, pokud jde o výkon a využití paměti.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="6c8a9-145">Ve skutečnosti, pokud LINQ a (LINQ na XML) byly tento přístup, by se nezdaří v reálných situacích.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="6c8a9-146">Dalším možným přístupem by bylo vložit nějakou syntaxi transakce do LINQ a mít kompilátor pokus o analýzu kódu a zjistit, zda je třeba zhmotnit nějakou konkrétní kolekci.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="6c8a9-147">Však pokus o určení všech kód, který má vedlejší účinky je neuvěřitelně složité.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="6c8a9-148">Uvažujte následující kód:</span><span class="sxs-lookup"><span data-stu-id="6c8a9-148">Consider the following code:</span></span>  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 <span data-ttu-id="6c8a9-149">Takový kód analýzy by bylo třeba analyzovat metody TestSomeCondition a DoMyProjection a všechny metody, které tyto metody volal, k určení, pokud nějaký kód měl vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="6c8a9-150">Ale kód analýzy nemohl jen hledat žádný kód, který měl vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="6c8a9-151">Bude muset vybrat pouze pro kód, který měl vedlejší `root` účinky na podřízené prvky v této situaci.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="6c8a9-152">LINQ na XML se nepokouší provést žádnou takovou analýzu.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="6c8a9-153">Je na vás, abyste se těmto problémům vyhnuli.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="6c8a9-154">Doprovodné materiály</span><span class="sxs-lookup"><span data-stu-id="6c8a9-154">Guidance</span></span>  
 <span data-ttu-id="6c8a9-155">Za prvé, nemíchejte deklarativní a imperativní kód.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="6c8a9-156">I v případě, že přesně znáte sémantiku vašich sbírek a sémantiku metod, které upravují strom XML, pokud napíšete nějaký chytrý kód, který se těmto kategoriím problémů vyhne, bude váš kód muset v budoucnu udržovat jiní vývojáři a nemusí být v otázkách tak jasné.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="6c8a9-157">Pokud smícháte deklarativní a imperativní styly kódování, váš kód bude křehčí.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="6c8a9-158">Pokud napíšete kód, který zhmotní kolekci tak, aby se tyto problémy vyhnout, poznamenejte si s komentáři podle potřeby ve vašem kódu, takže programátoři údržby bude rozumět problému.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="6c8a9-159">Za druhé, pokud výkon a další aspekty umožňují, použijte pouze deklarativní kód.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="6c8a9-160">Neupravujte existující strom XML.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="6c8a9-161">Vygenerujte nový.</span><span class="sxs-lookup"><span data-stu-id="6c8a9-161">Generate a new one.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
XElement newRoot = new XElement("Root",  
    root.Elements(),  
    root.Elements()  
);  
Console.WriteLine(newRoot);  
```  
