---
title: Instance systému SQL Server Express uživatele
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.openlocfilehash: 31c0efbe953b56304c264444082185b9a9227d60
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745095"
---
# <a name="sql-server-express-user-instances"></a>Instance systému SQL Server Express uživatele
Microsoft SQL Server Express Edition (SQL Server Express) podporuje funkci instance uživatele, která je dostupná jenom při použití zprostředkovatele dat .NET Framework pro SQL Server (`SqlClient`). Uživatelské instance se samostatnou instanci SQL serveru Express databázového stroje, který je generován nadřazená instance. Uživatelské instance povolit uživatelům, kteří nejsou správci na svých místních počítačích k připojení a připojení k databázím SQL Server Express. Každá instance spouští v kontextu zabezpečení jednotlivých uživatelů, na jednu instanci každého uživatele zvlášť.  
  
## <a name="user-instance-capabilities"></a>Možnosti uživatele Instance  
 Uživatelské instance jsou užitečné pro uživatele, kteří používají Windows pod účtem uživatele s minimálními oprávněními (LUA), protože každý uživatel má správce systému SQL Server (`sysadmin`) oprávnění v instanci spuštěné na svém počítači bez nutnosti spustit jako Windows i správce. Spuštění softwaru na uživatelskou instanci s omezenými oprávněními nemůže provádět změny celý systém, protože instance systému SQL Server Express je spuštěný pod účtem Windows bez oprávnění správce uživatele, ne jako službu. Každý uživatel instance je izolovaná od své nadřazené instance a z dalších uživatelské instance běží na stejném počítači. Databáze spuštěné v instanci uživatele jsou otevřeny v jednouživatelském režimu pouze a není možné pro více uživatelů pro připojení k databázím běžící na uživatelskou instanci. Replikace a distribuovaných dotazů jsou zakázané taky pro uživatelské instance.  
  
 Další informace najdete v tématu "Uživatelské instance" SQL Server Books Online.  
  
> [!NOTE]
>  Uživatelské instance nejsou potřeba pro uživatele, kteří už jsou správci na svých počítačích nebo pro scénáře zahrnující více uživatelů databáze.  
  
## <a name="enabling-user-instances"></a>Povolení uživatelské instance  
 Ke generování uživatelských instancí, musí být spuštěná nadřazená instance systému SQL Server Express. Uživatelské instance se ve výchozím nastavení povolená, když je nainstalován systém SQL Server Express a může být explicitně povoleno nebo zakázáno správcem systému spouštění **uložené procedury sp_configure** systémové uložené procedury na nadřazená instance.  
  
