---
title: Izolace snímku v systému SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: b9167d7a92ba1b4951d0a9e3c9eea3565bbdc196
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365012"
---
# <a name="snapshot-isolation-in-sql-server"></a>Izolace snímku v systému SQL Server
Izolace snímku vylepšuje souběžnosti pro OLTP aplikace.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Seznámení s izolací snímku a správa verzí řádku  
 Jakmile je povolena izolace snímku, verze aktualizované řádek pro každou transakci jsou zachována ve **databáze tempdb**. Pořadové číslo jedinečný transakce identifikuje každou transakci, a tato čísla jedinečná zaznamenávají pro každou verzi řádek. Transakce pracuje s nejnovějšími verzemi řádek s pořadovým číslem před pořadové číslo transakce. Novější verze řádku vytvořené po zahájení transakce se ignorují transakce.  
  
 Termín "snímek" odráží fakt, že všechny dotazy v transakci uvidí stejnou verzi nebo snímek, databáze, na základě stavu databáze v tuto chvíli v čas zahájení transakce. Žádné zámky jsou získali na zadané řádky dat nebo datových stránek v transakci snímku, který umožňuje dalších transakcí provést bez blokována předchozí nedokončené transakce. Transakce, které upravují data neblokují transakce, které číst data a transakce, které číst data neblokují transakce, které zápis dat, stejně jako za normálních okolností pod výchozí READ COMMITTED úroveň izolace v systému SQL Server. Toto chování neblokující také významně snižuje pravděpodobnost zablokování pro komplexní transakce.  
  
 Izolace snímku používá model optimistickou metodu souběžného. Pokud transakce snapshot pokusů o potvrzení změny dat, které se změnily od začátku transakce, transakce se vrátit zpět a chybu, bude vyvolána. To se můžete vyhnout pomocí UPDLOCK pomocné parametry pro příkazy SELECT, které přístup k datům, která má být změněn. Další informace najdete v části "Pomocné parametry zámku" v SQL Server Books Online.  
  
 Nastavením možnosti databáze ALLOW_SNAPSHOT_ISOLATION ON, než bude použit v transakce musí být povolena izolace snímku. Tím dojde k aktivaci mechanizmus pro ukládání verzí řádek do dočasné databáze (**databáze tempdb**). Je nutné povolit izolaci snímku v každou databázi, která používá s příkazem ALTER DATABASE Transact-SQL. V tomto ohledu izolace snímku se liší od úrovně tradiční izolace READ COMMITTED, REPEATABLE READ, SERIALIZABLE a READ UNCOMMITTED, které vyžadují žádná konfigurace. Následující příkazy aktivovat izolaci snímku a nahraďte výchozí chování READ COMMITTED SNAPSHOT:  
  
