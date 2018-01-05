---
title: "Optimistickou metodu souběžného: Přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 91684f1971692e83664fe41a0385a6d68b327237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="optimistic-concurrency-overview"></a>Optimistickou metodu souběžného: Přehled
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje optimistické řízení souběžného. Následující tabulka popisuje podmínky, které platí pro optimistickou metodu souběžného v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentaci:  
  
|Podmínky|Popis|  
|-----------|-----------------|  
|souběžnost|Situace, ve kterém pokusí aktualizovat na stejném řádku databáze dvě nebo více uživatelů najednou.|  
|konflikt souběžnosti|Situace, ve kterém pokusí odeslat konfliktní hodnoty, které mají některé sloupce řádku dvě nebo více uživatelů najednou.|  
|kontrola souběžnosti|Metoda používaná k řešení konfliktů souběžnosti.|  
|optimistické řízení souběžného|Postup, který nejprve prověří, zda dalších transakcí změnily hodnoty v řádku před umožňující změny, které mají být odeslána.<br /><br /> Rozdíl oproti *řízení pesimistické souběžnosti*, který zamkne záznam, aby nedocházelo ke konfliktům souběžnosti.<br /><br /> *Optimistické* řízení se říká, protože považuje za pravděpodobnost jednu transakci zasahovala do jiného pravděpodobně nebude.|  
|řešení konfliktů.|Proces obnovení položku konfliktní opakujte dotaz na databázi a potom sjednocování rozdílů.<br /><br /> Při aktualizaci objektu, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modul sledování změny obsahuje následující data:<br /><br /> Zkontrolujte-hodnoty původně provést z databáze a použít pro aktualizaci.<br />-Nové databáze hodnoty z následných dotazu.<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]pak určuje, zda objekt je v konfliktu (to znamená, zda jeden nebo více hodnot členů změnil). Pokud objekt je v konfliktu, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vedle Určuje, které svých členů je v konfliktu.<br /><br /> Každý člen konfliktu, který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zjistí přidá do seznamu konflikt.|  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model *optimistickou metodu souběžného konflikt* nastane, když jsou splněny obě následující podmínky:  
  
-   Klient se pokusí odeslat změny do databáze.  
  
-   Jedna nebo více hodnot kontrolu aktualizací v databázi byly aktualizovány od posledního čtení klienta.  
  
 Řešení konfliktu obsahuje zjišťování, kteří členové objektu jsou v konfliktu a teprve potom co chcete udělat o něm.  
  
> [!NOTE]
>  Pouze členové mapovaná jako <xref:System.Data.Linq.Mapping.UpdateCheck.Always> nebo <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> účastnit optimistickou metodu souběžného kontroly. Pro členy označené je provedena žádná kontrola <xref:System.Data.Linq.Mapping.UpdateCheck.Never>. Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.UpdateCheck>.  
  
## <a name="example"></a>Příklad  
 Například v následujícím scénáři uživatel1 začne Příprava aktualizace pomocí dotazu na databázi pro řádek. Uživatel1 obdrží řádek s hodnotami Alfreds Marie a organizační jednotky prodej.  
  
 Uživatel1 chce změnit hodnotu pro sloupec Manager Alfred a hodnota sloupce oddělení marketingu. Předtím, než se tyto změny můžete odeslat uživatel1, uživatel2 byla odeslána změny databáze. Hodnota sloupce pomocníka tak teď má byl změněn na Marie a hodnota sloupce oddělení službě.  
  
 Když uživatel1 se nyní pokusí odeslat změny, odeslání selže a <xref:System.Data.Linq.ChangeConflictException> je vyvolána výjimka. Tato situace nastane, protože hodnot v databázi pro oddělení a sloupec pomocníka nejsou ty, které nebyly očekávány. Členy představující asistenta a oddělení sloupce je v konfliktu. Následující tabulka shrnuje situaci.  
  
||Správce|Pomocník pro|Oddělení|  
|------|-------------|---------------|----------------|  
|Původního stavu|Alfreds|Marie|Prodeje|  
|Uživatel1|Alfred||Marketingové|  
|uživatel2||Marie|Služba|  
  
 Konflikty například to může vyřešit různými způsoby. Další informace najdete v tématu [postupy: Správa konfliktů změnu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="conflict-detection-and-resolution-checklist"></a>Zjišťování konfliktů a kontrolní seznam řešení  
 Můžete zjišťovat a řešení konfliktů na požadované úrovni podrobností. V jedné extreme můžete vyřešit všechny konflikty v jednom ze tří způsobů (viz <xref:System.Data.Linq.RefreshMode>) bez další pozornost. V jiných extreme můžete určit konkrétní akce pro každý typ konflikt na každý člen v konfliktu.  
  
-   Zadejte nebo zkontrolovat <xref:System.Data.Linq.Mapping.UpdateCheck> možnosti v objektovém modelu.  
  
     Další informace najdete v tématu [postup: Určete který členové jsou testovány souběžnosti konflikty](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).  
  
-   V try/catch – blok volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, určete, jaké okamžiku má vyvolání výjimky.  
  
     Další informace najdete v tématu [postup: zadejte při souběžnosti jsou výjimky vyvolány](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
-   Určit, kolik podrobností o konfliktu můžete obnovit a zahrnout kódu do vaší bloku try/catch odpovídajícím způsobem.  
  
     Další informace najdete v tématu [postupy: načtení Entity konflikt informace](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md) a [postup: načíst informace o konfliktu člen](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md).  
  
-   Zahrnout do vaší `try` / `catch` code, jakým způsobem chcete řešení různých konfliktů zjistíte.  
  
     Další informace najdete v tématu [postup: vyřešit konflikty ponechá databázi hodnoty](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md), [postup: vyřešit konflikty hodnoty přepsání databáze](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md), a [postup: vyřešit konflikty ve sloučení s hodnotami databáze](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md).  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>Technologie LINQ to SQL typy, které podporují konflikt zjišťování a řešení  
 Třídy a funkce, které chcete podporovat řešení konfliktů v optimistickou metodu souběžného v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] patří:  
  
-   <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.MemberChangeConflict?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.ChangeConflictException?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.RefreshMode?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Správa konfliktů změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
