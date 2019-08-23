---
title: 'Postupy: Řešení konfliktů sloučením s hodnotami v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: ccd2e37457e686bc5faed6d8979c2b266d05c829
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943441"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a>Postupy: Řešení konfliktů sloučením s hodnotami v databázi
Pro sjednocení rozdílů mezi očekávanými a skutečnými hodnotami databáze předtím, než se pokusíte znovu odeslat změny <xref:System.Data.Linq.RefreshMode.KeepChanges> , můžete použít ke sloučení hodnot databáze s aktuálními hodnotami členů klienta. Další informace najdete v tématu [Optimistická souběžnost: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
> Ve všech případech se záznam v klientovi poprvé aktualizuje načtením aktualizovaných dat z databáze. Tato akce zajistí, že se další pokus o aktualizaci nebude při stejných kontrolách souběžnosti selhat.  
  
## <a name="example"></a>Příklad  
 V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> je vyvolána výjimka, když se uživatel1 pokusí odeslat změny, protože uživatel2 má mezitím změněné sloupce asistent a oddělení. V následující tabulce je uvedena situace.  
  
||Správce|Pomocníka|Oddělení|  
|------|-------------|---------------|----------------|  
|Původní stav databáze při dotazování od uživatele User1 a uživatel2.|Alfreds|Maria|Prodej|  
|Uživatel1 připraví odeslání těchto změn.|Alfred||Marketing|  
|Uživatel2 již odeslal tyto změny.||Marie|Služba|  
  
 Uživatel1 se rozhodne tento konflikt vyřešit sloučením hodnot databáze s aktuálními hodnotami členů klienta. Výsledkem bude, že hodnoty databáze budou přepsány pouze v případě, že aktuální sada změn také změnila tuto hodnotu.  
  
 Když uživatel1 vyřeší konflikt <xref:System.Data.Linq.RefreshMode.KeepChanges>pomocí, výsledek v databázi je, jak je uvedeno v následující tabulce:  
  
||Správce|Pomocníka|Oddělení|  
|------|-------------|---------------|----------------|  
|Nový stav po vyřešení konfliktu.|Alfred<br /><br /> (od uživatele user1)|Marie<br /><br /> (z uživatel2)|Marketing<br /><br /> (od uživatele user1)|  
  
 Následující příklad ukazuje, jak sloučit hodnoty databáze s aktuálními hodnotami členů klienta (Pokud klient nezměnil také tuto hodnotu). Nedochází k žádné kontrole nebo vlastní manipulaci s jednotlivými konflikty členů.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Řešení konfliktů přepsáním hodnot databáze](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)
- [Postupy: Řešení konfliktů zachováním hodnot databáze](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)
- [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
