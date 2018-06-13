---
title: 'Postupy: načtení informací o konflikt člena'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 5d0788daac6c1be8dd7670c330d1efc36b074c2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354378"
---
# <a name="how-to-retrieve-member-conflict-information"></a>Postupy: načtení informací o konflikt člena
Můžete použít <xref:System.Data.Linq.MemberChangeConflict> třídy k načtení informací o jednotlivé členy v konfliktu. V tomto kontextu stejné můžete zadat vlastní zpracování chyb jsou v konfliktu u člena. Další informace najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Příklad  
 Následující kód iteruje <xref:System.Data.Linq.ObjectChangeConflict> objekty. Pro každý objekt, se pak provádí iteraci <xref:System.Data.Linq.MemberChangeConflict> objekty.  
  
> [!NOTE]
>  Zahrnout <xref:System.Reflection> Chcete-li poskytovat <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informace.  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
