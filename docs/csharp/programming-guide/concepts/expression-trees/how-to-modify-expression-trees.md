---
title: 'Postupy: úpravy stromů výrazů (C#)'
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 3a43e2365475644d5081ced7bfec11e1a2b5121e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329839"
---
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="025b3-102">Postupy: úpravy stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="025b3-102">How to: Modify Expression Trees (C#)</span></span>
<span data-ttu-id="025b3-103">Toto téma ukazuje, jak upravit strom výrazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="025b3-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="025b3-104">Stromy výrazů jsou neměnné, což znamená, že je nelze změnit přímo.</span><span class="sxs-lookup"><span data-stu-id="025b3-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="025b3-105">Chcete-li změnit strom výrazu, musíte vytvořit kopii existující strom výrazu a při vytváření kopie, proveďte požadované změny.</span><span class="sxs-lookup"><span data-stu-id="025b3-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="025b3-106">Můžete použít <xref:System.Linq.Expressions.ExpressionVisitor> tříd procházení stávající strom výrazu a zkopírovat každý uzel, který ho navštíví.</span><span class="sxs-lookup"><span data-stu-id="025b3-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="025b3-107">Chcete-li upravit strom výrazu se nezdařilo</span><span class="sxs-lookup"><span data-stu-id="025b3-107">To modify an expression tree</span></span>  
  
1.  <span data-ttu-id="025b3-108">Vytvořte novou **konzolové aplikace** projektu.</span><span class="sxs-lookup"><span data-stu-id="025b3-108">Create a new **Console Application** project.</span></span>  
  
2.  <span data-ttu-id="025b3-109">Přidat `using` direktivy v souboru `System.Linq.Expressions` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="025b3-109">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3.  <span data-ttu-id="025b3-110">Přidat `AndAlsoModifier` třídu do projektu.</span><span class="sxs-lookup"><span data-stu-id="025b3-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="025b3-111">Tato třída dědí <xref:System.Linq.Expressions.ExpressionVisitor> třídy a se specializuje k úpravě výrazy, které představují podmíněného `AND` operace.</span><span class="sxs-lookup"><span data-stu-id="025b3-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="025b3-112">Změní tyto operace z podmíněného `AND` k podmíněného `OR`.</span><span class="sxs-lookup"><span data-stu-id="025b3-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="025b3-113">K tomu, třída přepsání <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metoda základního typu, protože podmíněného `AND` výrazy jsou reprezentovány jako binární výrazy.</span><span class="sxs-lookup"><span data-stu-id="025b3-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="025b3-114">V `VisitBinary` metodu, pokud výraz, který je předán představuje podmíněného `AND` operace, kód vytvoří nový výraz, který obsahuje podmínku `OR` operátor místo podmínku `AND` operátor.</span><span class="sxs-lookup"><span data-stu-id="025b3-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="025b3-115">Pokud výraz, který je předán `VisitBinary` nepředstavuje podmíněného `AND` operace, metody odkládat údaje k implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="025b3-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="025b3-116">Metody třídy base konstrukce uzlů, které jsou podobné stromů výrazů, které se předávají v, ale uzly mají jejich dílčí stromy nahradí stromů výrazů, které se vytváří rekurzivně návštěvníkem.</span><span class="sxs-lookup"><span data-stu-id="025b3-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4.  <span data-ttu-id="025b3-117">Přidat `using` direktivy v souboru `System.Linq.Expressions` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="025b3-117">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5.  <span data-ttu-id="025b3-118">Přidejte kód, který `Main` metoda v souboru Program.cs vytvořit strom výrazu a jejich předávání do metody, upraví.</span><span class="sxs-lookup"><span data-stu-id="025b3-118">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="025b3-119">Kód vytvoří výraz, který obsahuje podmíněného `AND` operaci.</span><span class="sxs-lookup"><span data-stu-id="025b3-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="025b3-120">Potom vytvoří instanci `AndAlsoModifier` třídy a předá výraz, který se `Modify` metoda této třídy.</span><span class="sxs-lookup"><span data-stu-id="025b3-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="025b3-121">Chcete-li zobrazit změny jsou výstupem původní i stromy upravené výrazů.</span><span class="sxs-lookup"><span data-stu-id="025b3-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6.  <span data-ttu-id="025b3-122">Zkompilování a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="025b3-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="025b3-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="025b3-123">See Also</span></span>  
 [<span data-ttu-id="025b3-124">Postupy: provádění stromů výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="025b3-124">How to: Execute Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [<span data-ttu-id="025b3-125">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="025b3-125">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
