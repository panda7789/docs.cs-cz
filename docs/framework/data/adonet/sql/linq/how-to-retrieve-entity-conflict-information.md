---
title: 'Postupy: Načtení informací o konfliktech entit'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: 825ba2a32e7c75e922ca08386b9f6efede7b2693
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904069"
---
# <a name="how-to-retrieve-entity-conflict-information"></a>Postupy: Načtení informací o konfliktech entit
Můžete použít objekty <xref:System.Data.Linq.ObjectChangeConflict> třídy k poskytnutí informací o konfliktech neposkytuje <xref:System.Data.Linq.ChangeConflictException> výjimky. Další informace najdete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad Iteruje přes seznam součet je v konfliktu.  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
