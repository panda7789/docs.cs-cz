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
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="ccbeb-102">Postupy: Úpravy stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccbeb-102">How to: Modify Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="ccbeb-103">Toto téma ukazuje, jak upravit strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="ccbeb-104">Stromy výrazů jsou neměnné, což znamená, že nejde změnit napřímo.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="ccbeb-105">Chcete-li změnit strom výrazu, musíte vytvořit kopie stávající strom výrazu a při vytváření kopie, proveďte požadované změny.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="ccbeb-106">Můžete použít <xref:System.Linq.Expressions.ExpressionVisitor> třídy k procházení stávající strom výrazu a zkopírovat každý uzel, který ho navštíví.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="ccbeb-107">Chcete-li změnit strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-107">To modify an expression tree</span></span>  
  
1.  <span data-ttu-id="ccbeb-108">Vytvořte nový **konzolovou aplikaci** projektu.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-108">Create a new **Console Application** project.</span></span>  
  
2.  <span data-ttu-id="ccbeb-109">Přidat `Imports` – příkaz souboru `System.Linq.Expressions` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-109">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3.  <span data-ttu-id="ccbeb-110">Přidat `AndAlsoModifier` třídy do projektu.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="ccbeb-111">Tato třída dědí <xref:System.Linq.Expressions.ExpressionVisitor> třídy a je zaměřena na upravte výrazy, které představují podmíněného `AND` operace.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="ccbeb-112">Tyto operace se změní z s podmínkou `AND` do s podmínkou `OR`.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="ccbeb-113">K tomu, třída přepsání <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metodu základního typu, protože podmíněné `AND` výrazy jsou reprezentovány jako binární výrazy.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="ccbeb-114">V `VisitBinary` metodu, pokud výraz, který je předán představuje s podmínkou `AND` operace, vytvoří kód, který obsahuje podmíněný výraz new `OR` místo podmíněný operátor `AND` operátor.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="ccbeb-115">Pokud výraz, který je předán `VisitBinary` nepředstavuje s podmínkou `AND` operace, odloží metody k implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="ccbeb-116">Metody třídy base konstrukce uzlů, které jsou podobné stromů výrazů, které jsou předány v, ale uzly mají jejich sub stromů nahradí stromů výrazů, které jsou vytvořené rekurzivně návštěvníkem.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4.  <span data-ttu-id="ccbeb-117">Přidat `Imports` – příkaz souboru `System.Linq.Expressions` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-117">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5.  <span data-ttu-id="ccbeb-118">Přidejte kód, který `Main` metody v souboru Module1.vb vytvoření stromu výrazů a předat ho metodě, která jej upravíte.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-118">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="ccbeb-119">Kód vytvoří výraz, který obsahuje s podmínkou `AND` operace.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="ccbeb-120">Potom vytvoří instanci `AndAlsoModifier` třídy a předává výraz, který má `Modify` metody této třídy.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="ccbeb-121">Původní a stromů výrazů změny jsou výstupem ještě neprojevila změna.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6.  <span data-ttu-id="ccbeb-122">Kompilace a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ccbeb-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccbeb-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccbeb-123">See also</span></span>

- [<span data-ttu-id="ccbeb-124">Postupy: Provádění stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccbeb-124">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="ccbeb-125">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccbeb-125">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
