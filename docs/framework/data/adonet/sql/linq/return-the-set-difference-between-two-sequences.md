---
title: Vrátí množinových rozdílů mezi dvěma pořadí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 80348961d2848e9664e6978789ceb2441ea2f89a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356215"
---
# <a name="return-the-set-difference-between-two-sequences"></a>Vrátí množinových rozdílů mezi dvěma pořadí
Použití <xref:System.Linq.Queryable.Except%2A> operátor vrátit množinových rozdílů mezi dvěma pořadí.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Queryable.Except%2A> vrátit pořadí všech zemí, ve kterém `Customers` za chodu ale které není `Employees` za provozu.  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> operace je dobře definované jenom na sady. Sémantika pro multisets není definován.  
  
## <a name="see-also"></a>Viz také  
 [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Převod standardních operátorů dotazů](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
