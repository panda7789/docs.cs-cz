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
# <a name="how-to-use-table-valued-user-defined-functions"></a>Postupy: používání uživatelsky definovaných funkcí s hodnotou tabulky
Funkce vracející tabulku vrací jedinou sadu řádků (na rozdíl od uložených procedur, které mohou vracet více tvarů výsledků). Vzhledem k tomu, že návratový typ funkce vracející tabulku je `Table`, můžete použít funkci vracející tabulku kdekoli v SQL, kterou můžete použít v tabulce. Funkci vracející tabulku můžete také zacházet stejně jako s tabulkou.  
  
## <a name="example"></a>Příklad  
 Následující funkce SQL explicitně uvádí, že vrací `TABLE`. Proto je vrácená struktura sady řádků implicitně definovaná.  
  
```sql
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje funkci následujícím způsobem:  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a>Příklad  
 Následující kód SQL ukazuje, že se můžete připojit k tabulce, kterou funkce vrátí, a jinak ji nakládat jako na jinou tabulku:  
  
```sql
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se dotaz vykreslí takto:  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Uživatelem definované funkce](user-defined-functions.md)
