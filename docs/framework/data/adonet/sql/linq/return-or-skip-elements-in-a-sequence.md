---
title: Vrácení nebo přeskočení prvků v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: a5c32afc913443787ad8371f31f1fe330b126398
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792753"
---
# <a name="return-or-skip-elements-in-a-sequence"></a>Vrácení nebo přeskočení prvků v posloupnosti
<xref:System.Linq.Queryable.Take%2A> Operátor můžete použít k vrácení daného počtu prvků v sekvenci a následném přeskočení na zbytek.  
  
 <xref:System.Linq.Queryable.Skip%2A> Operátor můžete použít k přeskočení určitého počtu prvků v sekvenci a následnému vrácení zbytku.  
  
> [!NOTE]
> <xref:System.Linq.Enumerable.Take%2A>a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, pokud se používají v dotazech proti SQL Server 2000. Další informace najdete v části "přeskočení a přijetí výjimek v SQL Server 2000" v tématu [řešení potíží](troubleshooting.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]překládá <xref:System.Linq.Queryable.Skip%2A> se pomocí poddotazu s klauzulí SQL `NOT EXISTS` . Tento převod má následující omezení:  
  
- Argument musí být sada. Množiny s více sadami se nepodporují, i když jsou seřazené.  
  
- Vygenerovaný dotaz může být mnohem složitější než dotaz vygenerovaný pro základní dotaz, na kterém <xref:System.Linq.Queryable.Skip%2A> se používá. Tato složitost může způsobit snížení výkonu nebo dokonce i vypršení časového limitu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Take` k výběru prvních pět `Employees` najatých. Všimněte si, že kolekce je nejprve seřazena podle `HireDate`.  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Queryable.Skip%2A> k výběru vše kromě nejdražšího `Products`10.  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kombinuje <xref:System.Linq.Queryable.Skip%2A> metody a <xref:System.Linq.Queryable.Take%2A> pro přeskočení prvních 50 záznamů a potom vrátí další 10.  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <xref:System.Linq.Queryable.Take%2A>a <xref:System.Linq.Queryable.Skip%2A> operace jsou dobře definovány pouze proti seřazeným sadám. Sémantika pro neuspořádané sady nebo více sad není definována.  
  
 Z důvodu omezení řazení v SQL se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokusí přesunout pořadí argumentu <xref:System.Linq.Queryable.Take%2A> operátoru OR <xref:System.Linq.Queryable.Skip%2A> na výsledek operátoru.  
  
> [!NOTE]
> Překlad se liší od SQL Server 2000 a SQL Server 2005. Pokud plánujete použití <xref:System.Linq.Queryable.Skip%2A> s dotazem jakékoli složitosti, použijte SQL Server 2005.  
  
 Vezměte v úvahu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] následující dotaz SQL Server 2000:  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Přesune řazení na konec v kódu SQL následujícím způsobem:  
  
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
  
 Když <xref:System.Linq.Queryable.Take%2A> a<xref:System.Linq.Queryable.Skip%2A> jsou zřetězeny, všechna zadaná řazení musí být konzistentní. V opačném případě nejsou výsledky definovány.  
  
 Pro nezáporné konstantní celočíselné argumenty založené na specifikaci SQL, <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A> jsou dobře definovány.  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](query-examples.md)
- [Převod standardních operátorů dotazů](standard-query-operator-translation.md)
