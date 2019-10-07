---
title: 'Postupy: použití uložených procedur mapovaných pro sekvenční obrazce výsledků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 8378a175ab2479ab9769ca08579e1c89269eaba4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003219"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="95647-102">Postupy: použití uložených procedur mapovaných pro sekvenční obrazce výsledků</span><span class="sxs-lookup"><span data-stu-id="95647-102">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>
<span data-ttu-id="95647-103">Tento druh uložené procedury může generovat více než jeden obrazec výsledku, ale víte, v jakém pořadí se výsledky vrátí.</span><span class="sxs-lookup"><span data-stu-id="95647-103">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="95647-104">Porovnejte tento scénář se scénářem, ve kterém neznáte sekvenci vrácených možností.</span><span class="sxs-lookup"><span data-stu-id="95647-104">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="95647-105">Další informace najdete v tématu [Postupy: použití uložených procedur mapovaných pro více obrazců výsledků](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="95647-105">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95647-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="95647-106">Example</span></span>  
 <span data-ttu-id="95647-107">Zde je T-SQL uložené procedury, která vrací více výsledných tvarů postupně:</span><span class="sxs-lookup"><span data-stu-id="95647-107">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```sql
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="95647-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="95647-108">Example</span></span>  
 <span data-ttu-id="95647-109">Chcete-li provést tuto uloženou proceduru, použijte kód podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="95647-109">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="95647-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95647-110">See also</span></span>

- [<span data-ttu-id="95647-111">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="95647-111">Stored Procedures</span></span>](stored-procedures.md)