```  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 V části úroveň izolace READ COMMITTED výchozí nastavení možnost READ_COMMITTED_SNAPSHOT ON umožňuje přístup k verzí řádků. Pokud je možnost READ_COMMITTED_SNAPSHOT nastavena na hodnotu OFF, musíte explicitně nastavit úroveň izolace snímku pro každou relaci pro přístup verzí řádků.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Správa souběžnosti s úrovní izolace  
 Úroveň izolace, pod kterým příkazu Transact-SQL provede určuje chování jeho zamykání a řádek správy verzí. Úroveň izolace má připojení oboru a po jejím nastavení pro připojení s příkazem nastavte úroveň izolace transakce, zůstává v platnosti, dokud připojení je ukončeno, nebo je nastaven jinou úroveň izolace. Při připojení je ukončeno a vrácení do fondu se uchovávají úroveň izolace z posledního příkazu, nastavte úroveň izolace transakce. Další připojení, opětovné použití používat ve fondu připojení úroveň izolace, která byla platit v době připojení je ve fondu.  
  
 Jednotlivé dotazy vydané v rámci připojení může obsahovat pomocné parametry zámku, která upravit izolaci pro jediný příkaz nebo transakci, ale neovlivní úroveň izolace připojení. Úrovně izolace nebo pomocné parametry zámku nastavte v uložené procedury nebo funkce neměňte úroveň izolace připojení, které je volá a jsou platné pouze po dobu trvání volání uložené procedury nebo funkce.  
  
 Čtyři úrovně izolace definované ve standardu SQL 92 byly podporované v dřívějších verzích systému SQL Server:  
  
-   READ UNCOMMITTED je nejméně omezující úroveň izolace, protože ignoruje zámků podle dalších transakcí. Provádění v rámci čtení NEPOTVRZENÉ transakce může číst hodnot změny dat, které nebyly dosud přiděleny do dalších transakcí; Toto nastavení se nazývá "nepřesné".  
  
-   READ COMMITTED je výchozí úroveň izolace pro SQL Server. Zabrání nepřesné zadáním, že příkazy nelze přečíst hodnot dat, které byla upravena, ale ještě nebyly potvrzeny podle dalších transakcí. Ostatní transakce stále můžete změnit, vložit nebo odstranit data mezi jednotlivými spuštěními jednotlivých příkazů v rámci aktuální transakce, výsledkem-opakovatelných čtení nebo "výsledkem je fiktivní" data.  
  
-   REPEATABLE READ je víc omezující úroveň izolace než READ COMMITTED. Ho zahrnuje potvrzené pro čtení a kromě toho určuje, že žádné další transakce můžete upravit nebo odstranit data, která je již přečtena aktuální transakce, dokud aktuální transakce se potvrdí. Concurrency je nižší než pro čtení potvrzené, protože sdílené na čtení dat zámky po dobu trvání transakce místo vydán na konci každý příkaz.  
  
-   SERIALIZOVATELNÉ je nejvíce omezující úroveň izolace, protože Zamkne celý rozsahy klíčů a obsahuje zámky až do dokončení transakce. To zahrnuje OPAKOVATELNÝCH pro čtení a přidá omezení, které ostatní transakce nelze vložit nové řádky rozsahy, které byly načteny transakce až do dokončení transakce.  
  
 Další informace najdete v tématu "Úrovních izolace" v SQL Server Books Online.  
  
### <a name="snapshot-isolation-level-extensions"></a>Rozšíření na úrovni izolace snímku  
 SQL Server do úrovně izolace SQL 92 s zavedení úroveň izolace SNÍMKU a další implementace READ COMMITTED zavádí rozšíření. Úroveň izolace READ_COMMITTED_SNAPSHOT může transparentně nahradit READ COMMITTED pro všechny transakce.  
  
-   Izolace SNÍMKU Určuje, že data načtená v transakci se nikdy projeví změny provedené při dalších souběžných transakcí. Transakce používá verze řádek dat, které existují při zahájení transakce. Žádné zámky jsou umístěny na datech, když je pro čtení, tak transakcí SNÍMKŮ neblokují dalších transakcí z zápis dat. Transakce, které zápis dat neblokují transakcí snímků čtením data. Budete muset povolit izolaci snímku nastavením možnosti databáze ALLOW_SNAPSHOT_ISOLATION odborných.  
  
-   Možnost databáze READ_COMMITTED_SNAPSHOT určuje úroveň izolace READ COMMITTED výchozí chování, když je povolena izolace snímku v databázi. Pokud nezadáte explicitně READ_COMMITTED_SNAPSHOT ON, READ COMMITTED se použijí pro všechny implicitní transakce. To vytváří stejné chování jako nastavení READ_COMMITTED_SNAPSHOT VYPNETE (výchozí). Je-li READ_COMMITTED_SNAPSHOT vypnout platná, databázový stroj používá sdílené uzamčení vynutit výchozí úroveň izolace. Pokud nastavíte možnost databáze READ_COMMITTED_SNAPSHOT na ON, databázový stroj používá jako výchozí, místo použití zámky k ochraně dat řádek Správa verzí a snímku izolace.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Jak snímek izolace a pracovní verze řádku  
 Pokud je povolená úroveň izolace SNÍMKU, pokaždé, když se aktualizuje na řádek, databázového stroje SQL Server ukládá kopie původní řádek v **databáze tempdb**a přidá číslo sekvence transakce na řádek. Toto je posloupnost událostí, ke kterému dochází:  
  
-   Je zahájeno novou transakci a má přiřazené pořadové číslo transakce.  
  
-   Databázový stroj přečte řádek v rámci transakce a načte verze řádku z **databáze tempdb** jehož pořadové číslo je nejblíže k a nižší než pořadové číslo transakce.  
  
-   Databázový stroj zkontroluje Pokud transakce pořadové číslo není v seznamu transakce pořadí počtu nepotvrzené transakce aktivní, při spuštění transakce snímku.  
  
-   Transakce čtení verze řádku, od **databáze tempdb** , který byl aktuální od začátku transakce. Nové řádky vložené po transakce bylo spuštěno, protože tyto hodnoty pro číslo sekvence bude vyšší než hodnota pořadové číslo transakce v nezobrazí.  
  
-   Aktuální transakce se zobrazí řádky, které byly odstraněny po začal transakce, protože bude mít verze řádku v **databáze tempdb** s nižší hodnotou pořadí čísel.  
  
 Net účinku izolaci snímku je, že všechna data transakce uvidí tak, jak byly na začátku transakce, bez ctít zásady nebo umístění žádné zámky na základní tabulky. To může mít za následek vylepšení výkonu v situacích, kde je nutné vyřešit.  
  
 Transakce snapshot vždy používá optimistické řízení souběžného, odmítnutí žádné zámky, které by jinak znemožňovaly dalších transakcí z aktualizace řádků. Pokud transakce snímku se pokusí provést aktualizaci na řádek, který změnil po zahájení transakce, transakce je vrácena zpět a je vyvolána chyba.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Práce s izolací snímku v technologii ADO.NET  
 Izolace snímku se podporuje v ADO.NET pomocí <xref:System.Data.SqlClient.SqlTransaction> třídy. Pokud databáze byla povolená pro izolaci snímku, ale není nakonfigurován pro READ_COMMITTED_SNAPSHOT ON, je nutné inicializovat <xref:System.Data.SqlClient.SqlTransaction> pomocí **IsolationLevel.Snapshot** hodnota výčtu při volání metody <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> Metoda. Tento fragment kódu předpokládá, že připojení je otevřenou <xref:System.Data.SqlClient.SqlConnection> objektu.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje chování izolace různé úrovně podle pokusu o přístup k uzamčení dat a není určena pro použití v produkčním kódu.  
  
 Kód se připojí k **AdventureWorks** ukázkové databáze serveru SQL Server a vytvoří tabulku s názvem **TestSnapshot** a vloží jeden řádek dat. Kód používá příkaz ALTER DATABASE Transact-SQL zapnutí izolace snímku pro databázi, ale není nastavena možnost READ_COMMITTED_SNAPSHOT ponechat výchozí chování úroveň izolace READ COMMITTED v platnosti. Kód pak provede následující akce:  
  
-   Začne, ale není dokončena, sqlTransaction1, který používá ke spuštění transakce aktualizace úrovně izolace SERIALIZABLE. To má za následek zamykání v tabulce.  
  
-   Otevře druhé připojení a inicializuje druhý pomocí úroveň izolace SNÍMKU číst data v transakci **TestSnapshot** tabulky. Protože je povolena izolace snímku, může tato transakce číst data, která existovala předtím, než sqlTransaction1 spuštěna.  
  
-   Otevře třetí připojení a inicializuje transakci pomocí úroveň izolace potvrzené pro čtení k pokusu o čtení dat v tabulce. V tomto případě kód nemůže číst data, protože nelze přečíst po zámků v tabulce v první transakce a časový limit. Stejný výsledek by dojít, pokud úroveň izolace OPAKOVATELNÝCH pro čtení a SERIALIZABLE měla použít, protože tyto úrovně izolace také nelze přečíst po zámků v první transakce.  
  
-   Otevře čtvrtý připojení a spustí pomocí čtení NEPOTVRZENÉ úroveň izolace, který provádí nepřesný nepotvrzené hodnoty v sqlTransaction1 transakci. Tato hodnota může v databázi existují ve skutečnosti, pokud první transakce není potvrzena.  
  
-   Vrátí zpět první transakce a vyčistí odstraněním **TestSnapshot** tabulky a vypnutí izolaci pro snímku **AdventureWorks** databáze.  
  
> [!NOTE]
>  Následující příklady používají stejný připojovací řetězec s sdružování připojení vypnutý. Pokud je ve fondu připojení, resetování její úroveň izolace neprovádí vynulování úroveň izolace na serveru. V důsledku toho další připojení, které používají stejné připojení ve fondu vnitřní začínat jejich izolace úrovně nastavena na hodnotu u ve fondu připojení. Alternativu k vypnutí sdružování připojení je nastavit úroveň izolace explicitně pro každé připojení.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje chování izolace snímku, když je upravována data. Kód provede následující akce:  
  
-   Připojí k **AdventureWorks** ukázkové databáze a umožňuje izolaci SNÍMKU.  
  
-   Vytvoří tabulku s názvem **TestSnapshotUpdate** a vloží tři řádky ukázková data.  
  
-   Začne, ale není dokončena, sqlTransaction1 pomocí izolace SNÍMKU. Tří řádků dat jsou vybrány v transakci.  
  
-   Vytvoří druhý **SqlConnection** k **AdventureWorks** a vytvoří druhý transakci pomocí úrovně izolace READ COMMITTED, která aktualizuje hodnotu v jednom z vybraných v sqlTransaction1 řádků.  
  
-   Potvrdí sqlTransaction2.  
  
-   Vrátí sqlTransaction1 a pokusy o aktualizaci na stejném řádku této sqlTransaction1 již potvrzen. Vyvolána chyba 3960 a sqlTransaction1 je vrácena zpět automaticky. **SqlException.Number** a **SqlException.Message** se zobrazí v okně konzoly.  
  
-   Spustí kód čištění, chcete-li vypnout izolaci snímku v **AdventureWorks** a odstraňte **TestSnapshotUpdate** tabulky.  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Pomocné parametry zámku pomocí izolace snímku  
 V předchozím příkladu vybere první transakce dat a druhý transakce aktualizuje data před první transakce je možné dokončit, vyvolá způsobila aktualizační konflikt, pokud první transakce pokusit o aktualizaci pro stejný řádek. Zadáním pomocné parametry zámku na začátku transakce můžete snížit riziko aktualizace konfliktů v dlouhotrvajících transakcí snímku. Následující příkaz SELECT používá pomocný parametr UPDLOCK k uzamčení vybrané řádky:  
  
```  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 Pomocí bloků pomocný parametr zámku UPDLOCK žádné řádky pokus o aktualizaci řádky před dokončením první transakce. To zaručuje, že vybrané řádky mají ke konfliktům, když jsou aktualizovány později v transakci. Najdete v části "Pomocné parametry zámku" v Online knihách serveru SQL.  
  
 Pokud vaše aplikace má velký počet konfliktů, nemusí být izolaci snímku nejlepší volbou. Pomocné parametry lze používat pouze v případě potřeby skutečně. Aplikace by neměl být navržené tak, aby je neustále závislé na pomocné parametry zámku při své činnosti.  
  
## <a name="see-also"></a>Viz také  
 [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
