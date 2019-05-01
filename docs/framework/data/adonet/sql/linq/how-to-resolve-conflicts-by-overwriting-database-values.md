---
title: 'Postupy: Řešení konfliktů přepsáním hodnot v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 7b8d7cf8ab2335c064062ed3ab4072d81e8042fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033654"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a>Postupy: Řešení konfliktů přepsáním hodnot v databázi
Sjednocení rozdílů mezi hodnotami očekávaných a aktuálních databáze, než se pokusíte znovu odeslat změny, můžete použít <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> pro přepsání hodnot v databázi. Další informace najdete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Ve všech případech se záznam na straně klienta se aktualizují nejprve načtením aktualizovaná data z databáze. Tato akce zajistí, že dalším pokusu o aktualizaci nebudou na stejném kontrolách souběžnosti.  
  
## <a name="example"></a>Příklad  
 V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> User1 se pokusí odeslat změny, protože uživatel2 se mezitím změnila Pomocníka s nastavením a oddělení sloupců je vyvolána výjimka. V následující tabulce jsou uvedeny situace.  
  
||Správce|Pomocníka s nastavením|Oddělení|  
|------|-------------|---------------|----------------|  
|Když dotazovat uživatel1, uživatel2 tak původní stav databáze.|Alfreds|Maria|Prodej|  
|Uživatel1 připravuje k odeslání těchto změn.|Alfred||Marketing|  
|Uživatel2 už odeslal tyto změny.||Mary|Služba|  
  
 User1 se rozhodne tento konflikt přepsáním hodnot v databázi pomocí aktuálních hodnot členů klienta.  
  
 Když uživatel User1 konflikt pomocí <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, výsledek v databázi je stejně jako v následující tabulce:  
  
||Správce|Pomocníka s nastavením|Oddělení|  
|------|-------------|---------------|----------------|  
|Nový stav po vyřešení konfliktu.|Alfred<br /><br /> (z User1)|Maria<br /><br /> (původní)|Marketing<br /><br /> (z User1)|  
  
 Následující příklad kódu ukazuje, jak přepsat aktuální hodnoty členů klienta hodnot v databázi. (Žádné kontroly nebo vlastního zpracování konfliktů jednotliví členové dojde k.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
