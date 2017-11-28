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
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="3f473-102">Postupy: úpravy stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f473-102">How to: Modify Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="3f473-103">Toto téma ukazuje, jak upravit strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="3f473-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="3f473-104">Stromy výrazů jsou neměnné, což znamená, že je nelze změnit přímo.</span><span class="sxs-lookup"><span data-stu-id="3f473-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="3f473-105">Chcete-li změnit strom výrazu, musíte vytvořit kopii existující strom výrazu a při vytváření kopie, proveďte požadované změny.</span><span class="sxs-lookup"><span data-stu-id="3f473-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="3f473-106">Můžete použít <xref:System.Linq.Expressions.ExpressionVisitor> tříd procházení stávající strom výrazu a zkopírovat každý uzel, který ho navštíví.</span><span class="sxs-lookup"><span data-stu-id="3f473-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="3f473-107">Chcete-li upravit strom výrazu se nezdařilo</span><span class="sxs-lookup"><span data-stu-id="3f473-107">To modify an expression tree</span></span>  
  
1.  <span data-ttu-id="3f473-108">Vytvořte novou **konzolové aplikace** projektu.</span><span class="sxs-lookup"><span data-stu-id="3f473-108">Create a new **Console Application** project.</span></span>  
  
2.  <span data-ttu-id="3f473-109">Přidat `Imports` příkaz v souboru `System.Linq.Expressions` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3f473-109">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3.  <span data-ttu-id="3f473-110">Přidat `AndAlsoModifier` třídu do projektu.</span><span class="sxs-lookup"><span data-stu-id="3f473-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="3f473-111">Tato třída dědí <xref:System.Linq.Expressions.ExpressionVisitor> třídy a se specializuje k úpravě výrazy, které představují podmíněného `AND` operace.</span><span class="sxs-lookup"><span data-stu-id="3f473-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="3f473-112">Změní tyto operace z podmíněného `AND` k podmíněného `OR`.</span><span class="sxs-lookup"><span data-stu-id="3f473-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="3f473-113">K tomu, třída přepsání <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metoda základního typu, protože podmíněného `AND` výrazy jsou reprezentovány jako binární výrazy.</span><span class="sxs-lookup"><span data-stu-id="3f473-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="3f473-114">V `VisitBinary` metodu, pokud výraz, který je předán představuje podmíněného `AND` operace, kód vytvoří nový výraz, který obsahuje podmínku `OR` operátor místo podmínku `AND` operátor.</span><span class="sxs-lookup"><span data-stu-id="3f473-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="3f473-115">Pokud výraz, který je předán `VisitBinary` nepředstavuje podmíněného `AND` operace, metody odkládat údaje k implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="3f473-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="3f473-116">Metody třídy base konstrukce uzlů, které jsou podobné stromů výrazů, které se předávají v, ale uzly mají jejich dílčí stromy nahradí stromů výrazů, které se vytváří rekurzivně návštěvníkem.</span><span class="sxs-lookup"><span data-stu-id="3f473-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4.  <span data-ttu-id="3f473-117">Přidat `Imports` příkaz v souboru `System.Linq.Expressions` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3f473-117">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5.  <span data-ttu-id="3f473-118">Přidejte kód, který `Main` metoda v souboru Module1.vb vytvořit strom výrazu a jejich předávání do metody, upraví.</span><span class="sxs-lookup"><span data-stu-id="3f473-118">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="3f473-119">Kód vytvoří výraz, který obsahuje podmíněného `AND` operaci.</span><span class="sxs-lookup"><span data-stu-id="3f473-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="3f473-120">Potom vytvoří instanci `AndAlsoModifier` třídy a předá výraz, který se `Modify` metoda této třídy.</span><span class="sxs-lookup"><span data-stu-id="3f473-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="3f473-121">Chcete-li zobrazit změny jsou výstupem původní i stromy upravené výrazů.</span><span class="sxs-lookup"><span data-stu-id="3f473-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6.  <span data-ttu-id="3f473-122">Zkompilování a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="3f473-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f473-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f473-123">See Also</span></span>  
 [<span data-ttu-id="3f473-124">Postupy: provádění stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f473-124">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [<span data-ttu-id="3f473-125">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f473-125">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
