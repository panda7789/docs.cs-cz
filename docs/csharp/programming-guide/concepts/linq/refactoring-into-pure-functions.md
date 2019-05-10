---
title: Refaktoring do čistých funkcí (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 3a498588e9ca1ab85602946b75b593804fa0953a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596881"
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="bb8cc-102">Refaktoring do čistých funkcí (C#)</span><span class="sxs-lookup"><span data-stu-id="bb8cc-102">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="bb8cc-103">Důležitou součástí čistě funkčním transformacím je učit, jak Refaktorovat kód pomocí čisté funkce.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb8cc-104">Běžné do funkčního programování se, že Refaktorovat programy pomocí čisté funkce.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-104">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="bb8cc-105">V jazyce Visual Basic a C++ ten je v souladu s použitím funkce v příslušné jazyky.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-105">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="bb8cc-106">V jazyce C#, ale funkce jsou volány metody.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-106">However, in C#, functions are called methods.</span></span> <span data-ttu-id="bb8cc-107">Pro účely této diskuse je implementovaný čistě funkce jako metody v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-107">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="bb8cc-108">Jak je uvedeno dříve v této části, čistě funkci má dvě užitečné vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="bb8cc-108">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
- <span data-ttu-id="bb8cc-109">Nemá žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-109">It has no side effects.</span></span> <span data-ttu-id="bb8cc-110">Funkce nezmění žádné proměnné nebo dat libovolného typu mimo funkci.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-110">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
- <span data-ttu-id="bb8cc-111">To je konzistentní.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-111">It is consistent.</span></span> <span data-ttu-id="bb8cc-112">S ohledem stejnou sadu vstupních dat, vždycky vrátí stejnou hodnotu výstup.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-112">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="bb8cc-113">Jeden způsob, jak přechod do funkčního programování je Refaktorujte již existující kód k odstranění nepotřebných vedlejší účinky a externích závislostí.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-113">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="bb8cc-114">Tímto způsobem můžete vytvořit čistě funkce verze stávajícího kódu.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-114">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="bb8cc-115">Toto téma popisuje čistě funkce je a co není.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-115">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="bb8cc-116">[Kurzu: Manipulace s obsahem v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurz ukazuje, jak pracovat s dokumentu WordprocessingML a obsahuje dva příklady toho, jak refaktorace pomocí čisté funkce.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-116">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="bb8cc-117">Odstranění vedlejší účinky a externí závislosti</span><span class="sxs-lookup"><span data-stu-id="bb8cc-117">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="bb8cc-118">Následující příklady kontrastu dvě funkce čistě a čistě funkce.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-118">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="bb8cc-119">Čistě funkce, která se mění členem třídy.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-119">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="bb8cc-120">V následujícím kódu `HyphenatedConcat` funkce není čistě funkcí, protože upravuje `aMember` datový člen třídy:</span><span class="sxs-lookup"><span data-stu-id="bb8cc-120">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
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
  
 <span data-ttu-id="bb8cc-121">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="bb8cc-121">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="bb8cc-122">Všimněte si, že je bezvýznamná toho, jestli má úpravy dat `public` nebo `private` přístup, nebo je `static` člen nebo člen instance.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-122">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="bb8cc-123">Čistě funkce nemění žádná data mimo funkci.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-123">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="bb8cc-124">Čistě funkce, která se mění Argument</span><span class="sxs-lookup"><span data-stu-id="bb8cc-124">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="bb8cc-125">Následující verze stejné funkce kromě toho není čistě, protože mění obsah svůj parametr, `sb`.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-125">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
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
  
 <span data-ttu-id="bb8cc-126">Tuto verzi programu vytváří stejný výstup jako první verze, protože `HyphenatedConcat` funkce změnila jejím prvním parametrem (stav) hodnota vyvoláním <xref:System.Text.StringBuilder.Append%2A> členskou funkci.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="bb8cc-127">Všimněte si, že tato změna nastane bez ohledu na tom, který `HyphenatedConcat` používá předávání parametrů volání podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-127">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bb8cc-128">Pro typy odkazů Pokud předáte parametr podle hodnoty, výsledkem zkopírovat odkaz na objekt je předán.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="bb8cc-129">Tato kopie je stále spojena se stejná data jako odkaz na původní instanci (až do nového objektu přiřadí proměnná odkaz).</span><span class="sxs-lookup"><span data-stu-id="bb8cc-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="bb8cc-130">Volání odkazem se nutně nevyžaduje pro funkci, kterou chcete upravit parametr.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-130">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="bb8cc-131">Pure – funkce</span><span class="sxs-lookup"><span data-stu-id="bb8cc-131">Pure Function</span></span>  
<span data-ttu-id="bb8cc-132">Tato další verze program ukazuje, jak implementovat `HyphenatedConcat` fungovat jako čistě funkce.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="bb8cc-133">Znovu, vytvoří tato verze stejného řádku výstupu: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="bb8cc-134">Všimněte si, že pokud chcete zachovat zřetězené hodnotě, uloží se zprostředkující proměnné `s2`.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-134">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="bb8cc-135">Je jedním z přístupů, které mohou být velmi užitečná k zápisu funkcí, které jsou místně znečištěná (to znamená, že deklarace a upravit místní proměnné), ale jsou globálně čistě.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="bb8cc-136">Tyto funkce mají mnoho vlastností žádoucí skládání, ale Vyhněte se některé z více složitými funkční programovací idiomy, jako je například museli použít rekurzi při jednoduché smyčky by provést totéž.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="bb8cc-137">Standardní operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="bb8cc-137">Standard Query Operators</span></span>  
 <span data-ttu-id="bb8cc-138">Důležitou vlastnost operátory standardního dotazu je, že jsou implementovány jako čistě funkce.</span><span class="sxs-lookup"><span data-stu-id="bb8cc-138">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="bb8cc-139">Další informace najdete v tématu [přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bb8cc-139">For more information, see [Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb8cc-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb8cc-140">See also</span></span>

- [<span data-ttu-id="bb8cc-141">Úvod k čistě funkčním transformacím (C#)</span><span class="sxs-lookup"><span data-stu-id="bb8cc-141">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="bb8cc-142">Funkční programování vs. Imperativní programování (C#)</span><span class="sxs-lookup"><span data-stu-id="bb8cc-142">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
