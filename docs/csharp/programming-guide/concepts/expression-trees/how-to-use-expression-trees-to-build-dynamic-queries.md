---
title: Použití stromů výrazů k sestavování dynamických dotazů (C#)
description: Naučte se používat stromy výrazů k vytváření dynamických dotazů LINQ. Tyto dotazy jsou užitečné v případě, že konkrétní dotazy nejsou v době kompilace známy.
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: edcef4068c19ba8e789683cf6ba4d5ef2477e0d8
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105593"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>Použití stromů výrazů k sestavování dynamických dotazů (C#)
V technologii LINQ se stromy výrazů používají k reprezentování strukturovaných dotazů, které cílí na zdroje dat, která implementují <xref:System.Linq.IQueryable%601> . Například poskytovatel LINQ implementuje <xref:System.Linq.IQueryable%601> rozhraní pro dotazování relačních úložišť dat. Kompilátor jazyka C# zkompiluje dotazy, které cílí na takové zdroje dat, do kódu, který vytvoří strom výrazu za běhu. Poskytovatel dotazu pak může procházet strukturu dat stromu výrazů a překládat ji do dotazovacího jazyka vhodného pro zdroj dat.  
  
 Stromy výrazů jsou také používány v LINQ k reprezentování výrazů lambda, které jsou přiřazeny proměnným typu <xref:System.Linq.Expressions.Expression%601> .  
  
 Toto téma popisuje použití stromů výrazů k vytváření dynamických dotazů LINQ. Dynamické dotazy jsou užitečné v případě, že specifické výrazy dotazu nejsou známy v době kompilace. Například aplikace může poskytovat uživatelské rozhraní, které umožňuje koncovému uživateli určit jeden nebo více predikátů pro filtrování dat. Aby bylo možné používat LINQ pro dotazování, tento druh aplikace musí pomocí stromů výrazů vytvořit dotaz LINQ za běhu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít stromy výrazů k vytvoření dotazu na `IQueryable` zdroj dat a jeho následné spuštění. Kód vytvoří strom výrazu pro reprezentaci následujícího dotazu:  
  
 ```csharp
 companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))
          .OrderBy(company => company)
 ```
  
 Metody továrny v <xref:System.Linq.Expressions> oboru názvů slouží k vytváření stromů výrazů, které představují výrazy, které tvoří celkový dotaz. Výrazy, které reprezentují volání standardních metod operátoru dotazu, odkazují na <xref:System.Linq.Queryable> implementace těchto metod. Konečný strom výrazu je předán <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementaci poskytovatele `IQueryable` zdroje dat pro vytvoření spustitelného dotazu typu `IQueryable` . Výsledky jsou získány vytvořením výčtu proměnné dotazu.  
  
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
  
 Tento kód používá pevný počet výrazů v predikátu, který je předán `Queryable.Where` metodě. Můžete však napsat aplikaci, která kombinuje proměnlivý počet výrazů predikátů, který závisí na vstupu uživatele. V závislosti na vstupu od uživatele můžete také měnit standardní operátory dotazů, které jsou v dotazu volány.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Zahrňte obor názvů System. Linq. Expressions.  
  
## <a name="see-also"></a>Viz také

- [Stromy výrazů (C#)](./index.md)
- [Spuštění stromů výrazů (C#)](./how-to-execute-expression-trees.md)
- [Dynamické určování filtrů predikátů při běhu](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
