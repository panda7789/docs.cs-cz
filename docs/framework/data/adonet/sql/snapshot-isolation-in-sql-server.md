---
title: Izolace snímků na SQL Serveru
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: 8313ffc8eef70c1e5efc24b09a160edb7cec1595
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174261"
---
# <a name="snapshot-isolation-in-sql-server"></a>Izolace snímků na SQL Serveru
Snímek izolace zvyšuje souběžnost pro aplikace OLTP.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Principy izolace snímků a správy verzí řádků  
 Jakmile je povolena izolace snímku, musí být zachovány aktualizované verze řádků pro každou transakci.  Před SQL Server 2019 byly tyto verze uloženy v **databázi tempdb**. SQL Server 2019 zavádí novou funkci, Accelerated Database Recovery (ADR), která vyžaduje vlastní sadu verzí řádků.  Takže jako SQL Server 2019, pokud ADR není povolena, verze řádků jsou uchovávány v **tempdb** jako vždy.  Pokud je povolena ADR, pak jsou všechny verze řádků, které souvisejí s izolací snímků a ADR, uloženy v úložišti trvalých verzí ADR (PVS), který je umístěn v databázi uživatelů ve skupině souborů, kterou uživatel určuje. Jedinečné pořadové číslo transakce identifikuje každou transakci a tato jedinečná čísla jsou zaznamenána pro každou verzi řádku. Transakce pracuje s nejnovějšími verzemi řádků, které mají pořadové číslo před pořadovým číslem transakce. Novější verze řádků vytvořené po zahájení transakce jsou transakcí ignorovány.  
  
 Termín "snímek" odráží skutečnost, že všechny dotazy v transakci zobrazit stejnou verzi nebo snímek databáze, na základě stavu databáze v okamžiku zahájení transakce. Žádné zámky jsou získány na podkladových datových řádků nebo datových stránek v transakci snímek, který umožňuje jiné transakce provést bez blokování předchozí nedokončené transakce. Transakce, které upravují data, neblokují transakce, které čtou data, a transakce, které čtou data, neblokují transakce, které zapisují data, jako by to obvykle bylo v rámci výchozí úrovně izolace READ COMMITTED na serveru SQL Server. Toto chování bez blokování také výrazně snižuje pravděpodobnost zablokování pro složité transakce.  
  
 Snímek izolace používá optimistický model souběžnosti. Pokud snímek transakce pokusí potvrdit změny dat, která se změnila od zahájení transakce, transakce se vrátí zpět a bude vyvolána chyba. Můžete se tomu vyhnout pomocí nápovědy UPDLOCK pro příkazy SELECT, které přístup k datům, které mají být změněny. Další informace naleznete v tématu "Locking Hints" v sql server books online.  
  
 Snímek izolace musí být povolena nastavením ALLOW_SNAPSHOT_ISOLATION ON databáze možnost před použitím v transakcích. Tím se aktivuje mechanismus pro ukládání verzí řádků v dočasné databázi (**tempdb**). Je nutné povolit izolaci snímek v každé databázi, která ji používá s příkazem Transact-SQL ALTER DATABASE. V tomto ohledu snímek izolace se liší od tradiční úrovně izolace read committed, opakovatelné čtení, serializovata a čtení UNCOMMITTED, které nevyžadují žádnou konfiguraci. Následující příkazy aktivují izolaci snímku a nahradí výchozí chování READ COMMITTED s snapshotem:  
  
