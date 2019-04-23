---
title: 'Postupy: Řešení konfliktů zachováním hodnot v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: 8440ffe61e254403357970d771aea207a6eb6092
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230106"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a>Postupy: Řešení konfliktů zachováním hodnot v databázi
Sjednocení rozdílů mezi hodnotami očekávaných a aktuálních databáze, než se pokusíte znovu odeslat změny, můžete použít <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> zachovat na hodnoty zjištěné v databázi. Pak budou přepsány aktuální hodnoty v objektovém modelu. Další informace najdete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Ve všech případech se záznam na straně klienta se aktualizují nejprve načtením aktualizovaná data z databáze. Tato akce zajistí, že dalším pokusu o aktualizaci nebudou na stejném kontrolách souběžnosti.  
  
## <a name="example"></a>Příklad  
 V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> User1 se pokusí odeslat změny, protože uživatel2 se mezitím změnila Pomocníka s nastavením a oddělení sloupců je vyvolána výjimka. V následující tabulce jsou uvedeny situace.  
  
||Správce|Pomocníka s nastavením|Oddělení|  
|------|-------------|---------------|----------------|  
|Když dotazovat uživatel1, uživatel2 tak původní stav databáze.|Alfreds|Maria|Prodej|  
|Uživatel1 připravuje k odeslání těchto změn.|Alfred||Marketing|  
|Uživatel2 už odeslal tyto změny.||Mary|Služba|  
  
 Uživatel User1 se rozhodne tento konflikt vyřešit tím, že novější hodnot v databázi přepsat aktuální hodnoty v objektovém modelu.  
  
 Když uživatel User1 konflikt pomocí <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, výsledek v databázi je následujícím způsobem v tabulce:  
  
||Správce|Pomocníka s nastavením|Oddělení|  
|------|-------------|---------------|----------------|  
|Nový stav po vyřešení konfliktu.|Alfreds<br /><br /> (původní)|Mary<br /><br /> (z uživatel2)|Služba<br /><br /> (z uživatel2)|  
  
 Následující příklad kódu ukazuje, jak přepsat aktuální hodnoty v objektovém modelu pomocí hodnot v databázi. (Žádné kontroly nebo vlastního zpracování konfliktů jednotliví členové dojde k.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
