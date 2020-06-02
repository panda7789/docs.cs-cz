---
title: 'Postupy: Použití uživatelem definovaných funkcí s tabulkovými hodnotami'
description: Pomocí těchto příkladů se naučíte, jak vytvořit funkci vracející tabulku, která vrací jedinou sadu řádků. Tuto funkci vracející tabulku použijte stejně jako tabulku.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: 44866367393e321d7dd2db965e2fad8a2e6b63e9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286323"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="255d4-104">Postupy: Použití uživatelem definovaných funkcí s tabulkovými hodnotami</span><span class="sxs-lookup"><span data-stu-id="255d4-104">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="255d4-105">Funkce vracející tabulku vrací jedinou sadu řádků (na rozdíl od uložených procedur, které mohou vracet více tvarů výsledků).</span><span class="sxs-lookup"><span data-stu-id="255d4-105">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="255d4-106">Vzhledem k tomu, že návratový typ funkce vracející tabulku je `Table` , můžete použít funkci vracející tabulku kdekoli v SQL, kterou můžete použít v tabulce.</span><span class="sxs-lookup"><span data-stu-id="255d4-106">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="255d4-107">Funkci vracející tabulku můžete také zacházet stejně jako s tabulkou.</span><span class="sxs-lookup"><span data-stu-id="255d4-107">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="255d4-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="255d4-108">Example</span></span>  
 <span data-ttu-id="255d4-109">Následující funkce SQL explicitně uvádí, že vrátí `TABLE` .</span><span class="sxs-lookup"><span data-stu-id="255d4-109">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="255d4-110">Proto je vrácená struktura sady řádků implicitně definovaná.</span><span class="sxs-lookup"><span data-stu-id="255d4-110">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```sql
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="255d4-111">mapuje funkci následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="255d4-111">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="255d4-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="255d4-112">Example</span></span>  
 <span data-ttu-id="255d4-113">Následující kód SQL ukazuje, že se můžete připojit k tabulce, kterou funkce vrátí, a jinak ji nakládat jako na jinou tabulku:</span><span class="sxs-lookup"><span data-stu-id="255d4-113">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```sql
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="255d4-114">V nástroji se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotaz vykreslí takto:</span><span class="sxs-lookup"><span data-stu-id="255d4-114">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="255d4-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="255d4-115">See also</span></span>

- [<span data-ttu-id="255d4-116">Uživatelsky definované funkce</span><span class="sxs-lookup"><span data-stu-id="255d4-116">User-Defined Functions</span></span>](user-defined-functions.md)
