---
title: Uživatelské instance SQL Serveru Express
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.openlocfilehash: fabd9b94b8c0a3f0e0db220e84d6c2eca3537c50
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894416"
---
# <a name="sql-server-express-user-instances"></a>Uživatelské instance SQL Serveru Express
Edice Microsoft SQL Server Express (SQL Server Express) podporuje funkci uživatelské instance, která je k dispozici pouze při použití .NET Framework Zprostředkovatel dat pro SQL Server (`SqlClient`). Uživatelská instance je samostatná instance SQL Server Express databázového stroje, který je generován nadřazenou instancí. Uživatelské instance umožňují uživatelům, kteří nejsou správci na místních počítačích, připojovat se k SQL Server Express databází a připojovat se k nim. Každá instance se spouští v rámci kontextu zabezpečení jednotlivého uživatele, a to na základě jednoho jednotlivého uživatele.  
  
## <a name="user-instance-capabilities"></a>Možnosti uživatelské instance  
 Uživatelské instance jsou užitečné pro uživatele, kteří používají Windows pod uživatelským účtem s minimálním oprávněním (lua), protože každý uživatel má SQL Server`sysadmin`oprávnění správce systému () nad instancí běžící na svém počítači, aniž by bylo nutné spouštět jako Windows. také správce. Software spuštěný na uživatelské instanci s omezenými oprávněními nemůže provádět změny v rámci systému, protože instance SQL Server Express je spuštěna v účtu uživatele systému Windows bez oprávnění správce, nikoli jako služba. Každá uživatelská instance je izolovaná od své nadřazené instance a ze všech ostatních uživatelských instancí spuštěných ve stejném počítači. Databáze běžící v uživatelské instanci se otevírají pouze v jednouživatelském režimu a není možné, aby se k databázím spuštěným v uživatelské instanci připojovali více uživatelů. Replikace a distribuované dotazy jsou taky pro uživatelské instance zakázané.  
  
 Další informace najdete v části "uživatelské instance" v tématu SQL Server Books Online.  
  
> [!NOTE]
> Uživatelské instance nejsou nutné pro uživatele, kteří jsou již správci na svých počítačích, nebo pro scénáře zahrnující více uživatelů databáze.  
  
## <a name="enabling-user-instances"></a>Povolení uživatelských instancí  
 Aby bylo možné generovat uživatelské instance, musí být spuštěná Nadřazená instance SQL Server Express. Uživatelské instance jsou ve výchozím nastavení povolené, když je nainstalovaná SQL Server Express a může je explicitně povolit nebo zakázat Správce systému, který spouští systémovou uloženou proceduru **sp_configure** u nadřazené instance.  
  
```sql  
-- Enable user instances.  
sp_configure 'user instances enabled','1'
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 Síťový protokol pro uživatelské instance musí být místní pojmenované kanály. Uživatelskou instanci nelze spustit ve vzdálené instanci SQL Server a přihlášení SQL Server nejsou povolena.  
  
## <a name="connecting-to-a-user-instance"></a>Připojení k uživatelské instanci  
 Klíčová `AttachDBFilename` slova a<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>umožňují připojení<xref:System.Data.SqlClient.SqlConnection> k uživatelské instanci. `User Instance` Uživatelské instance jsou podporovány <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `UserInstance` také vlastnostmi a `AttachDBFilename` .  
  
 Všimněte si následujícího ukázkového připojovacího řetězce, který vidíte níže:  
  
- `Data Source` Klíčové slovo odkazuje na nadřazenou instanci SQL Server Express, která generuje uživatelskou instanci. Výchozí instance je .\SQLEXPRESS.  
  
- `Integrated Security`je nastaven na `true`. Pro připojení k uživatelské instanci je vyžadováno ověřování systému Windows. Přihlašovací jména SQL Server nejsou podporovaná.  
  
- Je nastaven na `true`, který vyvolá uživatelskou instanci. `User Instance` (Výchozí hodnota je `false`.)  
  
- Klíčové `AttachDbFileName` slovo připojovacího řetězce se používá pro připojení primárního databázového souboru (. mdf), který musí obsahovat úplný název cesty. `AttachDbFileName`také odpovídá klíčům "rozšířené vlastnosti" a "prvotnímu názvu souboru" v <xref:System.Data.SqlClient.SqlConnection> připojovacím řetězci.  
  
- `|DataDirectory|` Náhradní řetězec uzavřený v symbolech kanálu označuje datový adresář aplikace, který otevírá připojení, a poskytuje relativní cestu, která označuje umístění databáze. mdf a. ldf a souborů protokolu. Pokud chcete tyto soubory najít jinde, musíte zadat úplnou cestu k souborům.  
  
```text
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
> Můžete také použít <xref:System.Data.SqlClient.SqlConnectionStringBuilder> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> vlastnosti a <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> k sestavení připojovacího řetězce v době běhu.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>&#124;Použití náhradního řetězce&#124; DataDirectory  
 `AttachDbFileName`bylo rozšířeno v ADO.NET 2,0 s úvodním `|DataDirectory|` řetězcem (uzavřeným v symbolech kanálu). `DataDirectory`používá se ve spojení s `AttachDbFileName` nástrojem k označení relativní cesty k datovému souboru a umožňuje vývojářům vytvářet připojovací řetězce, které jsou založeny na relativní cestě ke zdroji dat místo nutnosti zadat úplnou cestu.  
  
 Fyzické umístění, na `DataDirectory` které odkazuje, závisí na typu aplikace. V tomto příkladu je soubor Northwind. mdf, který se má připojit, umístěný ve složce \App_Data aplikace.  
  
