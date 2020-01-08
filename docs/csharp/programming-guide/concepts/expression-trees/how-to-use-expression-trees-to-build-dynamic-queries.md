---
title: Použití stromů výrazů k sestavování dynamických dotazů (C#)
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 6114ec13dd43a7df146b87dda00fba06d6eb870c
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635896"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a><span data-ttu-id="44b78-102">Použití stromů výrazů k sestavování dynamických dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="44b78-102">How to use expression trees to build dynamic queries (C#)</span></span>
<span data-ttu-id="44b78-103">V technologii LINQ se stromy výrazů používají k reprezentování strukturovaných dotazů, které cílí na zdroje dat, které implementují <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="44b78-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="44b78-104">Zprostředkovatel LINQ například implementuje rozhraní <xref:System.Linq.IQueryable%601> pro dotazování na relačních úložištích dat.</span><span class="sxs-lookup"><span data-stu-id="44b78-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="44b78-105">C# Kompilátor zkompiluje dotazy, které cílí na takové zdroje dat, do kódu, který vytvoří strom výrazu za běhu.</span><span class="sxs-lookup"><span data-stu-id="44b78-105">The C# compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="44b78-106">Poskytovatel dotazu pak může procházet strukturu dat stromu výrazů a překládat ji do dotazovacího jazyka vhodného pro zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="44b78-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="44b78-107">Stromy výrazů jsou také používány v LINQ k reprezentování výrazů lambda, které jsou přiřazeny proměnným typu <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="44b78-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="44b78-108">Toto téma popisuje použití stromů výrazů k vytváření dynamických dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="44b78-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="44b78-109">Dynamické dotazy jsou užitečné v případě, že specifické výrazy dotazu nejsou známy v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="44b78-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="44b78-110">Například aplikace může poskytovat uživatelské rozhraní, které umožňuje koncovému uživateli určit jeden nebo více predikátů pro filtrování dat.</span><span class="sxs-lookup"><span data-stu-id="44b78-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="44b78-111">Aby bylo možné používat LINQ pro dotazování, tento druh aplikace musí pomocí stromů výrazů vytvořit dotaz LINQ za běhu.</span><span class="sxs-lookup"><span data-stu-id="44b78-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44b78-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="44b78-112">Example</span></span>  
 <span data-ttu-id="44b78-113">Následující příklad ukazuje, jak pomocí stromů výrazů sestavit dotaz na zdroj dat `IQueryable` a pak ho spustit.</span><span class="sxs-lookup"><span data-stu-id="44b78-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="44b78-114">Kód vytvoří strom výrazu pro reprezentaci následujícího dotazu:</span><span class="sxs-lookup"><span data-stu-id="44b78-114">The code builds an expression tree to represent the following query:</span></span>  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 <span data-ttu-id="44b78-115">Metody továrny v oboru názvů <xref:System.Linq.Expressions> slouží k vytváření stromů výrazů, které představují výrazy, které tvoří celkový dotaz.</span><span class="sxs-lookup"><span data-stu-id="44b78-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="44b78-116">Výrazy, které reprezentují volání standardních metod operátoru dotazu, odkazují na <xref:System.Linq.Queryable> implementace těchto metod.</span><span class="sxs-lookup"><span data-stu-id="44b78-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="44b78-117">Konečný strom výrazu je předán <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementaci zprostředkovatele `IQueryable` zdroje dat, aby bylo možné vytvořit spustitelný dotaz typu `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="44b78-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="44b78-118">Výsledky jsou získány vytvořením výčtu proměnné dotazu.</span><span class="sxs-lookup"><span data-stu-id="44b78-118">The results are obtained by enumerating that query variable.</span></span>  
  
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
  
 <span data-ttu-id="44b78-119">Tento kód používá pevný počet výrazů v predikátu, který je předán metodě `Queryable.Where`.</span><span class="sxs-lookup"><span data-stu-id="44b78-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="44b78-120">Můžete však napsat aplikaci, která kombinuje proměnlivý počet výrazů predikátů, který závisí na vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="44b78-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="44b78-121">V závislosti na vstupu od uživatele můžete také měnit standardní operátory dotazů, které jsou v dotazu volány.</span><span class="sxs-lookup"><span data-stu-id="44b78-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="44b78-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="44b78-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="44b78-123">Zahrňte obor názvů System. Linq. Expressions.</span><span class="sxs-lookup"><span data-stu-id="44b78-123">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b78-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44b78-124">See also</span></span>

- [<span data-ttu-id="44b78-125">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="44b78-125">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="44b78-126">Spuštění stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="44b78-126">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="44b78-127">Dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="44b78-127">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
