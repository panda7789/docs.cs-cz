---
title: 'Postupy: používání uživatelsky definovaných funkcí s hodnotou tabulky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: c4b5290e4f1aa69c7f55951d526ccb303a5a95ec
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003181"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="7dc7f-102">Postupy: používání uživatelsky definovaných funkcí s hodnotou tabulky</span><span class="sxs-lookup"><span data-stu-id="7dc7f-102">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="7dc7f-103">Funkce vracející tabulku vrací jedinou sadu řádků (na rozdíl od uložených procedur, které mohou vracet více tvarů výsledků).</span><span class="sxs-lookup"><span data-stu-id="7dc7f-103">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="7dc7f-104">Vzhledem k tomu, že návratový typ funkce vracející tabulku je `Table`, můžete použít funkci vracející tabulku kdekoli v SQL, kterou můžete použít v tabulce.</span><span class="sxs-lookup"><span data-stu-id="7dc7f-104">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="7dc7f-105">Funkci vracející tabulku můžete také zacházet stejně jako s tabulkou.</span><span class="sxs-lookup"><span data-stu-id="7dc7f-105">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dc7f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7dc7f-106">Example</span></span>  
 <span data-ttu-id="7dc7f-107">Následující funkce SQL explicitně uvádí, že vrací `TABLE`.</span><span class="sxs-lookup"><span data-stu-id="7dc7f-107">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="7dc7f-108">Proto je vrácená struktura sady řádků implicitně definovaná.</span><span class="sxs-lookup"><span data-stu-id="7dc7f-108">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```sql
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7dc7f-109">mapuje funkci následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7dc7f-109">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="7dc7f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="7dc7f-110">Example</span></span>  
 <span data-ttu-id="7dc7f-111">Následující kód SQL ukazuje, že se můžete připojit k tabulce, kterou funkce vrátí, a jinak ji nakládat jako na jinou tabulku:</span><span class="sxs-lookup"><span data-stu-id="7dc7f-111">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```sql
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="7dc7f-112">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se dotaz vykreslí takto:</span><span class="sxs-lookup"><span data-stu-id="7dc7f-112">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7dc7f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7dc7f-113">See also</span></span>

- [<span data-ttu-id="7dc7f-114">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="7dc7f-114">User-Defined Functions</span></span>](user-defined-functions.md)
