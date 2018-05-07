---
title: 'Postupy: použití stromů výrazů k sestavování dynamických dotazů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: a2101598a083f8d0738cb531ebbaea0f7a87a577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a>Postupy: použití stromů výrazů k sestavování dynamických dotazů (Visual Basic)
V technologii LINQ, stromy výrazů se používají k vyjádření strukturovaných dotazů, které cílí zdroje dat, které implementují <xref:System.Linq.IQueryable%601>. Například implementuje poskytovatele LINQ <xref:System.Linq.IQueryable%601> rozhraní pro dotazování relační datové úložiště. Visual Basic – kompilátor zkompiluje dotazy, které cílí na tyto zdroje dat do kódu, který sestaví strom výrazu za běhu. Dotaz na zprostředkovatele můžete procházet stromové struktury dat. výraz a přeloží ji do dotazovací jazyk, který je vhodný pro zdroj dat.  
  
 Stromy výrazů se také používají v technologii LINQ k vyjádření výrazy lambda, které jsou přiřazeny k proměnné typu <xref:System.Linq.Expressions.Expression%601>.  
  
 Toto téma popisuje postup použití stromů výrazů k vytvoření dynamických dotazů LINQ. Dynamické dotazy jsou užitečné, když jsou specifikace dotazu nejsou známá v době kompilace. Aplikace může například zadat uživatelské rozhraní, která umožňuje koncovému uživateli umožňují určit jeden nebo více predikáty filtrovat data. Tento druh aplikace pomocí LINQ pro dotazování, musíte použít stromů výrazů k vytvoření dotazu LINQ za běhu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit dotazy na použití stromů výrazů `IQueryable` zdroje dat a pak ho provést. Kód vytvoří strom výrazu představují následující dotaz:  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 Metody vytváření v <xref:System.Linq.Expressions> obor názvů se používají k vytváření stromů výrazů, které představují výrazy, které tvoří celkové dotazu. Výrazy, které představují volání metody operátor standardní dotazů odkazovat na <xref:System.Linq.Queryable> implementace z těchto metod. Předaný stromu výsledný výraz <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementace zprostředkovatele `IQueryable` zdroj dat pro vytvoření spustitelného souboru dotazu typu `IQueryable`. Výsledky jsou získala při vytváření výčtu tuto proměnnou dotazu.  
  
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
  
 Tento kód používá pevný počet výrazů v predikátu, který je předán `Queryable.Where` metoda. Nicméně můžete napsat aplikaci, která kombinuje proměnné číslo predikátem výrazů, které závisí na vstup uživatele. Také můžete měnit operátory standardní dotazu, které se nazývají v dotazu, v závislosti na vstup od uživatele.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Vytvořte novou **konzolové aplikace** projektu.  
  
-   Přidáte odkaz na System.Core.dll, pokud už neodkazuje.  
  
-   Obor názvů System.Linq.Expressions patří.  
  
-   Zkopírujte kód z příkladu a vložte ji do `Main` `Sub` postupu.  
  
## <a name="see-also"></a>Viz také  
 [Stromy výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [Postupy: provádění stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
