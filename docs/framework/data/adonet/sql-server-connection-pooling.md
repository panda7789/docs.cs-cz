---
title: Připojení k SQL serveru sdružování (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e51d44e-7c4e-4040-9332-f0190fe36f07
ms.openlocfilehash: f416ae8252d9991905da7eeaf4ce6398ff0e7461
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406493"
---
# <a name="sql-server-connection-pooling-adonet"></a>Připojení k SQL serveru sdružování (ADO.NET)
Připojování k databázovému serveru, obvykle se skládá z několika kroků časově náročné. Fyzické kanál například soket nebo pojmenovaný kanál musí navázat, počáteční metody handshake se serverem se musí vyskytovat, informace o připojovacím řetězci musí být analyzován, server musí být ověřené připojení, kontroly musí být spuštěn pro zařazování aktuální transakce a tak dále.  
  
 V praxi používat většinu aplikací pouze jednu nebo několik různých konfigurací pro připojení. To znamená, že při spuštění aplikace, mnoho stejné připojení bude možné opakovaně otevřel a uzavřel. Chcete-li minimalizovat náklady na otevření připojení, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] používá optimalizaci techniky označované jako *sdružování připojení*.  
  
 Sdružování připojení snižuje počet případů, kdy se nové připojení musí být otevřeny. *Pro sdružování* udržuje vlastnictví fyzické připojení. Spravuje připojení udržováním aktivní sadu aktivních připojení pro každou konfiguraci dané připojení. Vždy, když uživateli zavolá `Open` na připojení, hledá pro sdružování připojení k dispozici ve fondu. Pokud je k dispozici ve fondu připojení, se vrátí volajícímu místo otevřít nové připojení. Když aplikace volá `Close` připojení, pro sdružování vrátí ji do klientů ve fondu sadu aktivních připojení místo jeho uzavřením. Po připojení se vrátí do fondu, je připraven znovu použije při dalším `Open` volání.  
  
 Pouze připojení se stejnou konfigurací můžete ve fondu. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] udržuje několik fondů ve stejnou dobu, jeden pro každou konfiguraci. Připojení jsou rozděleny do fondů pomocí připojovacího řetězce a identita Windows při použití integrovaného zabezpečení. Připojení se spojují také závislosti na tom, zda je uveden v transakci. Při použití <xref:System.Data.SqlClient.SqlConnection.ChangePassword%2A>, <xref:System.Data.SqlClient.SqlCredential> instance má vliv na fond připojení. Různé instance <xref:System.Data.SqlClient.SqlCredential> používat fondy jiné připojení, i v případě, že ID uživatele a heslo jsou stejné.  
  
 Sdružování připojení může výrazně zlepšit výkon a škálovatelnost aplikace. Ve výchozím nastavení, je povoleno sdružování připojení v [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Pokud zakážete explicitně ji, optimalizuje pro sdružování připojení jsou otevřené a uzavřené ve vaší aplikaci. Můžete také zadat několik modifikátory připojovací řetězec můžete řídit chování sdružování připojení. Další informace najdete v tématu "Řízení připojení sdružování s připojovací řetězec klíčová slova" dále v tomto tématu.  
  
> [!NOTE]
>  Pokud je povoleno sdružování připojení, pokud dojde k vypršení časového limitu nebo jiná chyba přihlášení, bude vyvolána výjimka a následné pokusy o připojení se nezdaří pro další pět sekund, "blokování období". Pokud se aplikace pokusí o připojení v rámci doby blokování, první výjimka vyvolána znovu. Další chyby po skončení blokování období způsobí nové blokování období, která je dvakrát až předchozí blokování období až do maximálního počtu jednu minutu.  
  
## <a name="pool-creation-and-assignment"></a>Vytvoření fondu a přiřazení  
 Při prvním otevření připojení se vytvoří fond připojení podle přesně odpovídající algoritmus, který přidruží připojovací řetězec v připojení k fondu. Každý fond připojení souvisí s distinct připojovací řetězec. Při otevření nové připojení připojovací řetězec není přesná shoda do existujícího fondu, je vytvořen nový fond. Proces pro doménu aplikace, na připojovací řetězec a při použití integrovaného zabezpečení na Windows identity klientů ve fondu připojení. Připojovací řetězce musí být také přesnou shodu. klíčová slova uvedená v jiném pořadí pro stejné připojení bude ve fondu samostatně.  
  
 V následujícím příkladu C#, tři nové <xref:System.Data.SqlClient.SqlConnection> jsou vytvořeny objekty, ale pouze dva fondy připojení jsou nutné k jejich správě. Všimněte si, že první a druhý připojovací řetězce se liší podle hodnoty přiřazené pro `Initial Catalog`.  
  
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
  
 Pokud `MinPoolSize` v připojovacím řetězci nebyl zadán nebo je zadán jako nula, připojení ve fondu se zavře po určité době nečinnosti. Ale pokud zadaný `MinPoolSize` je větší než nula, fond připojení není zničen až `AppDomain` je uvolněna a proces skončí. Údržby není neaktivní nebo prázdný fondů zahrnuje minimální systém režii.  
  
> [!NOTE]
>  Fondu jsou automaticky vymazány, pokud dojde k závažné chybě, jako je převzetí služeb při selhání.  
  
## <a name="adding-connections"></a>Přidání připojení  
 Fond připojení se vytvoří pro každý jedinečných připojovací řetězec. Při vytvoření fondu jsou více objektů připojení vytvořen a přidán do fondu tak, aby velikost požadavek na minimální fond není splněna. Připojení se přidají do fondu podle potřeby až do maximální velikosti fondu zadána (výchozí hodnota je 100). Připojení se vydávají zpět do fondu, pokud jsou ukončen nebo odstraněn.  
  
 Když <xref:System.Data.SqlClient.SqlConnection> je požadován objekt, se získávají z fondu, pokud je k dispozici použitelné připojení. Má být použitelná, připojení musí nevyužité, nemají odpovídající kontext transakce nebo nepřidružené k žádnému kontextu transakce a mít platný odkaz na serveru.  
  
 Pro sdružování připojení splňuje požadavky pro připojení pomocí přerozdělení připojení při jejich vydání zpět do fondu. Pokud bylo dosaženo maximální velikosti fondu a není k dispozici žádné použitelné připojení, je požadavek ve frontě. Pro sdružování pokusí uvolnit všechna připojení, dokud nebude dosaženo časového limitu (výchozí hodnota je 15 sekund). Pokud pro sdružování nemůže požadavek splnit, předtím, než vyprší časový limit připojení, je vyvolána výjimka.  
  
> [!CAUTION]
>  Důrazně doporučujeme po dokončení jeho použití tak, aby připojení bude vrácen do fondu vždy ukončení připojení. Můžete provést buď pomocí `Close` nebo `Dispose` metody `Connection` objektu, nebo otevřením všechna připojení v rámci `using` příkaz v jazyce C#, nebo `Using` v sadě Visual Studio. Připojení, které nebyly uzavřeny explicitně nemusí přidali nebo vrácen do fondu. Další informace najdete v tématu [příkaz using](~/docs/csharp/language-reference/keywords/using-statement.md) nebo [postupy: odstranění systémového prostředku](~/docs/visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md) v jazyce Visual Basic.  
  
> [!NOTE]
>  Nevolejte `Close` nebo `Dispose` na `Connection`, `DataReader`, nebo jakýkoli jiný spravovaný objekt v `Finalize` metoda vaší třídy. V finalizační metodu jenom uvolnění nespravovaných prostředků, které vaše třída vlastní přímo. Pokud vaše třída není vlastníkem jakýchkoliv nespravovaných prostředků, nezahrnujte `Finalize` metoda v definici třídy. Další informace najdete v tématu [uvolňování](../../../../docs/standard/garbage-collection/index.md).  
  
Další informace o událostech, které jsou přidružené k otevření a zavření připojení najdete v tématu [třídy události auditování přihlášení](/sql/relational-databases/event-classes/audit-login-event-class) a [třída událostí auditu odhlášení](/sql/relational-databases/event-classes/audit-logout-event-class) v dokumentaci k SQL serveru.  
  
## <a name="removing-connections"></a>Odebrání připojení  
 Pro sdružování připojení odebere z fondu připojení, poté, co byl nečinný přibližně 4. – 8 minut, nebo pokud pro sdružování zjistí, že připojení k serveru bylo porušeno. Všimněte si, že přerušená připojení lze zjistit pouze po pokusu o komunikaci se serverem. Pokud připojení není nalezen, který není připojený k serveru, je označena jako neplatná. Neplatné připojení se odeberou z fondu připojení, pouze když jsou uzavřeny nebo uvolnit.  
  
 Pokud připojení existuje na serveru, který chybí, lze toto připojení rozlišovat z fondu i v případě, že nebyl zjištěn přerušená připojení a označena jako neplatná pro sdružování připojení. To platí, protože režii kontrole, že připojení je stále platný by o výhodách pro sdružování způsobením učiníte serveru dojde k odstranění. V tomto případě první pokus o připojení k zjistí, že připojení bylo porušeno. a je vyvolána výjimka.  
  
## <a name="clearing-the-pool"></a>Vymazává se fondu  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 zavedené dvě nové metody pro vymazávání fondu: <xref:System.Data.SqlClient.SqlConnection.ClearAllPools%2A> a <xref:System.Data.SqlClient.SqlConnection.ClearPool%2A>. `ClearAllPools` Vymaže sdružení připojení pro daného poskytovatele a `ClearPool` vymaže fondu připojení, který je spojen s konkrétním připojení. Pokud je připojení používaná v okamžiku volání, jsou označen odpovídajícím způsobem. Když jsou uzavřeny, jsou zahozeny místo se vrací do fondu.  
  
## <a name="transaction-support"></a>Podpora transakcí  
 Připojení jsou vykreslovány vedle z fondu a kontext přiřazené na základě transakce. Není-li `Enlist=false` zadaná v připojovacím řetězci, fond připojení zajišťuje, že připojení je uveden v <xref:System.Transactions.Transaction.Current%2A> kontextu. Pokud je připojení uzavřen a vrácen do fondu se zařazených `System.Transactions` transakce, to je odložena tak, že další žádosti pro tento fond připojení se stejným `System.Transactions` transakce se vrátí stejné připojení, pokud je k dispozici. Pokud takový požadavek vydává a nejsou k dispozici žádné připojení ve fondu, je připojení ze součástí fondu beztransakční a zařazen. Pokud v obou oblastech fondu jsou k dispozici žádné připojení, se nové připojení a zařazeny.  
  
 Když je připojení ukončeno, uvolní se zpět do fondu a do příslušné dělení na základě jeho kontextu transakce. Proto můžete zavřít připojení bez dojde k chybě, i když distribuované transakce je stále čekající na vyřízení. To umožňuje potvrzení nebo přerušení později distribuované transakce.  
  
## <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Řízení sdružování připojení s klíčovými slovy připojovací řetězec  
 `ConnectionString` Vlastnost <xref:System.Data.SqlClient.SqlConnection> objekt podporuje dvojice klíč/hodnota řetězce připojení, které lze použít k úpravě chování logiky sdružování připojení. Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="pool-fragmentation"></a>Fragmentace fondu  
 Fragmentace fondu je běžný problém v mnoha webových aplikací, kde aplikace může vytvářet velký počet fondů, které nejsou uvolněny, dokud se proces ukončí. Velký počet připojení tak zůstanou otevřené a využívání paměti, což má za následek nízký výkon.  
  
### <a name="pool-fragmentation-due-to-integrated-security"></a>Fragmentace fondu z důvodu integrované zabezpečení  
 Připojení se sdílejí ve fondech podle připojovací řetězec a identitu uživatele. Proto pokud používáte základní ověřování nebo ověřování Windows na webovém serveru a integrované zabezpečené přihlášení, můžete získat jeden fond na uživatele. I když to zlepšuje výkon při následné databáze požadavků pro jednoho uživatele, tento uživatel nemůže využít připojení provedené ostatními uživateli. Výsledkem je také alespoň jedno připojení na uživatele pro databázový server. Toto je vedlejším účinkem konkrétní architektura pro webové aplikace, které musí vývojáři naváží s požadavky na auditování a zabezpečení.  
  
### <a name="pool-fragmentation-due-to-many-databases"></a>Fragmentace fondu z důvodu velkého počtu databází  
 Mnoho poskytovatelů služeb Internetu hostování několika webů na jednom serveru. Potvrďte účet ověřování formulářů a pak otevřete připojení ke konkrétní databázi pro uživatele nebo skupinu uživatelů mohou používat izolované databáze. Připojení k databázi ověřování je ve fondu a používání pro všechny uživatele. Je však samostatný fond připojení pro každou databázi, která zvýšit počet připojení k serveru.  
  
 Toto je také vedlejší efekt návrh aplikace. Je poměrně jednoduchý způsob, jak tomuto vedlejšímu efektu zabránit bez narušení zabezpečení, když se připojíte k serveru SQL Server. Místo připojování k samostatnou databázi pro jednotlivé uživatele nebo skupiny, připojení ke stejné databázi na serveru a následné provádění [!INCLUDE[tsql](../../../../includes/tsql-md.md)] příkaz USE změnit na požadované databáze. Následující fragment kódu ukazuje vytvoření počátečního připojení k `master` databáze a poté přepnete do požadovaného databázi zadané v `databaseName` proměnné řetězce.  
  
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
 Po SQL Server aktivoval se aplikační role voláním `sp_setapprole` systémové uložené procedury, kontext zabezpečení připojení nelze resetovat. Ale pokud je povoleno sdružování připojení je vrácen do fondu a dojde k chybě, když je znovu použít ve fondu připojení. Další informace najdete v článku znalostní báze Knowledge Base "[chyby role SQL aplikace s sdružování prostředků OLE DB](https://support.microsoft.com/default.aspx?scid=KB;EN-US;Q229564)."  
  
### <a name="application-role-alternatives"></a>Alternativy Role aplikace  
 Doporučujeme vám, že využijete mechanismy zabezpečení, které můžete použít namísto aplikační role. Další informace najdete v tématu [vytváření rolí aplikací v systému SQL Server](../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md).  
  
## <a name="see-also"></a>Viz také  
 [Sdružování připojení](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [SQL Server a ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [Čítače výkonu](../../../../docs/framework/data/adonet/performance-counters.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
