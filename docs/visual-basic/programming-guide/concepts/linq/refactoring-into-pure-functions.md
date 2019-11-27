---
title: Refaktoring do čistých funkcí
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 22b371c6136836d6e0f1281f824b69378c0d3e4a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346525"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="c54a6-102">Refaktoring na čistě funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c54a6-102">Refactoring Into Pure Functions (Visual Basic)</span></span>

<span data-ttu-id="c54a6-103">Důležitým aspektem čistě funkční transformace je učení, jak refaktorovat kód pomocí čistě funkcí.</span><span class="sxs-lookup"><span data-stu-id="c54a6-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>

<span data-ttu-id="c54a6-104">Jak bylo uvedeno dříve v této části, funkce Pure má dvě užitečné charakteristiky:</span><span class="sxs-lookup"><span data-stu-id="c54a6-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>

- <span data-ttu-id="c54a6-105">Nemá žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="c54a6-105">It has no side effects.</span></span> <span data-ttu-id="c54a6-106">Funkce nemění žádné proměnné ani data žádného typu mimo funkci.</span><span class="sxs-lookup"><span data-stu-id="c54a6-106">The function does not change any variables or the data of any type outside of the function.</span></span>

- <span data-ttu-id="c54a6-107">Je konzistentní.</span><span class="sxs-lookup"><span data-stu-id="c54a6-107">It is consistent.</span></span> <span data-ttu-id="c54a6-108">V případě stejné sady vstupních dat bude vždy vracet stejnou výstupní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c54a6-108">Given the same set of input data, it will always return the same output value.</span></span>

 <span data-ttu-id="c54a6-109">Jedním ze způsobů, jak přecházet do funkčního programování, je refaktorující existující kód, který eliminuje nepotřebné vedlejší účinky a externí závislosti.</span><span class="sxs-lookup"><span data-stu-id="c54a6-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="c54a6-110">Tímto způsobem můžete vytvářet čistě verze funkcí stávajícího kódu.</span><span class="sxs-lookup"><span data-stu-id="c54a6-110">In this way, you can create pure function versions of existing code.</span></span>

<span data-ttu-id="c54a6-111">Toto téma popisuje, co je funkce Pure a co není.</span><span class="sxs-lookup"><span data-stu-id="c54a6-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="c54a6-112">[Kurz: manipulace s obsahem v kurzu WordprocessingML dokumentu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) ukazuje, jak manipulovat s dokumentem WordprocessingML a obsahuje dva příklady refaktorování pomocí funkce Pure.</span><span class="sxs-lookup"><span data-stu-id="c54a6-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>

## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="c54a6-113">Vyloučení vedlejších efektů a externích závislostí</span><span class="sxs-lookup"><span data-stu-id="c54a6-113">Eliminating Side Effects and External Dependencies</span></span>

<span data-ttu-id="c54a6-114">Následující příklady kontrastují dvě nečisté funkce a funkci Pure.</span><span class="sxs-lookup"><span data-stu-id="c54a6-114">The following examples contrast two non-pure functions and a pure function.</span></span>

### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="c54a6-115">Nečistá funkce, která mění člena třídy</span><span class="sxs-lookup"><span data-stu-id="c54a6-115">Non-Pure Function that Changes a Class Member</span></span>

<span data-ttu-id="c54a6-116">V následujícím kódu není funkce `HyphenatedConcat` čistě funkcí, protože upravuje datový člen `aMember` ve třídě:</span><span class="sxs-lookup"><span data-stu-id="c54a6-116">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>

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

<span data-ttu-id="c54a6-117">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c54a6-117">This code produces the following output:</span></span>

```console
StringOne-StringTwo
```

<span data-ttu-id="c54a6-118">Všimněte si, že je důležité, aby data, která jsou upravována, měla `public` nebo `private` přístup, nebo je členem `shared` člena nebo instance.</span><span class="sxs-lookup"><span data-stu-id="c54a6-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="c54a6-119">Funkce Pure nemění žádná data mimo funkci.</span><span class="sxs-lookup"><span data-stu-id="c54a6-119">A pure function does not change any data outside of the function.</span></span>

### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="c54a6-120">Nečistá funkce, která mění argument</span><span class="sxs-lookup"><span data-stu-id="c54a6-120">Non-Pure Function that Changes an Argument</span></span>

<span data-ttu-id="c54a6-121">Kromě toho tato verze stejné funkce není čistá, protože upravuje obsah svého parametru `sb`.</span><span class="sxs-lookup"><span data-stu-id="c54a6-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>

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

<span data-ttu-id="c54a6-122">Tato verze programu vytvoří stejný výstup jako první verze, protože funkce `HyphenatedConcat` změnila hodnotu (stav) jeho prvního parametru vyvoláním členské funkce <xref:System.Text.StringBuilder.Append%2A>.</span><span class="sxs-lookup"><span data-stu-id="c54a6-122">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="c54a6-123">Všimněte si, že tato změna probíhá navzdory tomu, že `HyphenatedConcat` používá předávání parametru volání podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c54a6-123">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c54a6-124">Pro typy odkazů, Pokud předáte parametr podle hodnoty, výsledkem bude kopie odkazu na předaný objekt.</span><span class="sxs-lookup"><span data-stu-id="c54a6-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="c54a6-125">Tato kopie je stále přidružená ke stejným datům instance jako původní odkaz (dokud referenční proměnná není přiřazena k novému objektu).</span><span class="sxs-lookup"><span data-stu-id="c54a6-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="c54a6-126">Volání po odkazech nemusí nutně vyžadovat, aby funkce mohla upravovat parametr.</span><span class="sxs-lookup"><span data-stu-id="c54a6-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>

### <a name="pure-function"></a><span data-ttu-id="c54a6-127">Funkce Pure</span><span class="sxs-lookup"><span data-stu-id="c54a6-127">Pure Function</span></span>

<span data-ttu-id="c54a6-128">Tato další verze programu Hows, jak implementovat funkci `HyphenatedConcat` jako čistě funkci.</span><span class="sxs-lookup"><span data-stu-id="c54a6-128">This next version of the program hows how to implement the `HyphenatedConcat` function as a pure function.</span></span>

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

<span data-ttu-id="c54a6-129">Tato verze znovu vytvoří stejný řádek výstupu: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="c54a6-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="c54a6-130">Všimněte si, že pokud chcete zachovat zřetězenou hodnotu, je uložena do mezilehlé proměnné `s2`.</span><span class="sxs-lookup"><span data-stu-id="c54a6-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>

<span data-ttu-id="c54a6-131">Jedním z přístupů, které mohou být velmi užitečné, je psaní funkcí, které jsou místně nečisté (to znamená, že deklarují a mění místní proměnné), ale jsou globálně čistě.</span><span class="sxs-lookup"><span data-stu-id="c54a6-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="c54a6-132">Tyto funkce mají mnoho z hlediska žádoucích vlastností, ale nemusíte používat rekurzi idiomy, jako je třeba použití rekurze, když by jednoduchá smyčka mohla dosáhnout stejné věci.</span><span class="sxs-lookup"><span data-stu-id="c54a6-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>

## <a name="standard-query-operators"></a><span data-ttu-id="c54a6-133">Standardní operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="c54a6-133">Standard Query Operators</span></span>

<span data-ttu-id="c54a6-134">Důležitou vlastností standardních operátorů dotazu je to, že jsou implementované jako čisté funkce.</span><span class="sxs-lookup"><span data-stu-id="c54a6-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>

<span data-ttu-id="c54a6-135">Další informace najdete v tématu [Přehled standardních operátorů dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c54a6-135">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c54a6-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c54a6-136">See also</span></span>

- [<span data-ttu-id="c54a6-137">Úvod do čistě funkční transformace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c54a6-137">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="c54a6-138">Funkční programování vs. imperativní programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c54a6-138">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
