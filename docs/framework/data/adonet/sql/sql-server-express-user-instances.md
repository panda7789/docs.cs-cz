---
title: "Instance systému SQL Server Express uživatele"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f963aba983379d1474c3eedc348860751306a1bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-express-user-instances"></a>Instance systému SQL Server Express uživatele
Microsoft SQL Server Express Edition (SQL Server Express) podporuje funkci instance uživatele, která je k dispozici pouze při použití zprostředkovatele dat .NET Framework pro SQL Server (`SqlClient`). Uživatelskou instanci je samostatnou instanci SQL serveru Express databázový stroj, který je generován nadřazená instance. Uživatelské instance povolit uživatelům, kteří nejsou správci na svých místních počítačích pro připojení a připojení k databázím SQL Server Express. Každá instance běží v kontextu zabezpečení jednotlivé uživatele, na jednu instanci každého uživatele zvlášť.  
  
## <a name="user-instance-capabilities"></a>Možnosti uživatele Instance  
 Uživatelské instance jsou užitečné pro uživatele, kteří používají systém Windows pod účtem uživatele s minimálními oprávněními (LUA), protože každý uživatel má správce systému SQL Server (`sysadmin`) oprávnění v rámci instancí spuštěnou na svém počítači bez nutnosti spustit jako systému Windows také správce. Spuštění softwaru na uživatelskou instanci s omezenými oprávněními nelze provést změny systému, protože instance systému SQL Server Express běží pod účtem systému Windows bez oprávnění správce uživatele, ne jako službu. Každá instance uživatele je izolovaný z její nadřazená instance a všechny ostatní uživatele instance na stejném počítači spuštěna. Databáze spuštěné v instanci uživatele jsou v režimu jednoho uživatele jenom otevřené, a není možné pro více uživatelů k připojování k databázím systémem uživatelskou instanci. Replikace a distribuované dotazy jsou také zakázaná pro uživatelské instance.  
  
 Další informace najdete v tématu "Uživatelské instance" v SQL Server Books Online.  
  
> [!NOTE]
>  Uživatelské instance nejsou potřeba pro uživatele, kteří jsou již správci v jejich počítačích nebo pro scénáře zahrnující více uživatelů databáze.  
  
## <a name="enabling-user-instances"></a>Povolení uživatelské instance  
 Chcete-li vygenerovat uživatelské instance, musí být spuštěn nadřazená instance systému SQL Server Express. Uživatelské instance jsou ve výchozím nastavení povolené, když je nainstalován systém SQL Server Express a může být explicitně povoleno nebo zakázáno správcem systému provádění **sp_configure** systémové uložené procedury na nadřazená instance.  
  
