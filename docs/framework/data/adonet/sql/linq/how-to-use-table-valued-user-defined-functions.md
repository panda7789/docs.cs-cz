---
title: 'Postupy: Použití uživatelem definovaných funkcí s tabulkovými hodnotami'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: eedc2e9b997e91ed9fe0038f260aa475d23a0627
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186826"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="268d2-102">Postupy: Použití uživatelem definovaných funkcí s tabulkovými hodnotami</span><span class="sxs-lookup"><span data-stu-id="268d2-102">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="268d2-103">Funkce vracející tabulku vrátí jednu sadu řádků (na rozdíl od uložené procedury, které může vrátit vícečetné tvary výsledků).</span><span class="sxs-lookup"><span data-stu-id="268d2-103">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="268d2-104">Vzhledem k tomu, že je návratový typ funkce vracející tabulku `Table`, funkce vracející tabulku můžete použít kdekoli v SQL, můžete použít tabulku.</span><span class="sxs-lookup"><span data-stu-id="268d2-104">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="268d2-105">Funkce vracející tabulku lze považovat také stejně jako tabulku.</span><span class="sxs-lookup"><span data-stu-id="268d2-105">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="268d2-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="268d2-106">Example</span></span>  
 <span data-ttu-id="268d2-107">Následující příkaz SQL funkce explicitně stavy, které se vrátí `TABLE`.</span><span class="sxs-lookup"><span data-stu-id="268d2-107">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="268d2-108">Proto je implicitně definovaný struktura vrácené sady řádků.</span><span class="sxs-lookup"><span data-stu-id="268d2-108">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="268d2-109">mapování funkce takto:</span><span class="sxs-lookup"><span data-stu-id="268d2-109">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="268d2-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="268d2-110">Example</span></span>  
 <span data-ttu-id="268d2-111">Následující kód SQL ukazuje, můžete připojit k tabulce, která vrací funkce a v opačném případě ji zpracovávat stejně jako ostatní tabulky:</span><span class="sxs-lookup"><span data-stu-id="268d2-111">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="268d2-112">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], dotaz by být vykreslen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="268d2-112">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="268d2-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="268d2-113">See also</span></span>

- [<span data-ttu-id="268d2-114">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="268d2-114">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
