---
title: Refaktoring do čistých funkcí (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 4cf91ff078bd1c4582daa05475a91c4a4ecaba3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253102"
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="ef1d5-102">Refaktoring do čistých funkcí (C#)</span><span class="sxs-lookup"><span data-stu-id="ef1d5-102">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="ef1d5-103">Důležitým aspektem čistě funkční transformace je naučit se refaktorovat kód pomocí čisté funkce.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef1d5-104">Běžnou nomenklaturou ve funkčním programování je, že refaktorujete programy pomocí čistých funkcí.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-104">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="ef1d5-105">V jazyce Visual Basic a C++ to zarovná s použitím funkcí v příslušných jazycích.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-105">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="ef1d5-106">Však v C#, funkce se nazývají metody.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-106">However, in C#, functions are called methods.</span></span> <span data-ttu-id="ef1d5-107">Pro účely této diskuse je čistá funkce implementována jako metoda v c#.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-107">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="ef1d5-108">Jak je uvedeno dříve v této části, čistá funkce má dvě užitečné vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="ef1d5-108">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
- <span data-ttu-id="ef1d5-109">Nemá žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-109">It has no side effects.</span></span> <span data-ttu-id="ef1d5-110">Funkce nemění žádné proměnné nebo data jakéhokoli typu mimo funkci.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-110">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
- <span data-ttu-id="ef1d5-111">Je to konzistentní.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-111">It is consistent.</span></span> <span data-ttu-id="ef1d5-112">Vzhledem ke stejné sadě vstupních dat vždy vrátí stejnou výstupní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-112">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="ef1d5-113">Jedním ze způsobů přechodu na funkční programování je refaktorovat existující kód k odstranění zbytečných vedlejších účinků a externích závislostí.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-113">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="ef1d5-114">Tímto způsobem můžete vytvořit čistě funkční verze existujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-114">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="ef1d5-115">Toto téma popisuje, co je čistá funkce a co není.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-115">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="ef1d5-116">[Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md) kurz ukazuje, jak manipulovat s dokumentem WordprocessingML a obsahuje dva příklady, jak refaktorovat pomocí čisté funkce.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-116">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](./shape-of-wordprocessingml-documents.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="ef1d5-117">Odstranění vedlejších účinků a externích závislostí</span><span class="sxs-lookup"><span data-stu-id="ef1d5-117">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="ef1d5-118">Následující příklady kontrastují dvě nečisté funkce a čistou funkci.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-118">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="ef1d5-119">Nečistá funkce, která mění člen třídy</span><span class="sxs-lookup"><span data-stu-id="ef1d5-119">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="ef1d5-120">V následujícím kódu `HyphenatedConcat` funkce není čistě, protože upravuje `aMember` datový člen ve třídě:</span><span class="sxs-lookup"><span data-stu-id="ef1d5-120">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
```csharp  
public class Program  
{  
    private static string aMember = "StringOne";  
  
    public static void HyphenatedConcat(string appendStr)  
    {  
        aMember += '-' + appendStr;  
    }  
  
    public static void Main()  
    {  
        HyphenatedConcat("StringTwo");  
        Console.WriteLine(aMember);  
    }  
}  
```  
  
 <span data-ttu-id="ef1d5-121">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ef1d5-121">This code produces the following output:</span></span>  
  
```output  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="ef1d5-122">Všimněte si, že je irelevantní, zda má upravná data `public` nebo `private` přístup, nebo je `static` členem nebo členem instance.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-122">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="ef1d5-123">Čistá funkce nemění žádná data mimo funkci.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-123">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="ef1d5-124">Nečistá funkce, která mění argument</span><span class="sxs-lookup"><span data-stu-id="ef1d5-124">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="ef1d5-125">Kromě toho následující verze stejné funkce není čistá, protože upravuje obsah svého `sb`parametru .</span><span class="sxs-lookup"><span data-stu-id="ef1d5-125">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
```csharp  
public class Program  
{  
    public static void HyphenatedConcat(StringBuilder sb, String appendStr)  
    {  
        sb.Append('-' + appendStr);  
    }  
  
    public static void Main()  
    {  
        StringBuilder sb1 = new StringBuilder("StringOne");  
        HyphenatedConcat(sb1, "StringTwo");  
        Console.WriteLine(sb1);  
    }  
}  
```  
  
 <span data-ttu-id="ef1d5-126">Tato verze programu vytváří stejný výstup jako první verze, protože `HyphenatedConcat` funkce změnila hodnotu (stav) svého prvního parametru <xref:System.Text.StringBuilder.Append%2A> vyvoláním členské funkce.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="ef1d5-127">Všimněte si, že k `HyphenatedConcat` této změně dochází navzdory skutečnosti, že používá předávání parametru call-by-value.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-127">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ef1d5-128">Pro typy odkazů, pokud předáte parametr podle hodnoty, výsledkem je kopie odkazu na předávaný objekt.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="ef1d5-129">Tato kopie je stále přidružena ke stejným datům instance jako původní odkaz (dokud není referenční proměnná přiřazena novému objektu).</span><span class="sxs-lookup"><span data-stu-id="ef1d5-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="ef1d5-130">Volání podle odkazu není nutně nutné pro funkci upravit parametr.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-130">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="ef1d5-131">Čistá funkce</span><span class="sxs-lookup"><span data-stu-id="ef1d5-131">Pure Function</span></span>  
<span data-ttu-id="ef1d5-132">Tato další verze programu ukazuje, `HyphenatedConcat` jak implementovat funkci jako čistou funkci.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>  
  
```csharp  
class Program  
{  
    public static string HyphenatedConcat(string s, string appendStr)  
    {  
        return (s + '-' + appendStr);  
    }  
  
    public static void Main(string[] args)  
    {  
        string s1 = "StringOne";  
        string s2 = HyphenatedConcat(s1, "StringTwo");  
        Console.WriteLine(s2);  
    }  
}  
```  
  
 <span data-ttu-id="ef1d5-133">Opět platí, že tato verze produkuje `StringOne-StringTwo`stejný řádek výstupu: .</span><span class="sxs-lookup"><span data-stu-id="ef1d5-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="ef1d5-134">Všimněte si, že chcete-li zachovat zřetězenou `s2`hodnotu, je uložen v zprostředkující proměnné .</span><span class="sxs-lookup"><span data-stu-id="ef1d5-134">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="ef1d5-135">Jeden přístup, který může být velmi užitečné, je psát funkce, které jsou místně nečisté (to znamená, že deklarují a upravují místní proměnné), ale jsou globálně čisté.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="ef1d5-136">Tyto funkce mají mnoho žádoucí charakteristiky kompozity, ale vyhnout se některé více spletité funkční programovací idiomy, jako je například nutnost používat rekurze, když jednoduchá smyčka by dosáhnout totéž.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="ef1d5-137">Standardní operátory dotazů</span><span class="sxs-lookup"><span data-stu-id="ef1d5-137">Standard Query Operators</span></span>  
 <span data-ttu-id="ef1d5-138">Důležitou charakteristikou standardních operátorů dotazů je, že jsou implementovány jako čisté funkce.</span><span class="sxs-lookup"><span data-stu-id="ef1d5-138">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="ef1d5-139">Další informace naleznete [v tématu Přehled operátorů standardních dotazů (C#)](./standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ef1d5-139">For more information, see [Standard Query Operators Overview (C#)](./standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef1d5-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef1d5-140">See also</span></span>

- [<span data-ttu-id="ef1d5-141">Úvod do čistě funkčních transformací (C#)</span><span class="sxs-lookup"><span data-stu-id="ef1d5-141">Introduction to Pure Functional Transformations (C#)</span></span>](./introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="ef1d5-142">Funkční programování vs. imperativní programování (C#)</span><span class="sxs-lookup"><span data-stu-id="ef1d5-142">Functional Programming vs. Imperative Programming (C#)</span></span>](./functional-programming-vs-imperative-programming.md)
