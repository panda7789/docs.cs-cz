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
Pomocí operátoru <xref:System.Linq.Queryable.Take%2A> můžete vrátit daný počet prvků v sekvenci a potom přeskočit zbytek.  
  
 Použijte operátor <xref:System.Linq.Queryable.Skip%2A>, chcete-li přeskočit daný počet prvků v sekvenci a potom vrátit zbytek.  
  
> [!NOTE]
> <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, pokud se používají v dotazech proti SQL Server 2000. Další informace najdete v části "přeskočení a přijetí výjimek v SQL Server 2000" v tématu [řešení potíží](troubleshooting.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá <xref:System.Linq.Queryable.Skip%2A> pomocí poddotazu s klauzulí SQL `NOT EXISTS`. Tento převod má následující omezení:  
  
- Argument musí být sada. Množiny s více sadami se nepodporují, i když jsou seřazené.  
  
- Vygenerovaný dotaz může být mnohem složitější než dotaz vygenerovaný pro základní dotaz, na kterém se používá <xref:System.Linq.Queryable.Skip%2A>. Tato složitost může způsobit snížení výkonu nebo dokonce i vypršení časového limitu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Take` pro výběr prvních pěti `Employees` najatých. Všimněte si, že je kolekce nejprve řazena podle `HireDate`.  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Queryable.Skip%2A> pro výběr všech možností s výjimkou 10 nejdražších `Products`.  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kombinuje metody <xref:System.Linq.Queryable.Skip%2A> a <xref:System.Linq.Queryable.Take%2A> pro přeskočení prvních 50 záznamů a potom vrátí další 10.  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 operace <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A> jsou dobře definovány pouze proti seřazeným sadám. Sémantika pro neuspořádané sady nebo více sad není definována.  
  
 Z důvodu omezení řazení v SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se pokusí přesunout pořadí argumentu operátoru <xref:System.Linq.Queryable.Take%2A> nebo <xref:System.Linq.Queryable.Skip%2A> na výsledek operátoru.  
  
> [!NOTE]
> Překlad se liší od SQL Server 2000 a SQL Server 2005. Pokud plánujete použít <xref:System.Linq.Queryable.Skip%2A> s dotazem jakékoli složitosti, použijte SQL Server 2005.  
  
 Vezměte v úvahu následující @no__t dotaz-0 pro SQL Server 2000:  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přesune řazení na konec kódu SQL následujícím způsobem:  
  
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
  
 Pokud jsou zřetězeny společně <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A>, musí být všechna zadaná řazení konzistentní. V opačném případě nejsou výsledky definovány.  
  
 U nezáporných celočíselných argumentů založených na specifikaci SQL jsou jasně definovány <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](query-examples.md)
- [Převod standardních operátorů dotazů](standard-query-operator-translation.md)
