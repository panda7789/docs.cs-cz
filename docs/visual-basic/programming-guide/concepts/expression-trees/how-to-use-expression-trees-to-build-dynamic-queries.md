---
title: 'Postupy: Použití stromů výrazů k sestavování dynamických dotazů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: 2f91d95f888ab98902cc300afb61c41b62e64050
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966215"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a>Postupy: Použití stromů výrazů k sestavování dynamických dotazů (Visual Basic)
V technologii LINQ, stromy výrazů se používají k vyjádření strukturovaných dotazů, které se zaměřují zdroje dat, které implementují <xref:System.Linq.IQueryable%601>. Například implementuje zprostředkovatele LINQ <xref:System.Linq.IQueryable%601> rozhraní pro dotazování na relačních dat úložiště. Kompilátor jazyka Visual Basic zkompiluje dotazy, které se zaměřují takovým zdrojům dat do kódu, který vytváří strom výrazu v době běhu. Poskytovatele dotazů můžete procházet stromovou strukturu dat výraz a přeloží ji do dotazovací jazyk, který je vhodný pro zdroj dat.  
  
 Stromy výrazů se také používají v technologii LINQ k reprezentaci lambda výrazy, které jsou přiřazeny proměnné typu <xref:System.Linq.Expressions.Expression%601>.  
  
 Toto téma popisuje postup použití stromů výrazů k vytvoření dynamických dotazů LINQ. Dynamické dotazy jsou užitečné, pokud nejsou v době kompilace znám podrobnosti dotazu. Aplikace může například nabízí uživatelské rozhraní, která umožňuje koncovému uživateli zadat jeden nebo více predikátů filtrovat data. Pokud chcete používat pro dotazování na LINQ, musí tento typ aplikace použití stromů výrazů k vytvoření dotazu LINQ v době běhu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít k vytvoření dotazu na stromů výrazů `IQueryable` zdroje dat a následné provádění. Kód sestavení strom výrazu k reprezentaci následující dotaz:  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 Metody pro vytváření objektů v <xref:System.Linq.Expressions> obor názvů slouží k vytvoření stromů výrazů, které představují výrazy, které tvoří celkové dotazu. Výrazy, které představují volání metody standardních dotazovacích operátorů odkazovat na <xref:System.Linq.Queryable> implementace těchto metod. Výsledný výraz stromu je předána <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementace poskytovatele `IQueryable` zdroj dat k vytvoření dotazu spustitelný soubor typu `IQueryable`. Výsledky jsou získat výčtem této proměnné dotazu.  
  
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
  
 Tento kód používá pevný počet výrazů v predikátu, který je předán `Queryable.Where` metody. Ale můžete napsat aplikaci, která kombinuje proměnný počet predikátů výrazy, které závisí na vstup uživatele. Můžete také měnit standardních operátorů pro dotazování, které jsou volány v dotazu, v závislosti na vstup od uživatele.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Vytvořte nový **konzolovou aplikaci** projektu.  
  
- Pokud se už neodkazuje, přidejte odkaz na System.Core.dll.  
  
- Zahrnout System.Linq.Expressions oboru názvů.  
  
- Zkopírovat kód z příkladu a vložte ho do `Main` `Sub` postup.  
  
## <a name="see-also"></a>Viz také:

- [Stromy výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Postupy: Provádění stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
