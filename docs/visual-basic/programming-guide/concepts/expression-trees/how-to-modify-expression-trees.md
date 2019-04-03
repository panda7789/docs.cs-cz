---
title: 'Postupy: Úpravy stromů výrazů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: c53983c6dfc601a7e8e32ad020f5f7feb66cfe04
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834332"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Postupy: Úpravy stromů výrazů (Visual Basic)
Toto téma ukazuje, jak upravit strom výrazu. Stromy výrazů jsou neměnné, což znamená, že nejde změnit napřímo. Chcete-li změnit strom výrazu, musíte vytvořit kopie stávající strom výrazu a při vytváření kopie, proveďte požadované změny. Můžete použít <xref:System.Linq.Expressions.ExpressionVisitor> třídy k procházení stávající strom výrazu a zkopírovat každý uzel, který ho navštíví.  
  
### <a name="to-modify-an-expression-tree"></a>Chcete-li změnit strom výrazu.  
  
1.  Vytvořte nový **konzolovou aplikaci** projektu.  
  
2.  Přidat `Imports` – příkaz souboru `System.Linq.Expressions` oboru názvů.  
  
3.  Přidat `AndAlsoModifier` třídy do projektu.  
  
    ```vb  
    Public Class AndAlsoModifier  
        Inherits ExpressionVisitor  
  
        Public Function Modify(ByVal expr As Expression) As Expression  
            Return Visit(expr)  
        End Function  
  
        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression  
            If b.NodeType = ExpressionType.AndAlso Then  
                Dim left = Me.Visit(b.Left)  
                Dim right = Me.Visit(b.Right)  
  
                ' Make this binary expression an OrElse operation instead   
                ' of an AndAlso operation.  
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _  
                                             b.IsLiftedToNull, b.Method)  
            End If  
  
            Return MyBase.VisitBinary(b)  
        End Function  
    End Class  
    ```  
  
     Tato třída dědí <xref:System.Linq.Expressions.ExpressionVisitor> třídy a je zaměřena na upravte výrazy, které představují podmíněného `AND` operace. Tyto operace se změní z s podmínkou `AND` do s podmínkou `OR`. K tomu, třída přepsání <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metodu základního typu, protože podmíněné `AND` výrazy jsou reprezentovány jako binární výrazy. V `VisitBinary` metodu, pokud výraz, který je předán představuje s podmínkou `AND` operace, vytvoří kód, který obsahuje podmíněný výraz new `OR` místo podmíněný operátor `AND` operátor. Pokud výraz, který je předán `VisitBinary` nepředstavuje s podmínkou `AND` operace, odloží metody k implementaci základní třídy. Metody třídy base konstrukce uzlů, které jsou podobné stromů výrazů, které jsou předány v, ale uzly mají jejich sub stromů nahradí stromů výrazů, které jsou vytvořené rekurzivně návštěvníkem.  
  
4.  Přidat `Imports` – příkaz souboru `System.Linq.Expressions` oboru názvů.  
  
5.  Přidejte kód, který `Main` metody v souboru Module1.vb vytvoření stromu výrazů a předat ho metodě, která jej upravíte.  
  
    ```vb  
    Dim expr As Expression(Of Func(Of String, Boolean)) = _  
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")  
  
    Console.WriteLine(expr)  
  
    Dim modifier As New AndAlsoModifier()  
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))  
  
    Console.WriteLine(modifiedExpr)  
  
    ' This code produces the following output:  
    ' name => ((name.Length > 10) && name.StartsWith("G"))  
    ' name => ((name.Length > 10) || name.StartsWith("G"))  
    ```  
  
     Kód vytvoří výraz, který obsahuje s podmínkou `AND` operace. Potom vytvoří instanci `AndAlsoModifier` třídy a předává výraz, který má `Modify` metody této třídy. Původní a stromů výrazů změny jsou výstupem ještě neprojevila změna.  
  
6.  Kompilace a spuštění aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Provádění stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Stromy výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
