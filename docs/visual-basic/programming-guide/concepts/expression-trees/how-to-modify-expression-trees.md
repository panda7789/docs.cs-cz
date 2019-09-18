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
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="8d815-102">Postupy: Úprava stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d815-102">How to: Modify Expression Trees (Visual Basic)</span></span>

<span data-ttu-id="8d815-103">V tomto tématu se dozvíte, jak upravit strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="8d815-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="8d815-104">Stromy výrazů jsou neměnné, což znamená, že je nelze upravovat přímo.</span><span class="sxs-lookup"><span data-stu-id="8d815-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="8d815-105">Chcete-li změnit strom výrazu, je nutné vytvořit kopii existujícího stromu výrazů a při vytváření kopie provést požadované změny.</span><span class="sxs-lookup"><span data-stu-id="8d815-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="8d815-106"><xref:System.Linq.Expressions.ExpressionVisitor> Třídu můžete použít k procházení existujícího stromu výrazů a ke zkopírování jednotlivých uzlů, které navštíví.</span><span class="sxs-lookup"><span data-stu-id="8d815-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>

## <a name="to-modify-an-expression-tree"></a><span data-ttu-id="8d815-107">Úprava stromu výrazu</span><span class="sxs-lookup"><span data-stu-id="8d815-107">To modify an expression tree</span></span>

1. <span data-ttu-id="8d815-108">Vytvořte nový projekt **konzolové aplikace** .</span><span class="sxs-lookup"><span data-stu-id="8d815-108">Create a new **Console Application** project.</span></span>

2. <span data-ttu-id="8d815-109">Přidejte příkaz do souboru `System.Linq.Expressions` pro obor názvů. `Imports`</span><span class="sxs-lookup"><span data-stu-id="8d815-109">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

3. <span data-ttu-id="8d815-110">`AndAlsoModifier` Přidejte třídu do projektu.</span><span class="sxs-lookup"><span data-stu-id="8d815-110">Add the `AndAlsoModifier` class to your project.</span></span>

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

    <span data-ttu-id="8d815-111">Tato třída dědí <xref:System.Linq.Expressions.ExpressionVisitor> třídu a je specializovaná na úpravu výrazů, které reprezentují podmíněné `AND` operace.</span><span class="sxs-lookup"><span data-stu-id="8d815-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="8d815-112">Tyto operace mění z podmíněného `AND` na podmíněný. `OR`</span><span class="sxs-lookup"><span data-stu-id="8d815-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="8d815-113">K tomu třída Přepisuje <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metodu základního typu, protože podmíněné `AND` výrazy jsou reprezentovány jako binární výrazy.</span><span class="sxs-lookup"><span data-stu-id="8d815-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="8d815-114">V případě, že výraz, který je předán do, představuje podmíněnou `AND` operaci, kód vytvoří nový výraz, který obsahuje podmíněný `OR` operátor místo podmíněného `AND`. `VisitBinary` podnikatel.</span><span class="sxs-lookup"><span data-stu-id="8d815-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="8d815-115">Pokud výraz, který je předán do `VisitBinary` , nepředstavuje podmíněnou `AND` operaci, metoda se odloží k implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8d815-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="8d815-116">Metody základní třídy konstrukce uzly, které jsou jako stromy výrazů, které jsou předány, ale uzly mají své dílčí stromy nahrazené stromy výrazů, které jsou vytvářeny rekurzivně návštěvníkem.</span><span class="sxs-lookup"><span data-stu-id="8d815-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>

4. <span data-ttu-id="8d815-117">Přidejte příkaz do souboru `System.Linq.Expressions` pro obor názvů. `Imports`</span><span class="sxs-lookup"><span data-stu-id="8d815-117">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

5. <span data-ttu-id="8d815-118">Přidejte kód do `Main` metody v souboru Module1. vb pro vytvoření stromu výrazu a předejte ho do metody, která ho upraví.</span><span class="sxs-lookup"><span data-stu-id="8d815-118">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>

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

    <span data-ttu-id="8d815-119">Kód vytvoří výraz, který obsahuje podmíněnou `AND` operaci.</span><span class="sxs-lookup"><span data-stu-id="8d815-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="8d815-120">Potom vytvoří instanci `AndAlsoModifier` třídy a předá výraz `Modify` metodě této třídy.</span><span class="sxs-lookup"><span data-stu-id="8d815-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="8d815-121">Původní a upravené stromy výrazů jsou zobrazeny, aby se změna zobrazila.</span><span class="sxs-lookup"><span data-stu-id="8d815-121">Both the original and the modified expression trees are outputted to show the change.</span></span>

6. <span data-ttu-id="8d815-122">Zkompilujte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d815-122">Compile and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d815-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d815-123">See also</span></span>

- [<span data-ttu-id="8d815-124">Postupy: Spuštění stromů výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d815-124">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="8d815-125">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d815-125">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
