---
title: 'Optimistická metoda souběžného zpracování: Přehled'
ms.date: 03/30/2017
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
ms.openlocfilehash: 8f3bd35cc1391339d99d5aa0a4021e29fa81756c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767485"
---
# <a name="optimistic-concurrency-overview"></a>Optimistická metoda souběžného zpracování: Přehled
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje optimistického řízení souběžnosti. Následující tabulka popisuje podmínky, které se vztahují k optimistického řízení souběžnosti v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentaci:  
  
|Podmínky|Popis|  
|-----------|-----------------|  
|souběžnost|Situace, ve kterém dvě nebo více uživatelů současně pokusí aktualizovat na stejném řádku databáze.|  
|ke konfliktu souběžnosti|Situace, ve kterém dvě nebo více uživatelů současně pokusí odeslat konfliktní hodnoty pro jeden nebo více sloupců řádků.|  
|kontrola souběžnosti|Metoda používaná k řešení konfliktů souběžnosti.|  
|Optimistického řízení souběžnosti|Technika, který nejprve prověří, zda ostatní transakce změnily hodnoty v řádku před umožňující změny k odeslání.<br /><br /> Rozdíl oproti *pesimistické řízení souběžnosti*, které se uzamkne záznamu, aby nedocházelo ke konfliktům souběžnosti.<br /><br /> *Optimistická* protože považuje za šance na jednu transakci zasahovala do jiného a pravděpodobně nebude tak jako ovládací prvek.|  
|Řešení konfliktů|Proces aktualizace konfliktní položku znovu dotazování na databázi a potom sjednocování rozdílů.<br /><br /> Při aktualizaci objektu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modul sledování změny obsahuje následující data:<br /><br /> -Zkontrolujte hodnoty původně přijatých z databáze a použít pro aktualizaci.<br />-Nových hodnot v databázi z dalších dotazů.<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pak určuje, zda je objekt v konfliktu (to znamená, zda jeden nebo více hodnot členů změnil). Pokud objekt je v konfliktu, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vedle Určuje, které její členy jsou v konfliktu.<br /><br /> Každý člen v konfliktu, který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zjišťuje se přidá do seznamu ke konfliktu.|  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model *optimistického řízení souběžnosti konflikt* nastane, pokud jsou splněny obě následující podmínky:  
  
- Klient se pokusí odeslat změny do databáze.  
  
- Jeden nebo více hodnot kontrolu aktualizací v databázi byly aktualizovány od klienta posledního čtení.  
  
 Řešení konfliktu obsahuje zjišťování, které členy objektu je v konfliktu a potom rozhodování o tom, co chcete udělat.  
  
> [!NOTE]
>  Pouze členové mapován jako <xref:System.Data.Linq.Mapping.UpdateCheck.Always> nebo <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> účastnit kontroly optimistické souběžnosti. Není žádná kontrola se provádí pro členy označené <xref:System.Data.Linq.Mapping.UpdateCheck.Never>. Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.UpdateCheck>.  
  
## <a name="example"></a>Příklad  
 Například v následujícím scénáři User1 začne připravit aktualizace dotazování na databázi pro řádek. Uživatel1 obdrží řádek s hodnotami Alfreds, Marie a prodej.  
  
 Chcete-li změnit hodnotu sloupce správce Alfred a hodnota sloupce oddělení marketingu chce, aby User1. Předtím, než tyto změny můžete odeslat uživatel1, uživatel2 odeslal změny v databázi. Takže teď hodnotu sloupce Pomocníka s nastavením se změnil na Marie a hodnota sloupce oddělení do služby.  
  
 Když User1 se nyní pokusí odeslat změny, odesílání selže a <xref:System.Data.Linq.ChangeConflictException> je vyvolána výjimka. Tato situace nastane, protože pro oddělení a Pomocníka s nastavením sloupec hodnot v databázi nejsou ty, které nebyly očekávány. Představuje sloupci Pomocníka s nastavením a oddělení členy jsou v konfliktu. Následující tabulka shrnuje situace.  
  
||Správce|Pomocníka s nastavením|Oddělení|  
|------|-------------|---------------|----------------|  
|Původní stav|Alfreds|Maria|Prodej|  
|User1|Alfred||Marketing|  
|User2||Mary|Služba|  
  
 Konflikt takovou situaci můžete vyřešit různými způsoby. Další informace najdete v tématu [jak: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="conflict-detection-and-resolution-checklist"></a>Kontrolní seznam řešení a zjišťování konfliktů  
 Můžete zjišťovat a řešit konflikty na libovolné úrovni podrobností. Na jeden extreme, můžete vyřešit všechny konflikty v jednom ze tří způsobů (viz <xref:System.Data.Linq.RefreshMode>) bez pečlivě zvážit. V jiných extreme můžete určit konkrétní akci pro každý typ konfliktu na každého člena v konfliktu.  
  
- Zadejte nebo revidovat <xref:System.Data.Linq.Mapping.UpdateCheck> možnosti v objektovém modelu.  
  
     Další informace najdete v tématu [jak: Zadejte, kteří členové jsou testovat na konflikty souběžnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).  
  
- V bloku try/catch – volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, určete, kdy chcete výjimky, která je vyvolána.  
  
     Další informace najdete v tématu [jak: Zadejte mají objevit výjimky souběžnosti při](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
- Určit, kolik detailů konflikt, které chcete načíst a zahrnutí kódu do vašeho bloku try/catch odpovídajícím způsobem.  
  
     Další informace najdete v tématu [jak: Načtení informací o konfliktech entit](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md) a [jak: Načtení informací o konfliktech členů](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md).  
  
- Zahrnout do vaší `try` / `catch` kódu, jak chcete vyřešit konflikty různých zjistíte.  
  
     Další informace najdete v tématu [jak: Řešení konfliktů zachováním hodnot v databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md), [jak: Řešení konfliktů přepsáním hodnot v databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md), a [jak: Řešení konfliktů sloučení s hodnotami v databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md).  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>Technologie LINQ to SQL typy, které podporují konflikt zjišťování a řešení  
 Třídy a funkce, které podporují řešení konfliktů v optimistického řízení souběžnosti v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] patří následující:  
  
- <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.MemberChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictException?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.RefreshMode?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
