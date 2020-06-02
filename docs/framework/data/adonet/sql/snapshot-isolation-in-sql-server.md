---
title: Izolace snímků na SQL Serveru
description: Přečtěte si přehled izolace snímků a správy verzí řádků v SQL Server a Naučte se spravovat souběžnost s úrovněmi izolace.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: 7fa769448dd922925a5eccf4c85bd1840155df68
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286242"
---
# <a name="snapshot-isolation-in-sql-server"></a>Izolace snímků na SQL Serveru
Izolace snímků vylepšuje souběžnost pro aplikace OLTP.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Principy izolace snímků a správy verzí řádků  
 Když je povolená izolace snímku, musí se udržovat aktualizované verze řádků pro každou transakci.  Před SQL Server 2019 byly tyto verze uloženy v **databázi tempdb**. SQL Server 2019 zavádí novou funkci, která zrychluje obnovení databáze (ADR), které vyžaduje vlastní sadu verzí řádků.  Pokud je tedy pro SQL Server 2019 povolená možnost ADR, verze řádků se v **databázi tempdb** uchovávají jako vždy.  Pokud je povoleno pravidlo automatického nasazení, pak všechny verze řádků, jak souvisí s izolací snímku a ADR, jsou uchovávány v úložišti trvalé verze (PVS), které je umístěno v uživatelské databázi ve skupině souborů, kterou uživatel určí. Jedinečné pořadové číslo transakce identifikuje každou transakci a tato jedinečná čísla se zaznamenávají pro každou verzi řádku. Transakce funguje s nejnovějšími verzemi řádků, které mají pořadové číslo před pořadovým číslem transakce. Novější verze řádků vytvořené po zahájení transakce jsou transakce ignorovány.  
  
 Pojem "snímek" odráží skutečnost, že všechny dotazy v transakci jsou ve stejné verzi nebo snímku databáze, na základě stavu databáze v okamžiku, kdy transakce začíná. Na podkladové datové řádky nebo datové stránky v transakci snímku se nezískávají žádné zámky, což umožňuje provádět jiné transakce bez zablokování předchozí nedokončená transakce. Transakce, které upravují data, neblokují transakce, které čtou data, a transakce, které čtou data, neblokují transakce, které zapisují data, protože normálně mají pod výchozí úroveň izolace POTVRZENé pro čtení v SQL Server. Toto neblokující chování také významně snižuje pravděpodobnost zablokování pro komplexní transakce.  
  
 Izolace snímku používá optimistický model souběžnosti. Pokud se transakce snímku pokusí potvrdit změny dat, která se změnila od zahájení transakce, transakce se vrátí zpět a bude vyvolána chyba. K tomu se můžete vyhnout použitím UPDLOCK tipů pro příkazy SELECT, které přistupují k datům, která se mají upravit. Další informace najdete v tématu věnovaném přepínacím pokynům na webu SQL Server Books Online.  
  
 Aby bylo možné použít izolaci snímku, musí být povoleno nastavení možnosti ALLOW_SNAPSHOT_ISOLATION ON Database, než se použije v transakcích. Tím se aktivuje mechanismus pro ukládání verzí řádků v dočasné databázi (**tempdb**). Je nutné povolit izolaci snímku v každé databázi, která ji používá, pomocí příkazu Transact-SQL ALTER DATABASE. V tomto ohledu se izolace snímku liší od tradičních úrovní izolace, které jsou POTVRZENé, je nutné je znovu načíst, SERIALIZOVAT a číst nepotvrzené, které nevyžadují žádnou konfiguraci. Následující příkazy aktivují izolaci snímků a nahradí výchozí chování při čtení pomocí snímku:  
  