```  
-- Enable user instances.  
sp_configure 'user instances enabled','1'   
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 Síťový protokol pro uživatelské instance musí být místní pojmenovaných kanálů. Uživatelské instance nelze spustit ve vzdálené instanci systému SQL Server a SQL serveru přihlašovací jména nejsou povoleny.  
  
## <a name="connecting-to-a-user-instance"></a>Připojování k uživatelské instanci  
 `User Instance` a `AttachDBFilename` <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> povolit klíčová slova <xref:System.Data.SqlClient.SqlConnection> pro připojení k uživatelské instanci. Uživatelské instance jsou také podporovány <xref:System.Data.SqlClient.SqlConnectionStringBuilder> `UserInstance` a `AttachDBFilename` vlastnosti.  
  
 Mějte na paměti následující skutečnosti související ukázkové připojovací řetězec je uvedeno níže:  
  
-   `Data Source` – Klíčové slovo odkazuje na nadřazený instanci systému SQL Server Express, která generuje uživatelské instance. Je výchozí instanci. \sqlexpress.  
  
-   `Integrated Security` je nastavena na `true`. Pokud chcete připojit k uživatelské instanci, je potřeba; ověřování Windows Přihlášení serveru SQL Server nejsou podporovány.  
  
-   `User Instance` Je nastavena na `true`, která vyvolá uživatelskou instanci. (Výchozí hodnota je `false`.)  
  
-   `AttachDbFileName` Klíčové slovo připojovacího řetězce se použije k připojení primární soubor databáze (MDF), který musí obsahovat úplný název cesty. `AttachDbFileName` také odpovídá "rozšířené vlastnosti" a "počáteční název souboru" klíče v rámci <xref:System.Data.SqlClient.SqlConnection> připojovací řetězec.  
  
-   `|DataDirectory|` Náhradní řetězec v kanálu symboly odkazuje na data adresáře aplikace otevřete připojení a poskytuje relativní cesta určující umístění soubory MDF a LDF databáze a protokolu. Pokud chcete vyhledat tyto soubory jinde, musí zadat úplnou cestu k souborům.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
>  Můžete také použít <xref:System.Data.SqlClient.SqlConnectionStringBuilder> <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> a <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> vlastnosti, které chcete vytvořit připojovací řetězec při běhu.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>Použití &#124;DataDirectory&#124; náhradní řetězec  
 `AttachDbFileName` rozšířila po zavedení služby ve verzi 2.0 rozhraní ADO.NET `|DataDirectory|` (ohraničen symboly kanálu) náhradní řetězec. `DataDirectory` používá se společně s `AttachDbFileName` označující relativní cesta k souboru dat, umožňuje vývojářům vytvářet připojovací řetězce, které jsou založeny na relativní cestu ke zdroji dat namísto zapotřebí zadat úplnou cestu.  
  
 Fyzické umístění, která `DataDirectory` odkazuje na závisí na typu aplikace. V tomto příkladu je soubor Northwind.mdf bude připojený umístěn ve složce \app_data aplikace.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 Když `DataDirectory` se používá, výsledná cesta k souboru nemůže být vyšší v adresářové struktuře než directory, na které odkazují náhradní řetězec. Například pokud plně rozšířené `DataDirectory` C:\AppDirectory\app_data, je ukázkový řetězec připojení uvedené nahoře funguje, protože je pod c:\AppDirectory. Ale pokus zadat `DataDirectory` jako `|DataDirectory|\..\data` způsobí chybu, protože \data není kompatibilní se jedná o podadresář \AppDirectory.  
  
 Pokud má nesprávně naformátovanou náhradní řetězec, připojovací řetězec <xref:System.ArgumentException> bude vyvolána výjimka.  
  
> [!NOTE]
>  <xref:System.Data.SqlClient> Přeloží náhradní řetězce do úplné cesty prověří se systémem souborů místního počítače. Proto vzdálený server HTTP a UNC cestu názvy nejsou podporovány. Když je otevřeno připojení, pokud server není umístěný v místním počítači, je vyvolána výjimka.  
  
 Když <xref:System.Data.SqlClient.SqlConnection> je otevřen, přesměruje se z výchozí instance systému SQL Server Express na spuštěné instance za běhu spuštěný pod účtem volajícího.  
  
> [!NOTE]
>  Může být nutné zvýšit <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> hodnotu, protože uživatelské instance může trvat déle než pravidelných instancí.  
  
 Následující fragment kódu se otevře nový `SqlConnection`, připojovací řetězec se zobrazí v okně konzoly a poté uzavře připojení při ukončení `using` bloku kódu.  
  
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
>  Uživatelské instance nejsou podporovány v společný kód jazyka runtime (CLR), na kterém běží v rámci služby SQL Server. <xref:System.InvalidOperationException> Je vyvolána, pokud `Open` je volán na <xref:System.Data.SqlClient.SqlConnection> , který má `User Instance=true` v připojovacím řetězci.  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Životnost Instance připojení uživatele  
 Na rozdíl od verze SQL serveru, spuštěn jako služba, instance SQL serveru Express nemusí být ručně spustit a zastavit. Pokaždé, když uživatel přihlásí a připojí se k uživatelské instanci uživatelské instance se spustí, pokud ještě není spuštěná. Máte uživatelské instanci databáze `AutoClose` sada možností tak, že databáze je po určité době nečinnosti automaticky vypnout. Sqlservr.exe proces, který se spustil, zůstane spuštění pro omezený časový limit po uzavření posledního připojení k instanci, takže není nutné restartovat, pokud je otevřen jiným připojením, dříve, než vypršel časový limit. Uživatelské instance automaticky vypne pokud dříve, než tento časový limit vypršel, otevře se nové připojení. Správce systému v instanci nadřazeného můžete nastavit dobu trvání časového limitu pro uživatelskou instanci pomocí **uložené procedury sp_configure** změnit **uživatelské instance vypršení časového limitu** možnost. Výchozí hodnota je 60 minut.  
  
> [!NOTE]
>  Pokud `Min Pool Size` se používá v připojovacím řetězci s hodnotou větší než nula, bude pro sdružování připojení vždy udržovat několik otevřené připojení a uživatelské instance nebude automaticky vypnout.  
  
## <a name="how-user-instances-work"></a>Jak uživatel instance práce  
 Prvním je vygenerovat uživatelskou instanci pro každého uživatele, **hlavní** a **msdb** systémové databáze se zkopírují ze složky dat šablony na cestu v úložišti dat uživatele místní aplikace adresář pro výhradní použití podle uživatelské instance. Tato cesta je obvykle `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`. Při spouštění uživatelské instance, **tempdb**, protokolování a trasování soubory se zapisují také do tohoto adresáře. Název je generován pro instanci, která je zaručeně jedinečná pro každého uživatele.  
  
 Ve výchozím nastavení jsou všechny členy skupiny Windows Builtin\Users udělit oprávnění k připojení v místní instanci a oprávnění číst a spouštět na binární soubory systému SQL Server. Jakmile ověříte pověření volajícího uživatele hostování uživatelské instance, stane `sysadmin` u dané instance. Pouze sdílené paměti je povolená pro uživatelské instance, což znamená, že je možné pouze operace v místním počítači.  
  
 Uživatelé musejí mít oprávnění číst i zapisovat oprávnění u souborů .mdf a .ldf, zadaný v připojovacím řetězci.  
  
> [!NOTE]
>  Soubory MDF a LDF představují databázi a soubory protokolů, v uvedeném pořadí. Tyto dva soubory jsou odpovídající sady, tak, aby péče vzít do úvahy při zálohování a obnovení operací. Soubor databáze obsahuje informace o přesnou verzi souboru protokolu a databázi nelze otevřít, pokud je párována s chybný soubor protokolu.  
  
 Abyste zabránili poškození dat, s výhradním přístupem otevření databáze v uživatelské instanci. Pokud dvě různé uživatelské instance sdílejí stejnou databázi na stejný počítač, musí uživatel na první instanci zavřít databázi předtím, než ho můžete otevřít v druhé instance.  
  
## <a name="user-instance-scenarios"></a>Uživatelské Instance scénáře  
 Uživatelské instance poskytují vývojářům aplikací, databázi s úložištěm dat serveru SQL Server, který není závislý na vývojáře s účty pro správu na svých vývojových prostředích. Uživatelské instance jsou založeny na modelu přístup/Jet, databázové aplikace jednoduše připojuje k souboru, kde uživatel automaticky má úplná oprávnění ve všech objektů databáze bez nutnosti zásahu správce systému pro udělení oprávnění. Jeho účelem je fungovat v situacích, kde uživatel je spuštěný pod účtem uživatele s minimálními oprávněními (LUA) a nemá oprávnění správce na serveru nebo v místním počítači, ale potřebuje k vytvoření objektů databáze a aplikace. Uživatelské instance umožňuje uživatelům vytvářet instance v době běhu, které běží v kontextu zabezpečení vlastního uživatele a ne v kontextu zabezpečení privilegovanější systémové služby.  
  
> [!IMPORTANT]
>  Uživatelské instance by měla sloužit pouze ve scénářích kde jsou všechny aplikace pomocí jeho plně důvěryhodné.  
  
 Uživatelské instance scénáře patří:  
  
-   Všechny aplikace jednoho uživatele, kde sdílení dat se nevyžaduje.  
  
-   ClickOnce – nasazení. Pokud jsou na cílovém počítači již nainstalovány rozhraní .NET Framework 2.0 (nebo novější) a SQL Server Express, instalační balíček stáhli jako výsledek akce ClickOnce lze nainstalovat a používat uživatelé bez oprávnění správce. Mějte na paměti, musí správce nainstalovat systém SQL Server Express Pokud, který je součástí instalace. Další informace najdete v tématu [nasazení pro Windows Forms aplikací ClickOnce](https://msdn.microsoft.com/library/34d8c770-48f2-460c-8d67-4ea5684511df).  
  
-   Vyhrazené hostování v technologii ASP.NET pomocí ověřování Windows. Jedna instance systému SQL Server Express je možné hostovat na intranetu. Aplikace se připojí pomocí účtu Windows ASPNET, nikoli pomocí zosobnění. Uživatelské instance není vhodné používat pro třetí strany nebo sdílené hostování situacích, kdy všechny aplikace bude sdílet stejnou instanci uživatele a by už zůstat izolované od sebe navzájem.  
  
## <a name="see-also"></a>Viz také  
 [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [Připojovací řetězce](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [Připojení ke zdroji dat](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
