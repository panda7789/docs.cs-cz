---
title: Refaktoring do čistých funkcí (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 0a37b30278c850256355612cec09a4c017c7adc2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787163"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="bf0eb-102">Refaktoring do čistých funkcí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf0eb-102">Refactoring Into Pure Functions (Visual Basic)</span></span>

<span data-ttu-id="bf0eb-103">Důležitou součástí čistě funkčním transformacím je učit, jak Refaktorovat kód pomocí čisté funkce.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>

<span data-ttu-id="bf0eb-104">Jak je uvedeno dříve v této části, čistě funkci má dvě užitečné vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="bf0eb-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>

- <span data-ttu-id="bf0eb-105">Nemá žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-105">It has no side effects.</span></span> <span data-ttu-id="bf0eb-106">Funkce nezmění žádné proměnné nebo dat libovolného typu mimo funkci.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-106">The function does not change any variables or the data of any type outside of the function.</span></span>

- <span data-ttu-id="bf0eb-107">To je konzistentní.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-107">It is consistent.</span></span> <span data-ttu-id="bf0eb-108">S ohledem stejnou sadu vstupních dat, vždycky vrátí stejnou hodnotu výstup.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-108">Given the same set of input data, it will always return the same output value.</span></span>

 <span data-ttu-id="bf0eb-109">Jeden způsob, jak přechod do funkčního programování je Refaktorujte již existující kód k odstranění nepotřebných vedlejší účinky a externích závislostí.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="bf0eb-110">Tímto způsobem můžete vytvořit čistě funkce verze stávajícího kódu.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-110">In this way, you can create pure function versions of existing code.</span></span>

<span data-ttu-id="bf0eb-111">Toto téma popisuje čistě funkce je a co není.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="bf0eb-112">[Kurzu: Manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurz ukazuje, jak pracovat s dokumentu WordprocessingML a obsahuje dva příklady toho, jak refaktorace pomocí čisté funkce.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>

## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="bf0eb-113">Odstranění vedlejší účinky a externí závislosti</span><span class="sxs-lookup"><span data-stu-id="bf0eb-113">Eliminating Side Effects and External Dependencies</span></span>

<span data-ttu-id="bf0eb-114">Následující příklady kontrastu dvě funkce čistě a čistě funkce.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-114">The following examples contrast two non-pure functions and a pure function.</span></span>

### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="bf0eb-115">Čistě funkce, která se mění členem třídy.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-115">Non-Pure Function that Changes a Class Member</span></span>

<span data-ttu-id="bf0eb-116">V následujícím kódu `HyphenatedConcat` funkce není čistě funkcí, protože upravuje `aMember` datový člen třídy:</span><span class="sxs-lookup"><span data-stu-id="bf0eb-116">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

<span data-ttu-id="bf0eb-117">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="bf0eb-117">This code produces the following output:</span></span>

```
StringOne-StringTwo
```

<span data-ttu-id="bf0eb-118">Všimněte si, že je bezvýznamná toho, jestli má úpravy dat `public` nebo `private` přístup, nebo je `shared` člen nebo člen instance.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="bf0eb-119">Čistě funkce nemění žádná data mimo funkci.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-119">A pure function does not change any data outside of the function.</span></span>

### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="bf0eb-120">Čistě funkce, která se mění Argument</span><span class="sxs-lookup"><span data-stu-id="bf0eb-120">Non-Pure Function that Changes an Argument</span></span>

<span data-ttu-id="bf0eb-121">Následující verze stejné funkce kromě toho není čistě, protože mění obsah svůj parametr, `sb`.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

<span data-ttu-id="bf0eb-122">Tuto verzi programu vytváří stejný výstup jako první verze, protože `HyphenatedConcat` funkce změnila jejím prvním parametrem (stav) hodnota vyvoláním <xref:System.Text.StringBuilder.Append%2A> členskou funkci.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-122">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="bf0eb-123">Všimněte si, že tato změna nastane bez ohledu na tom, který `HyphenatedConcat` používá předávání parametrů volání podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-123">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf0eb-124">Pro typy odkazů Pokud předáte parametr podle hodnoty, výsledkem zkopírovat odkaz na objekt je předán.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="bf0eb-125">Tato kopie je stále spojena se stejná data jako odkaz na původní instanci (až do nového objektu přiřadí proměnná odkaz).</span><span class="sxs-lookup"><span data-stu-id="bf0eb-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="bf0eb-126">Volání odkazem se nutně nevyžaduje pro funkci, kterou chcete upravit parametr.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>

### <a name="pure-function"></a><span data-ttu-id="bf0eb-127">Pure – funkce</span><span class="sxs-lookup"><span data-stu-id="bf0eb-127">Pure Function</span></span>

<span data-ttu-id="bf0eb-128">Tato další verze programu postupy implementace `HyphenatedConcat` fungovat jako čistě funkce.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-128">This next version of the program hows how to implement the `HyphenatedConcat` function as a pure function.</span></span>

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

<span data-ttu-id="bf0eb-129">Znovu, vytvoří tato verze stejného řádku výstupu: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="bf0eb-130">Všimněte si, že pokud chcete zachovat zřetězené hodnotě, uloží se zprostředkující proměnné `s2`.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>

<span data-ttu-id="bf0eb-131">Je jedním z přístupů, které mohou být velmi užitečná k zápisu funkcí, které jsou místně znečištěná (to znamená, že deklarace a upravit místní proměnné), ale jsou globálně čistě.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="bf0eb-132">Tyto funkce mají mnoho vlastností žádoucí skládání, ale Vyhněte se některé z více složitými funkční programovací idiomy, jako je například museli použít rekurzi při jednoduché smyčky by provést totéž.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>

## <a name="standard-query-operators"></a><span data-ttu-id="bf0eb-133">Standardní operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="bf0eb-133">Standard Query Operators</span></span>

<span data-ttu-id="bf0eb-134">Důležitou vlastnost operátory standardního dotazu je, že jsou implementovány jako čistě funkce.</span><span class="sxs-lookup"><span data-stu-id="bf0eb-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>

<span data-ttu-id="bf0eb-135">Další informace najdete v tématu [přehled operátory standardního dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bf0eb-135">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bf0eb-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf0eb-136">See also</span></span>

- [<span data-ttu-id="bf0eb-137">Úvod k čistě funkčním transformacím (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf0eb-137">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="bf0eb-138">Funkční programování vs. Imperativní programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf0eb-138">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
