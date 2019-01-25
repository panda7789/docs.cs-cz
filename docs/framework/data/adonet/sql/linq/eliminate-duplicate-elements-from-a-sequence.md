---
title: Odstranění duplicitních prvků z posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: 604307bd179136c9c2b685faa5164f9b5ecabaf9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738167"
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a>Odstranění duplicitních prvků z posloupnosti
Použití <xref:System.Linq.Queryable.Distinct%2A> operátor odstranění duplicitních prvků z posloupnosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Queryable.Distinct%2A> k výběru pořadí jedinečný měst, které mají zákazníci.  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a>Viz také:
- [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
