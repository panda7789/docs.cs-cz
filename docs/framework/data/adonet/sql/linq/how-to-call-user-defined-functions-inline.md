---
title: 'Postupy: Volání uživatelem definovaných vložených funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 26eafb9a6ea1a0b416d205e94b0e420b0f4059d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941076"
---
# <a name="how-to-call-user-defined-functions-inline"></a>Postupy: Volání uživatelem definovaných vložených funkcí
I když můžete volat uživatelsky definované funkce vložené, funkce, které jsou zahrnuty v dotazu, jehož spuštění je odloženo, nejsou provedeny, dokud není dotaz proveden. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Když zavoláte stejnou funkci mimo dotaz, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří se jednoduchý dotaz z výrazu volání metody. Následuje syntaxe SQL (parametr `@p0` je svázán s předaným konstantou):  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Vytvoří následující:  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a>Příklad  
 V následujícím [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazu vidíte vložené volání do vygenerované uživatelsky definované metody `ReverseCustName`Function. Funkce není provedena ihned, protože provádění dotazu je odloženo. SQL sestavený pro tento dotaz se překládá na volání uživatelsky definované funkce v databázi (viz kód SQL, který následuje dotaz).  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a>Viz také:

- [Uživatelem definované funkce](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
