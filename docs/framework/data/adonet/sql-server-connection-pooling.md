---
title: Připojení k serveru SQL sdružování (ADO.NET)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7e51d44e-7c4e-4040-9332-f0190fe36f07
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: c0be63e767255508ac93555a503980f3798e70c0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="sql-server-connection-pooling-adonet"></a>Připojení k serveru SQL sdružování (ADO.NET)
Připojení k serveru databáze obvykle se skládá z několika kroků časově náročná. Fyzický kanál například soket nebo pojmenovaný kanál je třeba stanovit, musí dojít k počáteční metody handshake se serverem, informace o připojovacím řetězci musí být analyzovány, připojení musí být ověřeny serverem, musí být spuštěn kontroly pro zapsání v aktuální transakce a tak dále.  
  
 V praxi, většina aplikací použít pro připojení pouze jednu nebo několik různých konfigurací. To znamená, že během provádění aplikací, mnoha identické připojení bude možné opakovaně otevřít a uzavřen. Chcete-li minimalizovat náklady na otevření připojení, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] používá volat metodu optimalizace *sdružování připojení*.  
  
 Sdružování připojení snižuje počet pokusů, které musí být otevřeno nové připojení. *Pro sdružování* udržuje vlastnictví fyzické připojení. Spravuje připojení tak aktivní sadu aktivních připojení pro každou konfiguraci dané připojení. Vždy, když uživatel volá `Open` na připojení, pro sdružování hledá dostupné připojení ve fondu. Pokud je dostupné ve fondu připojení, vrátí ji do volající místo otevřít nové připojení. Pokud aplikace zavolá `Close` na připojení, pro sdružování vrátí ji do sadu aktivních připojení místo zavřením ve fondu. Po připojení se vrátí do fondu, je připraven k znovu použít při dalším `Open` volání.  
  
 Pouze připojení se stejnou konfigurací, můžete ve fondu. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] udržuje několik fondů ve stejnou dobu, jeden pro každou konfiguraci. Připojení jsou rozdělené do fondů připojovací řetězec a identitu systému Windows při použití integrovaného zabezpečení. Připojení jsou také fondu založené na tom, jestli jsou zařazeny v transakci. Při použití <xref:System.Data.SqlClient.SqlConnection.ChangePassword%2A>, <xref:System.Data.SqlClient.SqlCredential> instance ovlivňuje fondu připojení. Různé instance <xref:System.Data.SqlClient.SqlCredential> použije jiným připojením fondy, i v případě, že ID uživatele a heslo jsou stejné.  
  
 Sdružování připojení může výrazně zvýšit výkon a škálovatelnost vaší aplikace. Ve výchozím nastavení, je povoleno sdružování připojení v [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Pokud zakážete explicitně ho, optimalizuje pro sdružování připojení, jak jsou otevřené a uzavřené ve vaší aplikaci. Můžete také zadat několik modifikátory řetězec připojení můžete řídit chování sdružování připojení. Další informace najdete v tématu "Řízení připojení sdružování s připojovací řetězec klíčová slova" dál v tomto tématu.  
  
> [!NOTE]
>  Pokud je povoleno sdružování připojení, a pokud dojde k vypršení časového limitu nebo jiné chybě přihlášení, bude vyvolána výjimka, a následující pokusy o připojení se nezdaří pro další pět sekund, "blokování období". Pokud aplikace se pokusí připojit v rámci blokování období, bude první výjimka vyvolána znovu. Následné selhání po skončení blokování doby bude výsledkem nová blokování období, které je dvakrát stejně dlouho jako předchozí blokování období až do maximálního počtu jednu minutu.  
  
## <a name="pool-creation-and-assignment"></a>Vytvoření fondu a přiřazení  
 Při prvním otevření připojení, je vytvořen fond připojení podle přesný odpovídající algoritmu, který přidruží fondu připojovací řetězec v připojení. Každý fond připojení je přidružen odlišné připojovací řetězec. Když je otevřít nové připojení, pokud připojovací řetězec není přesnou shodu na existující fond, vytvoří se nový fond. Připojení jsou ve fondu podle procesu, podle aplikační domény, na připojovací řetězec a pokud se používá integrované zabezpečení za identitu systému Windows. Připojovací řetězce musí být také přesnou shodu; klíčová slova zadaná v jiném pořadí pro stejné připojení bude samostatně ve fondu.  
  
 V následujícím C# příkladu tři nové <xref:System.Data.SqlClient.SqlConnection> objekty se vytvoří, ale pouze dva fondy připojení jsou nezbytné ke správě je. První a druhý připojovací řetězce lišit podle hodnoty přiřazené `Initial Catalog`.  
  
```  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=Northwind"))  
    {  
        connection.Open();        
        // Pool A is created.  
    }  
  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=pubs"))  
    {  
        connection.Open();        
        // Pool B is created because the connection strings differ.  
    }  
  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=Northwind"))  
    {  
        connection.Open();        
        // The connection string matches pool A.  
    }  
```  
  
 Pokud `MinPoolSize` v připojovacím řetězci není zadána nebo je zadán jako nula, připojení ve fondu budou uzavřeny po určité době nečinnosti. Ale pokud zadaný `MinPoolSize` je větší než nula, fondu připojení nebude odstraněn, až `AppDomain` je odpojen a ukončení procesu. Údržby neaktivní nebo prázdný fondů zahrnuje režijní náklady na minimální systém.  
  
> [!NOTE]
>  Fondu je automaticky vymazán poté, co dojde k závažné chybě, jako je například převzetí služeb při selhání.  
  
## <a name="adding-connections"></a>Přidání připojení  
 Fond připojení se vytvoří pro každý jedinečný připojovací řetězec. Při vytváření fondu více objektů připojení jsou vytvořen a přidán do fondu, aby je nesplňuje požadavek na minimální fondu velikost. Připojení jsou přidány do fondu, podle potřeby až k maximální velikosti fondu zadána (výchozí hodnota je 100). Připojení jsou vydávány zpět do fondu, když jsou uzavřeny nebo zlikvidován.  
  
 Když <xref:System.Data.SqlClient.SqlConnection> je požadován objekt, se získávají z fondu, pokud je k dispozici použitelné připojení. Být použitelná, připojení musí nepoužívané, mají odpovídající kontext transakce nebo nepřidružený s jakýkoliv obsah transakcí a mít platný odkaz na serveru.  
  
 Pro sdružování připojení splňuje požadavky na připojení pomocí změna přidělování připojení při jejich vydání zpět do fondu. Pokud byl dosažen maximální počet a není k dispozici žádné použitelné připojení, požadavek ve frontě. Pro sdružování se potom pokusí získat všechna připojení, dokud nebude dosaženo časového limitu (výchozí hodnota je 15 sekund). Pokud pro sdružování nemůže splnit požadavek, než vyprší časový limit připojení, je vyvolána výjimka.  
  
> [!CAUTION]
>  Důrazně doporučujeme po dokončení pomocí ho, aby připojení bude vrácen do fondu vždy ukončení připojení. Můžete provést pomocí `Close` nebo `Dispose` metody `Connection` objektu, nebo pomocí otevírání všechna připojení uvnitř `using` příkaz v C#, nebo `Using` příkaz v jazyce Visual Basic. Připojení, které nejsou výslovně nemusí přidat nebo vrátí do fondu. Další informace najdete v tématu [pomocí příkazu](~/docs/csharp/language-reference/keywords/using-statement.md) nebo [postupy: odstranění systémového prostředku](~/docs/visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md) jazyka Visual Basic.  
  
> [!NOTE]
>  Nevolejte `Close` nebo `Dispose` na `Connection`, `DataReader`, nebo jiné spravovaného objektu v `Finalize` metoda vaší třídy. V finalizační metodu vydání pouze nespravovaných prostředků, které vlastní třídu přímo. Pokud vaše třída nevlastní žádné nespravovaných prostředků, nezahrnujte `Finalize` metoda v definici vaší třídy. Další informace najdete v tématu [uvolňování paměti](../../../../docs/standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Události přihlášení a odhlášení nebudou vyvolávat na serveru, pokud připojení je načtena z nebo vrátí do fondu připojení. Toto je, protože připojení není uzavřený ve skutečnosti, pokud se vrátí do fondu připojení. Další informace najdete v tématu [třídy událostí auditu přihlášení](http://msdn2.microsoft.com/library/ms190260.aspx) a [třídy událostí auditu odhlášení](http://msdn2.microsoft.com/library/ms175827.aspx) v SQL Server Books Online.  
  
## <a name="removing-connections"></a>Odebrání připojení  
 Poté, co se má přibližně 4-8 minutách nečinnosti nebo pokud pro sdružování zjistí, že má bylo porušeno připojení se serverem pro sdružování připojení Odebere připojení z fondu. Všimněte si, že bude možné zjišťovat poškozený připojení až po pokusu o komunikaci se serverem. Pokud se najde připojení, který je už připojený k serveru, je označena jako neplatná. Neplatný připojení jsou vyřazeny z fondu připojení jenom v případě, že jsou uzavřeny nebo uvolnit.  
  
 Pokud existuje připojení k serveru, který má smazán, můžete toto připojení čerpají z fondu i v případě, že nebyl zjištěn poškozený připojení a označena jako neplatná pro sdružování připojení. Je to tento případ, proto režii kontroluje, že připojení je stále platný by eliminovat o výhodách pro sdružování tím, že na jinou dobu odezvy na serveru, dochází. V takovém případě první pokus o připojení k zjistí, že připojení bylo porušeno. a je vyvolána výjimka.  
  
## <a name="clearing-the-pool"></a>Vymazání fondu  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 zavedená dva nové metody pro vymazávání fondu: <xref:System.Data.SqlClient.SqlConnection.ClearAllPools%2A> a <xref:System.Data.SqlClient.SqlConnection.ClearPool%2A>. `ClearAllPools` Vymaže fondy připojení pro daného zprostředkovatele, a `ClearPool` vymaže fondu připojení, která souvisí s konkrétním připojení. Pokud je připojení používá při volání, jsou označena odpovídajícím způsobem. Když jsou uzavřeny, jsou zahozeny místo nevrátila do fondu.  
  
## <a name="transaction-support"></a>Podpora transakcí  
 Připojení jsou vykreslovány z fondu a kontext přiřazené na základě transakce. Pokud `Enlist=false` je zadaný v připojovacím řetězci, fondu připojení je zajištěno, že toto připojení je uvedené v <xref:System.Transactions.Transaction.Current%2A> kontextu. Když je připojení ukončeno a vrátí do fondu s zařazené `System.Transactions` transakce, ho je vyčleněné tak, že další žádost o tomto fondu připojení se stejným `System.Transactions` transakce se vrátí stejné připojení, pokud je k dispozici. Pokud se objeví žádost a nejsou k dispozici žádná ve fondu připojení, je připojení čerpají z beztransakční součástí fondu a zařazen. Pokud žádná připojení jsou k dispozici v oblasti buď fondu, nové připojení se vytvoří a zařazen.  
  
 Když je připojení ukončeno, jeho vydání zpět do fondu a do příslušné pododdíl na základě jeho kontextu transakce. Proto můžete zavřít připojení bez generování chybu, i když je stále distribuovanou transakci čekající na vyřízení. To umožňuje potvrzení nebo přerušení později distribuované transakce.  
  
## <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Řízení sdružování připojení s klíčovými slovy řetězec připojení  
 `ConnectionString` Vlastnost <xref:System.Data.SqlClient.SqlConnection> objekt podporuje dvojice klíč/hodnota řetězce připojení, které lze použít k úpravě chování logiky sdružování připojení. Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="pool-fragmentation"></a>Fragmentace fondu  
 Fragmentace fondu je častých problémů v mnoha webových aplikací, kde aplikace může vytvářet velký počet fondy, které nejsou vydání, dokud proces bude ukončen. Velký počet připojení zůstane otevřené a využívání paměti, což vede k nižšímu výkonu.  
  
### <a name="pool-fragmentation-due-to-integrated-security"></a>Fragmentace fondu z důvodu integrované zabezpečení  
 Připojení jsou ve fondu podle připojovací řetězec a identity uživatele. Pokud používáte základní ověřování nebo ověřování systému Windows na webu a přihlášení k integrovanému zabezpečení, tedy získáte jeden fond na uživatele. I když to zlepšuje výkon při následné databáze požadavků pro jednoho uživatele, tento uživatel nemůže využít výhod připojení vytvořená jinými uživateli. Výsledkem je také alespoň jedno připojení na uživatele k databázovému serveru. Toto je vedlejším účinkem konkrétní architektura webové aplikace, které vývojáři musí naváží proti auditování požadavky na zabezpečení a.  
  
### <a name="pool-fragmentation-due-to-many-databases"></a>Fragmentace fondu z důvodu mnoha databázemi  
 Mnoho poskytovatelům internetových služeb hostovat několik webových serverů na jednom serveru. Potvrďte Forms ověřování přihlášení a pak otevřete připojení k databázi specifické pro uživatele nebo skupiny uživatelů, mohou používat jednu databázi. Připojení k databázi ověřování se ve fondu a kdokoliv používal. Je však samostatný fond připojení pro každou databázi, které zvýšit počet připojení k serveru.  
  
 Toto je také vedlejším účinkem návrh aplikace. Existuje relativně jednoduchý způsob, jak tomuto vedlejšímu efektu zabránit, aniž by to ohrozilo zabezpečení při připojení k systému SQL Server. Místo připojení k databázi samostatné pro jednotlivé uživatele nebo skupiny, připojit do stejné databáze na serveru a potom spusťte [!INCLUDE[tsql](../../../../includes/tsql-md.md)] příkaz USE změnit na požadovanou databázi. Následující fragment kódu ukazuje vytvoření počátečního připojení k `master` databáze a poté přepne na požadovanou databáze zadaná v `databaseName` proměnnou string.  
  
```vb  
' Assumes that command is a valid SqlCommand object and that  
' connectionString connects to master.  
    command.Text = "USE DatabaseName"  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
// Assumes that command is a SqlCommand object and that  
// connectionString connects to master.  
command.Text = "USE DatabaseName";  
using (SqlConnection connection = new SqlConnection(  
  connectionString))  
  {  
    connection.Open();  
    command.ExecuteNonQuery();  
  }  
```  
  
## <a name="application-roles-and-connection-pooling"></a>Aplikační role a sdružování připojení  
 Po systému SQL Server byl aktivován aplikační role voláním `sp_setapprole` systémové uložené procedury, kontext zabezpečení připojení nelze resetovat. Ale pokud je povoleno sdružování připojení se vrátí do fondu a při ve fondu připojení se znovu použije dojde k chybě. Další informace najdete v článku znalostní báze Knowledge Base "[chyby role SQL aplikace s sdružování prostředků OLE DB](http://support.microsoft.com/default.aspx?scid=KB;EN-US;Q229564)."  
  
### <a name="application-role-alternatives"></a>Aplikace Role alternativy  
 Doporučujeme vám, že můžete využít výhod mechanismy zabezpečení, které můžete použít místo aplikační role. Další informace najdete v tématu [vytváření aplikační role v systému SQL Server](../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md).  
  
## <a name="see-also"></a>Viz také  
 [Sdružování připojení](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [SQL Server a ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [Čítače výkonu](../../../../docs/framework/data/adonet/performance-counters.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
