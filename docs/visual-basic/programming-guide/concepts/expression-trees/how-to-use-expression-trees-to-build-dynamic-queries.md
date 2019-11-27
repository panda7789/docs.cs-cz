---
title: 'Postupy: Použití stromů výrazů k sestavování dynamických dotazů'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: bf15880c1988ac5639dd80ba56d330372dc3803b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344719"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a>Postupy: použití stromů výrazů k sestavování dynamických dotazů (Visual Basic)

V technologii LINQ se stromy výrazů používají k reprezentování strukturovaných dotazů, které cílí na zdroje dat, které implementují <xref:System.Linq.IQueryable%601>. Zprostředkovatel LINQ například implementuje rozhraní <xref:System.Linq.IQueryable%601> pro dotazování na relačních úložištích dat. Kompilátor Visual Basic zkompiluje dotazy, které cílí na takové zdroje dat, do kódu, který vytvoří strom výrazu za běhu. Poskytovatel dotazu pak může procházet strukturu dat stromu výrazů a překládat ji do dotazovacího jazyka vhodného pro zdroj dat.

Stromy výrazů jsou také používány v LINQ k reprezentování výrazů lambda, které jsou přiřazeny proměnným typu <xref:System.Linq.Expressions.Expression%601>.

Toto téma popisuje použití stromů výrazů k vytváření dynamických dotazů LINQ. Dynamické dotazy jsou užitečné v případě, že specifické výrazy dotazu nejsou známy v době kompilace. Například aplikace může poskytovat uživatelské rozhraní, které umožňuje koncovému uživateli určit jeden nebo více predikátů pro filtrování dat. Aby bylo možné používat LINQ pro dotazování, tento druh aplikace musí pomocí stromů výrazů vytvořit dotaz LINQ za běhu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak pomocí stromů výrazů sestavit dotaz na zdroj dat `IQueryable` a pak ho spustit. Kód vytvoří strom výrazu pro reprezentaci následujícího dotazu:

`companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`

Metody továrny v oboru názvů <xref:System.Linq.Expressions> slouží k vytváření stromů výrazů, které představují výrazy, které tvoří celkový dotaz. Výrazy, které reprezentují volání standardních metod operátoru dotazu, odkazují na <xref:System.Linq.Queryable> implementace těchto metod. Konečný strom výrazu je předán <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementaci zprostředkovatele `IQueryable` zdroje dat, aby bylo možné vytvořit spustitelný dotaz typu `IQueryable`. Výsledky jsou získány vytvořením výčtu proměnné dotazu.

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

Tento kód používá pevný počet výrazů v predikátu, který je předán metodě `Queryable.Where`. Můžete však napsat aplikaci, která kombinuje proměnlivý počet výrazů predikátů, který závisí na vstupu uživatele. V závislosti na vstupu od uživatele můžete také měnit standardní operátory dotazů, které jsou v dotazu volány.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

- Vytvořte nový projekt **konzolové aplikace** .

- Zahrňte obor názvů System. Linq. Expressions.

- Zkopírujte kód z příkladu a vložte ho do `Main` `Sub` postupu.

## <a name="see-also"></a>Viz také:

- [Stromy výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Postupy: spouštění stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
