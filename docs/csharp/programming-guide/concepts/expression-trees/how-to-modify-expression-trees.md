---
title: 'Postupy: Úpravy stromů výrazů (C#)'
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 26c00f3acc7ab44e74a81e346ab1c017d95d53b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308637"
---
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="5d479-102">Postupy: Úpravy stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="5d479-102">How to: Modify Expression Trees (C#)</span></span>
<span data-ttu-id="5d479-103">Toto téma ukazuje, jak upravit strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="5d479-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="5d479-104">Stromy výrazů jsou neměnné, což znamená, že nejde změnit napřímo.</span><span class="sxs-lookup"><span data-stu-id="5d479-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="5d479-105">Chcete-li změnit strom výrazu, musíte vytvořit kopie stávající strom výrazu a při vytváření kopie, proveďte požadované změny.</span><span class="sxs-lookup"><span data-stu-id="5d479-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="5d479-106">Můžete použít <xref:System.Linq.Expressions.ExpressionVisitor> třídy k procházení stávající strom výrazu a zkopírovat každý uzel, který ho navštíví.</span><span class="sxs-lookup"><span data-stu-id="5d479-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="5d479-107">Chcete-li změnit strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="5d479-107">To modify an expression tree</span></span>  
  
1. <span data-ttu-id="5d479-108">Vytvořte nový **konzolovou aplikaci** projektu.</span><span class="sxs-lookup"><span data-stu-id="5d479-108">Create a new **Console Application** project.</span></span>  
  
2. <span data-ttu-id="5d479-109">Přidat `using` direktivy v souboru `System.Linq.Expressions` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5d479-109">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3. <span data-ttu-id="5d479-110">Přidat `AndAlsoModifier` třídy do projektu.</span><span class="sxs-lookup"><span data-stu-id="5d479-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="5d479-111">Tato třída dědí <xref:System.Linq.Expressions.ExpressionVisitor> třídy a je zaměřena na upravte výrazy, které představují podmíněného `AND` operace.</span><span class="sxs-lookup"><span data-stu-id="5d479-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="5d479-112">Tyto operace se změní z s podmínkou `AND` do s podmínkou `OR`.</span><span class="sxs-lookup"><span data-stu-id="5d479-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="5d479-113">K tomu, třída přepsání <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metodu základního typu, protože podmíněné `AND` výrazy jsou reprezentovány jako binární výrazy.</span><span class="sxs-lookup"><span data-stu-id="5d479-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="5d479-114">V `VisitBinary` metodu, pokud výraz, který je předán představuje s podmínkou `AND` operace, vytvoří kód, který obsahuje podmíněný výraz new `OR` místo podmíněný operátor `AND` operátor.</span><span class="sxs-lookup"><span data-stu-id="5d479-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="5d479-115">Pokud výraz, který je předán `VisitBinary` nepředstavuje s podmínkou `AND` operace, odloží metody k implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="5d479-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="5d479-116">Metody třídy base konstrukce uzlů, které jsou podobné stromů výrazů, které jsou předány v, ale uzly mají jejich sub stromů nahradí stromů výrazů, které jsou vytvořené rekurzivně návštěvníkem.</span><span class="sxs-lookup"><span data-stu-id="5d479-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4. <span data-ttu-id="5d479-117">Přidat `using` direktivy v souboru `System.Linq.Expressions` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5d479-117">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5. <span data-ttu-id="5d479-118">Přidejte kód, který `Main` metody v souboru Program.cs vytvořte strom výrazů a předat ho metodě, která jej upravíte.</span><span class="sxs-lookup"><span data-stu-id="5d479-118">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="5d479-119">Kód vytvoří výraz, který obsahuje s podmínkou `AND` operace.</span><span class="sxs-lookup"><span data-stu-id="5d479-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="5d479-120">Potom vytvoří instanci `AndAlsoModifier` třídy a předává výraz, který má `Modify` metody této třídy.</span><span class="sxs-lookup"><span data-stu-id="5d479-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="5d479-121">Původní a stromů výrazů změny jsou výstupem ještě neprojevila změna.</span><span class="sxs-lookup"><span data-stu-id="5d479-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6. <span data-ttu-id="5d479-122">Kompilace a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d479-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d479-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d479-123">See also</span></span>

- [<span data-ttu-id="5d479-124">Postupy: Provádění stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="5d479-124">How to: Execute Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="5d479-125">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="5d479-125">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
