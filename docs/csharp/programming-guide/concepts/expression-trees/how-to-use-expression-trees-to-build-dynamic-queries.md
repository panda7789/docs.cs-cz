---
title: Použití stromů výrazů k sestavování dynamických dotazů (C#)
description: Naučte se používat stromy výrazů k vytváření dynamických dotazů LINQ. Tyto dotazy jsou užitečné v případě, že konkrétní dotazy nejsou v době kompilace známy.
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: edcef4068c19ba8e789683cf6ba4d5ef2477e0d8
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105593"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="4fd2b-104">Použití stromů výrazů k sestavování dynamických dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="4fd2b-104">How to use expression trees to build dynamic queries (C#)</span></span>
<span data-ttu-id="4fd2b-105">V technologii LINQ se stromy výrazů používají k reprezentování strukturovaných dotazů, které cílí na zdroje dat, která implementují <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="4fd2b-105">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="4fd2b-106">Například poskytovatel LINQ implementuje <xref:System.Linq.IQueryable%601> rozhraní pro dotazování relačních úložišť dat.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-106">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="4fd2b-107">Kompilátor jazyka C# zkompiluje dotazy, které cílí na takové zdroje dat, do kódu, který vytvoří strom výrazu za běhu.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-107">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="4fd2b-108">Poskytovatel dotazu pak může procházet strukturu dat stromu výrazů a překládat ji do dotazovacího jazyka vhodného pro zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-108">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="4fd2b-109">Stromy výrazů jsou také používány v LINQ k reprezentování výrazů lambda, které jsou přiřazeny proměnným typu <xref:System.Linq.Expressions.Expression%601> .</span><span class="sxs-lookup"><span data-stu-id="4fd2b-109">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="4fd2b-110">Toto téma popisuje použití stromů výrazů k vytváření dynamických dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-110">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="4fd2b-111">Dynamické dotazy jsou užitečné v případě, že specifické výrazy dotazu nejsou známy v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-111">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="4fd2b-112">Například aplikace může poskytovat uživatelské rozhraní, které umožňuje koncovému uživateli určit jeden nebo více predikátů pro filtrování dat.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-112">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="4fd2b-113">Aby bylo možné používat LINQ pro dotazování, tento druh aplikace musí pomocí stromů výrazů vytvořit dotaz LINQ za běhu.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-113">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fd2b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fd2b-114">Example</span></span>  
 <span data-ttu-id="4fd2b-115">Následující příklad ukazuje, jak použít stromy výrazů k vytvoření dotazu na `IQueryable` zdroj dat a jeho následné spuštění.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-115">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="4fd2b-116">Kód vytvoří strom výrazu pro reprezentaci následujícího dotazu:</span><span class="sxs-lookup"><span data-stu-id="4fd2b-116">The code builds an expression tree to represent the following query:</span></span>  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 <span data-ttu-id="4fd2b-117">Metody továrny v <xref:System.Linq.Expressions> oboru názvů slouží k vytváření stromů výrazů, které představují výrazy, které tvoří celkový dotaz.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-117">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="4fd2b-118">Výrazy, které reprezentují volání standardních metod operátoru dotazu, odkazují na <xref:System.Linq.Queryable> implementace těchto metod.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-118">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="4fd2b-119">Konečný strom výrazu je předán <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementaci poskytovatele `IQueryable` zdroje dat pro vytvoření spustitelného dotazu typu `IQueryable` .</span><span class="sxs-lookup"><span data-stu-id="4fd2b-119">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="4fd2b-120">Výsledky jsou získány vytvořením výčtu proměnné dotazu.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-120">The results are obtained by enumerating that query variable.</span></span>  
  
```csharp  
// Add a using directive for System.Linq.Expressions.  
  
string[] companies = { "Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",  
                   "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",  
                   "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",  
                   "Blue Yonder Airlines", "Trey Research", "The Phone Company",  
                   "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee" };  
  
// The IQueryable data to query.  
IQueryable<String> queryableData = companies.AsQueryable<string>();  
  
// Compose the expression tree that represents the parameter to the predicate.  
ParameterExpression pe = Expression.Parameter(typeof(string), "company");  
  
// ***** Where(company => (company.ToLower() == "coho winery" || company.Length > 16)) *****  
// Create an expression tree that represents the expression 'company.ToLower() == "coho winery"'.  
Expression left = Expression.Call(pe, typeof(string).GetMethod("ToLower", System.Type.EmptyTypes));  
Expression right = Expression.Constant("coho winery");  
Expression e1 = Expression.Equal(left, right);  
  
// Create an expression tree that represents the expression 'company.Length > 16'.  
left = Expression.Property(pe, typeof(string).GetProperty("Length"));  
right = Expression.Constant(16, typeof(int));  
Expression e2 = Expression.GreaterThan(left, right);  
  
// Combine the expression trees to create an expression tree that represents the  
// expression '(company.ToLower() == "coho winery" || company.Length > 16)'.  
Expression predicateBody = Expression.OrElse(e1, e2);  
  
// Create an expression tree that represents the expression  
// 'queryableData.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))'  
MethodCallExpression whereCallExpression = Expression.Call(  
    typeof(Queryable),  
    "Where",  
    new Type[] { queryableData.ElementType },  
    queryableData.Expression,  
    Expression.Lambda<Func<string, bool>>(predicateBody, new ParameterExpression[] { pe }));  
// ***** End Where *****  
  
// ***** OrderBy(company => company) *****  
// Create an expression tree that represents the expression  
// 'whereCallExpression.OrderBy(company => company)'  
MethodCallExpression orderByCallExpression = Expression.Call(  
    typeof(Queryable),  
    "OrderBy",  
    new Type[] { queryableData.ElementType, queryableData.ElementType },  
    whereCallExpression,  
    Expression.Lambda<Func<string, string>>(pe, new ParameterExpression[] { pe }));  
// ***** End OrderBy *****  
  
// Create an executable query from the expression tree.  
IQueryable<string> results = queryableData.Provider.CreateQuery<string>(orderByCallExpression);  
  
// Enumerate the results.  
foreach (string company in results)  
    Console.WriteLine(company);  
  
/*  This code produces the following output:  
  
    Blue Yonder Airlines  
    City Power & Light  
    Coho Winery  
    Consolidated Messenger  
    Graphic Design Institute  
    Humongous Insurance  
    Lucerne Publishing  
    Northwind Traders  
    The Phone Company  
    Wide World Importers  
*/  
```  
  
 <span data-ttu-id="4fd2b-121">Tento kód používá pevný počet výrazů v predikátu, který je předán `Queryable.Where` metodě.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-121">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="4fd2b-122">Můžete však napsat aplikaci, která kombinuje proměnlivý počet výrazů predikátů, který závisí na vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-122">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="4fd2b-123">V závislosti na vstupu od uživatele můžete také měnit standardní operátory dotazů, které jsou v dotazu volány.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-123">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4fd2b-124">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4fd2b-124">Compiling the Code</span></span>  
  
- <span data-ttu-id="4fd2b-125">Zahrňte obor názvů System. Linq. Expressions.</span><span class="sxs-lookup"><span data-stu-id="4fd2b-125">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd2b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fd2b-126">See also</span></span>

- [<span data-ttu-id="4fd2b-127">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="4fd2b-127">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="4fd2b-128">Spuštění stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="4fd2b-128">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="4fd2b-129">Dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="4fd2b-129">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
