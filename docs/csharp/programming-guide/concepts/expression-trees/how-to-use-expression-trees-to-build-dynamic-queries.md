---
title: 'Postupy: použití stromů výrazů k sestavování dynamických dotazů (C#)'
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 3ae21422576abccde51d7708007132a87bedbad6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327705"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="2ec10-102">Postupy: použití stromů výrazů k sestavování dynamických dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="2ec10-102">How to: Use Expression Trees to Build Dynamic Queries (C#)</span></span>
<span data-ttu-id="2ec10-103">V technologii LINQ, stromy výrazů se používají k vyjádření strukturovaných dotazů, které cílí zdroje dat, které implementují <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="2ec10-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="2ec10-104">Například implementuje poskytovatele LINQ <xref:System.Linq.IQueryable%601> rozhraní pro dotazování relační datové úložiště.</span><span class="sxs-lookup"><span data-stu-id="2ec10-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="2ec10-105">Kompilátor jazyka C# zkompiluje dotazy, které cílí na tyto zdroje dat do kódu, který sestaví strom výrazu za běhu.</span><span class="sxs-lookup"><span data-stu-id="2ec10-105">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="2ec10-106">Dotaz na zprostředkovatele můžete procházet stromové struktury dat. výraz a přeloží ji do dotazovací jazyk, který je vhodný pro zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="2ec10-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="2ec10-107">Stromy výrazů se také používají v technologii LINQ k vyjádření výrazy lambda, které jsou přiřazeny k proměnné typu <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="2ec10-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="2ec10-108">Toto téma popisuje postup použití stromů výrazů k vytvoření dynamických dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="2ec10-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="2ec10-109">Dynamické dotazy jsou užitečné, když jsou specifikace dotazu nejsou známá v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="2ec10-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="2ec10-110">Aplikace může například zadat uživatelské rozhraní, která umožňuje koncovému uživateli umožňují určit jeden nebo více predikáty filtrovat data.</span><span class="sxs-lookup"><span data-stu-id="2ec10-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="2ec10-111">Tento druh aplikace pomocí LINQ pro dotazování, musíte použít stromů výrazů k vytvoření dotazu LINQ za běhu.</span><span class="sxs-lookup"><span data-stu-id="2ec10-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ec10-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ec10-112">Example</span></span>  
 <span data-ttu-id="2ec10-113">Následující příklad ukazuje, jak vytvořit dotazy na použití stromů výrazů `IQueryable` zdroje dat a pak ho provést.</span><span class="sxs-lookup"><span data-stu-id="2ec10-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="2ec10-114">Kód vytvoří strom výrazu představují následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="2ec10-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 <span data-ttu-id="2ec10-115">Metody vytváření v <xref:System.Linq.Expressions> obor názvů se používají k vytváření stromů výrazů, které představují výrazy, které tvoří celkové dotazu.</span><span class="sxs-lookup"><span data-stu-id="2ec10-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="2ec10-116">Výrazy, které představují volání metody operátor standardní dotazů odkazovat na <xref:System.Linq.Queryable> implementace z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="2ec10-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="2ec10-117">Předaný stromu výsledný výraz <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementace zprostředkovatele `IQueryable` zdroj dat pro vytvoření spustitelného souboru dotazu typu `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="2ec10-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="2ec10-118">Výsledky jsou získala při vytváření výčtu tuto proměnnou dotazu.</span><span class="sxs-lookup"><span data-stu-id="2ec10-118">The results are obtained by enumerating that query variable.</span></span>  
  
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
  
 <span data-ttu-id="2ec10-119">Tento kód používá pevný počet výrazů v predikátu, který je předán `Queryable.Where` metoda.</span><span class="sxs-lookup"><span data-stu-id="2ec10-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="2ec10-120">Nicméně můžete napsat aplikaci, která kombinuje proměnné číslo predikátem výrazů, které závisí na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="2ec10-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="2ec10-121">Také můžete měnit operátory standardní dotazu, které se nazývají v dotazu, v závislosti na vstup od uživatele.</span><span class="sxs-lookup"><span data-stu-id="2ec10-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ec10-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2ec10-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="2ec10-123">Vytvořte novou **konzolové aplikace** projektu.</span><span class="sxs-lookup"><span data-stu-id="2ec10-123">Create a new **Console Application** project.</span></span>  
  
-   <span data-ttu-id="2ec10-124">Přidáte odkaz na System.Core.dll, pokud už neodkazuje.</span><span class="sxs-lookup"><span data-stu-id="2ec10-124">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="2ec10-125">Obor názvů System.Linq.Expressions patří.</span><span class="sxs-lookup"><span data-stu-id="2ec10-125">Include the System.Linq.Expressions namespace.</span></span>  
  
-   <span data-ttu-id="2ec10-126">Zkopírujte kód z příkladu a vložte ji do `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="2ec10-126">Copy the code from the example and paste it into the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec10-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ec10-127">See Also</span></span>  
 [<span data-ttu-id="2ec10-128">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="2ec10-128">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="2ec10-129">Postupy: provádění stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="2ec10-129">How to: Execute Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [<span data-ttu-id="2ec10-130">Postupy: dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="2ec10-130">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
