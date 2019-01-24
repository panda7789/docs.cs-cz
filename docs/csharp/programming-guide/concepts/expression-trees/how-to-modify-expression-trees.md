---
title: 'Postupy: Úpravy stromů výrazů (C#)'
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 1cdc6eb4017495fc7486025dd868352eb9d04892
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735607"
---
# <a name="how-to-modify-expression-trees-c"></a>Postupy: Úpravy stromů výrazů (C#)
Toto téma ukazuje, jak upravit strom výrazu. Stromy výrazů jsou neměnné, což znamená, že nejde změnit napřímo. Chcete-li změnit strom výrazu, musíte vytvořit kopie stávající strom výrazu a při vytváření kopie, proveďte požadované změny. Můžete použít <xref:System.Linq.Expressions.ExpressionVisitor> třídy k procházení stávající strom výrazu a zkopírovat každý uzel, který ho navštíví.  
  
### <a name="to-modify-an-expression-tree"></a>Chcete-li změnit strom výrazu.  
  
1.  Vytvořte nový **konzolovou aplikaci** projektu.  
  
2.  Přidat `using` direktivy v souboru `System.Linq.Expressions` oboru názvů.  
  
3.  Přidat `AndAlsoModifier` třídy do projektu.  
  
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
  
     Tato třída dědí <xref:System.Linq.Expressions.ExpressionVisitor> třídy a je zaměřena na upravte výrazy, které představují podmíněného `AND` operace. Tyto operace se změní z s podmínkou `AND` do s podmínkou `OR`. K tomu, třída přepsání <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metodu základního typu, protože podmíněné `AND` výrazy jsou reprezentovány jako binární výrazy. V `VisitBinary` metodu, pokud výraz, který je předán představuje s podmínkou `AND` operace, vytvoří kód, který obsahuje podmíněný výraz new `OR` místo podmíněný operátor `AND` operátor. Pokud výraz, který je předán `VisitBinary` nepředstavuje s podmínkou `AND` operace, odloží metody k implementaci základní třídy. Metody třídy base konstrukce uzlů, které jsou podobné stromů výrazů, které jsou předány v, ale uzly mají jejich sub stromů nahradí stromů výrazů, které jsou vytvořené rekurzivně návštěvníkem.  
  
4.  Přidat `using` direktivy v souboru `System.Linq.Expressions` oboru názvů.  
  
5.  Přidejte kód, který `Main` metody v souboru Program.cs vytvořte strom výrazů a předat ho metodě, která jej upravíte.  
  
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
  
     Kód vytvoří výraz, který obsahuje s podmínkou `AND` operace. Potom vytvoří instanci `AndAlsoModifier` třídy a předává výraz, který má `Modify` metody této třídy. Původní a stromů výrazů změny jsou výstupem ještě neprojevila změna.  
  
6.  Kompilace a spuštění aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Provádění stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Stromy výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
