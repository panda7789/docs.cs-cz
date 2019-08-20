---
title: 'Postupy: Úprava stromů výrazů (C#)'
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 7875cf1ccca8866cc87ebec80701ad77ad2bea2d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595055"
---
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="e36aa-102">Postupy: Úprava stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="e36aa-102">How to: Modify Expression Trees (C#)</span></span>
<span data-ttu-id="e36aa-103">V tomto tématu se dozvíte, jak upravit strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="e36aa-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="e36aa-104">Stromy výrazů jsou neměnné, což znamená, že je nelze upravovat přímo.</span><span class="sxs-lookup"><span data-stu-id="e36aa-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="e36aa-105">Chcete-li změnit strom výrazu, je nutné vytvořit kopii existujícího stromu výrazů a při vytváření kopie provést požadované změny.</span><span class="sxs-lookup"><span data-stu-id="e36aa-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="e36aa-106"><xref:System.Linq.Expressions.ExpressionVisitor> Třídu můžete použít k procházení existujícího stromu výrazů a ke zkopírování jednotlivých uzlů, které navštíví.</span><span class="sxs-lookup"><span data-stu-id="e36aa-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="e36aa-107">Úprava stromu výrazu</span><span class="sxs-lookup"><span data-stu-id="e36aa-107">To modify an expression tree</span></span>  
  
1. <span data-ttu-id="e36aa-108">Vytvořte nový projekt **konzolové aplikace** .</span><span class="sxs-lookup"><span data-stu-id="e36aa-108">Create a new **Console Application** project.</span></span>  
  
2. <span data-ttu-id="e36aa-109">Přidejte do souboru `System.Linq.Expressions` pro obor názvů direktivu.`using`</span><span class="sxs-lookup"><span data-stu-id="e36aa-109">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3. <span data-ttu-id="e36aa-110">`AndAlsoModifier` Přidejte třídu do projektu.</span><span class="sxs-lookup"><span data-stu-id="e36aa-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="e36aa-111">Tato třída dědí <xref:System.Linq.Expressions.ExpressionVisitor> třídu a je specializovaná na úpravu výrazů, které reprezentují podmíněné `AND` operace.</span><span class="sxs-lookup"><span data-stu-id="e36aa-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="e36aa-112">Tyto operace mění z podmíněného `AND` na podmíněný. `OR`</span><span class="sxs-lookup"><span data-stu-id="e36aa-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="e36aa-113">K tomu třída Přepisuje <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metodu základního typu, protože podmíněné `AND` výrazy jsou reprezentovány jako binární výrazy.</span><span class="sxs-lookup"><span data-stu-id="e36aa-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="e36aa-114">V případě, že výraz, který je předán do, představuje podmíněnou `AND` operaci, kód vytvoří nový výraz, který obsahuje podmíněný `OR` operátor místo podmíněného `AND`. `VisitBinary` podnikatel.</span><span class="sxs-lookup"><span data-stu-id="e36aa-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="e36aa-115">Pokud výraz, který je předán do `VisitBinary` , nepředstavuje podmíněnou `AND` operaci, metoda se odloží k implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="e36aa-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="e36aa-116">Metody základní třídy konstrukce uzly, které jsou jako stromy výrazů, které jsou předány, ale uzly mají své dílčí stromy nahrazené stromy výrazů, které jsou vytvářeny rekurzivně návštěvníkem.</span><span class="sxs-lookup"><span data-stu-id="e36aa-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4. <span data-ttu-id="e36aa-117">Přidejte do souboru `System.Linq.Expressions` pro obor názvů direktivu.`using`</span><span class="sxs-lookup"><span data-stu-id="e36aa-117">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5. <span data-ttu-id="e36aa-118">Přidejte kód do `Main` metody v souboru program.cs pro vytvoření stromu výrazu a předejte ho metodě, která ho upraví.</span><span class="sxs-lookup"><span data-stu-id="e36aa-118">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="e36aa-119">Kód vytvoří výraz, který obsahuje podmíněnou `AND` operaci.</span><span class="sxs-lookup"><span data-stu-id="e36aa-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="e36aa-120">Potom vytvoří instanci `AndAlsoModifier` třídy a předá výraz `Modify` metodě této třídy.</span><span class="sxs-lookup"><span data-stu-id="e36aa-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="e36aa-121">Původní a upravené stromy výrazů jsou zobrazeny, aby se změna zobrazila.</span><span class="sxs-lookup"><span data-stu-id="e36aa-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6. <span data-ttu-id="e36aa-122">Zkompilujte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e36aa-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e36aa-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e36aa-123">See also</span></span>

- [<span data-ttu-id="e36aa-124">Postupy: Spuštění stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="e36aa-124">How to: Execute Expression Trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="e36aa-125">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="e36aa-125">Expression Trees (C#)</span></span>](./index.md)
