---
title: Postup úpravy stromů výrazů (C#)
description: Naučte se, jak upravit strom výrazu vytvořením kopie existujícího stromu výrazů a provedením požadovaných změn.
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 45aea18e253811d4e5c60f23f7f8496d4358f64c
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105604"
---
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="665bb-103">Postup úpravy stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="665bb-103">How to modify expression trees (C#)</span></span>
<span data-ttu-id="665bb-104">V tomto tématu se dozvíte, jak upravit strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="665bb-104">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="665bb-105">Stromy výrazů jsou neměnné, což znamená, že je nelze upravovat přímo.</span><span class="sxs-lookup"><span data-stu-id="665bb-105">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="665bb-106">Chcete-li změnit strom výrazu, je nutné vytvořit kopii existujícího stromu výrazů a při vytváření kopie provést požadované změny.</span><span class="sxs-lookup"><span data-stu-id="665bb-106">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="665bb-107">Třídu můžete použít <xref:System.Linq.Expressions.ExpressionVisitor> k procházení existujícího stromu výrazů a ke zkopírování jednotlivých uzlů, které navštíví.</span><span class="sxs-lookup"><span data-stu-id="665bb-107">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="665bb-108">Úprava stromu výrazu</span><span class="sxs-lookup"><span data-stu-id="665bb-108">To modify an expression tree</span></span>  
  
1. <span data-ttu-id="665bb-109">Vytvořte nový projekt **konzolové aplikace** .</span><span class="sxs-lookup"><span data-stu-id="665bb-109">Create a new **Console Application** project.</span></span>  
  
2. <span data-ttu-id="665bb-110">Přidejte `using` do souboru pro obor názvů direktivu `System.Linq.Expressions` .</span><span class="sxs-lookup"><span data-stu-id="665bb-110">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3. <span data-ttu-id="665bb-111">Přidejte `AndAlsoModifier` třídu do projektu.</span><span class="sxs-lookup"><span data-stu-id="665bb-111">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="665bb-112">Tato třída dědí <xref:System.Linq.Expressions.ExpressionVisitor> třídu a je specializovaná na úpravu výrazů, které reprezentují podmíněné `AND` operace.</span><span class="sxs-lookup"><span data-stu-id="665bb-112">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="665bb-113">Tyto operace mění z podmíněného `AND` na podmíněný `OR` .</span><span class="sxs-lookup"><span data-stu-id="665bb-113">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="665bb-114">K tomu třída Přepisuje <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metodu základního typu, protože podmíněné `AND` výrazy jsou reprezentovány jako binární výrazy.</span><span class="sxs-lookup"><span data-stu-id="665bb-114">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="665bb-115">V `VisitBinary` metodě, pokud je výraz, který je předán, představuje podmíněnou `AND` operaci, kód vytvoří nový výraz, který obsahuje podmíněný `OR` operátor místo podmíněného `AND` operátoru.</span><span class="sxs-lookup"><span data-stu-id="665bb-115">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="665bb-116">Pokud výraz, který je předán do `VisitBinary` , nepředstavuje podmíněnou `AND` operaci, metoda se odloží k implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="665bb-116">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="665bb-117">Metody základní třídy konstrukce uzly, které jsou jako stromy výrazů, které jsou předány, ale uzly mají své dílčí stromy nahrazené stromy výrazů, které jsou vytvářeny rekurzivně návštěvníkem.</span><span class="sxs-lookup"><span data-stu-id="665bb-117">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4. <span data-ttu-id="665bb-118">Přidejte `using` do souboru pro obor názvů direktivu `System.Linq.Expressions` .</span><span class="sxs-lookup"><span data-stu-id="665bb-118">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5. <span data-ttu-id="665bb-119">Přidejte kód do `Main` metody v souboru program.cs pro vytvoření stromu výrazu a předejte ho metodě, která ho upraví.</span><span class="sxs-lookup"><span data-stu-id="665bb-119">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="665bb-120">Kód vytvoří výraz, který obsahuje podmíněnou `AND` operaci.</span><span class="sxs-lookup"><span data-stu-id="665bb-120">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="665bb-121">Potom vytvoří instanci `AndAlsoModifier` třídy a předá výraz `Modify` metodě této třídy.</span><span class="sxs-lookup"><span data-stu-id="665bb-121">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="665bb-122">Původní a upravené stromy výrazů jsou zobrazeny, aby se změna zobrazila.</span><span class="sxs-lookup"><span data-stu-id="665bb-122">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6. <span data-ttu-id="665bb-123">Zkompilujte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="665bb-123">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="665bb-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="665bb-124">See also</span></span>

- [<span data-ttu-id="665bb-125">Spuštění stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="665bb-125">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="665bb-126">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="665bb-126">Expression Trees (C#)</span></span>](./index.md)
