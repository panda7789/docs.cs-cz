---
title: Refaktoring do čistého funkce (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 207b77ff50cd2aaeede758db69b48c8f29a16ab1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654254"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="b9818-102">Refaktoring do čistého funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9818-102">Refactoring Into Pure Functions (Visual Basic)</span></span>
<span data-ttu-id="b9818-103">Důležitým aspektem čistý funkční transformace je naučit se Refaktorovat kódu pomocí čistý funkce.</span><span class="sxs-lookup"><span data-stu-id="b9818-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
 <span data-ttu-id="b9818-104">Jak je uvedeno dříve v této části, čistou funkci má dva užitečné charakteristiky:</span><span class="sxs-lookup"><span data-stu-id="b9818-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
-   <span data-ttu-id="b9818-105">Nemá žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="b9818-105">It has no side effects.</span></span> <span data-ttu-id="b9818-106">Funkce nezmění žádné proměnné nebo data mimo funkci libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="b9818-106">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
-   <span data-ttu-id="b9818-107">Je konzistentní.</span><span class="sxs-lookup"><span data-stu-id="b9818-107">It is consistent.</span></span> <span data-ttu-id="b9818-108">Zadané stejnou sadu vstupních dat, vždy vrátí stejné výstupní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b9818-108">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="b9818-109">Přechod do funkčního programování jeden ze způsobů je refaktorovat stávajícího kódu pro vyloučení nepotřebných vedlejší efekty a externí závislosti.</span><span class="sxs-lookup"><span data-stu-id="b9818-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="b9818-110">Tímto způsobem můžete vytvořit čistě funkce verzích existujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="b9818-110">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="b9818-111">Toto téma popisuje je čistě funkce a co není.</span><span class="sxs-lookup"><span data-stu-id="b9818-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="b9818-112">[Kurz: manipulace s obsahu v dokumentu WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurz ukazuje, jak pracovat s dokumentem WordprocessingML a obsahuje dva příklady, jak k refactor pomocí čistou funkci.</span><span class="sxs-lookup"><span data-stu-id="b9818-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="b9818-113">Odstranění vedlejší efekty a externí závislosti</span><span class="sxs-lookup"><span data-stu-id="b9818-113">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="b9818-114">Následující příklady kontrastu dvě-čistý funkce a čistou funkci.</span><span class="sxs-lookup"><span data-stu-id="b9818-114">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="b9818-115">Čistý funkce, která změní člena třídy</span><span class="sxs-lookup"><span data-stu-id="b9818-115">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="b9818-116">V následujícím kódu `HypenatedConcat` funkce není čistou funkci, protože upravuje `aMember` – datový člen třídy:</span><span class="sxs-lookup"><span data-stu-id="b9818-116">In the following code, the `HypenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
```vb  
Module Module1  
    Dim aMember As String = "StringOne"  
  
    Public Sub HypenatedConcat(ByVal appendStr As String)  
        aMember = aMember & "-" & appendStr  
    End Sub  
  
    Sub Main()  
        HypenatedConcat("StringTwo")  
        Console.WriteLine(aMember)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="b9818-117">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b9818-117">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="b9818-118">Všimněte si, že je irelevantní, jestli má data upravována `public` nebo `private` získat přístup, nebo je `shared` nebo členem instance.</span><span class="sxs-lookup"><span data-stu-id="b9818-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="b9818-119">Čistý funkce nemění žádná data mimo funkci.</span><span class="sxs-lookup"><span data-stu-id="b9818-119">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="b9818-120">Čistý funkce, která změní Argument</span><span class="sxs-lookup"><span data-stu-id="b9818-120">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="b9818-121">Následující verze této stejné funkce navíc není čistá, protože upravuje obsah parametru, `sb`.</span><span class="sxs-lookup"><span data-stu-id="b9818-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
```vb  
Module Module1  
    Public Sub HypenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)  
        sb.Append("-" & appendStr)  
    End Sub  
  
    Sub Main()  
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")  
        HypenatedConcat(sb1, "StringTwo")  
        Console.WriteLine(sb1)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="b9818-122">Tato verze programu vytváří stejný výstup jako první verze, protože `HypenatedConcat` funkce změnila hodnota (stav) její první parametr vyvoláním <xref:System.Text.StringBuilder.Append%2A> – členská funkce.</span><span class="sxs-lookup"><span data-stu-id="b9818-122">This version of the program produces the same output as the first version, because the `HypenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="b9818-123">Všimněte si, že dojde k této změnou i přes tato skutečnost, `HypenatedConcat` používá předávání volání hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="b9818-123">Note that this alteration occurs despite that fact that `HypenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b9818-124">U typů odkazu Pokud předáte parametr podle hodnoty, výsledkem kopii odkaz na objekt předávány.</span><span class="sxs-lookup"><span data-stu-id="b9818-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="b9818-125">Tato kopie je stále spojena se stejná data jako odkaz na původní instanci (dokud proměnnou odkaz je přiřazen k vytvoření nového objektu).</span><span class="sxs-lookup"><span data-stu-id="b9818-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="b9818-126">Volání odkazem není nezbytně nutné pro funkci, kterou chcete upravit parametr.</span><span class="sxs-lookup"><span data-stu-id="b9818-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="b9818-127">Čistý – funkce</span><span class="sxs-lookup"><span data-stu-id="b9818-127">Pure Function</span></span>  
 <span data-ttu-id="b9818-128">Tato další verze programu hows jak implementovat `HypenatedConcat` fungovat jako čistou funkci.</span><span class="sxs-lookup"><span data-stu-id="b9818-128">This next version of the program hows how to implement the `HypenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="b9818-129">Znovu, tato verze vytváří na stejný řádek výstupu: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="b9818-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="b9818-130">Všimněte si, že pokud chcete zachovat zřetězených hodnota, je uložený v proměnnou zprostředkující `s2`.</span><span class="sxs-lookup"><span data-stu-id="b9818-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="b9818-131">Jeden z přístupů, může být velmi užitečná je zápis funkce, které jsou místně znečištěná (to znamená, že deklarace a upravit místní proměnné), ale jsou globálně čistý.</span><span class="sxs-lookup"><span data-stu-id="b9818-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="b9818-132">Takové funkce mají mnoho společných vlastností s žádoucí composability, ale některé z více convoluted funkční programovací idioms, jako je například nutnosti použít rekurzi při totéž by provést jednoduché smyčky vyhnout.</span><span class="sxs-lookup"><span data-stu-id="b9818-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="b9818-133">Standardní operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="b9818-133">Standard Query Operators</span></span>  
 <span data-ttu-id="b9818-134">Důležitou vlastností objektu standardní operátory dotazu je, že jsou implementované jako čistý funkce.</span><span class="sxs-lookup"><span data-stu-id="b9818-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="b9818-135">Další informace najdete v tématu [standardní dotaz přehled operátory (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b9818-135">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9818-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9818-136">See Also</span></span>  
 [<span data-ttu-id="b9818-137">Úvod do čistého funkční transformace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9818-137">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [<span data-ttu-id="b9818-138">Funkční programování vs. Imperativní programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9818-138">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
