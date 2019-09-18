---
title: 'Postupy: Úprava stromů výrazů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: ac196b56f178659765437a97a25f46c04f8040fa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054203"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Postupy: Úprava stromů výrazů (Visual Basic)

V tomto tématu se dozvíte, jak upravit strom výrazu. Stromy výrazů jsou neměnné, což znamená, že je nelze upravovat přímo. Chcete-li změnit strom výrazu, je nutné vytvořit kopii existujícího stromu výrazů a při vytváření kopie provést požadované změny. <xref:System.Linq.Expressions.ExpressionVisitor> Třídu můžete použít k procházení existujícího stromu výrazů a ke zkopírování jednotlivých uzlů, které navštíví.

## <a name="to-modify-an-expression-tree"></a>Úprava stromu výrazu

1. Vytvořte nový projekt **konzolové aplikace** .

2. Přidejte příkaz do souboru `System.Linq.Expressions` pro obor názvů. `Imports`

3. `AndAlsoModifier` Přidejte třídu do projektu.

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

    Tato třída dědí <xref:System.Linq.Expressions.ExpressionVisitor> třídu a je specializovaná na úpravu výrazů, které reprezentují podmíněné `AND` operace. Tyto operace mění z podmíněného `AND` na podmíněný. `OR` K tomu třída Přepisuje <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metodu základního typu, protože podmíněné `AND` výrazy jsou reprezentovány jako binární výrazy. V případě, že výraz, který je předán do, představuje podmíněnou `AND` operaci, kód vytvoří nový výraz, který obsahuje podmíněný `OR` operátor místo podmíněného `AND`. `VisitBinary` podnikatel. Pokud výraz, který je předán do `VisitBinary` , nepředstavuje podmíněnou `AND` operaci, metoda se odloží k implementaci základní třídy. Metody základní třídy konstrukce uzly, které jsou jako stromy výrazů, které jsou předány, ale uzly mají své dílčí stromy nahrazené stromy výrazů, které jsou vytvářeny rekurzivně návštěvníkem.

4. Přidejte příkaz do souboru `System.Linq.Expressions` pro obor názvů. `Imports`

5. Přidejte kód do `Main` metody v souboru Module1. vb pro vytvoření stromu výrazu a předejte ho do metody, která ho upraví.

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

    Kód vytvoří výraz, který obsahuje podmíněnou `AND` operaci. Potom vytvoří instanci `AndAlsoModifier` třídy a předá výraz `Modify` metodě této třídy. Původní a upravené stromy výrazů jsou zobrazeny, aby se změna zobrazila.

6. Zkompilujte a spusťte aplikaci.

## <a name="see-also"></a>Viz také:

- [Postupy: Spuštění stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Stromy výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
