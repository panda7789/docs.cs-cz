---
title: 'Postupy: Použití uložených procedur mapovaných pro sekvenční tvary výsledků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: e51ebacb3f6be849f7b871f2d12db3ea7476b117
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877068"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="0f178-102">Postupy: Použití uložených procedur mapovaných pro sekvenční tvary výsledků</span><span class="sxs-lookup"><span data-stu-id="0f178-102">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>
<span data-ttu-id="0f178-103">Tento druh uložené procedury lze generovat více než jeden prvek výsledek, ale vy víte, v jakém pořadí jsou vráceny výsledky.</span><span class="sxs-lookup"><span data-stu-id="0f178-103">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="0f178-104">Tento scénář se scénářem, pokud si nejste jisti pořadí vrátí kontrast.</span><span class="sxs-lookup"><span data-stu-id="0f178-104">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="0f178-105">Další informace najdete v tématu [jak: Použití uložených procedur mapovaných pro vícečetné tvary výsledků](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="0f178-105">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f178-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="0f178-106">Example</span></span>  
 <span data-ttu-id="0f178-107">Tady je T-SQL uloženou proceduru, která postupně vrací vícečetné tvary výsledků:</span><span class="sxs-lookup"><span data-stu-id="0f178-107">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="0f178-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="0f178-108">Example</span></span>  
 <span data-ttu-id="0f178-109">Podobně jako následujícím kódu můžete použít k provedení tuto uloženou proceduru.</span><span class="sxs-lookup"><span data-stu-id="0f178-109">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="0f178-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f178-110">See also</span></span>

- [<span data-ttu-id="0f178-111">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="0f178-111">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
