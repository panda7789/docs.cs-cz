---
title: Refaktoring do čistě funkcí (C#)
description: Naučte se Refaktorovat kód pomocí čistě funkcí. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: cc5dd26923e2edaed34c8f1b742b3dfa1e935e68
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300225"
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="d8038-104">Refaktoring do čistě funkcí (C#)</span><span class="sxs-lookup"><span data-stu-id="d8038-104">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="d8038-105">Důležitým aspektem čistě funkční transformace je učení, jak refaktorovat kód pomocí čistě funkcí.</span><span class="sxs-lookup"><span data-stu-id="d8038-105">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8038-106">Běžnou klasifikací při funkčním programování je, že refaktoruje programy pomocí funkce Pure.</span><span class="sxs-lookup"><span data-stu-id="d8038-106">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="d8038-107">V Visual Basic a C++ se tato možnost zarovnává s použitím funkcí v odpovídajících jazycích.</span><span class="sxs-lookup"><span data-stu-id="d8038-107">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="d8038-108">V jazyce C# se však funkce nazývají metody.</span><span class="sxs-lookup"><span data-stu-id="d8038-108">However, in C#, functions are called methods.</span></span> <span data-ttu-id="d8038-109">Pro účely této diskuze je funkce Pure implementována jako metoda v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="d8038-109">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="d8038-110">Jak bylo uvedeno dříve v této části, funkce Pure má dvě užitečné charakteristiky:</span><span class="sxs-lookup"><span data-stu-id="d8038-110">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
- <span data-ttu-id="d8038-111">Nemá žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="d8038-111">It has no side effects.</span></span> <span data-ttu-id="d8038-112">Funkce nemění žádné proměnné ani data žádného typu mimo funkci.</span><span class="sxs-lookup"><span data-stu-id="d8038-112">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
- <span data-ttu-id="d8038-113">Je konzistentní.</span><span class="sxs-lookup"><span data-stu-id="d8038-113">It is consistent.</span></span> <span data-ttu-id="d8038-114">V případě stejné sady vstupních dat bude vždy vracet stejnou výstupní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d8038-114">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="d8038-115">Jedním ze způsobů, jak přecházet do funkčního programování, je refaktorující existující kód, který eliminuje nepotřebné vedlejší účinky a externí závislosti.</span><span class="sxs-lookup"><span data-stu-id="d8038-115">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="d8038-116">Tímto způsobem můžete vytvářet čistě verze funkcí stávajícího kódu.</span><span class="sxs-lookup"><span data-stu-id="d8038-116">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="d8038-117">Toto téma popisuje, co je funkce Pure a co není.</span><span class="sxs-lookup"><span data-stu-id="d8038-117">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="d8038-118">[Kurz: manipulace s obsahem v kurzu WordprocessingML dokumentu (C#)](./shape-of-wordprocessingml-documents.md) ukazuje, jak manipulovat s dokumentem WordprocessingML a obsahuje dva příklady refaktorování pomocí funkce Pure.</span><span class="sxs-lookup"><span data-stu-id="d8038-118">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](./shape-of-wordprocessingml-documents.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="d8038-119">Vyloučení vedlejších efektů a externích závislostí</span><span class="sxs-lookup"><span data-stu-id="d8038-119">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="d8038-120">Následující příklady kontrastují dvě nečisté funkce a funkci Pure.</span><span class="sxs-lookup"><span data-stu-id="d8038-120">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="d8038-121">Nečistá funkce, která mění člena třídy</span><span class="sxs-lookup"><span data-stu-id="d8038-121">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="d8038-122">V následujícím kódu není `HyphenatedConcat` funkce čistě funkcí, protože upravuje `aMember` datový člen ve třídě:</span><span class="sxs-lookup"><span data-stu-id="d8038-122">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
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
  
 <span data-ttu-id="d8038-123">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d8038-123">This code produces the following output:</span></span>  
  
```output  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="d8038-124">Všimněte si, že je nedůležité, jestli data, která jsou měněna `public` `private` , mají přístup nebo jsou členem `static` nebo členem instance.</span><span class="sxs-lookup"><span data-stu-id="d8038-124">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="d8038-125">Funkce Pure nemění žádná data mimo funkci.</span><span class="sxs-lookup"><span data-stu-id="d8038-125">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="d8038-126">Nečistá funkce, která mění argument</span><span class="sxs-lookup"><span data-stu-id="d8038-126">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="d8038-127">Kromě toho následující verze této funkce není čistá, protože upravuje obsah svého parametru, `sb` .</span><span class="sxs-lookup"><span data-stu-id="d8038-127">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
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
  
 <span data-ttu-id="d8038-128">Tato verze programu vytvoří stejný výstup jako první verze, protože `HyphenatedConcat` funkce změnila hodnotu (stav) jeho prvního parametru vyvoláním <xref:System.Text.StringBuilder.Append%2A> členské funkce.</span><span class="sxs-lookup"><span data-stu-id="d8038-128">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="d8038-129">Všimněte si, že tato změna probíhá navzdory tomu, že `HyphenatedConcat` používá předávání parametru volání podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d8038-129">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d8038-130">Pro typy odkazů, Pokud předáte parametr podle hodnoty, výsledkem bude kopie odkazu na předaný objekt.</span><span class="sxs-lookup"><span data-stu-id="d8038-130">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="d8038-131">Tato kopie je stále přidružená ke stejným datům instance jako původní odkaz (dokud referenční proměnná není přiřazena k novému objektu).</span><span class="sxs-lookup"><span data-stu-id="d8038-131">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="d8038-132">Volání po odkazech nemusí nutně vyžadovat, aby funkce mohla upravovat parametr.</span><span class="sxs-lookup"><span data-stu-id="d8038-132">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="d8038-133">Funkce Pure</span><span class="sxs-lookup"><span data-stu-id="d8038-133">Pure Function</span></span>  
<span data-ttu-id="d8038-134">Tato další verze programu ukazuje, jak implementovat `HyphenatedConcat` funkci jako čistě funkci.</span><span class="sxs-lookup"><span data-stu-id="d8038-134">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="d8038-135">Tato verze znovu vytvoří stejný řádek výstupu: `StringOne-StringTwo` .</span><span class="sxs-lookup"><span data-stu-id="d8038-135">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="d8038-136">Všimněte si, že pokud chcete zachovat zřetězenou hodnotu, je uložena v mezilehlé proměnné `s2` .</span><span class="sxs-lookup"><span data-stu-id="d8038-136">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="d8038-137">Jedním z přístupů, které mohou být velmi užitečné, je psaní funkcí, které jsou místně nečisté (to znamená, že deklarují a mění místní proměnné), ale jsou globálně čistě.</span><span class="sxs-lookup"><span data-stu-id="d8038-137">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="d8038-138">Tyto funkce mají mnoho z hlediska žádoucích vlastností, ale nemusíte používat rekurzi idiomy, jako je třeba použití rekurze, když by jednoduchá smyčka mohla dosáhnout stejné věci.</span><span class="sxs-lookup"><span data-stu-id="d8038-138">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="d8038-139">Standardní operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="d8038-139">Standard Query Operators</span></span>  
 <span data-ttu-id="d8038-140">Důležitou vlastností standardních operátorů dotazu je to, že jsou implementované jako čisté funkce.</span><span class="sxs-lookup"><span data-stu-id="d8038-140">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="d8038-141">Další informace najdete v tématu [Přehled standardních operátorů dotazu (C#)](./standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d8038-141">For more information, see [Standard Query Operators Overview (C#)](./standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8038-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8038-142">See also</span></span>

- [<span data-ttu-id="d8038-143">Úvod do čistě funkčních transformací (C#)</span><span class="sxs-lookup"><span data-stu-id="d8038-143">Introduction to Pure Functional Transformations (C#)</span></span>](./introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="d8038-144">Funkční programování vs. imperativní programování (C#)</span><span class="sxs-lookup"><span data-stu-id="d8038-144">Functional Programming vs. Imperative Programming (C#)</span></span>](./functional-programming-vs-imperative-programming.md)
