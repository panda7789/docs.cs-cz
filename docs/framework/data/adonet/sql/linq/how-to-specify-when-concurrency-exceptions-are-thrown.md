---
title: "Postupy: Zadejte, když nastanou výjimky souběžnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a1c7a9c7e8d6429b31f1810e31123d46a179fa4e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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