```sql  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 Nastavení možnosti READ_COMMITTED_SNAPSHOT ON umožňuje přístup k řádkům s verzí pod výchozí úrovní izolace READ COMMITTED. Pokud je možnost READ_COMMITTED_SNAPSHOT nastavena na vypnuto, je nutné explicitně nastavit úroveň izolace snímek pro každou relaci, aby bylo možné získat přístup k řádkům s verzí.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Správa souběžnosti s úrovněmi izolace  
 Úroveň izolace, pod kterou příkaz Transact-SQL provádí určuje jeho uzamčení a řádek správu verzí chování. Úroveň izolace má obor pro celé připojení a po nastavení pro připojení s příkazem SET TRANSACTION ISOLATION LEVEL zůstane v platnosti, dokud není připojení uzavřeno nebo je nastavena jiná úroveň izolace. Když je připojení uzavřeno a vráceno do fondu, úroveň izolace z posledního příkazu SET TRANSACTION ISOLATION LEVEL zůstane zachována. Následná připojení, která znovu používají sdružené připojení, používají úroveň izolace, která byla v platnosti v době, kdy je připojení sdruženo.  
  
 Jednotlivé dotazy vydané v rámci připojení může obsahovat rady při uzamčení, které upravují izolaci pro jeden příkaz nebo transakci, ale nemají vliv na úroveň izolace připojení. Úrovně izolace nebo rady při zamykání nastavené v uložených procedurách nebo funkcích nemění úroveň izolace připojení, které je volá, a jsou platné pouze po dobu trvání uložené procedury nebo volání funkce.  
  
 V dřívějších verzích serveru SQL Server byly podporovány čtyři úrovně izolace definované ve standardu SQL-92:  
  
- READ UNCOMMITTED je nejméně omezující úroveň izolace, protože ignoruje zámky umístěné jinými transakcemi. Transakce prováděné v rámci čtení UNCOMMITTED můžete číst změněné hodnoty dat, které dosud nebyly potvrzeny jinými transakcemi; tyto se nazývají "špinavé" čte.  
  
- Read COMMITTED je výchozí úroveň izolace pro SQL Server. Zabraňuje nečisté čtení zadáním, že příkazy nelze číst hodnoty dat, které byly změněny, ale dosud potvrzeny jinými transakcemi. Jiné transakce můžete stále upravovat, vkládat nebo odstraňovat data mezi spuštění jednotlivých příkazů v rámci aktuální transakce, výsledkem je neopakovatelné čtení nebo "fiktivní" data.  
  
- Opakovatelné čtení je více omezující úroveň izolace než READ COMMITTED. Zahrnuje READ COMMITTED a dále určuje, že žádné jiné transakce můžete upravit nebo odstranit data, která byla přečtena aktuální transakce, dokud aktuální transakce potvrdí. Souběžnost je nižší než pro READ COMMITTED, protože sdílené zámky na čtení dat jsou uchovávány po dobu trvání transakce namísto uvolnění na konci každého příkazu.  
  
- SERIALIZABLE je nejvíce omezující úroveň izolace, protože uzamkne celé rozsahy klíčů a zadrží zámky, dokud není transakce dokončena. Zahrnuje opakovatelné čtení a přidá omezení, které ostatní transakce nelze vložit nové řádky do rozsahů, které byly přečteny transakce, dokud transakce je dokončena.  
  
 Další informace naleznete v [průvodci uzamčením transakcí a verzí řádků](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide).  
  
### <a name="snapshot-isolation-level-extensions"></a>Rozšíření úrovně izolace snímků  
 SQL Server představil rozšíření úrovně izolace SQL-92 se zavedením úrovně izolace SNÍMEK a další implementace READ COMMITTED. Úroveň izolace READ_COMMITTED_SNAPSHOT může transparentně nahradit READ COMMITTED pro všechny transakce.  
  
- SNÍMEK izolace určuje, že data čtení v rámci transakce nikdy nebude odrážet změny provedené jinými souběžnými transakcemi. Transakce používá verze řádků dat, které existují při zahájení transakce. Žádné zámky jsou umístěny na data při čtení, takže transakce SNAPSHOT neblokují jiné transakce z zápisu dat. Transakce, které zapisují data neblokují transakce snímek z čtení dat. Je třeba povolit izolaci snímku nastavením možnosti databáze ALLOW_SNAPSHOT_ISOLATION, aby bylo možné ji použít.  
  
- Možnost READ_COMMITTED_SNAPSHOT databáze určuje chování výchozí úrovně izolace READ COMMITTED, pokud je v databázi povolena izolace snímku. Pokud explicitně nezadáte READ_COMMITTED_SNAPSHOT ON, read potvrzena se použije na všechny implicitní transakce. To vytváří stejné chování jako nastavení READ_COMMITTED_SNAPSHOT OFF (výchozí). Když READ_COMMITTED_SNAPSHOT OFF je v platnosti, Database Engine používá sdílené zámky vynutit výchozí úroveň izolace. Pokud nastavíte možnost READ_COMMITTED_SNAPSHOT databáze na ZAPNUTO, databázový stroj používá jako výchozí správu verzí řádků a izolaci snímků, místo toho, aby k ochraně dat používal zámky.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Jak funguje izolace snímků a správa verzí řádků  
 Je-li povolena úroveň izolace SNÍMEK, při každé aktualizaci řádku sql server databázový stroj uloží kopii původního řádku v **tempdb**a přidá pořadové číslo transakce do řádku. Následuje posloupnost událostí, ke kterým dochází:  
  
- Je zahájena nová transakce a je jí přiřazeno pořadové číslo transakce.  
  
- Database Engine přečte řádek v rámci transakce a načte verzi řádku z **tempdb,** jehož pořadové číslo je nejblíže a nižší než pořadové číslo transakce.  
  
- Databázový stroj zkontroluje, zda pořadové číslo transakce není v seznamu pořadových čísel transakcí nepotvrzených transakcí aktivních při spuštění transakce snímku.  
  
- Transakce přečte verzi řádku z **tempdb,** která byla aktuální od začátku transakce. Po spuštění transakce se nové řádky nezobrazí, protože tyto hodnoty pořadového čísla budou vyšší než hodnota pořadového čísla transakce.  
  
- Aktuální transakce uvidí řádky, které byly odstraněny po zahájení transakce, protože bude verze řádku v **tempdb** s nižší hodnotou pořadového čísla.  
  
 Čistý efekt snímek izolace je, že transakce vidí všechna data, jak existovala na začátku transakce, bez uctívání nebo umístění jakékoli zámky na podkladové tabulky. To může mít za následek zlepšení výkonu v situacích, kdy je tvrzení.  
  
 Snímek transakce vždy používá optimistické řízení souběžnosti, srážkové všechny zámky, které by zabránily jiné transakce z aktualizace řádků. Pokud snímek transakce pokusí potvrdit aktualizaci do řádku, který byl změněn po zahájení transakce, transakce je vrácena zpět a je vyvolána chyba.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Práce s izolací snímků v ADO.NET  
 Snímek izolace je <xref:System.Data.SqlClient.SqlTransaction> podporován v ADO.NET třídou. Pokud databáze byla povolena pro snímek izolace, ale není <xref:System.Data.SqlClient.SqlTransaction> nakonfigurován pro READ_COMMITTED_SNAPSHOT ON, je <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> nutné zahájit pomocí **IsolationLevel.Snapshot** výčet hodnoty při volání metody. Tento fragment kódu předpokládá, že <xref:System.Data.SqlClient.SqlConnection> připojení je otevřený objekt.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak se chovají různé úrovně izolace pokusem o přístup k uzamčeným datům a není určen k použití v produkčním kódu.  
  
 Kód se připojí k ukázkové databázi **AdventureWorks** na serveru SQL Server a vytvoří tabulku s názvem **TestSnapshot** a vloží jeden řádek dat. Kód používá příkaz ALTER DATABASE Transact-SQL k zapnutí izolace snímků pro databázi, ale nenastaví možnost READ_COMMITTED_SNAPSHOT, takže výchozí chování na úrovni izolace READ COMMITTED je v platnosti. Kód pak provede následující akce:  
  
- Začíná, ale nedokončí sqlTransaction1, který používá serializable úroveň izolace ke spuštění transakce aktualizace. To má za následek uzamčení tabulky.  
  
- Otevře druhé připojení a zahájí druhou transakci pomocí úrovně izolace SNÍMEK ke čtení dat v tabulce **TestSnapshot.** Vzhledem k tomu, že je povolena izolace snímku, tato transakce můžete číst data, která existovala před sqlTransaction1 started.  
  
- Otevře třetí připojení a zahájí transakci pomocí úrovně izolace READ COMMITTED k pokusu o čtení dat v tabulce. V tomto případě kód nelze číst data, protože nelze číst za zámky umístěné v tabulce v první transakci a časový čas. Stejný výsledek by došlo, pokud opakovatelné čtení a serializable úrovně izolace byly použity, protože tyto úrovně izolace také nelze číst za zámky umístěné v první transakci.  
  
- Otevře čtvrté připojení a zahájí transakci pomocí úrovně izolace READ UNCOMMITTED, která provádí nečisté čtení nepotvrzené hodnoty v sqlTransaction1. Tato hodnota může nikdy skutečně existovat v databázi, pokud první transakce není potvrzena.  
  
- Vrátí zpět první transakce a vyčistí odstraněním **TestSnapshot** tabulka a vypnutí izolace snímek pro **adventureworks** databáze.  
  
> [!NOTE]
> Následující příklady používají stejný připojovací řetězec s vypnutým sdružováním připojení. Pokud je připojení sdruženo, obnovení jeho úrovně izolace neobnoví úroveň izolace na serveru. V důsledku toho následná připojení, které používají stejné sdružené vnitřní připojení začít s jejich úrovně izolace nastavena na sdružené připojení. Alternativou k vypnutí sdružování připojení je explicitně nastavit úroveň izolace pro každé připojení.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje chování snímek izolace při změně dat. Kód provádí následující akce:  
  
- Připojí se k ukázkové databázi **AdventureWorks** a povolí izolaci SNAPSHOT.  
  
- Vytvoří tabulku s názvem **TestSnapshotUpdate** a vloží tři řádky ukázkových dat.  
  
- Začíná, ale nedokončí sqlTransaction1 pomocí izolace SNÍMEK. V transakci jsou vybrány tři řádky dat.  
  
- Vytvoří druhé **SqlConnection** na **AdventureWorks** a vytvoří druhou transakci pomocí úrovně izolace READ COMMITTED, která aktualizuje hodnotu v jednom z řádků vybraných v sqlTransaction1.  
  
- Potvrdí sqlTransaction2.  
  
- Vrátí sqlTransaction1 a pokusí se aktualizovat stejný řádek, který sqlTransaction1 již potvrzena. Je vyvolána chyba 3960 a sqlTransaction1 je vrácena zpět automaticky. **SqlException.Number** a **SqlException.Message** jsou zobrazeny v okně konzoly.  
  
- Spustí vyčištění kód vypnout snímek izolace v **AdventureWorks** a odstranit **TestSnapshotUpdate** tabulka.  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Použití rady při psaní bodů zámku s izolací snímků  
 V předchozím příkladu první transakce vybere data a druhá transakce aktualizuje data před první transakce je možné dokončit, což způsobuje konflikt aktualizace při první transakce se pokusí aktualizovat stejný řádek. Můžete snížit pravděpodobnost konfliktů aktualizace v dlouhotrvající snímek transakce zadáním rady zámku na začátku transakce. Následující příkaz SELECT používá nápovědu UPDLOCK k uzamčení vybraných řádků:  
  
```sql  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 Pomocí nápovědy zámku UPDLOCK blokuje všechny řádky, které se pokoušejí aktualizovat řádky před dokončením první transakce. To zaručuje, že vybrané řádky nemají žádné konflikty při jejich pozdější aktualizaci v transakci. Viz "Zamykání rady" v SQL Server Knihy Online.  
  
 Pokud vaše aplikace má mnoho konfliktů, snímek izolace nemusí být nejlepší volbou. Rady by měly být používány pouze v případě, že je to skutečně potřeba. Vaše aplikace by neměla být navržena tak, aby neustále spoléhá na tipy zámku pro jeho provoz.  
  
## <a name="see-also"></a>Viz také

- [SQL Server a ADO.NET](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
- [Průvodce uzamčením transakcí a verzí řádků](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide)
