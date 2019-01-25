---
title: 'Postupy: Použití uložených procedur mapovaných pro vícečetné tvary výsledků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 6ea318e89cf91dcbf16747117b8000dfa3f9571d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573666"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="10cd7-102">Postupy: Použití uložených procedur mapovaných pro vícečetné tvary výsledků</span><span class="sxs-lookup"><span data-stu-id="10cd7-102">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>
<span data-ttu-id="10cd7-103">Při vícečetné tvary výsledků můžete vrátit uložené procedury, návratový typ nelze silně typováno do obrazec jeden projekce.</span><span class="sxs-lookup"><span data-stu-id="10cd7-103">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="10cd7-104">I když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvářet všechny typy možných projekce, se nemůže vědět, pořadí, ve kterém bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="10cd7-104">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="10cd7-105">Tento scénář s uloženými procedurami, které postupně vyvolávají vícečetné tvary výsledků kontrast.</span><span class="sxs-lookup"><span data-stu-id="10cd7-105">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="10cd7-106">Další informace najdete v tématu [jak: Použití uložených procedur mapovaných pro sekvenční tvary výsledků](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="10cd7-106">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="10cd7-107"><xref:System.Data.Linq.Mapping.ResultTypeAttribute> Atributu se použije pro uložené procedury, které vrací více typů výsledků pro určení sady typů procedura může vrátit.</span><span class="sxs-lookup"><span data-stu-id="10cd7-107">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10cd7-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="10cd7-108">Example</span></span>  
 <span data-ttu-id="10cd7-109">V následujícím příkladu kódu SQL, tvar výsledek závisí na vstupu (`shape =1` nebo `shape = 2`).</span><span class="sxs-lookup"><span data-stu-id="10cd7-109">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="10cd7-110">Nevíte, které projekce bude vrácen první.</span><span class="sxs-lookup"><span data-stu-id="10cd7-110">You do not know which projection will be returned first.</span></span>  
  
```  
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="10cd7-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="10cd7-111">Example</span></span>  
 <span data-ttu-id="10cd7-112">Podobně jako následujícím kódu můžete použít k provedení tuto uloženou proceduru.</span><span class="sxs-lookup"><span data-stu-id="10cd7-112">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10cd7-113">Je nutné použít <xref:System.Data.Linq.IMultipleResults.GetResult%2A> vzor, který má získat enumerátor správný typ, na základě vašich znalostí uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="10cd7-113">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="10cd7-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10cd7-114">See also</span></span>
- [<span data-ttu-id="10cd7-115">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="10cd7-115">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
