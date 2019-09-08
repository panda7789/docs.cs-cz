---
title: 'Postupy: Načtení informací o konfliktech členů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 40caa07488cb40ca8e9e3eb3a570c325b92de491
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793302"
---
# <a name="how-to-retrieve-member-conflict-information"></a>Postupy: Načtení informací o konfliktech členů
<xref:System.Data.Linq.MemberChangeConflict> Třídu můžete použít k načtení informací o jednotlivých členech v konfliktu. V tomto stejném kontextu můžete poskytnout vlastní zpracování konfliktu pro libovolného člena. Další informace najdete v tématu [Optimistická souběžnost: Přehled](optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Příklad  
 Následující kód prochází <xref:System.Data.Linq.ObjectChangeConflict> objekty. Pro každý objekt pak prochází <xref:System.Data.Linq.MemberChangeConflict> objekty.  
  
> [!NOTE]
> Zahrňte <xref:System.Reflection> do poskytování <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informací.  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Správa konfliktů změn](how-to-manage-change-conflicts.md)
