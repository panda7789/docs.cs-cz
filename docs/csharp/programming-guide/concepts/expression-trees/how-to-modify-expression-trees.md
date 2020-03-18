---
title: Jak upravit stromy výrazů (C#)
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: e921c594497d02f5eb16cc60294e947e83636d7a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73969894"
---
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="e6646-102">Jak upravit stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="e6646-102">How to modify expression trees (C#)</span></span>
<span data-ttu-id="e6646-103">Toto téma ukazuje, jak upravit strom výrazů.</span><span class="sxs-lookup"><span data-stu-id="e6646-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="e6646-104">Stromy výrazů jsou neměnné, což znamená, že je nelze přímo změnit.</span><span class="sxs-lookup"><span data-stu-id="e6646-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="e6646-105">Chcete-li změnit strom výrazů, musíte vytvořit kopii existujícího stromu výrazů a při vytváření kopie proveďte požadované změny.</span><span class="sxs-lookup"><span data-stu-id="e6646-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="e6646-106">Třídu <xref:System.Linq.Expressions.ExpressionVisitor> můžete použít k procházení existujícího stromu výrazů a ke kopírování každého uzlu, který navštíví.</span><span class="sxs-lookup"><span data-stu-id="e6646-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="e6646-107">Úprava stromu výrazů</span><span class="sxs-lookup"><span data-stu-id="e6646-107">To modify an expression tree</span></span>  
  
1. <span data-ttu-id="e6646-108">Vytvořte nový projekt **konzolové aplikace.**</span><span class="sxs-lookup"><span data-stu-id="e6646-108">Create a new **Console Application** project.</span></span>  
  
2. <span data-ttu-id="e6646-109">Přidejte `using` direktivu `System.Linq.Expressions` do souboru pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e6646-109">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3. <span data-ttu-id="e6646-110">Přidejte `AndAlsoModifier` třídu do projektu.</span><span class="sxs-lookup"><span data-stu-id="e6646-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="e6646-111">Tato třída dědí třídu <xref:System.Linq.Expressions.ExpressionVisitor> a je specializovaná `AND` na úpravu výrazů, které představují podmíněné operace.</span><span class="sxs-lookup"><span data-stu-id="e6646-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="e6646-112">Změní tyto operace z `AND` podmíněné `OR`na podmíněné .</span><span class="sxs-lookup"><span data-stu-id="e6646-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="e6646-113">Chcete-li to provést, <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> třída přepíše metodu `AND` základního typu, protože podmíněné výrazy jsou reprezentovány jako binární výrazy.</span><span class="sxs-lookup"><span data-stu-id="e6646-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="e6646-114">V `VisitBinary` metodě, pokud výraz, který je `AND` předán představuje podmíněné operace, kód vytvoří `OR` nový výraz, `AND` který obsahuje podmíněný operátor namísto podmíněné operátor.</span><span class="sxs-lookup"><span data-stu-id="e6646-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="e6646-115">Pokud výraz, který `VisitBinary` je předán nepředstavuje podmíněné `AND` operace, metoda odkládá na implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="e6646-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="e6646-116">Metody základní třídy vytvářejí uzly, které jsou jako stromy výrazů, které jsou předány, ale uzly mají své dílčí stromy nahrazeny stromy výrazů, které jsou vytvářeny rekurzivně návštěvníkem.</span><span class="sxs-lookup"><span data-stu-id="e6646-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4. <span data-ttu-id="e6646-117">Přidejte `using` direktivu `System.Linq.Expressions` do souboru pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e6646-117">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5. <span data-ttu-id="e6646-118">Přidejte kód `Main` do metody v souboru Program.cs vytvořit strom výrazů a předat jej metodě, která jej upraví.</span><span class="sxs-lookup"><span data-stu-id="e6646-118">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="e6646-119">Kód vytvoří výraz, který `AND` obsahuje podmíněnou operaci.</span><span class="sxs-lookup"><span data-stu-id="e6646-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="e6646-120">Potom vytvoří instanci `AndAlsoModifier` třídy a předá výraz metodě `Modify` této třídy.</span><span class="sxs-lookup"><span data-stu-id="e6646-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="e6646-121">Původní i upravené stromy výrazů jsou výstupem pro zobrazení změny.</span><span class="sxs-lookup"><span data-stu-id="e6646-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6. <span data-ttu-id="e6646-122">Zkompilujte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e6646-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6646-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6646-123">See also</span></span>

- [<span data-ttu-id="e6646-124">Jak spustit stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="e6646-124">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="e6646-125">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="e6646-125">Expression Trees (C#)</span></span>](./index.md)
