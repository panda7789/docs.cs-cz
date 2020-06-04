---
title: Chyby smíšeného deklarativního a imperativního kódu (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
ms.openlocfilehash: e5526a64805b19ea293d3ef28636738923d03662
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84361070"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a><span data-ttu-id="138ad-102">Smíšený deklarativní kód/chyby nepodmíněných kódů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="138ad-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="138ad-103">obsahuje různé metody, které umožňují přímou úpravu stromu XML.</span><span class="sxs-lookup"><span data-stu-id="138ad-103">contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="138ad-104">Můžete přidat prvky, odstranit prvky, změnit obsah elementu, přidat atributy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="138ad-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="138ad-105">Toto programovací rozhraní je popsáno v tématu [Úprava stromů XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="138ad-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md).</span></span> <span data-ttu-id="138ad-106">Pokud provádíte iteraci na jednu z OS, jako je například <xref:System.Xml.Linq.XContainer.Elements%2A> , a upravujete strom XML při iteraci přes osu, můžete ukončit některé neobvyklé chyby.</span><span class="sxs-lookup"><span data-stu-id="138ad-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="138ad-107">Tento problém se někdy označuje jako "problém Halloweenem".</span><span class="sxs-lookup"><span data-stu-id="138ad-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="138ad-108">Definice problému</span><span class="sxs-lookup"><span data-stu-id="138ad-108">Definition of the Problem</span></span>  
 <span data-ttu-id="138ad-109">Při psaní kódu pomocí LINQ, který projde kolekcí, píšete kód v deklarativním stylu.</span><span class="sxs-lookup"><span data-stu-id="138ad-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="138ad-110">K popisu *toho, co* chcete udělat, je další podobají, a to tak, *jak* chcete.</span><span class="sxs-lookup"><span data-stu-id="138ad-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="138ad-111">Pokud napíšete kód, který 1) získá první prvek, 2) ho testuje v nějaké podmínce, 3) ho upraví a 4) ho vrátí zpátky do seznamu, pak by to byl imperativní kód.</span><span class="sxs-lookup"><span data-stu-id="138ad-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="138ad-112">Informujete o tom, *jak* se má počítač provést.</span><span class="sxs-lookup"><span data-stu-id="138ad-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="138ad-113">Kombinování těchto stylů kódu ve stejné operaci je to, co vede k problémům.</span><span class="sxs-lookup"><span data-stu-id="138ad-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="138ad-114">Zvažte použití těchto zdrojů:</span><span class="sxs-lookup"><span data-stu-id="138ad-114">Consider the following:</span></span>  
  
 <span data-ttu-id="138ad-115">Předpokládejme, že máte propojený seznam se třemi položkami (a, b a c):</span><span class="sxs-lookup"><span data-stu-id="138ad-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="138ad-116">Nyní předpokládejme, že chcete přejít přes propojený seznam a přidat tři nové položky (a, b a c).</span><span class="sxs-lookup"><span data-stu-id="138ad-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="138ad-117">Chcete, aby výsledný propojený seznam vypadal takto:</span><span class="sxs-lookup"><span data-stu-id="138ad-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="138ad-118">Takže napíšete kód, který projde seznamem, a pro každou položku přidá novou položku hned po ní.</span><span class="sxs-lookup"><span data-stu-id="138ad-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="138ad-119">Co se stane, váš kód nejprve uvidí `a` prvek a vloží `a'` za něj.</span><span class="sxs-lookup"><span data-stu-id="138ad-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="138ad-120">Nyní se váš kód přesune na další uzel v seznamu, který je nyní `a'` !</span><span class="sxs-lookup"><span data-stu-id="138ad-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="138ad-121">Happily IT přidá novou položku do seznamu, `a''` .</span><span class="sxs-lookup"><span data-stu-id="138ad-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="138ad-122">Jak to byste měli v reálném světě vyřešit?</span><span class="sxs-lookup"><span data-stu-id="138ad-122">How would you solve this in the real world?</span></span> <span data-ttu-id="138ad-123">Také můžete vytvořit kopii původního propojeného seznamu a vytvořit úplně nový seznam.</span><span class="sxs-lookup"><span data-stu-id="138ad-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="138ad-124">Nebo pokud píšete čistě imperativní kód, můžete najít první položku, přidat novou položku a pak dvakrát v propojeném seznamu a přejít tak na prvek, který jste právě přidali.</span><span class="sxs-lookup"><span data-stu-id="138ad-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="138ad-125">Přidávání během iterací</span><span class="sxs-lookup"><span data-stu-id="138ad-125">Adding While Iterating</span></span>  
 <span data-ttu-id="138ad-126">Předpokládejme například, že chcete napsat kód, který je pro každý prvek ve stromové struktuře, chcete vytvořit duplicitní prvek:</span><span class="sxs-lookup"><span data-stu-id="138ad-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
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
  
 <span data-ttu-id="138ad-127">Tento kód přejde do nekonečné smyčky.</span><span class="sxs-lookup"><span data-stu-id="138ad-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="138ad-128">`foreach`Příkaz prochází `Elements()` osu a přidává nové prvky do `doc` prvku.</span><span class="sxs-lookup"><span data-stu-id="138ad-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="138ad-129">Ukončí iteraci také prostřednictvím prvků, které jste právě přidali.</span><span class="sxs-lookup"><span data-stu-id="138ad-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="138ad-130">A protože přiděluje nové objekty s každou iterací smyčky, bude nakonec využívat veškerou dostupnou paměť.</span><span class="sxs-lookup"><span data-stu-id="138ad-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="138ad-131">Tento problém můžete vyřešit tak, že narazíte kolekci do paměti pomocí <xref:System.Linq.Enumerable.ToList%2A> standardního operátoru dotazu, a to takto:</span><span class="sxs-lookup"><span data-stu-id="138ad-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
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
  
 <span data-ttu-id="138ad-132">Nyní kód funguje.</span><span class="sxs-lookup"><span data-stu-id="138ad-132">Now the code works.</span></span> <span data-ttu-id="138ad-133">Výsledný strom XML je následující:</span><span class="sxs-lookup"><span data-stu-id="138ad-133">The resulting XML tree is the following:</span></span>  
  
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
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="138ad-134">Odstraňování během iterace</span><span class="sxs-lookup"><span data-stu-id="138ad-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="138ad-135">Pokud chcete odstranit všechny uzly na určité úrovni, můžete se rozhodnout, že napíšete kód podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="138ad-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
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
  
 <span data-ttu-id="138ad-136">To ale neudělá to, co chcete.</span><span class="sxs-lookup"><span data-stu-id="138ad-136">However, this does not do what you want.</span></span> <span data-ttu-id="138ad-137">V takové situaci, po odebrání prvního prvku, je odebrán ze stromu XML obsaženého v kořenovém adresáři a kódem v metodě element, který provádí iteraci, nelze najít další prvek.</span><span class="sxs-lookup"><span data-stu-id="138ad-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="138ad-138">Předchozí kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="138ad-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="138ad-139">Řešením je znovu zavolat <xref:System.Linq.Enumerable.ToList%2A> do vyhodnotit kolekce následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="138ad-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
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
  
 <span data-ttu-id="138ad-140">Výsledkem je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="138ad-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="138ad-141">Alternativně můžete iteraci eliminovat zcela voláním <xref:System.Xml.Linq.XElement.RemoveAll%2A> na nadřazený element:</span><span class="sxs-lookup"><span data-stu-id="138ad-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
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
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="138ad-142">Proč nedokážete tuto technologii LINQ automaticky zpracovat?</span><span class="sxs-lookup"><span data-stu-id="138ad-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="138ad-143">Jedním z přístupů je vždycky přenášet vše do paměti namísto opožděného vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="138ad-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="138ad-144">Je ale velmi nákladný z pohledu výkonu a využití paměti.</span><span class="sxs-lookup"><span data-stu-id="138ad-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="138ad-145">Pokud by se jednalo o tento přístup v praxi LINQ and (LINQ to XML), nedošlo by k chybě v reálných situacích.</span><span class="sxs-lookup"><span data-stu-id="138ad-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="138ad-146">Dalším možným přístupem by bylo, že se do LINQ vloží syntaxe transakce a pokusí se kompilátor analyzovat kód a určí, jestli je potřeba vyhodnocená konkrétní kolekce.</span><span class="sxs-lookup"><span data-stu-id="138ad-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="138ad-147">Nicméně pokus o určení veškerého kódu, který má vedlejší účinky, je neuvěřitelně složitý.</span><span class="sxs-lookup"><span data-stu-id="138ad-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="138ad-148">Uvažujte následující kód:</span><span class="sxs-lookup"><span data-stu-id="138ad-148">Consider the following code:</span></span>  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 <span data-ttu-id="138ad-149">Takový kód analýzy by musel analyzovat metody TestSomeCondition a DoMyProjection a všechny metody, které tyto metody volaly, k určení, zda nějaký kód měl vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="138ad-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="138ad-150">Ale kód analýzy nemůže vyhledat žádný kód, který má vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="138ad-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="138ad-151">Je nutné vybrat pouze kód, který měl vedlejší účinky na podřízené prvky `root` v této situaci.</span><span class="sxs-lookup"><span data-stu-id="138ad-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="138ad-152">LINQ to XML se neprovede žádná taková analýza.</span><span class="sxs-lookup"><span data-stu-id="138ad-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="138ad-153">Abyste se těmto problémům vyhnuli, je to na vás.</span><span class="sxs-lookup"><span data-stu-id="138ad-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="138ad-154">Pokyny</span><span class="sxs-lookup"><span data-stu-id="138ad-154">Guidance</span></span>  
 <span data-ttu-id="138ad-155">Nejdříve Nekombinujte deklarativní a imperativní kód.</span><span class="sxs-lookup"><span data-stu-id="138ad-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="138ad-156">I v případě, že znáte přesně sémantiku vašich kolekcí a sémantiku metod, které mění strom XML, pokud napíšete kód chytřejší, který brání těmto kategoriím problémů, váš kód bude muset být v budoucnu udržován jinými vývojáři a nemusí být jasný, pokud jde o problémy.</span><span class="sxs-lookup"><span data-stu-id="138ad-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="138ad-157">Pokud kombinujete deklarativní a imperativní styly kódování, váš kód bude více poměrně křehký.</span><span class="sxs-lookup"><span data-stu-id="138ad-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="138ad-158">Pokud píšete kód, který materializuje kolekci tak, aby se tyto problémy předešly, poznamenejte si je podle potřeby v kódu, aby Programátori údržby porozuměli problému.</span><span class="sxs-lookup"><span data-stu-id="138ad-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="138ad-159">Za druhé, pokud povolíte výkon a další okolnosti, používejte pouze deklarativní kód.</span><span class="sxs-lookup"><span data-stu-id="138ad-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="138ad-160">Neměňte existující strom XML.</span><span class="sxs-lookup"><span data-stu-id="138ad-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="138ad-161">Vygenerujte nový.</span><span class="sxs-lookup"><span data-stu-id="138ad-161">Generate a new one.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="138ad-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="138ad-162">See also</span></span>

- [<span data-ttu-id="138ad-163">Rozšířené programování LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="138ad-163">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
