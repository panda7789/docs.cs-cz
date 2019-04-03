---
title: Smíšeného deklarativního a imperativního kódu chyby (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
ms.openlocfilehash: e7b3b624bb91525d2cda9477c29291e25eba1b07
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842275"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a><span data-ttu-id="61312-102">Smíšený kód deklarativní nebo imperativní kód chyby (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61312-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="61312-103">obsahuje různé metody, které umožňují upravit stromu XML přímo.</span><span class="sxs-lookup"><span data-stu-id="61312-103">contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="61312-104">Můžete přidat prvky, odstranění prvků, změňte obsah elementu, přidejte atributy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="61312-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="61312-105">Toto programovací rozhraní je popsán v [změna stromů XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="61312-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span> <span data-ttu-id="61312-106">Pokud jste se provede iterace přes jeden z OS, jako <xref:System.Xml.Linq.XContainer.Elements%2A>a jak iterovat na ose upravujete stromu XML, můžete skončit s některé chyby neobvyklé.</span><span class="sxs-lookup"><span data-stu-id="61312-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="61312-107">Tento problém se někdy označuje jako "The Halloweenem problém".</span><span class="sxs-lookup"><span data-stu-id="61312-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="61312-108">Definice problému</span><span class="sxs-lookup"><span data-stu-id="61312-108">Definition of the Problem</span></span>  
 <span data-ttu-id="61312-109">Při psaní kódu s využitím LINQ, který Iteruje přes kolekci jsou deklarativní stylem psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="61312-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="61312-110">Se více podobají popisující *co* chcete, místo toho, který *jak* chcete pracovat efektivněji.</span><span class="sxs-lookup"><span data-stu-id="61312-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="61312-111">Pokud píšete kód, který 1) získá první prvek, 2) testy se některé podmínky, 3) upraví jeho a 4) vloží jej zpět do seznamu, pak by to imperativního kódu.</span><span class="sxs-lookup"><span data-stu-id="61312-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="61312-112">Oznamujete tím počítače *jak* udělat, co chcete Hotovo.</span><span class="sxs-lookup"><span data-stu-id="61312-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="61312-113">Kombinování tyto styly kódu v rámci jedné operace je co vede k problémům.</span><span class="sxs-lookup"><span data-stu-id="61312-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="61312-114">Zvažte použití těchto zdrojů:</span><span class="sxs-lookup"><span data-stu-id="61312-114">Consider the following:</span></span>  
  
 <span data-ttu-id="61312-115">Předpokládejme, že v něm máte odkazovaného seznamu se tři položky (a, b a c):</span><span class="sxs-lookup"><span data-stu-id="61312-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="61312-116">Nyní předpokládejme, že chcete přesunout prostřednictvím propojeného seznamu přidáte tři nové položky (", b" a jazyka c ").</span><span class="sxs-lookup"><span data-stu-id="61312-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="61312-117">Chcete, aby výsledný odkazovaného seznamu vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="61312-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="61312-118">Proto můžete napsat kód, který Iteruje přes seznam a pro každou položku, přidá nové právo položku za ním.</span><span class="sxs-lookup"><span data-stu-id="61312-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="61312-119">Co se stane, je, že váš kód se nejprve zobrazí `a` elementu a vložit `a'` po něm.</span><span class="sxs-lookup"><span data-stu-id="61312-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="61312-120">Nyní, váš kód se přesune na další uzel v seznamu, který je teď `a'`!</span><span class="sxs-lookup"><span data-stu-id="61312-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="61312-121">Využívá elastic přidá novou položku do seznamu, `a''`.</span><span class="sxs-lookup"><span data-stu-id="61312-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="61312-122">Jak by vás tento problém vyřešit v reálném světě?</span><span class="sxs-lookup"><span data-stu-id="61312-122">How would you solve this in the real world?</span></span> <span data-ttu-id="61312-123">Dobře můžete vytvořit kopii původní propojeného seznamu a vytvořit zcela nový seznam.</span><span class="sxs-lookup"><span data-stu-id="61312-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="61312-124">Nebo pokud vytváříte čistě imperativního kódu, můžete se setkat na první položku Přidat novou položku a pak přejděte dvakrát v propojeném seznamu posunutí je nad prvkem, který jste právě přidali.</span><span class="sxs-lookup"><span data-stu-id="61312-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="61312-125">Přidání během iterace</span><span class="sxs-lookup"><span data-stu-id="61312-125">Adding While Iterating</span></span>  
 <span data-ttu-id="61312-126">Předpokládejme například, že chcete napsat kód pro každý element ve stromové struktuře chcete vytvořit duplicitní element:</span><span class="sxs-lookup"><span data-stu-id="61312-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements()  
    root.Add(New XElement(e.Name, e.Value))  
