---
title: "Postupy: řešení konfliktů přepsáním hodnot v databázi"
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
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1dd9a6be51ad1723aab7c3102387a42d1c24996
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a>Postupy: řešení konfliktů přepsáním hodnot v databázi
Chcete-li sjednocení rozdílů mezi hodnotami očekávaných a aktuálních databáze, než se pokusíte odeslat znovu provedené změny, můžete použít <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> přepsat hodnot v databázi. Další informace najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Ve všech případech je nejprve záznamu v klientovi aktualizovat načtením aktualizovaná data z databáze. Tato akce je zajištěno, že na další pokus o aktualizaci nebudou na stejném kontrolách souběžnosti.  
  
## <a name="example"></a>Příklad  
 V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> je vyvolána výjimka, když se uživatel1 pokusí odeslat změny, protože uživatel2 mezitím změnila sloupce asistenta a oddělení. V následující tabulce jsou uvedeny situaci.  
  
||Správce|Pomocník pro|Oddělení|  
|------|-------------|---------------|----------------|  
|Při dotazu uživatel1 a uživatel2 původního stavu databáze.|Alfreds|Marie|Prodeje|  
|Uživatel1 připraví odešle tyto změny.|Alfred||Marketing|  
|Uživatel2 již odeslána tyto změny.||Marie|Služba|  
  
 Uživatel1 rozhodne na tento konflikt vyřešit tak, že přepíše hodnot v databázi s aktuální hodnoty členů klienta.  
  
 Když uživatel1 vyřeší konflikt pomocí <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, výsledek v databázi je jako v následující tabulce:  
  
||Správce|Pomocník pro|Oddělení|  
|------|-------------|---------------|----------------|  
|Nový stav po řešení konfliktů.|Alfred<br /><br /> (z uživatel1)|Marie<br /><br /> (původní)|Marketing<br /><br /> (z uživatel1)|  
  
 Následující příklad kódu ukazuje, jak chcete přepsat aktuální hodnoty členů klienta hodnot v databázi. (Bez kontroly nebo vlastní zpracování konfliktů jednotlivými členy nastane.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
