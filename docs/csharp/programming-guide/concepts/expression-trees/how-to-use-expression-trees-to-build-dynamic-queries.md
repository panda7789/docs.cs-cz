---
title: 'Postupy: použití stromů výrazů k sestavování dynamických dotazů (C#)'
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: e3afbea647bb429d25f41f37fde268565bc5bf8a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591409"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>Postupy: použití stromů výrazů k sestavování dynamických dotazů (C#)
V technologii LINQ, stromy výrazů se používají k vyjádření strukturovaných dotazů, které se zaměřují zdroje dat, které implementují <xref:System.Linq.IQueryable%601>. Například implementuje zprostředkovatele LINQ <xref:System.Linq.IQueryable%601> rozhraní pro dotazování na relačních dat úložiště. Kompilátor jazyka C# kompiluje dotazy, které se zaměřují takovým zdrojům dat do kódu, který vytváří strom výrazu v době běhu. Poskytovatele dotazů můžete procházet stromovou strukturu dat výraz a přeloží ji do dotazovací jazyk, který je vhodný pro zdroj dat.  
  
 Stromy výrazů se také používají v technologii LINQ k reprezentaci lambda výrazy, které jsou přiřazeny proměnné typu <xref:System.Linq.Expressions.Expression%601>.  
  
 Toto téma popisuje postup použití stromů výrazů k vytvoření dynamických dotazů LINQ. Dynamické dotazy jsou užitečné, pokud nejsou v době kompilace znám podrobnosti dotazu. Aplikace může například nabízí uživatelské rozhraní, která umožňuje koncovému uživateli zadat jeden nebo více predikátů filtrovat data. Pokud chcete používat pro dotazování na LINQ, musí tento typ aplikace použití stromů výrazů k vytvoření dotazu LINQ v době běhu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít k vytvoření dotazu na stromů výrazů `IQueryable` zdroje dat a následné provádění. Kód sestavení strom výrazu k reprezentaci následující dotaz:  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 Metody pro vytváření objektů v <xref:System.Linq.Expressions> obor názvů slouží k vytvoření stromů výrazů, které představují výrazy, které tvoří celkové dotazu. Výrazy, které představují volání metody standardních dotazovacích operátorů odkazovat na <xref:System.Linq.Queryable> implementace těchto metod. Výsledný výraz stromu je předána <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementace poskytovatele `IQueryable` zdroj dat k vytvoření dotazu spustitelný soubor typu `IQueryable`. Výsledky jsou získat výčtem této proměnné dotazu.  
  
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
  
 Tento kód používá pevný počet výrazů v predikátu, který je předán `Queryable.Where` metody. Ale můžete napsat aplikaci, která kombinuje proměnný počet predikátů výrazy, které závisí na vstup uživatele. Můžete také měnit standardních operátorů pro dotazování, které jsou volány v dotazu, v závislosti na vstup od uživatele.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Vytvořte nový **konzolovou aplikaci** projektu.  
  
-   Pokud se už neodkazuje, přidejte odkaz na System.Core.dll.  
  
-   Zahrnout System.Linq.Expressions oboru názvů.  
  
-   Zkopírovat kód z příkladu a vložte ho do `Main` metody.  
  
## <a name="see-also"></a>Viz také

- [Stromy výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
- [Postupy: provádění stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
- [Postupy: dynamické určování filtrů predikátů při běhu](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
