---
title: Postup úpravy stromů výrazů (C#)
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: e921c594497d02f5eb16cc60294e947e83636d7a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969894"
---
# <a name="how-to-modify-expression-trees-c"></a>Postup úpravy stromů výrazů (C#)
V tomto tématu se dozvíte, jak upravit strom výrazu. Stromy výrazů jsou neměnné, což znamená, že je nelze upravovat přímo. Chcete-li změnit strom výrazu, je nutné vytvořit kopii existujícího stromu výrazů a při vytváření kopie provést požadované změny. Třídu <xref:System.Linq.Expressions.ExpressionVisitor> lze použít k procházení existujícího stromu výrazů a ke kopírování jednotlivých uzlů, které navštíví.  
  
### <a name="to-modify-an-expression-tree"></a>Úprava stromu výrazu  
  
1. Vytvořte nový projekt **konzolové aplikace** .  
  
2. Přidejte do souboru `using`ovou direktivu pro obor názvů `System.Linq.Expressions`.  
  
3. Přidejte třídu `AndAlsoModifier` do projektu.  
  
    ```csharp  
    public class AndAlsoModifier : ExpressionVisitor  
    {  
        public Expression Modify(Expression expression)  
        {  
            return Visit(expression);  
        }  
  
        protected override Expression VisitBinary(BinaryExpression b)  
        {  
            if (b.NodeType == ExpressionType.AndAlso)  
            {  
                Expression left = this.Visit(b.Left);  
                Expression right = this.Visit(b.Right);  
  
                // Make this binary expression an OrElse operation instead of an AndAlso operation.  
                return Expression.MakeBinary(ExpressionType.OrElse, left, right, b.IsLiftedToNull, b.Method);  
            }  
  
            return base.VisitBinary(b);  
        }  
    }  
    ```  
  
     Tato třída dědí třídu <xref:System.Linq.Expressions.ExpressionVisitor> a je specializovaná na úpravu výrazů, které reprezentují podmíněné `AND` operace. Tyto operace mění z podmíněného `AND` na podmíněný `OR`. K tomu třída přepíše metodu <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> základního typu, protože podmíněné `AND` výrazy jsou reprezentovány jako binární výrazy. V metodě `VisitBinary`, pokud výraz, který je předán, představuje podmíněnou operaci `AND`, kód vytvoří nový výraz, který obsahuje podmíněný operátor `OR` namísto podmíněného `AND`ho operátoru. Pokud výraz předaný `VisitBinary` nepředstavuje podmíněnou operaci `AND`, metoda se odloží k implementaci základní třídy. Metody základní třídy konstrukce uzly, které jsou jako stromy výrazů, které jsou předány, ale uzly mají své dílčí stromy nahrazené stromy výrazů, které jsou vytvářeny rekurzivně návštěvníkem.  
  
4. Přidejte do souboru `using`ovou direktivu pro obor názvů `System.Linq.Expressions`.  
  
5. Přidejte kód do metody `Main` v souboru Program.cs pro vytvoření stromu výrazu a předejte ho do metody, která ho upraví.  
  
    ```csharp  
    Expression<Func<string, bool>> expr = name => name.Length > 10 && name.StartsWith("G");  
    Console.WriteLine(expr);  
  
    AndAlsoModifier treeModifier = new AndAlsoModifier();  
    Expression modifiedExpr = treeModifier.Modify((Expression) expr);  
  
    Console.WriteLine(modifiedExpr);  
  
    /*  This code produces the following output:  
  
        name => ((name.Length > 10) && name.StartsWith("G"))  
        name => ((name.Length > 10) || name.StartsWith("G"))  
    */  
    ```  
  
     Kód vytvoří výraz, který obsahuje podmíněnou operaci `AND`. Potom vytvoří instanci třídy `AndAlsoModifier` a předá výraz metodě `Modify` této třídy. Původní a upravené stromy výrazů jsou zobrazeny, aby se změna zobrazila.  
  
6. Zkompilujte a spusťte aplikaci.  
  
## <a name="see-also"></a>Viz také:

- [Spuštění stromů výrazů (C#)](./how-to-execute-expression-trees.md)
- [Stromy výrazů (C#)](./index.md)
