---
title: 'Postupy: pomocí uložených procedur mapovaný pro sekvenční výsledek tvarů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: ade123f10e1c9ffd6d042b45599cc6e352614e5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351937"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="ba5dd-102">Postupy: pomocí uložených procedur mapovaný pro sekvenční výsledek tvarů</span><span class="sxs-lookup"><span data-stu-id="ba5dd-102">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>
<span data-ttu-id="ba5dd-103">Tento druh uložené procedury mohou generovat více než jeden výsledek tvaru, ale vy víte, že pořadí, v jakém jsou vráceny výsledky.</span><span class="sxs-lookup"><span data-stu-id="ba5dd-103">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="ba5dd-104">Tento scénář se scénářem, kde si nejste jisti, pořadí se vrátí protějšek.</span><span class="sxs-lookup"><span data-stu-id="ba5dd-104">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="ba5dd-105">Další informace najdete v tématu [postupy: použití uložené procedury mapovaný pro více obrazců výsledek](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="ba5dd-105">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba5dd-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba5dd-106">Example</span></span>  
 <span data-ttu-id="ba5dd-107">Tady je T-SQL uložené procedury, jež vrátí více výsledků obrazců postupně:</span><span class="sxs-lookup"><span data-stu-id="ba5dd-107">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="ba5dd-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba5dd-108">Example</span></span>  
 <span data-ttu-id="ba5dd-109">Podobný následujícímu kódu byste použili k spouštět tuto uloženou proceduru.</span><span class="sxs-lookup"><span data-stu-id="ba5dd-109">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="ba5dd-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba5dd-110">See Also</span></span>  
 [<span data-ttu-id="ba5dd-111">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="ba5dd-111">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
