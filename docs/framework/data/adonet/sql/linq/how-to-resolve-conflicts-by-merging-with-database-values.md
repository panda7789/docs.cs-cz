---
title: 'Postupy: Řešení konfliktů sloučením s hodnotami v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: 429bca7501bd58440ee894345855141a2a2ed12c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130205"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a>Postupy: Řešení konfliktů sloučením s hodnotami v databázi
Sjednocení rozdílů mezi hodnotami očekávaných a aktuálních databáze, než se pokusíte znovu odeslat změny, můžete použít <xref:System.Data.Linq.RefreshMode.KeepChanges> sloučit hodnot v databázi pomocí aktuálních hodnot členů klienta. Další informace najdete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Ve všech případech se záznam na straně klienta se aktualizují nejprve načtením aktualizovaná data z databáze. Tato akce zajistí, že dalším pokusu o aktualizaci nebudou na stejném kontrolách souběžnosti.  
  
## <a name="example"></a>Příklad  
 V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> User1 se pokusí odeslat změny, protože uživatel2 se mezitím změnila Pomocníka s nastavením a oddělení sloupců je vyvolána výjimka. V následující tabulce jsou uvedeny situace.  
  
||Správce|Pomocníka s nastavením|Oddělení|  
|------|-------------|---------------|----------------|  
|Když dotazovat uživatel1, uživatel2 tak původní stav databáze.|Alfreds|Maria|Prodej|  
|Uživatel1 připravuje k odeslání těchto změn.|Alfred||Marketing|  
|Uživatel2 už odeslal tyto změny.||Mary|Služba|  
  
 Uživatel User1 se rozhodne tento konflikt sloučení hodnot v databázi pomocí aktuálních hodnot členů klienta. Výsledkem bude tuto databázi, hodnoty jsou přepsány, pouze v případě, že aktuální sady změn také změnil tuto hodnotu.  
  
 Když uživatel User1 konflikt pomocí <xref:System.Data.Linq.RefreshMode.KeepChanges>, výsledek v databázi je stejně jako v následující tabulce:  
  
||Správce|Pomocníka s nastavením|Oddělení|  
|------|-------------|---------------|----------------|  
|Nový stav po vyřešení konfliktu.|Alfred<br /><br /> (z User1)|Mary<br /><br /> (z uživatel2)|Marketing<br /><br /> (z User1)|  
  
 Následující příklad ukazuje, jak sloučit hodnot v databázi pomocí aktuálních hodnot členů klienta (Pokud klient také změnil tuto hodnotu). Dojde k žádné kontroly nebo vlastního zpracování konfliktů jednotliví členové.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Řešení konfliktů přepsáním hodnot v databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)
- [Postupy: Řešení konfliktů zachováním hodnot v databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)
- [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
