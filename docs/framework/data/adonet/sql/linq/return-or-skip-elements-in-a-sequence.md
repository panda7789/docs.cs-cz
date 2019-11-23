---
title: Vrácení nebo přeskočení prvků v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 7c98681493738b4e94ed14417fa1437efb6c12ac
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003307"
---
# <a name="return-or-skip-elements-in-a-sequence"></a>Vrácení nebo přeskočení prvků v posloupnosti
Použijte operátor <xref:System.Linq.Queryable.Take%2A>, který vrátí daný počet prvků v sekvenci a pak přeskočí na zbytek.  
  
 Pomocí operátoru <xref:System.Linq.Queryable.Skip%2A> můžete přeskočit daný počet prvků v sekvenci a potom vrátit zbytek.  
  
> [!NOTE]
> <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, pokud se používají v dotazech proti SQL Server 2000. Další informace najdete v části "přeskočení a přijetí výjimek v SQL Server 2000" v tématu [řešení potíží](troubleshooting.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá <xref:System.Linq.Queryable.Skip%2A> pomocí poddotazu s klauzulí SQL `NOT EXISTS`. Tento převod má následující omezení:  
  
- Argument musí být sada. Množiny s více sadami se nepodporují, i když jsou seřazené.  
  
- Vygenerovaný dotaz může být mnohem složitější než dotaz vygenerovaný pro základní dotaz, na kterém je <xref:System.Linq.Queryable.Skip%2A> použito. Tato složitost může způsobit snížení výkonu nebo dokonce i vypršení časového limitu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Take` k výběru prvních pěti `Employees` přijatých. Všimněte si, že je kolekce nejprve řazena podle `HireDate`.  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Queryable.Skip%2A> k výběru všech, kromě nejdražších `Products`10.  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou kombinovány metody <xref:System.Linq.Queryable.Skip%2A> a <xref:System.Linq.Queryable.Take%2A> k přeskočení prvních 50 záznamů a pak se vrátí další 10.  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 operace <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A> jsou dobře definovány pouze proti seřazeným sadám. Sémantika pro neuspořádané sady nebo více sad není definována.  
  
 Z důvodu omezení pro řazení v SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se pokusí přesunout pořadí argumentu operátoru <xref:System.Linq.Queryable.Take%2A> nebo <xref:System.Linq.Queryable.Skip%2A> na výsledek operátoru.  
  
> [!NOTE]
> Překlad se liší od SQL Server 2000 a SQL Server 2005. Pokud plánujete použít <xref:System.Linq.Queryable.Skip%2A> s dotazem jakékoli složitosti, použijte SQL Server 2005.  
  
 Pro SQL Server 2000 Vezměte v úvahu následující [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazování:  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přesouvá řazení na konec v kódu SQL následujícím způsobem:  
  
```sql
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
  
 Při zřetězení <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A> musí být všechna zadaná řazení konzistentní. V opačném případě nejsou výsledky definovány.  
  
 Pro nezáporné konstantní celočíselné argumenty založené na specifikaci SQL jsou správně definovány <xref:System.Linq.Queryable.Take%2A> i <xref:System.Linq.Queryable.Skip%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](query-examples.md)
- [Převod standardních operátorů dotazů](standard-query-operator-translation.md)
