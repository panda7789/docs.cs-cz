---
title: Refaktoring do čistého funkcí (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: ed9b33ed2b9669cb4412177086fc648865e4954a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339550"
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="1e5b4-102">Refaktoring do čistého funkcí (C#)</span><span class="sxs-lookup"><span data-stu-id="1e5b4-102">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="1e5b4-103">Důležitým aspektem čistý funkční transformace je naučit se Refaktorovat kódu pomocí čistý funkce.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e5b4-104">Běžné klasifikace v funkční programování se, že zrefaktorujete programy pomocí čistý funkcí.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-104">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="1e5b4-105">V jazyce Visual Basic a C++ to zarovnaná s použití funkcí v příslušné jazyky.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-105">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="1e5b4-106">V jazyce C#, ale funkce se volají metody.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-106">However, in C#, functions are called methods.</span></span> <span data-ttu-id="1e5b4-107">Pro účely Tato diskuse se čistou funkci je implementovaný jako metody v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-107">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="1e5b4-108">Jak je uvedeno dříve v této části, čistou funkci má dva užitečné charakteristiky:</span><span class="sxs-lookup"><span data-stu-id="1e5b4-108">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
-   <span data-ttu-id="1e5b4-109">Nemá žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-109">It has no side effects.</span></span> <span data-ttu-id="1e5b4-110">Funkce nezmění žádné proměnné nebo data mimo funkci libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-110">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
-   <span data-ttu-id="1e5b4-111">Je konzistentní.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-111">It is consistent.</span></span> <span data-ttu-id="1e5b4-112">Zadané stejnou sadu vstupních dat, vždy vrátí stejné výstupní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-112">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="1e5b4-113">Přechod do funkčního programování jeden ze způsobů je refaktorovat stávajícího kódu pro vyloučení nepotřebných vedlejší efekty a externí závislosti.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-113">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="1e5b4-114">Tímto způsobem můžete vytvořit čistě funkce verzích existujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-114">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="1e5b4-115">Toto téma popisuje je čistě funkce a co není.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-115">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="1e5b4-116">[Kurz: manipulace s obsahu v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurz ukazuje, jak pracovat s dokumentem WordprocessingML a obsahuje dva příklady, jak k refactor pomocí čistou funkci.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-116">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="1e5b4-117">Odstranění vedlejší efekty a externí závislosti</span><span class="sxs-lookup"><span data-stu-id="1e5b4-117">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="1e5b4-118">Následující příklady kontrastu dvě-čistý funkce a čistou funkci.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-118">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="1e5b4-119">Čistý funkce, která změní člena třídy</span><span class="sxs-lookup"><span data-stu-id="1e5b4-119">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="1e5b4-120">V následujícím kódu `HyphenatedConcat` funkce není čistou funkci, protože upravuje `aMember` – datový člen třídy:</span><span class="sxs-lookup"><span data-stu-id="1e5b4-120">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
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
  
 <span data-ttu-id="1e5b4-121">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1e5b4-121">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="1e5b4-122">Všimněte si, že je irelevantní, jestli má data upravována `public` nebo `private` získat přístup, nebo je `static` nebo členem instance.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-122">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="1e5b4-123">Čistý funkce nemění žádná data mimo funkci.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-123">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="1e5b4-124">Čistý funkce, která změní Argument</span><span class="sxs-lookup"><span data-stu-id="1e5b4-124">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="1e5b4-125">Následující verze této stejné funkce navíc není čistá, protože upravuje obsah parametru, `sb`.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-125">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
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
  
 <span data-ttu-id="1e5b4-126">Tato verze programu vytváří stejný výstup jako první verze, protože `HyphenatedConcat` funkce změnila hodnota (stav) její první parametr vyvoláním <xref:System.Text.StringBuilder.Append%2A> – členská funkce.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="1e5b4-127">Všimněte si, že dojde k této změnou i přes tato skutečnost, `HyphenatedConcat` používá předávání volání hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-127">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1e5b4-128">U typů odkazu Pokud předáte parametr podle hodnoty, výsledkem kopii odkaz na objekt předávány.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="1e5b4-129">Tato kopie je stále spojena se stejná data jako odkaz na původní instanci (dokud proměnnou odkaz je přiřazen k vytvoření nového objektu).</span><span class="sxs-lookup"><span data-stu-id="1e5b4-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="1e5b4-130">Volání odkazem není nezbytně nutné pro funkci, kterou chcete upravit parametr.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-130">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="1e5b4-131">Čistý – funkce</span><span class="sxs-lookup"><span data-stu-id="1e5b4-131">Pure Function</span></span>  
<span data-ttu-id="1e5b4-132">Tato další verze programu ukazuje, jak implementovat `HyphenatedConcat` fungovat jako čistou funkci.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="1e5b4-133">Znovu, tato verze vytváří na stejný řádek výstupu: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="1e5b4-134">Všimněte si, že pokud chcete zachovat zřetězených hodnota, je uložený v proměnnou zprostředkující `s2`.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-134">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="1e5b4-135">Jeden z přístupů, může být velmi užitečná je zápis funkce, které jsou místně znečištěná (to znamená, že deklarace a upravit místní proměnné), ale jsou globálně čistý.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="1e5b4-136">Takové funkce mají mnoho společných vlastností s žádoucí composability, ale některé z více convoluted funkční programovací idioms, jako je například nutnosti použít rekurzi při totéž by provést jednoduché smyčky vyhnout.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="1e5b4-137">Standardní operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="1e5b4-137">Standard Query Operators</span></span>  
 <span data-ttu-id="1e5b4-138">Důležitou vlastností objektu standardní operátory dotazu je, že jsou implementované jako čistý funkce.</span><span class="sxs-lookup"><span data-stu-id="1e5b4-138">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="1e5b4-139">Další informace najdete v tématu [standardní přehled operátory dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1e5b4-139">For more information, see [Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5b4-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e5b4-140">See Also</span></span>  
 [<span data-ttu-id="1e5b4-141">Úvod do čistého funkční transformace (C#)</span><span class="sxs-lookup"><span data-stu-id="1e5b4-141">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [<span data-ttu-id="1e5b4-142">Funkční programování vs. Imperativní programování (C#)</span><span class="sxs-lookup"><span data-stu-id="1e5b4-142">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
