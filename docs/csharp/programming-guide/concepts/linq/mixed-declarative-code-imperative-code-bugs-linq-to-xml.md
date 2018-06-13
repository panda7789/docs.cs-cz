---
title: Smíšený kód deklarativní imperativní kód chyby (technologie LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: efc58aac69c53cda724e5fe348560a99311e8d4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337688"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a><span data-ttu-id="f6721-102">Smíšený kód deklarativní nebo imperativní kód chyby (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f6721-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f6721-103"> obsahuje různé metody, které vám umožní změnit strom XML přímo.</span><span class="sxs-lookup"><span data-stu-id="f6721-103"> contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="f6721-104">Můžete přidat elementy, odstraňte prvky, změňte obsah elementu, přidání atributů a podobně.</span><span class="sxs-lookup"><span data-stu-id="f6721-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="f6721-105">Toto programovací rozhraní je popsaná v [úpravy stromů XML (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f6721-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span> <span data-ttu-id="f6721-106">Pokud jste se iterace v rámci některá z OS, například <xref:System.Xml.Linq.XContainer.Elements%2A>a budete upravovat stromu XML jako iterace ose, můžou skončit s některé neznámé chyby.</span><span class="sxs-lookup"><span data-stu-id="f6721-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="f6721-107">Tento problém se někdy označuje jako "Potíží s Masopust".</span><span class="sxs-lookup"><span data-stu-id="f6721-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="f6721-108">Definice problému</span><span class="sxs-lookup"><span data-stu-id="f6721-108">Definition of the Problem</span></span>  
 <span data-ttu-id="f6721-109">Při psaní kódu s využitím LINQ, který iteruje v rámci kolekce jsou psaní kódu v deklarativní stylu.</span><span class="sxs-lookup"><span data-stu-id="f6721-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="f6721-110">Se více podobají popisující *co* chcete, místo, *jak* chcete ho provést.</span><span class="sxs-lookup"><span data-stu-id="f6721-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="f6721-111">Pokud napíšete kód, který 1) získá první prvek, 2) testy pro některé podmínky, 3) upraví ho a 4) vloží ho zpět do seznamu, pak bude nutné kódu.</span><span class="sxs-lookup"><span data-stu-id="f6721-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="f6721-112">Oznamujete počítač *jak* udělat, co chcete Hotovo.</span><span class="sxs-lookup"><span data-stu-id="f6721-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="f6721-113">Kombinování tyto styly kódu v rámci jedné operace je co vede k problémům.</span><span class="sxs-lookup"><span data-stu-id="f6721-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="f6721-114">Zvažte následující:</span><span class="sxs-lookup"><span data-stu-id="f6721-114">Consider the following:</span></span>  
  
 <span data-ttu-id="f6721-115">Předpokládejme, že máte odkazovaného seznamu s tři položky v něm (a, b a c):</span><span class="sxs-lookup"><span data-stu-id="f6721-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="f6721-116">Nyní předpokládejme, že chcete přesunout prostřednictvím odkazovaného seznamu přidání tři nové položky (", b" a c').</span><span class="sxs-lookup"><span data-stu-id="f6721-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="f6721-117">Je vhodné výsledné odkazovaného seznamu vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="f6721-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="f6721-118">Tak psát kód, který iteruje prostřednictvím seznamu a pro každou položku přidá novou položku vpravo za ním.</span><span class="sxs-lookup"><span data-stu-id="f6721-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="f6721-119">Co se stane, je, že se nejprve zobrazí kódu `a` prvku a vložení `a'` za ním.</span><span class="sxs-lookup"><span data-stu-id="f6721-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="f6721-120">Nyní se váš kód přesune na další uzel v seznamu, který je nyní `a'`!</span><span class="sxs-lookup"><span data-stu-id="f6721-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="f6721-121">Brouka přidá novou položku do seznamu, `a''`.</span><span class="sxs-lookup"><span data-stu-id="f6721-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="f6721-122">Jak by vám vyřešit to v praxi?</span><span class="sxs-lookup"><span data-stu-id="f6721-122">How would you solve this in the real world?</span></span> <span data-ttu-id="f6721-123">Dobře můžete vytvořit kopii původního odkazovaného seznamu a vytvořit zcela nový seznam.</span><span class="sxs-lookup"><span data-stu-id="f6721-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="f6721-124">Nebo pokud vytváříte čistě imperativní kód, můžete zjistit, první položka přidat novou položku a pak dvakrát v seznamu propojené přechodu přes elementu, který jste právě přidali zálohy.</span><span class="sxs-lookup"><span data-stu-id="f6721-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="f6721-125">Přidání při iterace</span><span class="sxs-lookup"><span data-stu-id="f6721-125">Adding While Iterating</span></span>  
 <span data-ttu-id="f6721-126">Předpokládejme například, že chcete napsat kód, že pro každý element ve stromu, kterou chcete vytvořit duplicitní element:</span><span class="sxs-lookup"><span data-stu-id="f6721-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 <span data-ttu-id="f6721-127">Tento kód přejde do nekonečné smyčce.</span><span class="sxs-lookup"><span data-stu-id="f6721-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="f6721-128">`foreach` Příkaz iteruje `Elements()` osy, přidávání nových elementů do `doc` elementu.</span><span class="sxs-lookup"><span data-stu-id="f6721-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="f6721-129">Ho ukončí si také iterace v rámci prvky, které právě přidali.</span><span class="sxs-lookup"><span data-stu-id="f6721-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="f6721-130">A protože přiděluje nový objekty s každou iteraci smyčky, bude nakonec využívat všechny dostupné paměti.</span><span class="sxs-lookup"><span data-stu-id="f6721-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="f6721-131">Tento problém můžete vyřešit přidáváním kolekci do paměti pomocí <xref:System.Linq.Enumerable.ToList%2A> operátor standardní dotazu, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f6721-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
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
  
 <span data-ttu-id="f6721-132">Nyní kód funguje.</span><span class="sxs-lookup"><span data-stu-id="f6721-132">Now the code works.</span></span> <span data-ttu-id="f6721-133">Výsledný strom XML je následující:</span><span class="sxs-lookup"><span data-stu-id="f6721-133">The resulting XML tree is the following:</span></span>  
  
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
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="f6721-134">Odstraňování při iterace</span><span class="sxs-lookup"><span data-stu-id="f6721-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="f6721-135">Pokud chcete odstranit všechny uzly na určité úrovni, může být tendenci napsat kód, podobně jako tento:</span><span class="sxs-lookup"><span data-stu-id="f6721-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
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
  
 <span data-ttu-id="f6721-136">Ale to neprovádí co chcete použít.</span><span class="sxs-lookup"><span data-stu-id="f6721-136">However, this does not do what you want.</span></span> <span data-ttu-id="f6721-137">V takovém případě po odebrání první prvek A, odebere se ze stromu XML obsažených v kořenové a kód v metodě elementy, který provádí iterace nelze najít na další prvek.</span><span class="sxs-lookup"><span data-stu-id="f6721-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="f6721-138">Předchozí kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f6721-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="f6721-139">Řešení, znovu je volání <xref:System.Linq.Enumerable.ToList%2A> do kolekce, vyhodnotit takto:</span><span class="sxs-lookup"><span data-stu-id="f6721-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
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
  
 <span data-ttu-id="f6721-140">To vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f6721-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="f6721-141">Alternativně můžete eliminovat iterace zcela voláním <xref:System.Xml.Linq.XElement.RemoveAll%2A> na nadřazený element:</span><span class="sxs-lookup"><span data-stu-id="f6721-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="f6721-142">Proč nelze LINQ zpracovávat automaticky to?</span><span class="sxs-lookup"><span data-stu-id="f6721-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="f6721-143">Jeden z přístupů by vždy všechno zařazení do paměti namísto provádění opožděné vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="f6721-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="f6721-144">Ale je velmi náročná z hlediska výkonu a paměti použití.</span><span class="sxs-lookup"><span data-stu-id="f6721-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="f6721-145">Ve skutečnosti Pokud LINQ a (technologie LINQ to XML) byly pro tento postup, je by selhání v reálných situacích.</span><span class="sxs-lookup"><span data-stu-id="f6721-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="f6721-146">Další možné přístup by mohla být chápat nějaká syntaxe transakce do LINQ a kompilátoru pokusil analyzovat kód a určit, pokud vyžaduje potřeba žádné konkrétní kolekce.</span><span class="sxs-lookup"><span data-stu-id="f6721-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="f6721-147">Při pokusu o určení všechen kód, který má vedlejší účinky je však velmi složitý.</span><span class="sxs-lookup"><span data-stu-id="f6721-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="f6721-148">Vezměte v úvahu následující kód:</span><span class="sxs-lookup"><span data-stu-id="f6721-148">Consider the following code:</span></span>  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 <span data-ttu-id="f6721-149">Takový kód analysis by bylo nutné analyzovat metody TestSomeCondition a DoMyProjection a všechny metody, které tyto metody voláno k určení, pokud žádný kód měl vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="f6721-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="f6721-150">Ale kód analysis nelze právě vyhledejte kód, který měl vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="f6721-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="f6721-151">Je potřeba zvolit pro pouze kód, který měl vedlejší účinky na podřízených elementů `root` v této situaci.</span><span class="sxs-lookup"><span data-stu-id="f6721-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="f6721-152">Technologie LINQ to XML se nebude pokoušet provést tyto analýzy.</span><span class="sxs-lookup"><span data-stu-id="f6721-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="f6721-153">Můžete se rozhodnout, nechcete-li tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="f6721-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="f6721-154">Doprovodné materiály</span><span class="sxs-lookup"><span data-stu-id="f6721-154">Guidance</span></span>  
 <span data-ttu-id="f6721-155">Nejprve nemíchat deklarativní a imperativní kódu.</span><span class="sxs-lookup"><span data-stu-id="f6721-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="f6721-156">I v případě, že znáte přesně sémantika kolekce a sémantika metody, které upravit stromu XML zápisu některé inteligentní kód, který zabraňuje těchto kategorií problémy, bude nutné udržovat jinými vývojáři v budoucnu kódu , a nemusí být jako prostý na problémy.</span><span class="sxs-lookup"><span data-stu-id="f6721-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="f6721-157">Pokud kombinujete deklarativní a imperativní kódování styly, bude váš kód více křehká.</span><span class="sxs-lookup"><span data-stu-id="f6721-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="f6721-158">Pokud napíšete kód, který bude realizována kolekce tak, aby se tak předejde tyto problémy, mějte na paměti, ho komentáře podle potřeby ve vašem kódu tak, aby se tento problém pochopit programátory údržby.</span><span class="sxs-lookup"><span data-stu-id="f6721-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="f6721-159">Druhý Pokud výkon a další důležité informace povolit, použijte jenom deklarativní kód.</span><span class="sxs-lookup"><span data-stu-id="f6721-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="f6721-160">Neupravujte vaše stávající strom XML.</span><span class="sxs-lookup"><span data-stu-id="f6721-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="f6721-161">Vygenerujte nový token.</span><span class="sxs-lookup"><span data-stu-id="f6721-161">Generate a new one.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f6721-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6721-162">See Also</span></span>  
 [<span data-ttu-id="f6721-163">Pokročilé technologie LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="f6721-163">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