```sql  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 Nastavení READ_COMMITTED_SNAPSHOT u možnosti umožňuje přístup k řádkům s verzí pod výchozí úrovní izolace READ. Pokud je možnost READ_COMMITTED_SNAPSHOT nastavena na vypnuto, je nutné explicitně nastavit úroveň izolace snímku pro každou relaci, aby bylo možné přistupovat k řádkům se správou verzí.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Správa souběžnosti s úrovněmi izolace  
 Úroveň izolace, pod kterou se spouští příkaz jazyka Transact-SQL, určuje chování při zamykání a nastavování řádků. Úroveň izolace má rozsah pro celé připojení a po nastavení připojení pomocí příkazu nastavit úroveň izolace transakce zůstane v platnosti, dokud nebude připojení uzavřeno nebo nastavena jiná úroveň izolace. Když je připojení ukončeno a vráceno do fondu, bude zachována úroveň izolace z poslední NASTAVENé úrovně izolace transakce. Následná připojení, která znovu používají sdružené připojení, používají úroveň izolace, která byla platná v době, kdy je připojení ve fondu.  
  
 Jednotlivé dotazy vydané v rámci připojení mohou obsahovat pomocný parametr zámku, který mění izolaci pro jeden příkaz nebo transakci, ale nemá vliv na úroveň izolace připojení. Úrovně izolace nebo pomocného parametru zámku nastavené v uložených procedurách nebo funkcích nemění úroveň izolace připojení, která je volá a jsou platné pouze pro dobu trvání uložené procedury nebo volání funkce.  
  
 V počátečních verzích SQL Server byly podporovány čtyři úrovně izolace definované ve standardu SQL-92:  
  
- ČTENÍ nepotvrzené je nejméně omezující úroveň izolace, protože ignoruje zámky, které jsou umístěny v jiných transakcích. Transakce spouštěné v nepotvrzené čtení mohou číst změněné hodnoty dat, které ještě nebyly potvrzeny jinými transakcemi. Tyto možnosti se nazývají "nečistých" čtení.  
  
- Hodnota čtení POTVRZENá je výchozí úroveň izolace pro SQL Server. Zabraňuje nečistým čtením zadáním, že příkazy nemohou číst hodnoty dat, které byly změněny, ale nebyly dosud potvrzeny jinými transakcemi. Jiné transakce mohou i nadále upravovat, vkládat nebo odstraňovat data mezi prováděním jednotlivých příkazů v rámci aktuální transakce, což vede k tomu, že neopakuje čtení nebo "fiktivní" data.  
  
- OPAKOVATELNOST čtení je přísnější úroveň izolace než čtení POTVRZENé. Zahrnuje potvrzování čtení a dále určuje, že žádné jiné transakce nemohou upravovat nebo odstraňovat data, která byla přečtena aktuální transakcí, dokud aktuální transakce neproběhne. Souběžnost je nižší než pro čtení POTVRZENé, protože sdílené zámky při čtení dat jsou uchovávány po dobu trvání transakce namísto uvolnění na konci každého příkazu.  
  
- SERIALIZOVATELNÝ je nejvyšší omezující úroveň izolace, protože zamkne celé rozsahy klíčů a drží zámky, dokud transakce není dokončena. Zahrnuje opakované čtení a přidává omezení, které ostatní transakce nemohou vkládat nové řádky do rozsahů, které transakce četly, dokud transakce není dokončena.  
  
 Další informace najdete v [Průvodci zámkem transakcí a správou verzí řádků](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide).  
  
### <a name="snapshot-isolation-level-extensions"></a>Rozšíření úrovně izolace snímku  
 SQL Server zavedla rozšíření na úrovně izolace SQL-92 s představením úrovně izolace snímku a další implementace pro čtení POTVRZENá. Úroveň izolace READ_COMMITTED_SNAPSHOT může transparentně nahradit POTVRZENé čtení pro všechny transakce.  
  
- Izolace snímků určuje, že data přečtená v rámci transakce nikdy nereflektují změny provedené jinými souběžnými transakcemi. Transakce používá verze datových řádků, které existují při zahájení transakce. Při čtení nejsou do dat vloženy žádné zámky, takže transakce snímků neblokují žádné další transakce v zápisu dat. Transakce, které zapisují data, neblokují transakce snímků od čtení dat. Je nutné povolit izolaci snímku nastavením možnosti databáze ALLOW_SNAPSHOT_ISOLATION, aby ji bylo možné použít.  
  
- Možnost databáze READ_COMMITTED_SNAPSHOT určuje chování výchozí úrovně izolace při čtení, pokud je v databázi povolená izolace snímku. Pokud explicitně neurčíte READ_COMMITTED_SNAPSHOT pro, použije se pro všechny implicitní transakce čtení POTVRZENé. Výsledkem je stejné chování jako u nastavení READ_COMMITTED_SNAPSHOT vypnuto (výchozí nastavení). Pokud platí READ_COMMITTED_SNAPSHOT vypnuto, databázový stroj použije ke vykonání výchozí úrovně izolace sdílené zámky. Pokud nastavíte možnost databáze READ_COMMITTED_SNAPSHOT na ZAPNUTo, databázový stroj použije jako výchozí izolaci verzí řádků a jako výchozí místo používání zámků k ochraně dat.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Jak funguje izolace snímku a správa verzí řádků  
 Když je povolena úroveň izolace snímku, při každém aktualizaci řádku ukládá databázový stroj SQL Server kopii původního řádku v **databázi tempdb**a do řádku přidá číslo sekvence transakce. Následuje posloupnost událostí, ke kterým dochází:  
  
- Je iniciována nová transakce a je jí přiřazeno pořadové číslo transakce.  
  
- Databázový stroj přečte řádek v rámci transakce a načte verzi řádku z **databáze tempdb** , jejíž číslo sekvence je nejbližší a nižší než číslo sekvence transakce.  
  
- Databázový stroj zkontroluje, zda není pořadové číslo transakce v seznamu čísel pořadí transakcí nepotvrzených transakcí aktivních při spuštění transakce snímku.  
  
- Transakce načte verzi řádku z **databáze tempdb** , která byla aktuální od začátku transakce. Po spuštění transakce se nebudou zobrazovat nové řádky, protože tyto hodnoty pořadových čísel budou vyšší než hodnota v pořadí transakcí.  
  
- Aktuální transakce uvidí řádky, které byly odstraněny po zahájení transakce, protože v **databázi tempdb** bude verze řádku s nižší hodnotou pořadového čísla.  
  
 Čistým účinkem izolace snímků je to, že transakce vidí všechna data, protože existovala na začátku transakce, aniž by se musela dodržet nebo umístit zámky na podkladové tabulky. To může mít za následek vylepšení výkonu v situacích, kdy dochází k sporům.  
  
 Transakce snímku vždy používá optimistické řízení souběžnosti, což odpírá všechny zámky, které by zabránily aktualizaci řádků v jiných transakcích. Pokud se transakce snímku pokusí Potvrdit aktualizaci na řádek, který byl změněn po zahájení transakce, transakce se vrátí zpět a vyvolá se chyba.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Práce s izolací snímku v ADO.NET  
 Izolace snímků je podporována třídou v ADO.NET <xref:System.Data.SqlClient.SqlTransaction> . Pokud je databáze povolena pro izolaci snímku, ale není nakonfigurována pro READ_COMMITTED_SNAPSHOT na, je nutné <xref:System.Data.SqlClient.SqlTransaction> při volání metody inicializovat použití hodnoty výčtu **IsolationLevel. Snapshot** <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> . Tento fragment kódu předpokládá, že připojení je otevřený <xref:System.Data.SqlClient.SqlConnection> objekt.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak se chovají různé úrovně izolace, při pokusu o přístup k uzamčeným datům a není určena pro použití v produkčním kódu.  
  
 Kód se připojí k ukázkové databázi **AdventureWorks** v SQL Server a vytvoří tabulku s názvem **TestSnapshot** a vloží jeden řádek dat. Kód používá příkaz jazyka Transact-SQL příkazu ALTER DATABASE k zapnutí izolace snímků pro databázi, ale nenastavuje možnost READ_COMMITTED_SNAPSHOT, přičemž výchozí čtení se zachováním na úrovni izolace je v platnosti. Kód pak provede následující akce:  
  
- Začíná, ale nedokončil, sqlTransaction1, který používá serializovatelný úroveň izolace ke spuštění transakce aktualizace. To má vliv na uzamykání tabulky.  
  
- Otevře se druhé připojení a inicializuje druhou transakci pomocí úrovně izolace snímku pro čtení dat v tabulce **TestSnapshot** . Vzhledem k tomu, že je povolena izolace snímku, může tato transakce číst data, která existovala před spuštěním sqlTransaction1.  
  
- Otevře se třetí připojení a zahájí transakci s použitím úrovně izolace READ POTVRZENé k pokusu o čtení dat v tabulce. V tomto případě kód nemůže číst data, protože nemůže číst za zámky umístěnými v tabulce v první transakci a vypršení časového limitu. Stejný výsledek nastane, pokud byly použity opakující se úrovně izolace READ a serializovatelný, protože tyto úrovně izolace také nemohou číst za zámky, které jsou umístěny v první transakci.  
  
- Otevře se čtvrté připojení a inicializuje transakci pomocí čtení nepotvrzené úrovně izolace, které provádí nevyřízené čtení nepotvrzené hodnoty v sqlTransaction1. Tato hodnota nemusí nikdy v databázi existovat, pokud není první transakce potvrzena.  
  
- Vrátí zpět první transakci a vyčistí odstraněním tabulky **TestSnapshot** a vypnutím izolace snímků pro databázi **AdventureWorks** .  
  
> [!NOTE]
> V následujících příkladech je použití stejného připojovacího řetězce při sdružování připojení vypnuto. Pokud je připojení ve fondu, resetování jeho úrovně izolace neobnoví úroveň izolace na serveru. V důsledku toho budou následná připojení, která používají stejné vnitřní připojení ve fondu, zahájena s úrovněmi izolace nastavenými na skupinu připojení. Alternativou k vypnutí sdružování připojení je nastavení úrovně izolace explicitně pro každé připojení.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje chování izolace snímku při úpravě dat. Kód provádí následující akce:  
  
- Připojí se k ukázkové databázi **AdventureWorks** a povolí izolaci snímků.  
  
- Vytvoří tabulku s názvem **TestSnapshotUpdate** a vloží tři řádky ukázkových dat.  
  
- Začíná, ale není dokončený, sqlTransaction1 pomocí izolace snímků. V transakci jsou vybrány tři řádky dat.  
  
- Vytvoří druhý **SqlConnection** k **AdventureWorks** a vytvoří druhou transakci pomocí úrovně izolace Read potvrzené, která aktualizuje hodnotu v jednom z řádků vybraných v sqlTransaction1.  
  
- Potvrdí sqlTransaction2.  
  
- Vrátí se do sqlTransaction1 a pokusí se aktualizovat stejný řádek, který sqlTransaction1 už potvrzený. Dojde k chybě 3960 a sqlTransaction1 se vrátí automaticky. V okně konzoly se zobrazí **SqlException. Number** a **SqlException. Message** .  
  
- Spustí čistý kód, který vypne izolaci snímků v **AdventureWorks** a odstraní tabulku **TestSnapshotUpdate** .  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Použití pomocných parametrů zámku s izolací snímku  
 V předchozím příkladu první transakce vybere data a druhá transakce aktualizuje data před tím, než se první transakce bude moci dokončit, což způsobí konflikt aktualizace, když se první transakce pokusí aktualizovat stejný řádek. Můžete snížit pravděpodobnost konfliktů aktualizací v dlouhotrvajících transakcích snímku tím, že zadáte pomocné parametry zámku na začátku transakce. Následující příkaz SELECT používá pomocný parametr UPDLOCK k uzamknutí vybraných řádků:  
  
```sql  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 Použití pomocného parametru UPDLOCK Lock blokuje všechny řádky, které se pokoušejí aktualizovat řádky před dokončením první transakce. To zaručuje, že vybrané řádky nebudou při aktualizaci později v transakci žádné konflikty. Přečtěte si téma "zamykání tipů" v tématu SQL Server Books Online.  
  
 Pokud má vaše aplikace mnoho konfliktů, nemusí být izolace snímku nejlepší volbou. Hinty by se měly používat jenom v případě, že skutečně potřebujete. Vaše aplikace by neměla být navržena tak, aby se neustále spoléhá na pomocné parametry zámku pro jeho operaci.  
  
## <a name="see-also"></a>Viz také

- [SQL Server a ADO.NET](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
- [Průvodce zámkem transakcí a správou verzí řádků](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide)
