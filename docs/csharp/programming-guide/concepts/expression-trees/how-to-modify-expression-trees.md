---
title: Postup úpravy stromů výrazů (C#)
description: Naučte se, jak upravit strom výrazu vytvořením kopie existujícího stromu výrazů a provedením požadovaných změn.
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 45aea18e253811d4e5c60f23f7f8496d4358f64c
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105604"
---
# <a name="how-to-modify-expression-trees-c"></a>Postup úpravy stromů výrazů (C#)
V tomto tématu se dozvíte, jak upravit strom výrazu. Stromy výrazů jsou neměnné, což znamená, že je nelze upravovat přímo. Chcete-li změnit strom výrazu, je nutné vytvořit kopii existujícího stromu výrazů a při vytváření kopie provést požadované změny. Třídu můžete použít <xref:System.Linq.Expressions.ExpressionVisitor> k procházení existujícího stromu výrazů a ke zkopírování jednotlivých uzlů, které navštíví.  
  
### <a name="to-modify-an-expression-tree"></a>Úprava stromu výrazu  
  
1. Vytvořte nový projekt **konzolové aplikace** .  
  
2. Přidejte `using` do souboru pro obor názvů direktivu `System.Linq.Expressions` .  
  
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
  
     Tato třída dědí <xref:System.Linq.Expressions.ExpressionVisitor> třídu a je specializovaná na úpravu výrazů, které reprezentují podmíněné `AND` operace. Tyto operace mění z podmíněného `AND` na podmíněný `OR` . K tomu třída Přepisuje <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metodu základního typu, protože podmíněné `AND` výrazy jsou reprezentovány jako binární výrazy. V `VisitBinary` metodě, pokud je výraz, který je předán, představuje podmíněnou `AND` operaci, kód vytvoří nový výraz, který obsahuje podmíněný `OR` operátor místo podmíněného `AND` operátoru. Pokud výraz, který je předán do `VisitBinary` , nepředstavuje podmíněnou `AND` operaci, metoda se odloží k implementaci základní třídy. Metody základní třídy konstrukce uzly, které jsou jako stromy výrazů, které jsou předány, ale uzly mají své dílčí stromy nahrazené stromy výrazů, které jsou vytvářeny rekurzivně návštěvníkem.  
  
4. Přidejte `using` do souboru pro obor názvů direktivu `System.Linq.Expressions` .  
  
5. Přidejte kód do `Main` metody v souboru program.cs pro vytvoření stromu výrazu a předejte ho metodě, která ho upraví.  
  
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
  
     Kód vytvoří výraz, který obsahuje podmíněnou `AND` operaci. Potom vytvoří instanci `AndAlsoModifier` třídy a předá výraz `Modify` metodě této třídy. Původní a upravené stromy výrazů jsou zobrazeny, aby se změna zobrazila.  
  
6. Zkompilujte a spusťte aplikaci.  
  
## <a name="see-also"></a>Viz také

- [Spuštění stromů výrazů (C#)](./how-to-execute-expression-trees.md)
- [Stromy výrazů (C#)](./index.md)
