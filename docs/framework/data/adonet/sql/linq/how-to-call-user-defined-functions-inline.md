---
title: 'Postupy: volání vložených funkcí definovaných uživatelem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 01ba9ab4359cbd124b2207c87d5dae904641911a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002981"
---
# <a name="how-to-call-user-defined-functions-inline"></a>Postupy: volání vložených funkcí definovaných uživatelem
I když můžete volat uživatelsky definované funkce vložené, funkce, které jsou zahrnuty v dotazu, jehož spuštění je odloženo, nejsou provedeny, dokud není dotaz proveden. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Když zavoláte stejnou funkci mimo dotaz, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří jednoduchý dotaz z výrazu volání metody. Následuje syntaxe SQL (parametr `@p0` je svázán s předaným konstantou):  
  
```sql  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří následující:  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a>Příklad  
 V následujících dotazech [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] můžete zobrazit vložené volání uživatelsky definované metody funkce `ReverseCustName`. Funkce není provedena ihned, protože provádění dotazu je odloženo. SQL sestavený pro tento dotaz se překládá na volání uživatelsky definované funkce v databázi (viz kód SQL, který následuje dotaz).  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```sql  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a>Viz také:

- [Uživatelem definované funkce](user-defined-functions.md)
