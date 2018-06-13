---
title: 'Postupy: použití stromů výrazů k sestavování dynamických dotazů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: a2101598a083f8d0738cb531ebbaea0f7a87a577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643369"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="7455b-102">Postupy: použití stromů výrazů k sestavování dynamických dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7455b-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>
<span data-ttu-id="7455b-103">V technologii LINQ, stromy výrazů se používají k vyjádření strukturovaných dotazů, které cílí zdroje dat, které implementují <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="7455b-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="7455b-104">Například implementuje poskytovatele LINQ <xref:System.Linq.IQueryable%601> rozhraní pro dotazování relační datové úložiště.</span><span class="sxs-lookup"><span data-stu-id="7455b-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="7455b-105">Visual Basic – kompilátor zkompiluje dotazy, které cílí na tyto zdroje dat do kódu, který sestaví strom výrazu za běhu.</span><span class="sxs-lookup"><span data-stu-id="7455b-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="7455b-106">Dotaz na zprostředkovatele můžete procházet stromové struktury dat. výraz a přeloží ji do dotazovací jazyk, který je vhodný pro zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="7455b-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="7455b-107">Stromy výrazů se také používají v technologii LINQ k vyjádření výrazy lambda, které jsou přiřazeny k proměnné typu <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="7455b-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="7455b-108">Toto téma popisuje postup použití stromů výrazů k vytvoření dynamických dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="7455b-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="7455b-109">Dynamické dotazy jsou užitečné, když jsou specifikace dotazu nejsou známá v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="7455b-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="7455b-110">Aplikace může například zadat uživatelské rozhraní, která umožňuje koncovému uživateli umožňují určit jeden nebo více predikáty filtrovat data.</span><span class="sxs-lookup"><span data-stu-id="7455b-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="7455b-111">Tento druh aplikace pomocí LINQ pro dotazování, musíte použít stromů výrazů k vytvoření dotazu LINQ za běhu.</span><span class="sxs-lookup"><span data-stu-id="7455b-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7455b-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="7455b-112">Example</span></span>  
 <span data-ttu-id="7455b-113">Následující příklad ukazuje, jak vytvořit dotazy na použití stromů výrazů `IQueryable` zdroje dat a pak ho provést.</span><span class="sxs-lookup"><span data-stu-id="7455b-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="7455b-114">Kód vytvoří strom výrazu představují následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="7455b-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 <span data-ttu-id="7455b-115">Metody vytváření v <xref:System.Linq.Expressions> obor názvů se používají k vytváření stromů výrazů, které představují výrazy, které tvoří celkové dotazu.</span><span class="sxs-lookup"><span data-stu-id="7455b-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="7455b-116">Výrazy, které představují volání metody operátor standardní dotazů odkazovat na <xref:System.Linq.Queryable> implementace z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="7455b-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="7455b-117">Předaný stromu výsledný výraz <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementace zprostředkovatele `IQueryable` zdroj dat pro vytvoření spustitelného souboru dotazu typu `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="7455b-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="7455b-118">Výsledky jsou získala při vytváření výčtu tuto proměnnou dotazu.</span><span class="sxs-lookup"><span data-stu-id="7455b-118">The results are obtained by enumerating that query variable.</span></span>  
  
```vb  
' Add an Imports statement for System.Linq.Expressions.  
  
Dim companies =   
    {"Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",   
     "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",   
     "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",   
     "Blue Yonder Airlines", "Trey Research", "The Phone Company",   
     "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee"}  
  
' The IQueryable data to query.  
Dim queryableData As IQueryable(Of String) = companies.AsQueryable()  
  
' Compose the expression tree that represents the parameter to the predicate.  
Dim pe As ParameterExpression = Expression.Parameter(GetType(String), "company")  
  
' ***** Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16) *****  
' Create an expression tree that represents the expression: company.ToLower() = "coho winery".  
Dim left As Expression = Expression.Call(pe, GetType(String).GetMethod("ToLower", System.Type.EmptyTypes))  
Dim right As Expression = Expression.Constant("coho winery")  
Dim e1 As Expression = Expression.Equal(left, right)  
  
' Create an expression tree that represents the expression: company.Length > 16.  
left = Expression.Property(pe, GetType(String).GetProperty("Length"))  
right = Expression.Constant(16, GetType(Integer))  
Dim e2 As Expression = Expression.GreaterThan(left, right)  
  
' Combine the expressions to create an expression tree that represents the  
' expression: company.ToLower() = "coho winery" OrElse company.Length > 16).  
Dim predicateBody As Expression = Expression.OrElse(e1, e2)  
  
' Create an expression tree that represents the expression:  
' queryableData.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16)  
Dim whereCallExpression As MethodCallExpression = Expression.Call(   
        GetType(Queryable),   
        "Where",   
        New Type() {queryableData.ElementType},   
        queryableData.Expression,   
        Expression.Lambda(Of Func(Of String, Boolean))(predicateBody, New ParameterExpression() {pe}))  
' ***** End Where *****  
  
' ***** OrderBy(Function(company) company) *****  
' Create an expression tree that represents the expression:  
' whereCallExpression.OrderBy(Function(company) company)  
Dim orderByCallExpression As MethodCallExpression = Expression.Call(   
        GetType(Queryable),   
        "OrderBy",   
        New Type() {queryableData.ElementType, queryableData.ElementType},   
        whereCallExpression,   
        Expression.Lambda(Of Func(Of String, String))(pe, New ParameterExpression() {pe}))  
' ***** End OrderBy *****  
  
' Create an executable query from the expression tree.  
Dim results As IQueryable(Of String) = queryableData.Provider.CreateQuery(Of String)(orderByCallExpression)  
  
' Enumerate the results.  
For Each company As String In results  
    Console.WriteLine(company)  
Next  
  
' This code produces the following output:  
'  
' Blue Yonder Airlines  
' City Power & Light  
' Coho Winery  
' Consolidated Messenger  
' Graphic Design Institute  
' Humongous Insurance  
' Lucerne Publishing  
' Northwind Traders  
' The Phone Company  
' Wide World Importers  
```  
  
 <span data-ttu-id="7455b-119">Tento kód používá pevný počet výrazů v predikátu, který je předán `Queryable.Where` metoda.</span><span class="sxs-lookup"><span data-stu-id="7455b-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="7455b-120">Nicméně můžete napsat aplikaci, která kombinuje proměnné číslo predikátem výrazů, které závisí na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="7455b-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="7455b-121">Také můžete měnit operátory standardní dotazu, které se nazývají v dotazu, v závislosti na vstup od uživatele.</span><span class="sxs-lookup"><span data-stu-id="7455b-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7455b-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7455b-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="7455b-123">Vytvořte novou **konzolové aplikace** projektu.</span><span class="sxs-lookup"><span data-stu-id="7455b-123">Create a new **Console Application** project.</span></span>  
  
-   <span data-ttu-id="7455b-124">Přidáte odkaz na System.Core.dll, pokud už neodkazuje.</span><span class="sxs-lookup"><span data-stu-id="7455b-124">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="7455b-125">Obor názvů System.Linq.Expressions patří.</span><span class="sxs-lookup"><span data-stu-id="7455b-125">Include the System.Linq.Expressions namespace.</span></span>  
  
-   <span data-ttu-id="7455b-126">Zkopírujte kód z příkladu a vložte ji do `Main` `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="7455b-126">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7455b-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="7455b-127">See Also</span></span>  
 [<span data-ttu-id="7455b-128">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7455b-128">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="7455b-129">Postupy: provádění stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7455b-129">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
