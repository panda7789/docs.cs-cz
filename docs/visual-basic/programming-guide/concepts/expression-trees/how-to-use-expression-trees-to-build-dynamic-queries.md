---
title: 'Postupy: Použití stromů výrazů k sestavování dynamických dotazů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: d9b1f97fd8bf3dfb15f3e1ab65b02a81b5607792
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642325"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="a1f27-102">Postupy: Použití stromů výrazů k sestavování dynamických dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1f27-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>
<span data-ttu-id="a1f27-103">V technologii LINQ, stromy výrazů se používají k vyjádření strukturovaných dotazů, které se zaměřují zdroje dat, které implementují <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="a1f27-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="a1f27-104">Například implementuje zprostředkovatele LINQ <xref:System.Linq.IQueryable%601> rozhraní pro dotazování na relačních dat úložiště.</span><span class="sxs-lookup"><span data-stu-id="a1f27-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="a1f27-105">Kompilátor jazyka Visual Basic zkompiluje dotazy, které se zaměřují takovým zdrojům dat do kódu, který vytváří strom výrazu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a1f27-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="a1f27-106">Poskytovatele dotazů můžete procházet stromovou strukturu dat výraz a přeloží ji do dotazovací jazyk, který je vhodný pro zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="a1f27-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="a1f27-107">Stromy výrazů se také používají v technologii LINQ k reprezentaci lambda výrazy, které jsou přiřazeny proměnné typu <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="a1f27-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="a1f27-108">Toto téma popisuje postup použití stromů výrazů k vytvoření dynamických dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="a1f27-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="a1f27-109">Dynamické dotazy jsou užitečné, pokud nejsou v době kompilace znám podrobnosti dotazu.</span><span class="sxs-lookup"><span data-stu-id="a1f27-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="a1f27-110">Aplikace může například nabízí uživatelské rozhraní, která umožňuje koncovému uživateli zadat jeden nebo více predikátů filtrovat data.</span><span class="sxs-lookup"><span data-stu-id="a1f27-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="a1f27-111">Pokud chcete používat pro dotazování na LINQ, musí tento typ aplikace použití stromů výrazů k vytvoření dotazu LINQ v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a1f27-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1f27-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1f27-112">Example</span></span>  
 <span data-ttu-id="a1f27-113">Následující příklad ukazuje, jak použít k vytvoření dotazu na stromů výrazů `IQueryable` zdroje dat a následné provádění.</span><span class="sxs-lookup"><span data-stu-id="a1f27-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="a1f27-114">Kód sestavení strom výrazu k reprezentaci následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="a1f27-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 <span data-ttu-id="a1f27-115">Metody pro vytváření objektů v <xref:System.Linq.Expressions> obor názvů slouží k vytvoření stromů výrazů, které představují výrazy, které tvoří celkové dotazu.</span><span class="sxs-lookup"><span data-stu-id="a1f27-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="a1f27-116">Výrazy, které představují volání metody standardních dotazovacích operátorů odkazovat na <xref:System.Linq.Queryable> implementace těchto metod.</span><span class="sxs-lookup"><span data-stu-id="a1f27-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="a1f27-117">Výsledný výraz stromu je předána <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementace poskytovatele `IQueryable` zdroj dat k vytvoření dotazu spustitelný soubor typu `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="a1f27-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="a1f27-118">Výsledky jsou získat výčtem této proměnné dotazu.</span><span class="sxs-lookup"><span data-stu-id="a1f27-118">The results are obtained by enumerating that query variable.</span></span>  
  
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
  
 <span data-ttu-id="a1f27-119">Tento kód používá pevný počet výrazů v predikátu, který je předán `Queryable.Where` metody.</span><span class="sxs-lookup"><span data-stu-id="a1f27-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="a1f27-120">Ale můžete napsat aplikaci, která kombinuje proměnný počet predikátů výrazy, které závisí na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="a1f27-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="a1f27-121">Můžete také měnit standardních operátorů pro dotazování, které jsou volány v dotazu, v závislosti na vstup od uživatele.</span><span class="sxs-lookup"><span data-stu-id="a1f27-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a1f27-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a1f27-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="a1f27-123">Vytvořte nový **konzolovou aplikaci** projektu.</span><span class="sxs-lookup"><span data-stu-id="a1f27-123">Create a new **Console Application** project.</span></span>  
  
- <span data-ttu-id="a1f27-124">Pokud se už neodkazuje, přidejte odkaz na System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="a1f27-124">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
- <span data-ttu-id="a1f27-125">Zahrnout System.Linq.Expressions oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a1f27-125">Include the System.Linq.Expressions namespace.</span></span>  
  
- <span data-ttu-id="a1f27-126">Zkopírovat kód z příkladu a vložte ho do `Main` `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="a1f27-126">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f27-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1f27-127">See also</span></span>

- [<span data-ttu-id="a1f27-128">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1f27-128">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="a1f27-129">Postupy: Provádění stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1f27-129">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
