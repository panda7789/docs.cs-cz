---
title: Vrácení sjednocení množin mezi dvěma sekvencemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 1b981d3002cf4a23897ce98927aebe96086f8a4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781232"
---
# <a name="return-the-set-union-of-two-sequences"></a>Vrácení sjednocení množin mezi dvěma sekvencemi
<xref:System.Linq.Queryable.Union%2A> Použijte operátor k vrácení sjednocení se dvěma sekvencemi.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Queryable.Union%2A> k vrácení posloupnosti všech zemí nebo oblastí, ve kterých existuje buď `Customers` nebo `Employees`.  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je [`UNION ALL`](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) operátor definován pro množiny jako neuspořádané zřetězení množin (efektivně výsledek klauzule v jazyce SQL). <xref:System.Linq.Queryable.Union%2A>

Další informace a příklady naleznete v tématu <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](query-examples.md)
- [Převod standardních operátorů dotazů](standard-query-operator-translation.md)
