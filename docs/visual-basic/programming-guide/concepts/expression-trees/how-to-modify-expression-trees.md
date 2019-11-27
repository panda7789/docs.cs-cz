---
title: 'Postupy: Úpravy stromů výrazů'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: 12ccad6df7d6c7d91ebc290163db362eae173209
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353750"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Postupy: Změna stromů výrazů (Visual Basic)

V tomto tématu se dozvíte, jak upravit strom výrazu. Stromy výrazů jsou neměnné, což znamená, že je nelze upravovat přímo. Chcete-li změnit strom výrazu, je nutné vytvořit kopii existujícího stromu výrazů a při vytváření kopie provést požadované změny. Třídu <xref:System.Linq.Expressions.ExpressionVisitor> lze použít k procházení existujícího stromu výrazů a ke kopírování jednotlivých uzlů, které navštíví.

## <a name="to-modify-an-expression-tree"></a>Úprava stromu výrazu

1. Vytvořte nový projekt **konzolové aplikace** .

2. Přidejte do souboru příkaz `Imports` pro obor názvů `System.Linq.Expressions`.

3. Přidejte třídu `AndAlsoModifier` do projektu.

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

    Tato třída dědí třídu <xref:System.Linq.Expressions.ExpressionVisitor> a je specializovaná na úpravu výrazů, které reprezentují podmíněné `AND` operace. Tyto operace mění z podmíněného `AND` na podmíněný `OR`. K tomu třída přepíše metodu <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> základního typu, protože podmíněné `AND` výrazy jsou reprezentovány jako binární výrazy. V metodě `VisitBinary`, pokud výraz, který je předán, představuje podmíněnou operaci `AND`, kód vytvoří nový výraz, který obsahuje podmíněný operátor `OR` namísto podmíněného `AND`ho operátoru. Pokud výraz předaný `VisitBinary` nepředstavuje podmíněnou operaci `AND`, metoda se odloží k implementaci základní třídy. Metody základní třídy konstrukce uzly, které jsou jako stromy výrazů, které jsou předány, ale uzly mají své dílčí stromy nahrazené stromy výrazů, které jsou vytvářeny rekurzivně návštěvníkem.

4. Přidejte do souboru příkaz `Imports` pro obor názvů `System.Linq.Expressions`.

5. Přidejte kód do metody `Main` v souboru Module1. vb pro vytvoření stromu výrazu a předejte ho metodě, která ho upraví.

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

    Kód vytvoří výraz, který obsahuje podmíněnou operaci `AND`. Potom vytvoří instanci třídy `AndAlsoModifier` a předá výraz metodě `Modify` této třídy. Původní a upravené stromy výrazů jsou zobrazeny, aby se změna zobrazila.

6. Zkompilujte a spusťte aplikaci.

## <a name="see-also"></a>Viz také:

- [Postupy: spouštění stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Stromy výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
