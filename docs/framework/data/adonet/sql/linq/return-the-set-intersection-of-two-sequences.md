---
title: Vrácení průniku množin mezi dvěma sekvencemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 944d0b2efe1e74f901a493d1c3202d0f180d599d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792703"
---
# <a name="return-the-set-intersection-of-two-sequences"></a>Vrácení průniku množin mezi dvěma sekvencemi
<xref:System.Linq.Queryable.Intersect%2A> Pomocí operátoru vraťte množinu průniku dvou sekvencí.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Queryable.Intersect%2A> k vrácení posloupnosti všech zemí nebo oblastí, ve kterých obojí `Customers` i `Employees` Live.  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]systémuje operacedobředefinovanápouzevsadách.<xref:System.Linq.Queryable.Intersect%2A> Sémantika pro více sad není definována.  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](query-examples.md)
- [Převod standardních operátorů dotazů](standard-query-operator-translation.md)
