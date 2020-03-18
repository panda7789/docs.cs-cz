---
title: Jak upravit stromy výrazů (C#)
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: e921c594497d02f5eb16cc60294e947e83636d7a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73969894"
---
# <a name="how-to-modify-expression-trees-c"></a>Jak upravit stromy výrazů (C#)
Toto téma ukazuje, jak upravit strom výrazů. Stromy výrazů jsou neměnné, což znamená, že je nelze přímo změnit. Chcete-li změnit strom výrazů, musíte vytvořit kopii existujícího stromu výrazů a při vytváření kopie proveďte požadované změny. Třídu <xref:System.Linq.Expressions.ExpressionVisitor> můžete použít k procházení existujícího stromu výrazů a ke kopírování každého uzlu, který navštíví.  
  
### <a name="to-modify-an-expression-tree"></a>Úprava stromu výrazů  
  
1. Vytvořte nový projekt **konzolové aplikace.**  
  
2. Přidejte `using` direktivu `System.Linq.Expressions` do souboru pro obor názvů.  
  
3. Přidejte `AndAlsoModifier` třídu do projektu.  
  
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
  
     Tato třída dědí třídu <xref:System.Linq.Expressions.ExpressionVisitor> a je specializovaná `AND` na úpravu výrazů, které představují podmíněné operace. Změní tyto operace z `AND` podmíněné `OR`na podmíněné . Chcete-li to provést, <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> třída přepíše metodu `AND` základního typu, protože podmíněné výrazy jsou reprezentovány jako binární výrazy. V `VisitBinary` metodě, pokud výraz, který je `AND` předán představuje podmíněné operace, kód vytvoří `OR` nový výraz, `AND` který obsahuje podmíněný operátor namísto podmíněné operátor. Pokud výraz, který `VisitBinary` je předán nepředstavuje podmíněné `AND` operace, metoda odkládá na implementaci základní třídy. Metody základní třídy vytvářejí uzly, které jsou jako stromy výrazů, které jsou předány, ale uzly mají své dílčí stromy nahrazeny stromy výrazů, které jsou vytvářeny rekurzivně návštěvníkem.  
  
4. Přidejte `using` direktivu `System.Linq.Expressions` do souboru pro obor názvů.  
  
5. Přidejte kód `Main` do metody v souboru Program.cs vytvořit strom výrazů a předat jej metodě, která jej upraví.  
  
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
  
     Kód vytvoří výraz, který `AND` obsahuje podmíněnou operaci. Potom vytvoří instanci `AndAlsoModifier` třídy a předá výraz metodě `Modify` této třídy. Původní i upravené stromy výrazů jsou výstupem pro zobrazení změny.  
  
6. Zkompilujte a spusťte aplikaci.  
  
## <a name="see-also"></a>Viz také

- [Jak spustit stromy výrazů (C#)](./how-to-execute-expression-trees.md)
- [Stromy výrazů (C#)](./index.md)
