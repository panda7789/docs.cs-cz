---
title: 'Optimistická metoda souběžného zpracování: Přehled'
ms.date: 03/30/2017
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
ms.openlocfilehash: fa7d423c0abc07e0d97f7d0d4d557aa11d675ee4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792923"
---
# <a name="optimistic-concurrency-overview"></a>Optimistická metoda souběžného zpracování: Přehled
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje optimistické řízení souběžnosti. Následující tabulka popisuje podmínky, které platí pro optimistickou souběžnost [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] v dokumentaci:  
  
|Uvedenými|Popis|  
|-----------|-----------------|  
|souběžnost|Situace, kdy se dva nebo více uživatelů současně pokusí aktualizovat stejný řádek databáze.|  
|konflikt souběžnosti|Situace, kdy se dva nebo více uživatelů ve stejnou chvíli pokusí odeslat konfliktní hodnoty do jednoho nebo více sloupců řádku.|  
|kontrola souběžnosti|Technika používaná k vyřešení konfliktů souběžnosti.|  
|optimistické řízení souběžnosti|Technika, která nejprve prověří, zda jiné transakce změnily hodnoty v řádku před tím, než povolí změny, které se mají odeslat.<br /><br /> Naproti tomu *pesimistické řízení souběžnosti*, které uzamkne záznam, aby nedocházelo ke konfliktům souběžnosti.<br /><br /> *Optimistický* ovládací prvek je tak považován za nepravděpodobné, že by to mělo vliv na jednu transakci, která je v konfliktu s jiným.|  
|řešení konfliktů|Proces aktualizace konfliktní položky opakovaným dotazem na databázi a následným sjednocením rozdílů.<br /><br /> Když je objekt aktualizován, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sledování změn obsahuje následující data:<br /><br /> – Hodnoty původně odebrané z databáze a použité pro kontrolu aktualizací.<br />– Nové hodnoty databáze z následujícího dotazu.<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]pak určuje, zda je objekt v konfliktu (tj. zda došlo ke změně jedné nebo více hodnot jeho členů). Pokud je objekt v konfliktu, další [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] určuje, který z jeho členů je v konfliktu.<br /><br /> Všechny konflikty členů, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] které zjišťují, jsou přidány do seznamu konfliktů.|  
  
 V objektovém modelu dochází *ke konfliktu optimistické souběžnosti* , pokud jsou splněny obě následující podmínky: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
- Klient se pokusí odeslat změny do databáze.  
  
- Jedna nebo více hodnot kontroly aktualizace byly v databázi aktualizovány, protože je klient naposledy přečetl.  
  
 Řešení tohoto konfliktu zahrnuje zjišťování, které členy objektu jsou v konfliktu, a pak rozhodnutí o tom, co chcete dělat.  
  
> [!NOTE]
> Pouze členové, kteří <xref:System.Data.Linq.Mapping.UpdateCheck.Always> jsou <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> mapováni nebo zapojeni do kontroly optimistického řízení souběžnosti. U označených <xref:System.Data.Linq.Mapping.UpdateCheck.Never>členů není provedena žádná kontroler. Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.UpdateCheck>.  
  
## <a name="example"></a>Příklad  
 Například v následujícím scénáři uživatel1 začíná připraví aktualizaci o dotazování databáze na řádek. Uživatel1 obdrží řádek s hodnotami Alfreds, Marie a Sales.  
  
 Uživatel1 chce změnit hodnotu sloupce nadřízený na Alfred a hodnotu sloupce oddělení na marketing. Aby mohl uživatel user1 odeslat tyto změny, uživatel2 odeslal změny do databáze. Takže teď se hodnota sloupce asistent změnila na Marie a hodnota sloupce oddělení na službu.  
  
 Když se uživatel1 nyní pokusí odeslat změny, odeslání se nepovede a <xref:System.Data.Linq.ChangeConflictException> vyvolá se výjimka. K tomuto výsledku dochází, protože hodnoty databáze pro sloupec asistent a sloupec oddělení nejsou očekávané. Členové, kteří představují sloupce asistenta a oddělení, jsou v konfliktu. Následující tabulka shrnuje situaci.  
  
||Správce|Pomocníka|Oddělení|  
|------|-------------|---------------|----------------|  
|Původní stav|Alfreds|Maria|Prodej|  
|User1|Alfred||Marketing|  
|Přidal||Marie|Služba|  
  
 Tyto konflikty můžete vyřešit různými způsoby. Další informace najdete v tématu [jak: Spravujte konflikty](how-to-manage-change-conflicts.md)změn.  
  
## <a name="conflict-detection-and-resolution-checklist"></a>Kontrolní seznam pro detekci konfliktů a rozlišení  
 Konflikty můžete detekovat a řešit na libovolné úrovni podrobností. V jednom krajním případě můžete vyřešit všechny konflikty jedním ze tří způsobů (viz <xref:System.Data.Linq.RefreshMode>) bez dalšího zvážení. V ostatních extrémních případech můžete určit určitou akci pro každý typ konfliktu u každého člena v konfliktu.  
  
- Zadejte nebo opravte <xref:System.Data.Linq.Mapping.UpdateCheck> možnosti v objektovém modelu.  
  
     Další informace najdete v tématu [jak: Určete, kteří členové jsou testováni pro konflikty](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)souběžnosti.  
  
- V bloku try/catch volání metody <xref:System.Data.Linq.DataContext.SubmitChanges%2A>určete, kde má být vyvolána výjimka.  
  
     Další informace najdete v tématu [jak: Určete, kdy jsou vyvolány](how-to-specify-when-concurrency-exceptions-are-thrown.md)výjimky souběžnosti.  
  
- Určete, kolik podrobností o konfliktech chcete načíst, a odpovídajícím způsobem zahrňte kód do bloku try/catch.  
  
     Další informace najdete v tématu [jak: Načtení informací o](how-to-retrieve-entity-conflict-information.md) konfliktech [entit a postupy: Načte informace o](how-to-retrieve-member-conflict-information.md)konfliktu členů.  
  
- Dokóduzahrňtezpůsob,jakýmchcetevyřešitrůznékonflikty,kteréjstezjistili./ `try` `catch`  
  
     Další informace najdete v tématu [jak: Vyřešte konflikty tím, že zachováte hodnoty](how-to-resolve-conflicts-by-retaining-database-values.md)databáze a [postupy: Řešení konfliktů přepsáním hodnot](how-to-resolve-conflicts-by-overwriting-database-values.md)databáze a [postupy: Vyřešte konflikty sloučením s hodnotami](how-to-resolve-conflicts-by-merging-with-database-values.md)databáze.  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>LINQ to SQL typy, které podporují zjišťování a řešení konfliktů  
 Třídy a funkce pro podporu řešení konfliktů v rámci optimistická souběžnosti v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] systému zahrnují následující:  
  
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

- [Postupy: Správa konfliktů změn](how-to-manage-change-conflicts.md)
