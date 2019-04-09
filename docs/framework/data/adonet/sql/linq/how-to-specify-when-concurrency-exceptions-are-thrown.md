---
title: 'Postupy: Určení, kdy se mají objevit výjimky souběžnosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: 30dd83c68472ecd3244cfc87b6df97b948b9a84f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182985"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a>Postupy: Určení, kdy se mají objevit výjimky souběžnosti
V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.ChangeConflictException> je vyvolána výjimka, pokud objekty nelze aktualizovat kvůli konfliktům optimistického řízení souběžnosti. Další informace najdete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 Před odesláním změn databáze můžete zadat při by měl být vyvolání výjimky souběžnosti:  
  
-   Vyvolání výjimky v prvním selhání (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).  
  
-   Dokončit všechny pokusy aktualizovat, accumulate všechny chyby a generování sestav nahromaděné chyby do výjimky (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).  
  
 Při vyvolání, <xref:System.Data.Linq.ChangeConflictException> výjimek poskytuje přístup k <xref:System.Data.Linq.ChangeConflictCollection> kolekce. Tato kolekce obsahuje podrobné informace pro každý konflikt (namapované na jedné aktualizace se nezdařila zkuste), včetně přístupu ke <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> kolekce. Každý člen konflikt mapuje na jeden člen v aktualizaci, která se nezdařila se kontrola souběžnosti.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje příklady obě hodnoty.  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
