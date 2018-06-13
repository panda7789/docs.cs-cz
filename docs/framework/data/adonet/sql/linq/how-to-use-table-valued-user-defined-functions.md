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
# <a name="how-to-use-table-valued-user-defined-functions"></a>Postupy: použití funkce vracející tabulku uživatelem definované
Funkce vracející tabulku vrátí jedné sady řádků (na rozdíl od uložené procedury, které může vrátit více výsledků obrazců). Vzhledem k tomu, že je návratový typ funkce vracející tabulku `Table`, funkce vracející tabulku můžete použít kdekoli v SQL, které můžete tabulku. Funkce vracející tabulku lze považovat také stejně jako tabulku.  
  
## <a name="example"></a>Příklad  
 Následující příkaz SQL funkce explicitně stavy, které vrátí `TABLE`. Proto je definována implicitně strukturu vrácených řádků.  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje funkce následujícím způsobem:  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a>Příklad  
 Následující kód SQL ukazuje, že můžete připojit k tabulce, která funkce vrátí hodnotu a jinak s nimi zacházet stejně jako ostatní tabulky:  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], dotaz vykreslená takto:  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Uživatelem definované funkce](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
