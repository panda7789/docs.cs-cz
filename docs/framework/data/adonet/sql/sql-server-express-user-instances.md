---
title: Uživatelské instance SQL Serveru Express
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.openlocfilehash: 2bd67a9315eda4161d4b76e1638f5c08f9598a52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174482"
---
# <a name="sql-server-express-user-instances"></a>Uživatelské instance SQL Serveru Express
Microsoft SQL Server Express Edition (SQL Server Express) podporuje funkci instance uživatele, která je k`SqlClient`dispozici pouze při použití zprostředkovatele dat rozhraní .NET Framework pro SQL Server ( ). Instance uživatele je samostatná instance databázového stroje SQL Server Express, která je generována nadřazenou instancí. Uživatelské instance umožňují uživatelům, kteří nejsou správci v místních počítačích, připojit databáze SQL Server Express a připojit se k němu. Každá instance běží v kontextu zabezpečení jednotlivých uživatelů na základě jedné instance na uživatele.  
  
## <a name="user-instance-capabilities"></a>Možnosti instance uživatele  
 Uživatelské instance jsou užitečné pro uživatele, kteří používají systém Windows pod uživatelským účtem s nejnižšími oprávněními (LUA). Každý uživatel má oprávnění`sysadmin`správce systému serveru SQL Server ( ) nad instancí spuštěnou v počítači, aniž by musel být spuštěn také jako správce systému Windows. Software prováděný v instanci uživatele s omezenými oprávněními nemůže provádět změny v celém systému, protože instance SQL Server Express je spuštěna pod účtem systému Windows, který není správcem, uživatele, nikoli jako služba. Každá instance uživatele je izolována od nadřazené instance a od všech ostatních instancí uživatelů spuštěných ve stejném počítači. Databáze spuštěné v instanci uživatele jsou otevřeny pouze v režimu jednoho uživatele a není možné, aby se více uživatelů připojilo k databázím spuštěným v instanci uživatele. Replikace a distribuované dotazy jsou také zakázány pro instance uživatelů.
  
> [!NOTE]
> Instance uživatelů nejsou potřeba pro uživatele, kteří jsou již správci ve svých vlastních počítačích, nebo pro scénáře zahrnující více uživatelů databáze.  
  
## <a name="enabling-user-instances"></a>Povolení uživatelských instancí  
 Chcete-li generovat instance uživatelů, musí být spuštěna nadřazená instance služby SQL Server Express. Uživatelské instance jsou ve výchozím nastavení povoleny při instalaci služby SQL Server Express a mohou být explicitně povoleny nebo zakázány správcem systému, který provádí **sp_configure** systému uloženou proceduru v nadřazené instanci.  
  
```sql  
-- Enable user instances.  
sp_configure 'user instances enabled','1'
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 Síťový protokol pro instance uživatelů musí být místní pojmenované kanály. Instanci uživatele nelze spustit na vzdálené instanci serveru SQL Server a přihlášení serveru SQL Server nejsou povolena.  
  
## <a name="connecting-to-a-user-instance"></a>Připojení k instanci uživatele  
 Klíčová `User Instance` `AttachDBFilename` <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> slova a <xref:System.Data.SqlClient.SqlConnection> umožňují připojení k instanci uživatele. Uživatelské instance jsou také <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `UserInstance` podporovány vlastnostmi a. `AttachDBFilename`  
  
 Všimněte si následujícího příkladu ukázkového připojovacího řetězce uvedeného níže:  
  
- Klíčové `Data Source` slovo odkazuje na nadřazenou instanci SQL Server Express, která generuje instanci uživatele. Výchozí instance je .\sqlexpress.  
  
- `Integrated Security`je nastavena na `true`. Chcete-li se připojit k instanci uživatele, je vyžadováno ověřování systému Windows. Přihlášení serveru SQL Server nejsou podporována.  
  
- Je `User Instance` nastavena `true`na , která vyvolá instanci uživatele. (Výchozí hodnota `false`je .)  
  
- Klíčové `AttachDbFileName` slovo připojovacího řetězce se používá k připojení primárního databázového souboru (.mdf), který musí obsahovat úplný název cesty. `AttachDbFileName`také odpovídá "rozšířené vlastnosti" a "název počáteční <xref:System.Data.SqlClient.SqlConnection> název souboru" klíče v rámci připojovacího řetězce.  
  
- Řetězec `|DataDirectory|` náhrady uzavřený v symbolech kanálu odkazuje na datový adresář aplikace, která otevírá připojení, a poskytuje relativní cestu označující umístění databáze MDF a .ldf a souborů protokolu. Chcete-li tyto soubory vyhledat jinde, je nutné zadat úplnou cestu k souborům.  
  
```text
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
> Vlastnosti <xref:System.Data.SqlClient.SqlConnectionStringBuilder> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> a <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> můžete také použít k vytvoření připojovacího řetězce za běhu.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>Použití substitučního řetězce&#124; &#124;DataDirectory  
 `AttachDbFileName`byla prodloužena v ADO.NET 2.0 `|DataDirectory|` se zavedením (uzavřeného v symbolech potrubí) náhradního řetězce. `DataDirectory`se používá ve `AttachDbFileName` spojení s k označení relativní cestu k datovému souboru, což umožňuje vývojářům vytvářet připojovací řetězce, které jsou založeny na relativní cestu ke zdroji dat namísto je nutné zadat úplnou cestu.  
  
 Fyzické umístění, `DataDirectory` na které odkazuje, závisí na typu aplikace. V tomto příkladu je soubor Northwind.mdf, který má být připojen, umístěn ve složce \app_data aplikace.  
  
