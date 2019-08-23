---
title: 'Postupy: Použití uložených procedur mapovaných pro vícečetné tvary výsledků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 22614be8e53d975c4efdf7004f41906c58639c61
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938693"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="0c657-102">Postupy: Použití uložených procedur mapovaných pro vícečetné tvary výsledků</span><span class="sxs-lookup"><span data-stu-id="0c657-102">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>
<span data-ttu-id="0c657-103">Pokud uložená procedura může vracet více tvarů výsledků, nemůže být návratový typ silným typem pro jeden obrazec projekce.</span><span class="sxs-lookup"><span data-stu-id="0c657-103">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="0c657-104">I [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] když může generovat všechny možné typy projekce, nemůže znát pořadí, ve kterém se budou vracet.</span><span class="sxs-lookup"><span data-stu-id="0c657-104">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="0c657-105">Porovnejte tento scénář s uloženými procedurami, které vydávají více výsledných tvarů postupně.</span><span class="sxs-lookup"><span data-stu-id="0c657-105">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="0c657-106">Další informace najdete v tématu [jak: Použijte uložené procedury mapované pro obrazce](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)sekvenčních výsledků.</span><span class="sxs-lookup"><span data-stu-id="0c657-106">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="0c657-107"><xref:System.Data.Linq.Mapping.ResultTypeAttribute> Atribut je použit pro uložené procedury, které vracejí více výsledků typů pro určení sady typů, které může procedura vracet.</span><span class="sxs-lookup"><span data-stu-id="0c657-107">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c657-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c657-108">Example</span></span>  
 <span data-ttu-id="0c657-109">V následujícím příkladu kódu SQL závisí obrazec výsledek na vstupu (`shape =1` nebo `shape = 2`).</span><span class="sxs-lookup"><span data-stu-id="0c657-109">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="0c657-110">Nevíte, které projekce se budou vracet jako první.</span><span class="sxs-lookup"><span data-stu-id="0c657-110">You do not know which projection will be returned first.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="0c657-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c657-111">Example</span></span>  
 <span data-ttu-id="0c657-112">Chcete-li provést tuto uloženou proceduru, použijte kód podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="0c657-112">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c657-113">Je nutné použít <xref:System.Data.Linq.IMultipleResults.GetResult%2A> vzor pro získání výčtu správného typu na základě vaší znalosti uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="0c657-113">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="0c657-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c657-114">See also</span></span>

- [<span data-ttu-id="0c657-115">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="0c657-115">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
