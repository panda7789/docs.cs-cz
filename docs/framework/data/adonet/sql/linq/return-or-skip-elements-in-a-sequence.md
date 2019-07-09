---
title: Vrácení nebo přeskočení prvků v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: e0f2c6300f8dccb8cc316527af9c75f6a40ff2df
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661900"
---
# <a name="return-or-skip-elements-in-a-sequence"></a>Vrácení nebo přeskočení prvků v posloupnosti
Použití <xref:System.Linq.Queryable.Take%2A> operátor potom přeskočit zbývající a vrátí daný počet prvků v sekvenci.  
  
 Použití <xref:System.Linq.Queryable.Skip%2A> operátor přeskočit daný počet prvků v posloupnosti a pak se vraťte zbytek.  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, když se používají v dotazech pro SQL Server 2000. Další informace najdete v tématu "Přeskočit a převzít výjimky v systému SQL Server 2000" položka v [Poradce při potížích s](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Přeloží <xref:System.Linq.Queryable.Skip%2A> pomocí poddotazu SQL `NOT EXISTS` klauzuli. Tento překlad má následující omezení:  
  
- Argument musí být sada. Multisets nejsou podporovány, i v případě, že řazení.  
  
- Generování dotazu může být mnohem složitější než dotaz vygenerovaný pro základní dotaz, na kterém <xref:System.Linq.Queryable.Skip%2A> platí. Tato složitost může způsobit snížení výkonu nebo dokonce i vypršení časového limitu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Take` vybrat prvních pět `Employees` pověřili. Všimněte si, že kolekce je nejprve seřazené podle `HireDate`.  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Queryable.Skip%2A> vybrat všechny s výjimkou nejdražší 10 `Products`.  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>Příklad  
 Kombinuje v následujícím příkladu <xref:System.Linq.Queryable.Skip%2A> a <xref:System.Linq.Queryable.Take%2A> metody přeskočte prvních 50 záznamy a vrátíte se na další 10.  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A> operace jsou dobře definované pouze proti seřazené sady. Sémantika pro Neseřazený sady nebo multisets není definován.  
  
 Z důvodu omezení na pořadí v SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se pokusí přesunout řazení v argumentu <xref:System.Linq.Queryable.Take%2A> nebo <xref:System.Linq.Queryable.Skip%2A> operátor má výsledek operátoru.  
  
> [!NOTE]
>  Překlad se liší pro SQL Server 2000 a SQL Server 2005. Pokud budete chtít použít <xref:System.Linq.Queryable.Skip%2A> pomocí dotazu jakékoli složitosti, SQL Server 2005.  
  
 Vezměte v úvahu následující [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotaz pro SQL Server 2000:  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Přesune řazení za účelem do kódu SQL, následujícím způsobem:  
  
```  
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 Když <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A> jsou zřetězen dohromady, všechny zadané řazení musí být konzistentní vzhledem k aplikacím. V opačném případě nejsou výsledky definovány.  
  
 Pro záporná, konstantní celočíselné argumenty podle specifikace SQL i <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A> jsou dobře definované.  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Převod standardních operátorů dotazů](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
