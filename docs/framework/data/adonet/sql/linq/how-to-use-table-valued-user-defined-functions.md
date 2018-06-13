---
title: 'Postupy: použití funkce vracející tabulku uživatelem definované'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: e0199bb0a783f54931885053681c48d288012404
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362896"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="e9e37-102">Postupy: použití funkce vracející tabulku uživatelem definované</span><span class="sxs-lookup"><span data-stu-id="e9e37-102">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="e9e37-103">Funkce vracející tabulku vrátí jedné sady řádků (na rozdíl od uložené procedury, které může vrátit více výsledků obrazců).</span><span class="sxs-lookup"><span data-stu-id="e9e37-103">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="e9e37-104">Vzhledem k tomu, že je návratový typ funkce vracející tabulku `Table`, funkce vracející tabulku můžete použít kdekoli v SQL, které můžete tabulku.</span><span class="sxs-lookup"><span data-stu-id="e9e37-104">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="e9e37-105">Funkce vracející tabulku lze považovat také stejně jako tabulku.</span><span class="sxs-lookup"><span data-stu-id="e9e37-105">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9e37-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9e37-106">Example</span></span>  
 <span data-ttu-id="e9e37-107">Následující příkaz SQL funkce explicitně stavy, které vrátí `TABLE`.</span><span class="sxs-lookup"><span data-stu-id="e9e37-107">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="e9e37-108">Proto je definována implicitně strukturu vrácených řádků.</span><span class="sxs-lookup"><span data-stu-id="e9e37-108">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="e9e37-109"> mapuje funkce následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e9e37-109"> maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="e9e37-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9e37-110">Example</span></span>  
 <span data-ttu-id="e9e37-111">Následující kód SQL ukazuje, že můžete připojit k tabulce, která funkce vrátí hodnotu a jinak s nimi zacházet stejně jako ostatní tabulky:</span><span class="sxs-lookup"><span data-stu-id="e9e37-111">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="e9e37-112">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], dotaz vykreslená takto:</span><span class="sxs-lookup"><span data-stu-id="e9e37-112">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e9e37-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9e37-113">See Also</span></span>  
 [<span data-ttu-id="e9e37-114">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="e9e37-114">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
