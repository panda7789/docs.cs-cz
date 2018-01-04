---
title: "Postupy: řešení konfliktů zachováním hodnot v databázi"
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
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1271d7b287dacdae0dd46f084ba21d0dc901bd49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a>Postupy: řešení konfliktů zachováním hodnot v databázi
Chcete-li sjednocení rozdílů mezi hodnotami očekávaných a aktuálních databáze, než se pokusíte odeslat znovu provedené změny, můžete použít <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> uchovat na hodnoty zjištěné v databázi. Aktuální hodnoty v objektu model se pak přepíší. Další informace najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Ve všech případech je nejprve záznamu v klientovi aktualizovat načtením aktualizovaná data z databáze. Tato akce je zajištěno, že na další pokus o aktualizaci nebudou na stejném kontrolách souběžnosti.  
  
## <a name="example"></a>Příklad  
 V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> je vyvolána výjimka, když se uživatel1 pokusí odeslat změny, protože uživatel2 mezitím změnila sloupce asistenta a oddělení. V následující tabulce jsou uvedeny situaci.  
  
||Správce|Pomocník pro|Oddělení|  
|------|-------------|---------------|----------------|  
|Při dotazu uživatel1 a uživatel2 původního stavu databáze.|Alfreds|Marie|Prodeje|  
|Uživatel1 připraví odešle tyto změny.|Alfred||Marketingové|  
|Uživatel2 již odeslána tyto změny.||Marie|Služba|  
  
 Uživatel1 rozhodne na tento konflikt vyřešit tak, že novější hodnot v databázi přepsat aktuální hodnoty v objektu modelu.  
  
 Když uživatel1 vyřeší konflikt pomocí <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, výsledek v databázi je v tabulce následující:  
  
||Správce|Pomocník pro|Oddělení|  
|------|-------------|---------------|----------------|  
|Nový stav po řešení konfliktů.|Alfreds<br /><br /> (původní)|Marie<br /><br /> (z uživatel2)|Služba<br /><br /> (z uživatel2)|  
  
 Následující příklad kódu ukazuje, jak přepsat aktuální hodnoty v objektovém modelu pomocí hodnot v databázi. (Bez kontroly nebo vlastní zpracování konfliktů jednotlivými členy nastane.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
