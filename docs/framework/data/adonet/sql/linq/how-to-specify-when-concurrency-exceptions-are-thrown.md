---
title: 'Postupy: Určení, kdy se mají objevit výjimky souběžnosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: c0f41d23264bbe5c9130cb5a0b03686331bc92b1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781617"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a>Postupy: Určení, kdy se mají objevit výjimky souběžnosti
V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]systému je <xref:System.Data.Linq.ChangeConflictException> vyvolána výjimka, pokud se objekty neaktualizují z důvodu optimistického konfliktu souběžnosti. Další informace najdete v tématu [Optimistická souběžnost: Přehled](optimistic-concurrency-overview.md).  
  
 Před odesláním změn do databáze můžete určit, kdy by měly být vyvolány výjimky souběžnosti:  
  
- Vyvolat výjimku při prvním selhání (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).  
  
- Dokončete všechny pokusy o aktualizaci, nashromáždí všechny selhání a nahlásí shromážděné chyby v výjimce<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>().  
  
 Při vyvolání <xref:System.Data.Linq.ChangeConflictException> poskytuje výjimka přístup <xref:System.Data.Linq.ChangeConflictCollection> ke kolekci. Tato kolekce obsahuje podrobné informace o každém konfliktu (namapované na jeden neúspěšný pokus o aktualizaci), včetně <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> přístupu ke kolekci. Každý členský konflikt se mapuje na jednoho člena v aktualizaci, u kterého došlo k selhání kontroly souběžnosti.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje příklady obou hodnot.  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Správa konfliktů změn](how-to-manage-change-conflicts.md)
- [Vytvoření a odeslání změn dat](making-and-submitting-data-changes.md)