```text
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 Při `DataDirectory` použití nemůže být výsledná cesta k souboru ve struktuře adresáře vyšší než adresář, na který je odkazováno substitučním řetězcem. Pokud je například `DataDirectory` plně rozbalené C:\AppDirectory\app_data, funguje výše uvedený ukázkový připojovací řetězec, protože je uveden pod c:\AppDirectory. Pokus o zadání `DataDirectory` však `|DataDirectory|\..\data` bude mít za následek chybu, protože \data nejsou podadresářem \AppDirectory.  
  
 Pokud má připojovací řetězec nesprávně formátovaný náhradní řetězec, <xref:System.ArgumentException> bude vyvolána.  
  
> [!NOTE]
> <xref:System.Data.SqlClient>přeloží substituční řetězce na úplné cesty proti systému souborů místního počítače. Proto nejsou podporovány názvy cest vzdáleného serveru, protokolu HTTP a UNC. Výjimka je vyvolána při otevření připojení, pokud server není umístěn v místním počítači.  
  
 <xref:System.Data.SqlClient.SqlConnection> Při otevření je přesměrován z výchozí instance SQL Server Express na instanci iniciovanou za běhu spuštěnou pod účtem volajícího.  
  
> [!NOTE]
> Může být nutné zvýšit <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> hodnotu, protože načtení instancí uživatelů může trvat déle než běžné instance.  
  
 Následující fragment kódu otevře `SqlConnection`nový , zobrazí připojovací řetězec v okně konzoly `using` a potom zavře připojení při ukončení bloku kódu.  
  
```vb  
Private Sub OpenSqlConnection()  
    ' Retrieve the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Using connection As New SqlConnection(connectionString)  
        connection.Open()  
        Console.WriteLine("ConnectionString: {0}", _  
           connection.ConnectionString)  
    End Using  