```  
-- Enable user instances.  
sp_configure 'user instances enabled','1'   
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 Síťový protokol pro uživatelské instance musí být místní pojmenovaných kanálů. Uživatelské instance nelze spustit na vzdálené instanci systému SQL Server, není povoleno přihlášení serveru SQL.  
  
## <a name="connecting-to-a-user-instance"></a>Připojování k uživatelské instanci  
 `User Instance` a `AttachDBFilename` <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> povolit klíčová slova <xref:System.Data.SqlClient.SqlConnection> pro připojení k uživatelské instanci. Uživatelské instance jsou také podporovány pomocí <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `UserInstance` a `AttachDBFilename` vlastnosti.  
  
 Vezměte na vědomí následující skutečnosti související připojovací řetězec ukázka vidíte níže:  
  
-   `Data Source` – Klíčové slovo odkazuje nadřazená instance systému SQL Server Express, která generuje uživatelské instance. Je výchozí instance. \sqlexpress.  
  
-   `Integrated Security`je nastavena na `true`. Ověřování systému Windows se pokud chcete připojit k uživatelské instanci, je požadovaná; Přihlášení serveru SQL nejsou podporovány.  
  
-   `User Instance` Je nastaven na `true`, který vyvolá uživatelskou instanci. (Výchozí hodnota je `false`.)  
  
-   `AttachDbFileName` Klíčové slovo připojovacího řetězce se používá k připojení primární soubor databáze (MDF), které musí obsahovat úplnou cestu. `AttachDbFileName`také odpovídá "rozšířené vlastnosti" a "počáteční název souboru" klíče v rámci <xref:System.Data.SqlClient.SqlConnection> připojovací řetězec.  
  
-   `|DataDirectory|` Náhradní řetězec v kanálu symboly odkazuje na adresář dat aplikace otevření připojení a poskytuje relativní cestu, která určuje umístění souborů .mdf a .ldf databáze a protokolu. Pokud chcete vyhledat tyto soubory jinde, musíte zadat úplnou cestu k souborům.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
>  Můžete také <xref:System.Data.SqlClient.SqlConnectionStringBuilder> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> a <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> vlastnosti, které chcete vytvořit připojovací řetězec na dobu běhu.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>Pomocí &#124; DataDirectory &#124; Náhradní řetězec  
 `AttachDbFileName`byla rozšířena v ADO.NET 2.0 se zavedením `|DataDirectory|` (uzavřený v kanálu symboly) náhradní řetězec. `DataDirectory`se používá ve spojení s `AttachDbFileName` udávajících relativní cestu k souboru dat umožňuje vývojářům vytvářet připojovací řetězce, které jsou založeny na relativní cestu ke zdroji dat namísto zapotřebí zadat úplnou cestu.  
  
 Fyzickému umístění, do které `DataDirectory` odkazuje na závisí na typu aplikace. V tomto příkladu souboru Northwind.mdf připojí se nachází ve složce \app_data aplikace.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 Když `DataDirectory` se používá, výsledná cesta k souboru nemůže být struktury adresářů vyšší než directory ukazující na náhradní řetězec. Například pokud plně rozšířené `DataDirectory` C:\AppDirectory\app_data, pak je odstavcích funguje, protože je pod c:\AppDirectory ukázka připojovací řetězec. Ale pokus o zadejte `DataDirectory` jako `|DataDirectory|\..\data` způsobí chybu, protože \data není podadresáři \AppDirectory.  
  
 Pokud připojovací řetězec má nesprávně naformátovaný náhradní řetězec <xref:System.ArgumentException> bude vyvolána.  
  
> [!NOTE]
>  <xref:System.Data.SqlClient>Přeloží náhradní řetězce do úplné cesty proti systému souborů v místním počítači. Proto vzdálený server, HTTP a UNC se nepodporují názvy cest. Po otevření připojení, pokud server není umístěný v místním počítači, je vyvolána výjimka.  
  
 Když <xref:System.Data.SqlClient.SqlConnection> je otevřít, ho přesměruje z výchozí instance systému SQL Server Express na spuštění initiated instance spuštěna pod účtem volajícího.  
  
> [!NOTE]
>  Může být nutné zvýšit <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> hodnotu vzhledem k tomu, že uživatelské instance může trvat déle než regulární instancí.  
  
 Následující fragment kódu otevře novou `SqlConnection`, zobrazí připojovací řetězec v okně konzoly a poté uzavře připojení při ukončení `using` blok kódu.  
  
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
>  Uživatelské instance nejsou podporovány v common language runtime (CLR) kódu, který běží v systému SQL Server. <xref:System.InvalidOperationException> Je vyvolána, pokud `Open` se volá na <xref:System.Data.SqlClient.SqlConnection> s `User Instance=true` v připojovacím řetězci.  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Doba platnosti Instance připojení uživatele  
 Na rozdíl od verze systému SQL Server, spuštění jako služba instance serveru SQL Server Express není nutné ručně spuštění a zastavení. Pokaždé, když uživatel přihlásí a připojí se k instanci uživatele uživatelské instance se spustí, pokud ještě není spuštěná. Máte uživatelské instance databáze `AutoClose` možnost set tak, že databáze je automaticky zastaví po určité době nečinnosti. Je udržováno sqlservr.exe proces, který se spustí systémem pro omezený časový limit po zavření posledního připojení k instanci, takže není nutné restartovat, je-li otevřeno jiné připojení než časový limit vypršela platnost. Uživatelské instance Pokud vypne automaticky otevře žádné nové připojení před uplynutím této doby vypršení časového limitu. Správce systému v instanci nadřazené můžete nastavit dobu trvání časového limitu pro uživatelské instance pomocí **sp_configure** změnit **uživatelské instance vypršení časového limitu** možnost. Výchozí hodnota je 60 minut.  
  
> [!NOTE]
>  Pokud `Min Pool Size` se používá v připojovacím řetězci s hodnotou větší než nula, bude pro sdružování připojení vždy udržovat několik otevřené připojení a uživatelské instance nebude automaticky vypnout.  
  
## <a name="how-user-instances-work"></a>Jak uživatel instancí pracovních  
 Při prvním uživatelskou instanci se vygeneruje pro každý uživatel, **hlavní** a **databázi msdb** systémové databáze se zkopírují ze složky dat šablony na cestu v části úložiště data uživatele místní aplikace adresář pro výhradní použití uživatelské instance. Obvykle je tato cesta `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`. Při spouštění uživatelské instance, **databáze tempdb**, protokolování a trasování soubory se zapisují také do tohoto adresáře. Název se generuje pro instanci, která se musí být jedinečný pro každého uživatele.  
  
 Ve výchozím nastavení jsou všichni členové skupiny Windows Builtin\Users udělena oprávnění k připojení na místní instanci a také číst a spouštět oprávnění na binární soubory systému SQL Server. Jakmile ověříte přihlašovací údaje volání uživatele hostování uživatelské instance se změní na tohoto uživatele `sysadmin` v této instanci. Pouze sdílené paměti je povolený pro uživatelské instance, což znamená, že je možné, jenom operace v místním počítači.  
  
 Uživatelé musejí mít oprávnění ke čtení i zápisu oprávnění u souborů .mdf a .ldf, zadaný v připojovacím řetězci.  
  
> [!NOTE]
>  Soubory MDF a LDF představují soubory databáze a protokolu v uvedeném pořadí. Tyto dva soubory jsou odpovídající sady, takže péče musí být přijata během zálohování a obnovení operací. Soubor databáze obsahuje informace o přesnou verzi souboru protokolu a databáze nebude otevřena, pokud je spolu s špatného souboru protokolu.  
  
 Chcete-li zabránit poškození dat, je databáze v uživatelské instance otevřené s výhradní přístup. Pokud dvě instance jiný uživatel sdílet stejnou databázi ve stejném počítači, musíte uživatele na první instance zavřít databázi před otevřením v druhé instance.  
  
## <a name="user-instance-scenarios"></a>Uživatelské Instance scénáře  
 Uživatelské instance poskytují vývojářům databázové aplikace s úložištěm dat systému SQL Server, které nezávisí na vývojáře s účty pro správu na svých počítačích vývoj. Uživatelské instance jsou založené na modelu přístup/Jet, databáze aplikace jednoduše připojuje k souboru, kde uživatel automaticky má plná oprávnění pro všechny objekty databáze bez nutnosti zásahu správce systému pro udělení oprávnění. Je určena k práci v situacích, kde uživatel běží pod účtem uživatele s minimálními oprávněními (LUA) a nemá oprávnění správce na serveru nebo místního počítače a zároveň musí vytvořit databázové objekty a aplikace. Uživatelské instance povolit uživatelům vytvářet instancí v době běhu, které spouštějí v kontextu zabezpečení přihlášeného uživatele a není v kontextu zabezpečení více privilegované služby systému.  
  
> [!IMPORTANT]
>  Uživatelské instance lze používat pouze ve scénářích kde jsou plně důvěryhodný pro všechny aplikace používat.  
  
 Uživatelské instance scénáře patří:  
  
-   Všechny aplikace jednoho uživatele, kde sdílení dat se nevyžaduje.  
  
-   ClickOnce – nasazení. Pokud jsou na cílovém počítači již nainstalovány rozhraní .NET Framework 2.0 (nebo novější) a SQL Server Express, instalační balíček stáhli v důsledku ClickOnce akce lze nainstalovat a používat uživatelé bez oprávnění správce. Všimněte si, že musí nainstalovat správce systému SQL Server Express Pokud, který je součástí instalačního programu. Další informace najdete v tématu [ClickOnce nasazení pro aplikace systému Windows Forms](http://msdn.microsoft.com/en-us/34d8c770-48f2-460c-8d67-4ea5684511df).  
  
-   Vyhrazené hostování prostředí ASP.NET pomocí ověřování systému Windows. Jedna instance systému SQL Server Express, může být hostovaný na intranetu. Aplikace se připojí pomocí účtu ASPNET Windows, není pomocí zosobnění. Uživatelské instance není vhodné používat pro třetí strany nebo sdílené hostování scénáře, kde všechny aplikace by sdílet stejnou instanci uživatele a by zůstala už od sebe navzájem oddělené.  
  
## <a name="see-also"></a>Viz také  
 [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [Připojovací řetězce](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [Připojení ke zdroji dat](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
