---
title: 'Postupy: Použití stromů výrazů k sestavování dynamických dotazů'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: 616aa3eba1e07a92983bb5d2048a9dbae936e77c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346056"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="59aae-102">Postupy: použití stromů výrazů k sestavování dynamických dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59aae-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>

<span data-ttu-id="59aae-103">V technologii LINQ se stromy výrazů používají k reprezentování strukturovaných dotazů, které cílí na zdroje dat, které implementují <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="59aae-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="59aae-104">Zprostředkovatel LINQ například implementuje rozhraní <xref:System.Linq.IQueryable%601> pro dotazování na relačních úložištích dat.</span><span class="sxs-lookup"><span data-stu-id="59aae-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="59aae-105">Kompilátor Visual Basic zkompiluje dotazy, které cílí na takové zdroje dat, do kódu, který vytvoří strom výrazu za běhu.</span><span class="sxs-lookup"><span data-stu-id="59aae-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="59aae-106">Poskytovatel dotazu pak může procházet strukturu dat stromu výrazů a překládat ji do dotazovacího jazyka vhodného pro zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="59aae-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>

<span data-ttu-id="59aae-107">Stromy výrazů jsou také používány v LINQ k reprezentování výrazů lambda, které jsou přiřazeny proměnným typu <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="59aae-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>

<span data-ttu-id="59aae-108">Toto téma popisuje použití stromů výrazů k vytváření dynamických dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="59aae-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="59aae-109">Dynamické dotazy jsou užitečné v případě, že specifické výrazy dotazu nejsou známy v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="59aae-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="59aae-110">Například aplikace může poskytovat uživatelské rozhraní, které umožňuje koncovému uživateli určit jeden nebo více predikátů pro filtrování dat.</span><span class="sxs-lookup"><span data-stu-id="59aae-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="59aae-111">Aby bylo možné používat LINQ pro dotazování, tento druh aplikace musí pomocí stromů výrazů vytvořit dotaz LINQ za běhu.</span><span class="sxs-lookup"><span data-stu-id="59aae-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>

## <a name="example"></a><span data-ttu-id="59aae-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="59aae-112">Example</span></span>

<span data-ttu-id="59aae-113">Následující příklad ukazuje, jak pomocí stromů výrazů sestavit dotaz na zdroj dat `IQueryable` a pak ho spustit.</span><span class="sxs-lookup"><span data-stu-id="59aae-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="59aae-114">Kód vytvoří strom výrazu pro reprezentaci následujícího dotazu:</span><span class="sxs-lookup"><span data-stu-id="59aae-114">The code builds an expression tree to represent the following query:</span></span>

`companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`

<span data-ttu-id="59aae-115">Metody továrny v oboru názvů <xref:System.Linq.Expressions> slouží k vytváření stromů výrazů, které představují výrazy, které tvoří celkový dotaz.</span><span class="sxs-lookup"><span data-stu-id="59aae-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="59aae-116">Výrazy, které reprezentují volání standardních metod operátoru dotazu, odkazují na <xref:System.Linq.Queryable> implementace těchto metod.</span><span class="sxs-lookup"><span data-stu-id="59aae-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="59aae-117">Konečný strom výrazu je předán <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementaci zprostředkovatele `IQueryable` zdroje dat, aby bylo možné vytvořit spustitelný dotaz typu `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="59aae-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="59aae-118">Výsledky jsou získány vytvořením výčtu proměnné dotazu.</span><span class="sxs-lookup"><span data-stu-id="59aae-118">The results are obtained by enumerating that query variable.</span></span>

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

<span data-ttu-id="59aae-119">Tento kód používá pevný počet výrazů v predikátu, který je předán metodě `Queryable.Where`.</span><span class="sxs-lookup"><span data-stu-id="59aae-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="59aae-120">Můžete však napsat aplikaci, která kombinuje proměnlivý počet výrazů predikátů, který závisí na vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="59aae-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="59aae-121">V závislosti na vstupu od uživatele můžete také měnit standardní operátory dotazů, které jsou v dotazu volány.</span><span class="sxs-lookup"><span data-stu-id="59aae-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="59aae-122">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="59aae-122">Compile the code</span></span>

- <span data-ttu-id="59aae-123">Vytvořte nový projekt **konzolové aplikace** .</span><span class="sxs-lookup"><span data-stu-id="59aae-123">Create a new **Console Application** project.</span></span>

- <span data-ttu-id="59aae-124">Zahrňte obor názvů System. Linq. Expressions.</span><span class="sxs-lookup"><span data-stu-id="59aae-124">Include the System.Linq.Expressions namespace.</span></span>

- <span data-ttu-id="59aae-125">Zkopírujte kód z příkladu a vložte ho do `Main` `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="59aae-125">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="59aae-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59aae-126">See also</span></span>

- [<span data-ttu-id="59aae-127">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59aae-127">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="59aae-128">Postupy: spouštění stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59aae-128">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
