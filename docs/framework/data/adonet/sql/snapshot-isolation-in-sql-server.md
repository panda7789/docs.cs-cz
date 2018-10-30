---
title: Izolace snímků na SQL serveru
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: d2683ead92eb4e76494e3e23bff1c688578a316d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200989"
---
# <a name="snapshot-isolation-in-sql-server"></a>Izolace snímků na SQL serveru
Izolace snímku vylepšuje souběžnosti pro aplikace s online zpracováním transakcí.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Principy izolaci snímku a správy verzí řádku  
 Jakmile je povolena izolace snímku, verze aktualizovaný řádek pro každou transakci jsou zachována ve **tempdb**. Pořadové číslo jedinečný transakce identifikuje každou transakci a Tato jedinečná čísla jsou zaznamenány pro každou verzi řádku. Transakce funguje s nejnovější verze řádků s pořadovým číslem než pořadové číslo transakce. Novější verze řádků po zahájení transakce jsou ignorovány transakcí.  
  
 Termín "snímku" odráží fakt, že všechny dotazy v transakci naleznete v tématu stejnou verzi nebo snímek databáze, na základě stavu databáze v okamžiku v čase zahájení transakce. Žádné zámky pořízené na základní řádky dat nebo datových stránek v transakci snímku, která umožňuje ostatní transakce provést bez blokována předchozí nedokončené transakce. Transakcí, které upravují data neblokují transakcí, které načítají data a transakcí, které načítají data neblokují transakcí, které budou zapisovat data, jako obvykle zadají v části výchozí úrovní izolace READ COMMITTED v systému SQL Server. Toto chování neblokující také významně snižuje pravděpodobnost, že zablokování pro složité transakce.  
  
 Izolace snímku používá model optimistického řízení souběžnosti. Pokud transakce snímku se pokusí o potvrzení změny dat, které se změnily od zahájení transakce, transakce se vrátit zpět a bude vyvolána k chybě. Tomu lze zabránit pomocí UPDLOCK tipů pro příkazy SELECT, které přístup k datům, která má být upraven. Další informace naleznete v tématu "Pomocné parametry zámku" SQL Server Books Online.  
  
 Nastavením je možnost databáze dále ALLOW_SNAPSHOT_ISOLATION předtím, než je použit v transakcích musí být povolena izolace snímku. Tím dojde k aktivaci mechanismus pro ukládání verze řádků v dočasné databázi (**tempdb**). Je nutné povolit izolaci snímku v každé databázi, která používá s příkazem jazyka Transact-SQL ALTER DATABASE. Izolace snímku se v tomto ohledu liší od úrovně tradiční izolace READ COMMITTED, REPEATABLE READ, SERIALIZABLE a READ UNCOMMITTED, které není potřeba konfigurovat. Následující příkazy aktivovat izolaci snímku a nahraďte výchozí chování READ COMMITTED SNAPSHOT:  
  
