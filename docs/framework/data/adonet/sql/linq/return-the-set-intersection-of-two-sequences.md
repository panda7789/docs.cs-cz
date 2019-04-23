---
title: Vrácení průniku množin mezi dvěma sekvencemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 07f48ab7ef1095ba80b1a955a4bd1ea602a75aa8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205901"
---
# <a name="return-the-set-intersection-of-two-sequences"></a>Vrácení průniku množin mezi dvěma sekvencemi
Použití <xref:System.Linq.Queryable.Intersect%2A> operátor se vraťte průniku množin mezi dvěma sekvencemi.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Queryable.Intersect%2A> k vrácení sekvence všech zemí, ve kterých `Customers` a `Employees` live.  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Intersect%2A> operace je dobře definovaný pouze na sady. Sémantika pro multisets není definován.  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Převod standardních operátorů dotazů](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
