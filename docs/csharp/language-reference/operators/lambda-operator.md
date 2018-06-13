---
title: =&gt; Operátor (referenční dokumentace jazyka C#)
ms.date: 10/02/2017
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: d1565e262fbd3ebcee2d1576a2a0c8ed3ba8ce38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288223"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="b2eab-102">=&gt; Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b2eab-102">=&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="b2eab-103">`=>` Operátor lze použít dvěma způsoby v jazyce C#:</span><span class="sxs-lookup"><span data-stu-id="b2eab-103">The `=>` operator can be used in two ways in C#:</span></span>

- <span data-ttu-id="b2eab-104">Jako [lambda operátor](#lamba-operator) v [výrazu lambda](../../lambda-expressions.md), ji odděluje vstupní proměnné z textu lambda.</span><span class="sxs-lookup"><span data-stu-id="b2eab-104">As the [lambda operator](#lamba-operator) in a [lambda expression](../../lambda-expressions.md), it separates the input variables from the lambda body.</span></span>
 
- <span data-ttu-id="b2eab-105">V [výraz text definice](#expression-body-definition), ji odděluje název člena z implementace člen.</span><span class="sxs-lookup"><span data-stu-id="b2eab-105">In an [expression body definition](#expression-body-definition), it separates a member name from the member implementation.</span></span> 

## <a name="lambda-operator"></a><span data-ttu-id="b2eab-106">Lambda – operátor</span><span class="sxs-lookup"><span data-stu-id="b2eab-106">Lambda operator</span></span>

<span data-ttu-id="b2eab-107">`=>` Token se označuje jako operátor lambda.</span><span class="sxs-lookup"><span data-stu-id="b2eab-107">The `=>` token is called the lambda operator.</span></span> <span data-ttu-id="b2eab-108">Používá se v *výrazy lambda* oddělit vstupní proměnné na levé straně z textu lambda na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="b2eab-108">It is used in *lambda expressions* to separate the input variables on the left side from the lambda body on the right side.</span></span> <span data-ttu-id="b2eab-109">Lambda – výrazy jsou podobná anonymní metody ale flexibilnější; vložené výrazy používají se hojně v dotazech LINQ, které jsou vyjádřeny v syntaxe využívající metody.</span><span class="sxs-lookup"><span data-stu-id="b2eab-109">Lambda expressions are inline expressions similar to anonymous methods but more flexible; they are used extensively in LINQ queries that are expressed in method syntax.</span></span> <span data-ttu-id="b2eab-110">Další informace najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b2eab-110">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="b2eab-111">Následující příklad ukazuje dva způsoby, jak vyhledat a zobrazit délky řetězce nejkratší v poli řetězců.</span><span class="sxs-lookup"><span data-stu-id="b2eab-111">The following example shows two ways to find and display the length of the shortest string in an array of strings.</span></span> <span data-ttu-id="b2eab-112">První část příkladu platí výrazu lambda (`w => w.Length`) pro každý element `words` pole a pak používá <xref:System.Linq.Enumerable.Min%2A> metody k vyhledání nejmenší délka.</span><span class="sxs-lookup"><span data-stu-id="b2eab-112">The first part of the example applies a lambda expression (`w => w.Length`) to each element of the `words` array and then uses the <xref:System.Linq.Enumerable.Min%2A> method to find the smallest length.</span></span> <span data-ttu-id="b2eab-113">Pro porovnání druhou částí příklad ukazuje delší řešení, které používá syntaxi dotazu pro stejnou věc udělat.</span><span class="sxs-lookup"><span data-stu-id="b2eab-113">For comparison, the second part of the example shows a longer solution that uses query syntax to do the same thing.</span></span>  
  
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
  
### <a name="remarks"></a><span data-ttu-id="b2eab-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2eab-114">Remarks</span></span>  
 <span data-ttu-id="b2eab-115">`=>` Operátor má stejnou prioritu jako operátor přiřazení (`=`) a je zprava asociativní.</span><span class="sxs-lookup"><span data-stu-id="b2eab-115">The `=>` operator has the same precedence as the assignment operator (`=`) and is right-associative.</span></span>  
  
 <span data-ttu-id="b2eab-116">Můžete zadat typ vstupní proměnné explicitně nebo to kompilátoru odvození. v obou případech je proměnná silného typu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="b2eab-116">You can specify the type of the input variable explicitly or let the compiler infer it; in either case, the variable is strongly typed at compile time.</span></span> <span data-ttu-id="b2eab-117">Když zadáte typu, je nutné uzavřít název typu a název proměnné v závorkách, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="b2eab-117">When you specify a type, you must enclose the type name and the variable name in parentheses, as the following example shows.</span></span>  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a><span data-ttu-id="b2eab-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2eab-118">Example</span></span>  
 <span data-ttu-id="b2eab-119">Následující příklad ukazuje, jak napsat výrazu lambda pro přetížení operátoru standardní dotazu <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> , která má dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="b2eab-119">The following example shows how to write a lambda expression for the overload of the standard query operator <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> that takes two arguments.</span></span> <span data-ttu-id="b2eab-120">Protože výrazu lambda má více než jeden parametr, parametry musí být uzavřena v závorkách.</span><span class="sxs-lookup"><span data-stu-id="b2eab-120">Because the lambda expression has more than one parameter, the parameters must be enclosed in parentheses.</span></span> <span data-ttu-id="b2eab-121">Druhý parametr `index`, představuje index aktuální element v kolekci.</span><span class="sxs-lookup"><span data-stu-id="b2eab-121">The second parameter, `index`, represents the index of the current element in the collection.</span></span> <span data-ttu-id="b2eab-122">`Where` Výraz vrátí všechny řetězce, jejichž délky mají hodnotu menší než jejich pozic index v poli.</span><span class="sxs-lookup"><span data-stu-id="b2eab-122">The `Where` expression returns all the strings whose lengths are less than their index positions in the array.</span></span>  
  
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
## <a name="expression-body-definition"></a><span data-ttu-id="b2eab-123">Výraz definice textu</span><span class="sxs-lookup"><span data-stu-id="b2eab-123">Expression body definition</span></span>

<span data-ttu-id="b2eab-124">Definici textu výraz poskytuje implementaci člena ve formuláři vysoce zhuštěné a čitelné.</span><span class="sxs-lookup"><span data-stu-id="b2eab-124">An expression body definition provides a member's implementation in a highly condensed, readable form.</span></span> <span data-ttu-id="b2eab-125">Má následující obecné syntaxi:</span><span class="sxs-lookup"><span data-stu-id="b2eab-125">It has the following general syntax:</span></span>

```csharp
member => expression;
```
<span data-ttu-id="b2eab-126">kde *výraz* je platný výraz.</span><span class="sxs-lookup"><span data-stu-id="b2eab-126">where *expression* is a valid expression.</span></span> <span data-ttu-id="b2eab-127">Všimněte si, že *výraz* může být *příkaz výraz* pouze pokud je člen návratový typ je `void`, nebo pokud je člen konstruktor nebo finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="b2eab-127">Note that *expression* can be a *statement expression* only if the member's return type is `void`, or if the member is a constructor or a finalizer.</span></span>

<span data-ttu-id="b2eab-128">Výraz definice textu pro metody a vlastnosti příkazy get jsou podporované od verze jazyka C# 6.</span><span class="sxs-lookup"><span data-stu-id="b2eab-128">Expression body definitions for methods and property get statements are supported starting with C# 6.</span></span> <span data-ttu-id="b2eab-129">Výraz definice textu pro konstruktory, finalizační metody, vlastnosti nastavte příkazy a indexery jsou podporované od verze jazyka C# 7.</span><span class="sxs-lookup"><span data-stu-id="b2eab-129">Expression body definitions for constructors, finalizers, property set statements, and indexers are supported starting with C# 7.</span></span>

<span data-ttu-id="b2eab-130">Následuje definici textu výraz `Person.ToString` metoda:</span><span class="sxs-lookup"><span data-stu-id="b2eab-130">The following is an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="b2eab-131">Je sdružená verzi následující definici metody:</span><span class="sxs-lookup"><span data-stu-id="b2eab-131">It is a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
<span data-ttu-id="b2eab-132">Podrobnější informace o výraz text definice, najdete v části [výraz vozidlo členy](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="b2eab-132">For more detailed information on expression body definitions, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b2eab-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2eab-133">See Also</span></span>  
<span data-ttu-id="b2eab-134">[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b2eab-134">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="b2eab-135">[Průvodce programováním v C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b2eab-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="b2eab-136">[Lambda – výrazy](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="b2eab-136">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span></span>  
<span data-ttu-id="b2eab-137">[Výraz vozidlo členy](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="b2eab-137">[Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>