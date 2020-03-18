---
title: Jak používat stromy výrazů k vytváření dynamických dotazů (C#)
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: 6114ec13dd43a7df146b87dda00fba06d6eb870c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635896"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>Jak používat stromy výrazů k vytváření dynamických dotazů (C#)
V LINQ stromy výrazů se používají k reprezentaci strukturovaných dotazů, které se zaměřují na zdroje dat, které implementují <xref:System.Linq.IQueryable%601>. Například linq zprostředkovatel implementuje <xref:System.Linq.IQueryable%601> rozhraní pro dotazování relační úložiště dat. Kompilátor Jazyka C# zkompiluje dotazy, které cílí na tyto zdroje dat do kódu, který vytváří strom výrazů za běhu. Poskytovatel dotazu pak může procházet strukturu dat stromu výrazů a přeložit ji do dotazovacího jazyka vhodného pro zdroj dat.  
  
 Stromy výrazů se také používají v LINQ k reprezentaci výrazů lambda, které jsou přiřazeny proměnným typu <xref:System.Linq.Expressions.Expression%601>.  
  
 Toto téma popisuje, jak pomocí stromů výrazů vytvářet dynamické dotazy LINQ. Dynamické dotazy jsou užitečné v případě, že specifika dotazu nejsou známy v době kompilace. Aplikace může například poskytnout uživatelské rozhraní, které umožňuje koncovému uživateli zadat jeden nebo více predikátů pro filtrování dat. Chcete-li použít LINQ pro dotazování, tento druh aplikace musí používat stromy výrazů k vytvoření dotazu LINQ za běhu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí stromů výrazů `IQueryable` vytvořit dotaz proti zdroji dat a potom jej spustit. Kód vytvoří strom výrazů představující následující dotaz:  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 Metody výroby v <xref:System.Linq.Expressions> oboru názvů se používají k vytvoření stromů výrazů, které představují výrazy, které tvoří celkový dotaz. Výrazy, které představují volání standardní metody operátoru dotazu odkazují na <xref:System.Linq.Queryable> implementace těchto metod. Konečný strom výrazů je <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> předán implementaci zprostředkovatele zdroje `IQueryable` dat k vytvoření `IQueryable`spustitelného dotazu typu . Výsledky jsou získány výčet této proměnné dotazu.  
  
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
  
 Tento kód používá pevný počet výrazů v predikátu, `Queryable.Where` který je předán metodě. Můžete však napsat aplikaci, která kombinuje proměnný počet predikátových výrazů, které závisí na vstupu uživatele. Můžete také měnit standardní operátory dotazu, které jsou volány v dotazu, v závislosti na vstupu od uživatele.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Zahrňte obor názvů System.Linq.Expressions.  
  
## <a name="see-also"></a>Viz také

- [Stromy výrazů (C#)](./index.md)
- [Jak spustit stromy výrazů (C#)](./how-to-execute-expression-trees.md)
- [Dynamické určování filtrů predikátů při běhu](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