End Sub  
```  
  
```csharp  
private static void OpenSqlConnection()  
{  
    // Retrieve the connection string.  
    string connectionString = GetConnectionString();  
  
    using (SqlConnection connection =
        new SqlConnection(connectionString))  
    {  
        connection.Open();  
        Console.WriteLine("ConnectionString: {0}",
             connection.ConnectionString);  
    }  
}  
```  
  
> [!NOTE]
> Uživatelské instance nejsou podporovány v kódu CLR (COMMON Language runtime), který je spuštěn uvnitř serveru SQL Server. Je <xref:System.InvalidOperationException> vyvolána, `Open` pokud je <xref:System.Data.SqlClient.SqlConnection> volána na který má `User Instance=true` v připojovacířetězec.  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Doba trvání připojení instance uživatele  
 Na rozdíl od verzí serveru SQL Server, které běží jako služba, instance SQL Server Express není nutné ručně spustit a zastavit. Pokaždé, když se uživatel přihlásí a připojí se k instanci uživatele, spustí se instance uživatele, pokud ještě není spuštěna. Databáze instancí `AutoClose` uživatele mají nastavenou možnost tak, aby se databáze po určité době nečinnosti automaticky vypnula. Proces sqlservr.exe, který je spuštěn, je spuštěn po omezenou dobu časového limitu po ukončení posledního připojení k instanci, takže není nutné jej restartovat, pokud je před vypršením časového limitu otevřeno jiné připojení. Instance uživatele se automaticky vypne, pokud se před vypršením tohoto časového limitu neotevře žádné nové připojení. Správce systému v nadřazené instanci může nastavit dobu trvání časového úseku pro instanci uživatele pomocí **sp_configure** ke změně možnosti **časového času instance uživatele.** Výchozí hodnota je 60 minut.  
  
> [!NOTE]
> Pokud `Min Pool Size` se používá v připojovacím řetězci s hodnotou větší než nula, sdružovací připojení vždy zachová několik otevřených připojení a instance uživatele se automaticky nevypne.  
  
## <a name="how-user-instances-work"></a>Jak fungují instance uživatelů  
 Při prvním generování instance uživatele pro každého uživatele jsou **hlavní** databáze a systémové databáze **MSDB** zkopírovány ze složky Data šablony do cesty v adresáři úložiště dat místní aplikace uživatele pro výhradní použití instancí uživatele. Tato cesta je `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`obvykle . Při spuštění instance uživatele jsou do tohoto adresáře zapsány také soubory **tempdb**, log a trace. Název je generován pro instanci, která je zaručena jedinečný pro každého uživatele.  
  
 Ve výchozím nastavení jsou všem členům skupiny Windows Builtin\Users udělena oprávnění k připojení k místní instanci a také ke čtení a spouštění oprávnění k binárním souborům serveru SQL Server. Po ověření pověření volajícího uživatele hostujícího instanci uživatele `sysadmin` se tento uživatel stane v této instanci. Pro instance uživatelů je povolena pouze sdílená paměť, což znamená, že jsou možné pouze operace v místním počítači.  
  
 Uživatelům musí být udělena oprávnění ke čtení i zápisu souborů MDF a LDF určených v připojovacím řetězci.  
  
> [!NOTE]
> Soubory MDF a LDF představují soubory databáze a protokolu. Tyto dva soubory jsou odpovídající sadu, takže je třeba dbát během zálohování a obnovení operací. Soubor databáze obsahuje informace o přesné verzi souboru protokolu a databáze se neotevře, pokud je spojena s nesprávným souborem protokolu.  
  
 Aby nedošlo k poškození dat, otevře se databáze v instanci uživatele s výhradním přístupem. Pokud dvě různé instance uživatelů sdílejí stejnou databázi ve stejném počítači, uživatel v první instanci musí databázi před otevřením v druhé instanci zavřít.  
  
## <a name="user-instance-scenarios"></a>Scénáře instancí uživatele  
 Uživatelské instance poskytují vývojářům databázových aplikací úložiště dat serveru SQL Server, které nezávisí na vývojáři mají účty pro správu na svých vývojových počítačích. Instance uživatelů jsou založeny na modelu Access/Jet, kde se databázová aplikace jednoduše připojí k souboru a uživatel má automaticky úplná oprávnění pro všechny databázové objekty bez nutnosti zásahu správce systému k udělení oprávnění. Je určen pro práci v situacích, kdy je uživatel spuštěn pod uživatelským účtem s nejnižšími oprávněními (LUA) a nemá oprávnění správce na serveru nebo místním počítači, ale je třeba vytvořit databázové objekty a aplikace. Uživatelské instance umožňují uživatelům vytvářet instance za běhu, které jsou spuštěny v kontextu vlastního zabezpečení uživatele a nikoli v kontextu zabezpečení více privilegované systémové služby.  
  
> [!IMPORTANT]
> Uživatelské instance by měly být používány pouze ve scénářích, kde jsou všechny aplikace, které je používají, plně důvěryhodné.  
  
 Scénáře instancí uživatele zahrnují:  
  
- Všechny aplikace pro jednoho uživatele, kde sdílení dat není vyžadováno.  
  
- ClickOnce nasazení. Pokud jsou v cílovém počítači již nainstalovány rozhraní .NET Framework 2.0 (nebo novější) a SQL Server Express, instalační balíček stažený v důsledku akce ClickOnce může být nainstalován a používán uživateli, kteří nejsou správci. Všimněte si, že správce musí nainstalovat SQL Server Express, pokud je součástí instalace. Další informace naleznete v [tématu ClickOnce Deployment for Windows Forms](../../../winforms/clickonce-deployment-for-windows-forms.md).
  
- Vyhrazené ASP.NET hostování pomocí ověřování systému Windows. Jedna instance SQL Server Express může být hostována v síti intranet. Aplikace se připojuje pomocí účtu aspnet systému Windows, nikoli pomocí zosobnění. Uživatelské instance by neměly být používány pro scénáře hostování třetích stran nebo sdíleného hostování, kde by všechny aplikace sdílely stejnou instanci uživatele a již by od sebe zůstaly izolované.  
  
## <a name="see-also"></a>Viz také

- [SQL Server a ADO.NET](index.md)
- [Připojovací řetězce](../connection-strings.md)
- [Připojení ke zdroji dat](../connecting-to-a-data-source.md)
- [Přehled ADO.NET](../ado-net-overview.md)
