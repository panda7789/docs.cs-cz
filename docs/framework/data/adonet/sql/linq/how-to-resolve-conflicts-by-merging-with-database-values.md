---
title: 'Postupy: řešení konfliktů sloučením s hodnotami databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: a263afb7daceccecf7153c6e9bcfc68e10638c30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a>Postupy: řešení konfliktů sloučením s hodnotami databáze
Chcete-li sjednocení rozdílů mezi hodnotami očekávaných a aktuálních databáze, než se pokusíte odeslat znovu provedené změny, můžete použít <xref:System.Data.Linq.RefreshMode.KeepChanges> sloučit hodnot v databázi s aktuální hodnoty členů klienta. Další informace najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Ve všech případech je nejprve záznamu v klientovi aktualizovat načtením aktualizovaná data z databáze. Tato akce je zajištěno, že na další pokus o aktualizaci nebudou na stejném kontrolách souběžnosti.  
  
## <a name="example"></a>Příklad  
 V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> je vyvolána výjimka, když se uživatel1 pokusí odeslat změny, protože uživatel2 mezitím změnila sloupce asistenta a oddělení. V následující tabulce jsou uvedeny situaci.  
  
||Správce|Pomocník pro|Oddělení|  
|------|-------------|---------------|----------------|  
|Při dotazu uživatel1 a uživatel2 původního stavu databáze.|Alfreds|Marie|Prodeje|  
|Uživatel1 připraví odešle tyto změny.|Alfred||Marketingové|  
|Uživatel2 již odeslána tyto změny.||Marie|Služba|  
  
 Uživatel1 rozhodne na tento konflikt vyřešte sloučením hodnot v databázi s aktuální hodnoty členů klienta. Výsledkem bude, že databáze, které hodnoty budou přepsána jenom v případě, že aktuální změn také změnil tuto hodnotu.  
  
 Když uživatel1 vyřeší konflikt pomocí <xref:System.Data.Linq.RefreshMode.KeepChanges>, výsledek v databázi je stejně jako v následující tabulce:  
  
||Správce|Pomocník pro|Oddělení|  
|------|-------------|---------------|----------------|  
|Nový stav po řešení konfliktů.|Alfred<br /><br /> (z uživatel1)|Marie<br /><br /> (z uživatel2)|Marketingové<br /><br /> (z uživatel1)|  
  
 Následující příklad ukazuje způsob sloučení hodnot v databázi s aktuální hodnoty členů klienta (Pokud klient změnil tuto hodnotu). Dojde k žádné kontroly nebo vlastní zpracování konfliktů jednotlivými členy.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Řešení konfliktů přepsáním hodnot v databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 [Postupy: Řešení konfliktů zachováním hodnot v databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
