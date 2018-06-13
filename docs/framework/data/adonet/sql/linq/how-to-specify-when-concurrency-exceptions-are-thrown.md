---
title: 'Postupy: Zadejte, když nastanou výjimky souběžnosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: 6890cc130f4f4101c02bb88c5f5666bcd5cf9b98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360816"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a>Postupy: Zadejte, když nastanou výjimky souběžnosti
V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.ChangeConflictException> při objekty nelze aktualizovat z důvodu konfliktu optimistickou metodu souběžného je vyvolána výjimka. Další informace najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 Před odesláním změny do databáze, můžete zadat, když by měl být vyvolány souběžného zpracování výjimky:  
  
-   Throw – výjimka v prvním selhání (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).  
  
-   Dokončit všechny aktualizace pokusů hromadit všechny chyby a sestavy Akumulovaná selhání v výjimce (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).  
  
 Při vyvolání, <xref:System.Data.Linq.ChangeConflictException> výjimka poskytuje přístup k <xref:System.Data.Linq.ChangeConflictCollection> kolekce. Tato kolekce obsahuje podrobné informace pro každý konflikt (namapované na zkuste jeden Chyba aktualizace), včetně přístupu ke <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> kolekce. Každý člen konflikt mapuje jednoho člena v aktualizaci, která se nezdařila kontrola souběžnosti.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje příklady obě hodnoty.  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
