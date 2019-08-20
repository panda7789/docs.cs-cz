---
title: Refaktoring do čistě funkcí (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: d6e8657da0f7db06d2fdbe1231bdc48e1aa0f954
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591334"
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="a3249-102">Refaktoring do čistě funkcí (C#)</span><span class="sxs-lookup"><span data-stu-id="a3249-102">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="a3249-103">Důležitým aspektem čistě funkční transformace je učení, jak refaktorovat kód pomocí čistě funkcí.</span><span class="sxs-lookup"><span data-stu-id="a3249-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3249-104">Běžnou klasifikací při funkčním programování je, že refaktoruje programy pomocí funkce Pure.</span><span class="sxs-lookup"><span data-stu-id="a3249-104">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="a3249-105">V Visual Basic a C++se tato možnost zarovnává s použitím funkcí v odpovídajících jazycích.</span><span class="sxs-lookup"><span data-stu-id="a3249-105">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="a3249-106">V C#nástroji se však funkce nazývají metody.</span><span class="sxs-lookup"><span data-stu-id="a3249-106">However, in C#, functions are called methods.</span></span> <span data-ttu-id="a3249-107">Pro účely této diskuze je funkce Pure implementována jako metoda v C#.</span><span class="sxs-lookup"><span data-stu-id="a3249-107">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="a3249-108">Jak bylo uvedeno dříve v této části, funkce Pure má dvě užitečné charakteristiky:</span><span class="sxs-lookup"><span data-stu-id="a3249-108">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
- <span data-ttu-id="a3249-109">Nemá žádné vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="a3249-109">It has no side effects.</span></span> <span data-ttu-id="a3249-110">Funkce nemění žádné proměnné ani data žádného typu mimo funkci.</span><span class="sxs-lookup"><span data-stu-id="a3249-110">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
- <span data-ttu-id="a3249-111">Je konzistentní.</span><span class="sxs-lookup"><span data-stu-id="a3249-111">It is consistent.</span></span> <span data-ttu-id="a3249-112">V případě stejné sady vstupních dat bude vždy vracet stejnou výstupní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a3249-112">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="a3249-113">Jedním ze způsobů, jak přecházet do funkčního programování, je refaktorující existující kód, který eliminuje nepotřebné vedlejší účinky a externí závislosti.</span><span class="sxs-lookup"><span data-stu-id="a3249-113">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="a3249-114">Tímto způsobem můžete vytvářet čistě verze funkcí stávajícího kódu.</span><span class="sxs-lookup"><span data-stu-id="a3249-114">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="a3249-115">Toto téma popisuje, co je funkce Pure a co není.</span><span class="sxs-lookup"><span data-stu-id="a3249-115">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="a3249-116">Tento [kurz: Seznámení s obsahem v kurzu WordprocessingMLC#Document](./shape-of-wordprocessingml-documents.md) () ukazuje, jak manipulovat s dokumentem WordprocessingML a obsahuje dva příklady refaktorování pomocí funkce Pure.</span><span class="sxs-lookup"><span data-stu-id="a3249-116">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](./shape-of-wordprocessingml-documents.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="a3249-117">Vyloučení vedlejších efektů a externích závislostí</span><span class="sxs-lookup"><span data-stu-id="a3249-117">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="a3249-118">Následující příklady kontrastují dvě nečisté funkce a funkci Pure.</span><span class="sxs-lookup"><span data-stu-id="a3249-118">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="a3249-119">Nečistá funkce, která mění člena třídy</span><span class="sxs-lookup"><span data-stu-id="a3249-119">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="a3249-120">V následujícím kódu `HyphenatedConcat` není funkce čistě funkcí, protože `aMember` upravuje datový člen ve třídě:</span><span class="sxs-lookup"><span data-stu-id="a3249-120">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
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
  
 <span data-ttu-id="a3249-121">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a3249-121">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="a3249-122">Všimněte si, že je nedůležité, jestli data, `public` která `private` jsou měněna, mají `static` přístup nebo jsou členem nebo členem instance.</span><span class="sxs-lookup"><span data-stu-id="a3249-122">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="a3249-123">Funkce Pure nemění žádná data mimo funkci.</span><span class="sxs-lookup"><span data-stu-id="a3249-123">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="a3249-124">Nečistá funkce, která mění argument</span><span class="sxs-lookup"><span data-stu-id="a3249-124">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="a3249-125">Kromě toho následující verze této funkce není čistá, protože upravuje obsah svého parametru, `sb`.</span><span class="sxs-lookup"><span data-stu-id="a3249-125">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
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
  
 <span data-ttu-id="a3249-126">Tato verze programu vytvoří stejný výstup jako první verze, protože `HyphenatedConcat` funkce změnila hodnotu (stav) jeho prvního parametru <xref:System.Text.StringBuilder.Append%2A> vyvoláním členské funkce.</span><span class="sxs-lookup"><span data-stu-id="a3249-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="a3249-127">Všimněte si, že tato změna probíhá navzdory tomu `HyphenatedConcat` , že používá předávání parametru volání podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a3249-127">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a3249-128">Pro typy odkazů, Pokud předáte parametr podle hodnoty, výsledkem bude kopie odkazu na předaný objekt.</span><span class="sxs-lookup"><span data-stu-id="a3249-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="a3249-129">Tato kopie je stále přidružená ke stejným datům instance jako původní odkaz (dokud referenční proměnná není přiřazena k novému objektu).</span><span class="sxs-lookup"><span data-stu-id="a3249-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="a3249-130">Volání po odkazech nemusí nutně vyžadovat, aby funkce mohla upravovat parametr.</span><span class="sxs-lookup"><span data-stu-id="a3249-130">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="a3249-131">Funkce Pure</span><span class="sxs-lookup"><span data-stu-id="a3249-131">Pure Function</span></span>  
<span data-ttu-id="a3249-132">Tato další verze programu ukazuje, jak implementovat `HyphenatedConcat` funkci jako čistě funkci.</span><span class="sxs-lookup"><span data-stu-id="a3249-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="a3249-133">Tato verze znovu vytvoří stejný řádek výstupu: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="a3249-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="a3249-134">Všimněte si, že pokud chcete zachovat zřetězenou hodnotu, je uložena v mezilehlé proměnné `s2`.</span><span class="sxs-lookup"><span data-stu-id="a3249-134">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="a3249-135">Jedním z přístupů, které mohou být velmi užitečné, je psaní funkcí, které jsou místně nečisté (to znamená, že deklarují a mění místní proměnné), ale jsou globálně čistě.</span><span class="sxs-lookup"><span data-stu-id="a3249-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="a3249-136">Tyto funkce mají mnoho z hlediska žádoucích vlastností, ale nemusíte používat rekurzi idiomy, jako je třeba použití rekurze, když by jednoduchá smyčka mohla dosáhnout stejné věci.</span><span class="sxs-lookup"><span data-stu-id="a3249-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="a3249-137">Standardní operátory dotazu</span><span class="sxs-lookup"><span data-stu-id="a3249-137">Standard Query Operators</span></span>  
 <span data-ttu-id="a3249-138">Důležitou vlastností standardních operátorů dotazu je to, že jsou implementované jako čisté funkce.</span><span class="sxs-lookup"><span data-stu-id="a3249-138">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="a3249-139">Další informace najdete v tématu [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a3249-139">For more information, see [Standard Query Operators Overview (C#)](./standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3249-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3249-140">See also</span></span>

- [<span data-ttu-id="a3249-141">Úvod do čistě funkční transformace (C#)</span><span class="sxs-lookup"><span data-stu-id="a3249-141">Introduction to Pure Functional Transformations (C#)</span></span>](./introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="a3249-142">Funkční programování vs. Imperativní programování (C#)</span><span class="sxs-lookup"><span data-stu-id="a3249-142">Functional Programming vs. Imperative Programming (C#)</span></span>](./functional-programming-vs-imperative-programming.md)