```sql  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 Pod úrovní izolace READ COMMITTED výchozí nastavení možnost READ_COMMITTED_SNAPSHOT dále umožňuje přístup k řádkům. Pokud je možnost READ_COMMITTED_SNAPSHOT nastavena na hodnotu OFF, musíte explicitně nastavit úroveň izolace snímku pro každou relaci za účelem přístupu k řádkům.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Správa souběžnosti s úrovní izolace  
 Úroveň izolace, pod kterým provádí příkaz jazyka Transact-SQL určuje jeho verzí chování zámku a řádek. Úroveň izolace má připojení oboru a po nastavení připojení pomocí příkazu nastavte úroveň izolace transakce, zůstává v platnosti, dokud se připojení uzavře nebo nastavte jinou úroveň izolace. Při zavření připojení a vrácen do fondu se uchovávají úroveň izolace z posledního příkazu nastavte úroveň izolace transakce. Další připojení, opětovné použití použití připojení z fondu, který je ve fondu úroveň izolace, která je v platnosti v době připojení.  
  
 Jednotlivé dotazy odeslané v rámci určitého připojení může obsahovat pomocné parametry zámku, která upravit izolaci pro jeden příkaz nebo transakce, ale nemají vliv na úroveň izolace připojení. Úrovně izolace nebo pomocné parametry zámku nastavit uložené procedury nebo funkce neměňte úroveň izolace, která je volá připojení a jsou platné jenom po dobu trvání volání uložené procedury nebo funkce.  
  
 Čtyři úrovně izolace definované ve standardu SQL 92 byly podporované v dřívějších verzích systému SQL Server:  
  
-   READ UNCOMMITTED se nejméně omezující úroveň izolace, protože ignoruje zámků jinými transakcemi. Provádění v rámci čtení NEPOTVRZENÉ transakce může číst změny datových hodnot, které nebyly dosud byla potvrzena dalšími transakcemi; ty se nazývají "hrubé" čtení.  
  
-   READ COMMITTED je výchozí úroveň izolace pro SQL Server. Ta brání nepřesné tak, že určíte, že příkazy nemůže číst hodnoty dat, které byla upravena, ale ještě nebyla potvrzena dalšími transakcemi. Ostatní transakce stále můžete změnit, vložení nebo odstranění dat mezi spuštěními jednotlivé příkazy v rámci aktuální transakce, což vede k-opakovatelné operace čtení nebo "fiktivní" data.  
  
-   REPEATABLE READ je více omezující úroveň izolace než READ COMMITTED. Zahrnuje potvrzené pro čtení a kromě toho určuje, že žádné další transakce můžete upravit nebo odstranit data, která byla načtena pomocí aktuální transakce dokud aktuální transakce potvrzena. Souběžnost je nižší než pro čtení potvrzené, protože sdílené na čtení dat zámky po dobu trvání transakce místo se vydávají na konci každého příkazu.  
  
-   SERIALIZOVATELNÝ je nejvíce omezující úroveň izolace, protože uzamkne celých rozsahů klíče a až do dokončení transakce obsahuje zámky. Zahrnuje OPAKOVATELNÉ čtení a přidá omezení, ostatní transakce nelze vložit nové řádky do oblastí, které byly načteny transakce až do dokončení transakce.  
  
 Další informace najdete [průvodce Správa verzí řádku a transakce uzamčení](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide).  
  
### <a name="snapshot-isolation-level-extensions"></a>Rozšíření úrovni izolace snímku  
 SQL Server zavádí rozšíření na úrovních izolace SQL 92 s po zavedení služby na úrovni izolace SNÍMKU a další provádění READ COMMITTED. Úroveň izolace READ_COMMITTED_SNAPSHOT můžete transparentně nahradit READ COMMITTED pro všechny transakce.  
  
-   Izolace SNÍMKU Určuje, že data načtená v rámci transakce nikdy odrážejí změny provedené jinými souběžných transakcemi. Transakce používá verze řádků dat, které existují při zahájení transakce. Žádné zámky jsou umístěny na data při je pro čtení, takže transakcí SNÍMKŮ neblokují ostatní transakce od vytváření dat. Transakcí, které zápis dat nedochází k blokování transakcí snímků z dat pro čtení. Je potřeba povolit izolaci snímku nastavením možnosti ALLOW_SNAPSHOT_ISOLATION databáze použít.  
  
-   Možnost databáze READ_COMMITTED_SNAPSHOT určuje chování výchozí úroveň izolace READ COMMITTED, pokud je povolena izolace snímku v databázi. Pokud možnost READ_COMMITTED_SNAPSHOT ON není explicitně zadán, READ COMMITTED platí pro všechny implicitní transakce. To vytváří stejné chování jako nastavení READ_COMMITTED_SNAPSHOT vypnuto (výchozí). Když READ_COMMITTED_SNAPSHOT vypnout je v platnosti, databázový stroj používá sdílené uzamčení k vynucení výchozí úroveň izolace. Pokud nastavíte možnost databáze READ_COMMITTED_SNAPSHOT na ON, databázový stroj řádek správy verzí a snímek izolace použije jako výchozí, místo použití zámků k ochraně dat.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Jak snímek izolace a řádek pracovní správy verzí  
 Pokud je povolena úroveň izolace SNÍMKU, pokaždé, když se aktualizuje řádek, databázový stroj SQL serveru ukládá jejich kopii původní řádek v **tempdb**a přidá číslo sekvence transakce na řádek. Posloupnost událostí, ke které dochází, je následující:  
  
-   Zahájené novou transakci a má přiřazené pořadové číslo transakce.  
  
-   Databázový stroj přečte řádek v rámci transakce a načte verze řádku z **tempdb** jehož pořadové číslo je nejblíže a nižší transakce pořadové číslo.  
  
-   Databázový stroj zkontroluje, zda transakce pořadové číslo není v seznamu číslem nepotvrzené transakce aktivní transakce, při zahájení transakce snímku.  
  
-   Transakce čtení verzi řádku z **tempdb** , který byl aktuální v době spuštění transakce. Neuvidí vložené po transakce bylo spuštěno, protože tyto hodnoty čísla pořadí bude vyšší než hodnota transakce pořadové číslo nové řádky.  
  
-   Aktuální transakce se zobrazí řádky, které byly odstraněny po zahájení transakce, protože budou verze řádku v **tempdb** s nižší hodnotou číslo sekvence.  
  
 Čistým důsledkem toho izolaci snímku je, že transakce se zobrazí všechna data tak, jak byly na začátku transakce, bez příslušných nebo umístění žádné zámky na základní tabulky. Může dojít k vylepšení výkonu v situacích, kde je nutné vyřešit.  
  
 Transakce snapshot vždy používá optimistického řízení souběžnosti, odmítnutí žádné zámky, které by jinak znemožňovaly ostatní transakce z aktualizace řádků. Pokud transakce snímku se pokusí provést aktualizace řádku, který byl změněn po zahájení transakce, transakce se zrušila a dojde k chybě.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Práce s izolací snímku v ADO.NET  
 Izolace snímku se podporuje v ADO.NET pomocí <xref:System.Data.SqlClient.SqlTransaction> třídy. Pokud databázi byl povolen pro izolaci snímku, ale není nakonfigurovaný pro možnost READ_COMMITTED_SNAPSHOT ON, je nutné inicializovat <xref:System.Data.SqlClient.SqlTransaction> pomocí **IsolationLevel.Snapshot** hodnota výčtu při volání <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> Metoda. Tento fragment kódu předpokládá, že připojení je otevřený <xref:System.Data.SqlClient.SqlConnection> objektu.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak se chovají úrovních různé izolace pokusem o přístup k datům uzamčené a není určena pro použití v produkčním kódu.  
  
 Kód se připojí k **AdventureWorks** ukázková databáze na SQL serveru a vytvoří tabulku s názvem **TestSnapshot** a vloží jeden řádek dat. Tento kód použije příkaz ALTER DATABASE jazyka Transact-SQL k zapnutí nastavení v izolaci snímku databáze, ale není nastavena možnost READ_COMMITTED_SNAPSHOT ponechat výchozí chování úroveň izolace READ COMMITTED v platnosti. Kód poté provede následující akce:  
  
-   Začne, ale nebude dokončen, sqlTransaction1, který používá ke spuštění transakce aktualizace úrovně izolace SERIALIZABLE. To má vliv na uzamčení v tabulce.  
  
-   Otevře se druhé připojení a inicializuje druhý pomocí na úrovni izolace SNÍMKU číst data v transakci **TestSnapshot** tabulky. Protože je povolena izolace snímku, tuto transakci může číst data, která existovala předtím, než sqlTransaction1 spuštěna.  
  
-   Otevře se třetí připojení a zahájí transakci pro čtení úrovně izolace pomocí pokus o čtení dat v tabulce. Kód v tomto případě nelze číst data, protože nelze přečíst poslední zámků v tabulce v první transakce a vyprší. Stejného výsledku ke kterým by úrovně izolace OPAKOVATELNÉ čtení a SERIALIZABLE byly použít, protože tyto úrovně izolace nelze také čtení za zámků v první transakce.  
  
-   Otevře čtvrtý připojení a zahájí pomocí NEPOTVRZENÉ čtení úroveň izolace, která vede sqlTransaction1 nepřesný hodnotu nepotvrzené transakce. Tato hodnota může nikdy skutečně existují v databázi, pokud první transakce není potvrzená.  
  
-   Vrátí první transakce a vyčistí odstraněním **TestSnapshot** izolace pro tabulky a vypnutí snímku **AdventureWorks** databáze.  
  
> [!NOTE]
>  Následující příklady používají stejný připojovací řetězec s sdružování připojení vypnuté. Pokud je ve fondu připojení, resetování jeho úroveň izolace není resetovaný úroveň izolace na serveru. V důsledku toho další připojení, které používají stejné připojení ve fondu vnitřní začínat jejich izolace úrovně nastavena na hodnotu, která ve fondu připojení. Alternativa k vypnutí sdružování připojení je nastavit úroveň izolace explicitně pro každé připojení.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje chování izolace snímku, když se změní data. Kód provede následující akce:  
  
-   Se připojí k **AdventureWorks** ukázkové databáze a umožňuje izolaci SNÍMKU.  
  
-   Vytvoří tabulku s názvem **TestSnapshotUpdate** a vloží tři řádky ukázková data.  
  
-   Začne, ale nebude dokončen, sqlTransaction1 pomocí izolace SNÍMKU. Tří řádků dat jsou vybrány v transakci.  
  
-   Vytvoří druhou **SqlConnection** k **AdventureWorks** a vytvoří druhý transakci pomocí úrovní izolace READ COMMITTED, která aktualizuje hodnotu v jednom z vybraných v sqlTransaction1 řádků.  
  
-   SqlTransaction2 potvrzení změn.  
  
-   Vrátí sqlTransaction1 a pokusy o aktualizaci na stejném řádku tohoto sqlTransaction1 už je potvrzená. Je vyvolána chyba 3960 a sqlTransaction1 se vrátí zpět automaticky. **SqlException.Number** a **SqlException.Message** jsou zobrazeny v okně konzoly.  
  
-   Spustí kód pro vyčištění k vypnutí možnosti izolace snímku v **AdventureWorks** a odstranit **TestSnapshotUpdate** tabulky.  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Použití pomocné parametry zámku s izolací snímku  
 V předchozím příkladu vybere první transakce data, a druhá transakce aktualizuje data před první transakce je možné dokončit, způsobí došlo ke konfliktu aktualizací, když se první transakce pokusí aktualizovat na stejném řádku. Zadáním pomocné parametry zámku na začátku transakce můžete snížit pravděpodobnost konfliktů při aktualizacích v dlouhotrvajících transakcí snímku. Následující příkaz SELECT pomocí pomocný parametr UPDLOCK uzamkne vybrané řádky:  
  
```sql  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 Pomocí bloků pomocný parametr zámku UPDLOCK všechny řádky, pokus o aktualizaci řádků před první transakce dokončena. Zaručí se tak, že mají vybrané řádky žádné konflikty. když se aktualizují později v transakci. Viz "Pomocné parametry zámku" v SQL Server Books Online.  
  
 Pokud vaše aplikace obsahuje mnoho konflikty, izolaci snímku nemusí být nejlepší volbou. Pomocné parametry by měla sloužit pouze při opravdu potřebujete. Aplikace by neměl být navržený tak, aby neustále spoléhá na pomocné parametry zámku pro jeho operace.  
  
## <a name="see-also"></a>Viz také  
 [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)      
 [Průvodce Správa verzí řádku a transakce uzamčení](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide)
