---
title: =&gt; – Operátor (referenční dokumentace jazyka C#)
ms.date: 10/02/2017
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: b9216cf61b6b9368112f769d952457df4aab4297
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43670766"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="fb6ad-102">=&gt; – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="fb6ad-102">=&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="fb6ad-103">`=>` Dvě možnosti, jak v jazyce C# lze použít operátor:</span><span class="sxs-lookup"><span data-stu-id="fb6ad-103">The `=>` operator can be used in two ways in C#:</span></span>

- <span data-ttu-id="fb6ad-104">Jako [operátor lambda](#lamba-operator) v [výraz lambda](../../lambda-expressions.md), rozděluje vstupní proměnné z hlavní část výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-104">As the [lambda operator](#lamba-operator) in a [lambda expression](../../lambda-expressions.md), it separates the input variables from the lambda body.</span></span>
 
- <span data-ttu-id="fb6ad-105">V [definice těla výrazu](#expression-body-definition), název člena ho odděluje od implementace členu.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-105">In an [expression body definition](#expression-body-definition), it separates a member name from the member implementation.</span></span> 

## <a name="lambda-operator"></a><span data-ttu-id="fb6ad-106">Lambda – operátor</span><span class="sxs-lookup"><span data-stu-id="fb6ad-106">Lambda operator</span></span>

<span data-ttu-id="fb6ad-107">`=>` Token se nazývá operátor lambda.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-107">The `=>` token is called the lambda operator.</span></span> <span data-ttu-id="fb6ad-108">Používá se v *výrazy lambda* oddělení vstupních proměnných na levé straně od hlavní část výrazu lambda na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-108">It is used in *lambda expressions* to separate the input variables on the left side from the lambda body on the right side.</span></span> <span data-ttu-id="fb6ad-109">Výrazy lambda jsou vložené výrazy podobné anonymní metody, ale flexibilnější; často se používají v dotazech LINQ, které jsou vyjádřeny syntaxe využívající metody.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-109">Lambda expressions are inline expressions similar to anonymous methods but more flexible; they are used extensively in LINQ queries that are expressed in method syntax.</span></span> <span data-ttu-id="fb6ad-110">Další informace najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="fb6ad-110">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="fb6ad-111">Následující příklad ukazuje dva způsoby, jak vyhledat a zobrazit délku nejkratší řetězce v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-111">The following example shows two ways to find and display the length of the shortest string in an array of strings.</span></span> <span data-ttu-id="fb6ad-112">První část v příkladu platí výrazu lambda (`w => w.Length`) ke každému prvku objektu `words` pole a pak použije <xref:System.Linq.Enumerable.Min%2A> metody k vyhledání minimální délku.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-112">The first part of the example applies a lambda expression (`w => w.Length`) to each element of the `words` array and then uses the <xref:System.Linq.Enumerable.Min%2A> method to find the smallest length.</span></span> <span data-ttu-id="fb6ad-113">Pro porovnání druhá část tento příklad ukazuje delší dobu řešení, které používá syntaxi dotazu pro stejnou věc udělat.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-113">For comparison, the second part of the example shows a longer solution that uses query syntax to do the same thing.</span></span>  
  
```csharp  
string[] words = { "cherry", "apple", "blueberry" };  
  
// Use method syntax to apply a lambda expression to each element  
// of the words array.   
int shortestWordLength = words.Min(w => w.Length);  
Console.WriteLine(shortestWordLength);  
  
// Compare the following code that uses query syntax.  
// Get the lengths of each word in the words array.  
var query = from w in words  
            select w.Length;  
// Apply the Min method to execute the query and get the shortest length.  
int shortestWordLength2 = query.Min();  
Console.WriteLine(shortestWordLength2);  
  
// Output:   
// 5  
// 5  
```  
  
### <a name="remarks"></a><span data-ttu-id="fb6ad-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb6ad-114">Remarks</span></span>  
 <span data-ttu-id="fb6ad-115">`=>` Operátor má stejnou prioritu jako operátor přiřazení (`=`) a je asociativní zprava.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-115">The `=>` operator has the same precedence as the assignment operator (`=`) and is right-associative.</span></span>  
  
 <span data-ttu-id="fb6ad-116">Můžete explicitně zadat typ je vstupní proměnná nebo umožnili kompilátoru odvodit. v obou případech je proměnná silného typu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-116">You can specify the type of the input variable explicitly or let the compiler infer it; in either case, the variable is strongly typed at compile time.</span></span> <span data-ttu-id="fb6ad-117">Při zadávání typu musíte uvést název typu a název proměnné v závorkách, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-117">When you specify a type, you must enclose the type name and the variable name in parentheses, as the following example shows.</span></span>  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a><span data-ttu-id="fb6ad-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb6ad-118">Example</span></span>  
 <span data-ttu-id="fb6ad-119">Následující příklad ukazuje, jak zapsat lambda výraz pro přetížení operátoru standardního dotazu <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> , který přebírá dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-119">The following example shows how to write a lambda expression for the overload of the standard query operator <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> that takes two arguments.</span></span> <span data-ttu-id="fb6ad-120">Vzhledem k tomu, že výraz lambda má více než jeden parametr, parametry musí být uzavřen v závorkách.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-120">Because the lambda expression has more than one parameter, the parameters must be enclosed in parentheses.</span></span> <span data-ttu-id="fb6ad-121">Druhý parametr `index`, představuje index aktuálního prvku kolekce.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-121">The second parameter, `index`, represents the index of the current element in the collection.</span></span> <span data-ttu-id="fb6ad-122">`Where` Výraz vrátí všechny řetězce, jejichž délky mají hodnotu menší než index pozice v poli.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-122">The `Where` expression returns all the strings whose lengths are less than their index positions in the array.</span></span>  
  
```csharp  
static void Main(string[] args)  
{  
    string[] digits = { "zero", "one", "two", "three", "four", "five",   
            "six", "seven", "eight", "nine" };  
  
    Console.WriteLine("Example that uses a lambda expression:");  
    var shortDigits = digits.Where((digit, index) => digit.Length < index);  
    foreach (var sD in shortDigits)  
    {  
        Console.WriteLine(sD);  
    }  
  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
## <a name="expression-body-definition"></a><span data-ttu-id="fb6ad-123">Definice textu výrazu</span><span class="sxs-lookup"><span data-stu-id="fb6ad-123">Expression body definition</span></span>

<span data-ttu-id="fb6ad-124">Definice těla výrazu obsahuje implementace člena ve vysoce zhuštěnému čitelné formy.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-124">An expression body definition provides a member's implementation in a highly condensed, readable form.</span></span> <span data-ttu-id="fb6ad-125">Má následující obecnou syntaxi:</span><span class="sxs-lookup"><span data-stu-id="fb6ad-125">It has the following general syntax:</span></span>

```csharp
member => expression;
```
<span data-ttu-id="fb6ad-126">kde *výraz* je platný výraz.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-126">where *expression* is a valid expression.</span></span> <span data-ttu-id="fb6ad-127">Všimněte si, že *výraz* může být *výrazu příkazu* pouze pokud je člen návratový typ je `void`, nebo pokud je člen konstruktoru nebo finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-127">Note that *expression* can be a *statement expression* only if the member's return type is `void`, or if the member is a constructor or a finalizer.</span></span>

<span data-ttu-id="fb6ad-128">Definice textu výrazu pro metody a vlastnosti get příkazy jsou podporovány od verze C# 6.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-128">Expression body definitions for methods and property get statements are supported starting with C# 6.</span></span> <span data-ttu-id="fb6ad-129">Definice těla výrazu pro konstruktory, finalizační metody, nastavte vlastnost příkazy a indexery jsou podporovány od verze C# 7.</span><span class="sxs-lookup"><span data-stu-id="fb6ad-129">Expression body definitions for constructors, finalizers, property set statements, and indexers are supported starting with C# 7.</span></span>

<span data-ttu-id="fb6ad-130">Tady je definice těla výrazu pro `Person.ToString` metody:</span><span class="sxs-lookup"><span data-stu-id="fb6ad-130">The following is an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="fb6ad-131">Je zkrácená verze následující definici metody:</span><span class="sxs-lookup"><span data-stu-id="fb6ad-131">It is a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
<span data-ttu-id="fb6ad-132">Podrobnější informace o definicích tělo výrazu, najdete v článku [členové tvoření](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="fb6ad-132">For more detailed information on expression body definitions, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb6ad-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb6ad-133">See Also</span></span>

- [<span data-ttu-id="fb6ad-134">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fb6ad-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)   
- [<span data-ttu-id="fb6ad-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fb6ad-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)   
- [<span data-ttu-id="fb6ad-136">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="fb6ad-136">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
- <span data-ttu-id="fb6ad-137">[Členové tvoření](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="fb6ad-137">[Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>