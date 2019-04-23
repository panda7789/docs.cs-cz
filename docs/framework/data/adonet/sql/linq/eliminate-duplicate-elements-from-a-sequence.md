---
title: Odstranění duplicitních prvků z posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: 49138e9b130b1a2137b5e9e779875d6107972578
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211527"
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a>Odstranění duplicitních prvků z posloupnosti
Použití <xref:System.Linq.Queryable.Distinct%2A> operátor odstranění duplicitních prvků z posloupnosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Queryable.Distinct%2A> k výběru pořadí jedinečný měst, které mají zákazníci.  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
