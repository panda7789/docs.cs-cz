---
title: 'Postupy: úpravy stromů výrazů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: 92a0fb37e2a383c68beb2e4a56deb16f89a9bd28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Postupy: úpravy stromů výrazů (Visual Basic)
Toto téma ukazuje, jak upravit strom výrazu se nezdařilo. Stromy výrazů jsou neměnné, což znamená, že je nelze změnit přímo. Chcete-li změnit strom výrazu, musíte vytvořit kopii existující strom výrazu a při vytváření kopie, proveďte požadované změny. Můžete použít <xref:System.Linq.Expressions.ExpressionVisitor> tříd procházení stávající strom výrazu a zkopírovat každý uzel, který ho navštíví.  
  
### <a name="to-modify-an-expression-tree"></a>Chcete-li upravit strom výrazu se nezdařilo  
  
1.  Vytvořte novou **konzolové aplikace** projektu.  
  
2.  Přidat `Imports` příkaz v souboru `System.Linq.Expressions` oboru názvů.  
  
3.  Přidat `AndAlsoModifier` třídu do projektu.  
  
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
  
     Tato třída dědí <xref:System.Linq.Expressions.ExpressionVisitor> třídy a se specializuje k úpravě výrazy, které představují podmíněného `AND` operace. Změní tyto operace z podmíněného `AND` k podmíněného `OR`. K tomu, třída přepsání <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metoda základního typu, protože podmíněného `AND` výrazy jsou reprezentovány jako binární výrazy. V `VisitBinary` metodu, pokud výraz, který je předán představuje podmíněného `AND` operace, kód vytvoří nový výraz, který obsahuje podmínku `OR` operátor místo podmínku `AND` operátor. Pokud výraz, který je předán `VisitBinary` nepředstavuje podmíněného `AND` operace, metody odkládat údaje k implementaci základní třídy. Metody třídy base konstrukce uzlů, které jsou podobné stromů výrazů, které se předávají v, ale uzly mají jejich dílčí stromy nahradí stromů výrazů, které se vytváří rekurzivně návštěvníkem.  
  
4.  Přidat `Imports` příkaz v souboru `System.Linq.Expressions` oboru názvů.  
  
5.  Přidejte kód, který `Main` metoda v souboru Module1.vb vytvořit strom výrazu a jejich předávání do metody, upraví.  
  
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
  
     Kód vytvoří výraz, který obsahuje podmíněného `AND` operaci. Potom vytvoří instanci `AndAlsoModifier` třídy a předá výraz, který se `Modify` metoda této třídy. Chcete-li zobrazit změny jsou výstupem původní i stromy upravené výrazů.  
  
6.  Zkompilování a spuštění aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: provádění stromů výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [Stromy výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