```text
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 Když `DataDirectory` se použije, výsledná cesta k souboru nemůže být vyšší v adresářové struktuře než adresář, na který odkazuje náhradní řetězec. Pokud je například plně rozbalený `DataDirectory` C:\AppDirectory\app_data, pak vzorový připojovací řetězec zobrazený výše funguje, protože je pod c:\AppDirectory. Ale pokus o zadání `DataDirectory` jako `|DataDirectory|\..\data` způsobí chybu, protože \Data není podadresářem \AppDirectory.  
  
 Pokud je v připojovacím řetězci nesprávně formátovaný řetězec nahrazení, <xref:System.ArgumentException> bude vyvolána výjimka.  
  
> [!NOTE]
> <xref:System.Data.SqlClient>přeloží nahrazující řetězce na úplné cesty proti systému souborů místního počítače. Proto se názvy vzdáleného serveru, protokolu HTTP a cesty UNC nepodporují. Pokud se server nenachází v místním počítači, vyvolá se při otevření připojení výjimka.  
  
 <xref:System.Data.SqlClient.SqlConnection> Když je otevřen, je přesměrován z výchozí instance SQL Server Express do spuštěné instance spuštěné v rámci účtu volajícího.  
  
> [!NOTE]
> Může být nutné zvýšit hodnotu, <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> protože instance uživatelů mohou trvat déle než běžné instance.  
  
 Následující fragment kódu otevře nový `SqlConnection`, zobrazí připojovací řetězec v okně konzoly a pak ukončí připojení při ukončení `using` bloku kódu.  
  
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
> Uživatelské instance nejsou podporovány v modulu CLR (Common Language Runtime), který je spuštěn v rámci SQL Server. Je vyvolána výjimka, `Open` Pokud je volána na <xref:System.Data.SqlClient.SqlConnection> typu, `User Instance=true` který obsahuje připojovací řetězec. <xref:System.InvalidOperationException>  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Doba života připojení uživatelské instance  
 Na rozdíl od verzí SQL Server spouštěných jako služba nemusí být instance SQL Server Express spouštěna a zastavena ručně. Pokaždé, když se uživatel přihlásí a připojí k uživatelské instanci, spustí se instance uživatele, pokud ještě není spuštěná. Databáze uživatelské instance mají `AutoClose` nastavenou možnost, aby se databáze automaticky ukončila po určité době nečinnosti. Proces soubor Sqlservr. exe, který je spuštěný, je spuštěný po dobu omezeného časového limitu po zavření posledního připojení k instanci, takže není potřeba ho restartovat, pokud se před vypršením časového limitu otevře jiné připojení. Uživatelská instance se automaticky vypne, pokud se žádné nové připojení neotevře před uplynutím časového limitu. Správce systému v nadřazené instanci může nastavit dobu trvání časového limitu pro uživatelskou instanci pomocí **procedury sp_configure** pro změnu **časového limitu uživatelské instance** . Výchozí hodnota je 60 minut.  
  
> [!NOTE]
> Pokud `Min Pool Size` se používá v připojovacím řetězci s hodnotou větší než nula, připojení Pooler vždycky udržuje několik otevřených připojení a uživatelská instance se automaticky nevypne.  
  
## <a name="how-user-instances-work"></a>Jak fungují uživatelské instance  
 Při prvním vygenerování uživatelské instance pro každého uživatele jsou **Hlavní** databáze a systémové databáze **msdb** zkopírovány ze složky data šablony do cesty v adresáři úložiště místních dat aplikace uživatele pro výhradní použití instancí uživatele. Tato cesta je obvykle `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`. Po spuštění uživatelské instance se do tohoto adresáře zapisují také soubory **tempdb**, log a Trace. Pro instanci je vygenerován název, který zaručuje, že bude jedinečný pro každého uživatele.  
  
 Ve výchozím nastavení mají všichni členové skupiny Windows Builtin\Users oprávnění k připojení k místní instanci a oprávnění ke čtení a spouštění pro SQL Server binárních souborů. Po ověření přihlašovacích údajů volajícího uživatele hostujícího uživatelskou instanci se tento uživatel `sysadmin` v této instanci stala. Pro uživatelské instance je povolena pouze sdílená paměť, což znamená, že jsou možné pouze operace na místním počítači.  
  
 Uživatelům musí být udělena oprávnění ke čtení i zápisu u souborů. mdf a. ldf zadaných v připojovacím řetězci.  
  
> [!NOTE]
> Soubory. mdf a. ldf reprezentují databázi a soubory protokolů, v uvedeném pořadí. Tyto dva soubory jsou odpovídající sadou, proto je třeba dbát na to, aby se operace zálohování a obnovení provedla. Databázový soubor obsahuje informace o přesné verzi souboru protokolu a databáze se neotevře, pokud je spojena s nesprávným souborem protokolu.  
  
 Aby nedošlo k poškození dat, otevře se databáze v uživatelské instanci s výhradním přístupem. Pokud dvě různé uživatelské instance sdílejí stejnou databázi na stejném počítači, uživatel první instance musí databázi zavřít, aby ji bylo možné otevřít v druhé instanci.  
  
## <a name="user-instance-scenarios"></a>Scénáře uživatelské instance  
 Uživatelské instance poskytují vývojářům databázových aplikací SQL Server úložiště dat, které nezávisí na vývojářích, kteří mají na svých vývojových počítačích účty pro správu. Uživatelské instance jsou založené na modelu Access/jet, kde se databázová aplikace jednoduše připojuje k souboru a uživatel má automaticky úplná oprávnění ke všem databázovým objektům, aniž by museli udělit zásah správce systému. nastaven. Má fungovat v situacích, kdy uživatel běží pod uživatelským účtem s minimálním oprávněním (LUA) a nemá oprávnění správce na serveru nebo v místním počítači, a proto musí vytvářet databázové objekty a aplikace. Uživatelské instance umožňují uživatelům vytvářet instance v době běhu, která běží pod vlastním kontextem zabezpečení uživatele, a ne v kontextu zabezpečení přísnější systémové služby.  
  
> [!IMPORTANT]
> Uživatelské instance by se měly používat jenom ve scénářích, kde jsou všechny aplikace, které ji používají, plně důvěryhodné.  
  
 Mezi scénáře uživatelské instance patří:  
  
- Libovolná aplikace s jedním uživatelem, kde se nevyžadují sdílení dat.  
  
- Nasazení ClickOnce. Pokud jsou v cílovém počítači již nainstalovány .NET Framework 2,0 (nebo novější) a SQL Server Express, instalační balíček stažený jako výsledek akce ClickOnce může být nainstalován a používán uživateli bez oprávnění správce. Všimněte si, že správce musí nainstalovat SQL Server Express, pokud je součástí instalačního programu. Další informace naleznete v tématu [nasazení ClickOnce pro model Windows Forms](../../../winforms/clickonce-deployment-for-windows-forms.md).
  
- Vyhrazené hostování ASP.NET pomocí ověřování systému Windows. Jedna instance SQL Server Express může být hostována v intranetu. Aplikace se připojuje pomocí účtu ASPNET systému Windows, nikoli pomocí zosobnění. Uživatelské instance by se neměly používat pro scénáře třetích stran nebo sdílené hostování, kde by všechny aplikace sdílely stejnou instanci uživatele a už by nezůstaly izolované od sebe.  
  
## <a name="see-also"></a>Viz také:

- [SQL Server a ADO.NET](index.md)
- [Připojovací řetězce](../connection-strings.md)
- [Připojení ke zdroji dat](../connecting-to-a-data-source.md)
- [Přehled ADO.NET](../ado-net-overview.md)
