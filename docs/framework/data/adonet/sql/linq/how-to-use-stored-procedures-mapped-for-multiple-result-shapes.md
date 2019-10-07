---
title: 'Postupy: použití uložených procedur mapovaných pro více obrazců výsledků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 065e866ec5937c4af31c0b1563a7582cb4112eba
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003267"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="6c05c-102">Postupy: použití uložených procedur mapovaných pro více obrazců výsledků</span><span class="sxs-lookup"><span data-stu-id="6c05c-102">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>
<span data-ttu-id="6c05c-103">Pokud uložená procedura může vracet více tvarů výsledků, nemůže být návratový typ silným typem pro jeden obrazec projekce.</span><span class="sxs-lookup"><span data-stu-id="6c05c-103">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="6c05c-104">I když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] může generovat všechny možné typy projekce, nemůže znát pořadí, ve kterém se budou vracet.</span><span class="sxs-lookup"><span data-stu-id="6c05c-104">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="6c05c-105">Porovnejte tento scénář s uloženými procedurami, které vydávají více výsledných tvarů postupně.</span><span class="sxs-lookup"><span data-stu-id="6c05c-105">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="6c05c-106">Další informace najdete v tématu [Postupy: použití uložených procedur mapovaných pro sekvenční obrazce výsledků](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="6c05c-106">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="6c05c-107">Atribut <xref:System.Data.Linq.Mapping.ResultTypeAttribute> se použije u uložených procedur, které vracejí více typů výsledků k určení sady typů, které může procedura vracet.</span><span class="sxs-lookup"><span data-stu-id="6c05c-107">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c05c-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c05c-108">Example</span></span>  
 <span data-ttu-id="6c05c-109">V následujícím příkladu kódu SQL závisí obrazec výsledků na vstupu (`shape =1` nebo `shape = 2`).</span><span class="sxs-lookup"><span data-stu-id="6c05c-109">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="6c05c-110">Nevíte, které projekce se budou vracet jako první.</span><span class="sxs-lookup"><span data-stu-id="6c05c-110">You do not know which projection will be returned first.</span></span>  
  
``` sql
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="6c05c-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c05c-111">Example</span></span>  
 <span data-ttu-id="6c05c-112">Chcete-li provést tuto uloženou proceduru, použijte kód podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="6c05c-112">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c05c-113">Je nutné použít vzor <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pro získání výčtu správného typu v závislosti na vaší znalosti uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="6c05c-113">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="6c05c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c05c-114">See also</span></span>

- [<span data-ttu-id="6c05c-115">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="6c05c-115">Stored Procedures</span></span>](stored-procedures.md)
