---
title: Vrácení rozdílu množin mezi dvěma sekvencemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 7edc60c7ab8510aadd9ac273529a88adeb41352a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037528"
---
# <a name="return-the-set-difference-between-two-sequences"></a>Vrácení rozdílu množin mezi dvěma sekvencemi
Použití <xref:System.Linq.Queryable.Except%2A> operátor vrácení rozdílů množin mezi dvěma sekvencemi.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Queryable.Except%2A> k vrácení sekvence všech zemí, ve kterém `Customers` provozu, ale v které ne `Employees` live.  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> operace je dobře definovaný pouze na sady. Sémantika pro multisets není definován.  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Převod standardních operátorů dotazů](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
