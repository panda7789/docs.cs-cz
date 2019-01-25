---
title: 'Postupy: Načtení informací o konfliktech členů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 478781e6c8ee31ebf6f5edd0e243a81d9e0524f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669559"
---
# <a name="how-to-retrieve-member-conflict-information"></a>Postupy: Načtení informací o konfliktech členů
Můžete použít <xref:System.Data.Linq.MemberChangeConflict> třídy k načtení informací o jednotlivých členů v konfliktu. V tomto kontextu stejné můžete zadat vlastní zpracování konflikt pro žádného člena. Další informace najdete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Příklad  
 Následující kód prochází <xref:System.Data.Linq.ObjectChangeConflict> objekty. Pro každý objekt, pak prochází <xref:System.Data.Linq.MemberChangeConflict> objekty.  
  
> [!NOTE]
>  Zahrnout <xref:System.Reflection> negace <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informace.  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
