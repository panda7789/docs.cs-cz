---
title: "Postupy: úpravy stromů výrazů (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4db0abec0df2bc4a17dca0ed1ee88b8a38b8ca8a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-expression-trees-c"></a>Postupy: úpravy stromů výrazů (C#)
Toto téma ukazuje, jak upravit strom výrazu se nezdařilo. Stromy výrazů jsou neměnné, což znamená, že je nelze změnit přímo. Chcete-li změnit strom výrazu, musíte vytvořit kopii existující strom výrazu a při vytváření kopie, proveďte požadované změny. Můžete použít <xref:System.Linq.Expressions.ExpressionVisitor> tříd procházení stávající strom výrazu a zkopírovat každý uzel, který ho navštíví.  
  
### <a name="to-modify-an-expression-tree"></a>Chcete-li upravit strom výrazu se nezdařilo  
  
1.  Vytvořte novou **konzolové aplikace** projektu.  
  
2.  Přidat `using` direktivy v souboru `System.Linq.Expressions` oboru názvů.  
  
3.  Přidat `AndAlsoModifier` třídu do projektu.  
  
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
  
     Tato třída dědí <xref:System.Linq.Expressions.ExpressionVisitor> třídy a se specializuje k úpravě výrazy, které představují podmíněného `AND` operace. Změní tyto operace z podmíněného `AND` k podmíněného `OR`. K tomu, třída přepsání <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metoda základního typu, protože podmíněného `AND` výrazy jsou reprezentovány jako binární výrazy. V `VisitBinary` metodu, pokud výraz, který je předán představuje podmíněného `AND` operace, kód vytvoří nový výraz, který obsahuje podmínku `OR` operátor místo podmínku `AND` operátor. Pokud výraz, který je předán `VisitBinary` nepředstavuje podmíněného `AND` operace, metody odkládat údaje k implementaci základní třídy. Metody třídy base konstrukce uzlů, které jsou podobné stromů výrazů, které se předávají v, ale uzly mají jejich dílčí stromy nahradí stromů výrazů, které se vytváří rekurzivně návštěvníkem.  
  
4.  Přidat `using` direktivy v souboru `System.Linq.Expressions` oboru názvů.  
  
5.  Přidejte kód, který `Main` metoda v souboru Program.cs vytvořit strom výrazu a jejich předávání do metody, upraví.  
  
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
  
     Kód vytvoří výraz, který obsahuje podmíněného `AND` operaci. Potom vytvoří instanci `AndAlsoModifier` třídy a předá výraz, který se `Modify` metoda této třídy. Chcete-li zobrazit změny jsou výstupem původní i stromy upravené výrazů.  
  
6.  Zkompilování a spuštění aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: provádění stromů výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [Stromy výrazů (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
