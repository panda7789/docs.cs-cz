---
title: 'Postupy: Volání uživatelem definovaných vložených funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: ed8071352902b8f97445cbfa5ff0ebe8fead9bb9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163706"
---
# <a name="how-to-call-user-defined-functions-inline"></a>Postupy: Volání uživatelem definovaných vložených funkcí
I když bude možné volat vložené uživatelem definované funkce, funkce, které jsou zahrnuty v dotazu, jehož spuštění je odloženo nejsou udělat, dokud je dotaz proveden. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Při volání stejné funkce mimo dotazu, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří jednoduchý dotaz z výrazu volání metody. Tady je syntaxe jazyka SQL (parametr `@p0` je vázán na konstantu předaný):  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří následující:  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a>Příklad  
 V následujícím [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazu, můžete zobrazit vložený volání metody generované uživatelem definovanou funkci `ReverseCustName`. Funkce není okamžitě provést, protože provádění dotazu je odloženo. SQL sestavena pro tento dotaz se přeloží na volání funkce definované uživatelem v databázi (viz kód SQL následující dotaz).  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a>Viz také:

- [Uživatelem definované funkce](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
