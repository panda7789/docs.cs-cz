---
title: "Postupy: úpravy stromů výrazů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 28a79a2dc8817a3fc6c7f3e2e01c1270d2981334
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