Next  
```  
  
 <span data-ttu-id="61312-127">Tento kód přejde do nekonečné smyčky.</span><span class="sxs-lookup"><span data-stu-id="61312-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="61312-128">`foreach` Příkaz prochází `Elements()` osy, přidávání nových elementů do `doc` elementu.</span><span class="sxs-lookup"><span data-stu-id="61312-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="61312-129">To končí také iterace prvků, které právě přidali.</span><span class="sxs-lookup"><span data-stu-id="61312-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="61312-130">A vzhledem k tomu, že ji přidělí nové objekty při každé iteraci smyčky, budou nakonec spotřebovávat veškerou dostupnou paměť.</span><span class="sxs-lookup"><span data-stu-id="61312-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="61312-131">Tento problém můžete vyřešit přidáním kolekci do paměti pomocí <xref:System.Linq.Enumerable.ToList%2A> standardní operátor dotazu, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="61312-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements().ToList()  
    root.Add(New XElement(e.Name, e.Value))  
Next  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="61312-132">Nyní kód funguje.</span><span class="sxs-lookup"><span data-stu-id="61312-132">Now the code works.</span></span> <span data-ttu-id="61312-133">Výsledný strom XML je následující:</span><span class="sxs-lookup"><span data-stu-id="61312-133">The resulting XML tree is the following:</span></span>  
  
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
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="61312-134">Odstraňuje se během iterace</span><span class="sxs-lookup"><span data-stu-id="61312-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="61312-135">Pokud chcete odstranit všechny uzly na určité úrovni, můžete mít tendenci psát kód podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="61312-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements()  
    e.Remove()  
Next  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="61312-136">Ale to není nutné co chcete.</span><span class="sxs-lookup"><span data-stu-id="61312-136">However, this does not do what you want.</span></span> <span data-ttu-id="61312-137">V takovém případě po odebrání prvního prvku, A odebere se ze stromu XML obsažených v kořenovém adresáři a kód v metodě prvků, který provádí iteraci nelze najít další prvek.</span><span class="sxs-lookup"><span data-stu-id="61312-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="61312-138">Předcházející kód vygeneruje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61312-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="61312-139">Toto řešení je opět volání <xref:System.Linq.Enumerable.ToList%2A> sloučit kolekci, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="61312-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements().ToList()  
    e.Remove()  
Next  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="61312-140">To vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61312-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="61312-141">Alternativně můžete eliminovat iterace úplně voláním <xref:System.Xml.Linq.XElement.RemoveAll%2A> na nadřazený element:</span><span class="sxs-lookup"><span data-stu-id="61312-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
root.RemoveAll()  
Console.WriteLine(root)  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="61312-142">Proč nelze LINQ umožňují automaticky zpracovat to?</span><span class="sxs-lookup"><span data-stu-id="61312-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="61312-143">Jedním z přístupů je vždy přenést vše do paměti namísto provádění opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="61312-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="61312-144">Nicméně by bylo velmi náročné z hlediska výkonu a paměti.</span><span class="sxs-lookup"><span data-stu-id="61312-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="61312-145">Ve skutečnosti LINQ a (LINQ to XML) byly pro tento postup, je selže v reálných situacích.</span><span class="sxs-lookup"><span data-stu-id="61312-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="61312-146">Další z možných způsobů je vložit nějaký druh transakce syntaxe na LINQ a mít kompilátoru pokus o analýzu kódu a určit, pokud materializace potřeba žádné konkrétní kolekce.</span><span class="sxs-lookup"><span data-stu-id="61312-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="61312-147">Pokus o určení veškerý kód, který má vedlejší účinky je ale mimořádně složité.</span><span class="sxs-lookup"><span data-stu-id="61312-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="61312-148">Vezměte v úvahu následující kód:</span><span class="sxs-lookup"><span data-stu-id="61312-148">Consider the following code:</span></span>  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 <span data-ttu-id="61312-149">Tyto analýzy kódu by bylo potřeba analyzovat metody TestSomeCondition a DoMyProjection a všechny metody, které tyto metody volat k určení, pokud žádný kód má vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="61312-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="61312-150">Ale analýzy kódu nelze právě hledat jakýkoli kód, který má vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="61312-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="61312-151">Je potřeba zvolit pro přesně takový kód, který má vedlejší účinky na podřízených elementů `root` v této situaci.</span><span class="sxs-lookup"><span data-stu-id="61312-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="61312-152">Technologie LINQ to XML nebude pokoušet provést tyto analýzy.</span><span class="sxs-lookup"><span data-stu-id="61312-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="61312-153">Je vás, abyste se těmto problémům vyhnuli.</span><span class="sxs-lookup"><span data-stu-id="61312-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="61312-154">Doprovodné materiály</span><span class="sxs-lookup"><span data-stu-id="61312-154">Guidance</span></span>  
 <span data-ttu-id="61312-155">Nekombinujte nejprve deklarativního a imperativního kódu.</span><span class="sxs-lookup"><span data-stu-id="61312-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="61312-156">I v případě, že víte přesně sémantiku kolekce a sémantika metody, které určuje stromu XML, pokud napsání chytřejší kódu, které se vyhýbají tyto druhy problémů, váš kód bude nutné udržovat jinými vývojáři v budoucnu , a nemusí být jako prostý na problémy.</span><span class="sxs-lookup"><span data-stu-id="61312-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="61312-157">Pokud kombinujete deklarativního a imperativního programování styly, bude váš kód více křehký.</span><span class="sxs-lookup"><span data-stu-id="61312-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="61312-158">Pokud píšete kód, který bude realizována kolekce tak, aby se vyhnout těmto problémům, poznamenejte si ji s komentáři, případně ve vašem kódu tak, aby programátoři údržba bude porozumět danému problému.</span><span class="sxs-lookup"><span data-stu-id="61312-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="61312-159">Za druhé Pokud výkon a další důležité informace povolit, použijte pouze deklarativního kódu.</span><span class="sxs-lookup"><span data-stu-id="61312-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="61312-160">Neupravujte vaše stávající stromu XML.</span><span class="sxs-lookup"><span data-stu-id="61312-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="61312-161">Vygenerujte nový token.</span><span class="sxs-lookup"><span data-stu-id="61312-161">Generate a new one.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
Dim newRoot As XElement = New XElement("Root", _  
    root.Elements(), root.Elements())  
Console.WriteLine(newRoot)  
```  
  
## <a name="see-also"></a><span data-ttu-id="61312-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61312-162">See also</span></span>

- [<span data-ttu-id="61312-163">Pokročilé technologie LINQ to XML programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61312-163">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
