---
title: "Syntaxi připojovacího řetězce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 83e08124b5d532cbb217cc5ff829af06c48518a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="connection-string-syntax"></a>Syntaxi připojovacího řetězce
Má každý zprostředkovatel dat .NET Framework `Connection` objekt, který dědí z <xref:System.Data.Common.DbConnection> a také konkrétního zprostředkovatele <xref:System.Data.Common.DbConnection.ConnectionString%2A> vlastnost. Syntaxi konkrétní připojovacího řetězce pro každého zprostředkovatele je popsána v jeho `ConnectionString` vlastnost. Následující tabulka uvádí zprostředkovatelé čtyři dat, které jsou zahrnuty v rozhraní .NET Framework.  
  
|Zprostředkovatel dat .NET framework|Popis|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Poskytuje přístup k datům pro Microsoft SQL Server. Další informace o syntaxi připojovacího řetězce, najdete v části <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.|  
|<xref:System.Data.OleDb>|Poskytuje přístup k datům pro zdroje dat, které jsou vystavené pomocí technologie OLE DB. Další informace o syntaxi připojovacího řetězce, najdete v části <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.|  
|<xref:System.Data.Odbc>|Poskytuje přístup k datům pro zdroje dat, které jsou vystavené pomocí rozhraní ODBC. Další informace o syntaxi připojovacího řetězce, najdete v části <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.|  
|<xref:System.Data.OracleClient>|Poskytuje přístup k datům pro Oracle verze 8.1.7 nebo novější. Další informace o syntaxi připojovacího řetězce, najdete v části <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.|  
  
## <a name="connection-string-builders"></a>Tvůrci řetězců pro připojení  
 ADO.NET 2.0 zavedly následující počítačů připojovací řetězec pro zprostředkovatele dat .NET Framework.  
  
-   <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
-   <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
-   <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
-   <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Tvůrci řetězců připojení umožňují vytvořit syntakticky připojovací řetězce v době běhu, takže není nutné ručně zřetězení hodnoty připojovacího řetězce v kódu. Další informace najdete v tématu [Tvůrci řetězců pro připojení](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="windows-authentication"></a>Ověřování systému Windows  
 Doporučujeme použít ověřování systému Windows (někdy označovány jako *integrované zabezpečení*) pro připojení ke zdrojům dat, které ji podporují. Syntaxe pracujících v připojovacím řetězci se liší podle zprostředkovatele. Následující tabulka ukazuje syntaxi ověřování systému Windows použít s zprostředkovatele dat .NET Framework.  
  
|Zprostředkovatel|Syntaxe|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
>  `Integrated Security=true`vyvolá výjimku, pokud se používá s `OleDb` zprostředkovatele.  
  
## <a name="sqlclient-connection-strings"></a>SqlClient připojovací řetězce  
 Syntaxe <xref:System.Data.SqlClient.SqlConnection> připojovací řetězec je popsána v <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> vlastnost. Můžete použít <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> vlastnost k získání nebo nastavení připojovací řetězec pro databázi systému SQL Server. Pokud potřebujete připojit na starší verzi systému SQL Server, musíte použít zprostředkovatel dat .NET Framework pro OleDb (<xref:System.Data.OleDb>). Většina klíčová slova připojovací řetězec také mapovat vlastnosti v <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Každý z následujících podob syntaxe použije ověřování systému Windows pro připojení k **AdventureWorks** databáze na místním serveru.  
  
```  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-logins"></a>Přihlášení serveru SQL  
 Ověřování systému Windows je upřednostňovaný pro připojení k systému SQL Server. Ale pokud je požadováno ověřování serveru SQL, použijte následující syntaxi a zadat uživatelské jméno a heslo. V tomto příkladu hvězdičky slouží k reprezentaci platné uživatelské jméno a heslo.  
  
```  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  
  
> [!IMPORTANT]
>  Výchozí nastavení `Persist Security Info` – klíčové slovo je `false`. Jeho nastavení na hodnotu `true` nebo `yes` umožňuje informace citlivé na zabezpečení, včetně ID uživatele a heslo, chcete-li získat připojení po otevření připojení. Zachovat `Persist Security Info` nastavena na `false` zajistit, že nedůvěryhodných nemá přístup k citlivým připojovacím řetězcem.  
  
 Pro připojení k pojmenované instanci systému SQL Server, použijte *název serveru ázev instance* syntaxe.  
  
```  
Data Source=MySqlServer\MSSQL1;"  
```  
  
 Můžete také nastavit <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> vlastnost `SqlConnectionStringBuilder` k názvu instance při sestavování připojovací řetězec. <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> Vlastnost <xref:System.Data.SqlClient.SqlConnection> objekt je jen pro čtení.  
  
> [!NOTE]
>  Ověřování systému Windows mají přednost před přihlášení serveru SQL. Pokud zadáte oba Integrated Security = true, a taky uživatelské jméno a heslo, bude ignorován uživatelského jména a hesla a ověřování systému Windows se použije.  
  
### <a name="type-system-version-changes"></a>Typ změny verze systému  
 `Type System Version` – Klíčové slovo v <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> určuje klienta reprezentace [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] typy. V tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> Další informace o `Type System Version` – klíčové slovo.  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>Připojení a připojení k systému SQL Server Express uživatelské instance  
 Uživatelské instance jsou funkcí v systému SQL Server Express. Umožňují uživatele systémem nejméně privilegovaným místní účet systému Windows pro připojení a databázi systému SQL Server lze spustit bez oprávnění správce. Uživatelskou instanci se provádí pomocí přihlašovacích údajů uživatele systému Windows, ne jako službu.  
  
 Další informace o práci s uživatelské instance najdete v tématu [instance služby SQL Server Express uživatele](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>Pomocí TrustServerCertificate  
 `TrustServerCertificate` – Klíčové slovo je platný pouze při připojování k [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] instance pomocí platného certifikátu. Když `TrustServerCertificate` je nastaven na `true`, přenosové vrstvy budou používat protokol SSL pro šifrování kanál a nepoužívat proti řetěz certifikátů pro ověření vztahu důvěryhodnosti.  
  
```  
"TrustServerCertificate=true;"   
```  
  
> [!NOTE]
>  Pokud `TrustServerCertificate` je nastaven na `true` a šifrování je zapnuté, úrovně šifrování zadaných na serveru, který se použije i v případě `Encrypt` je nastaven na `false` v připojovacím řetězci. Připojení se nezdaří jinak.  
  
### <a name="enabling-encryption"></a>Povolení šifrování  
 Povolit šifrování, pokud certifikát ještě není zřízené na serveru, **vynucení šifrování protokolu** a **důvěřovat certifikátu serveru** možnosti musí být nastavena v modulu snap-in Správce konfigurace serveru SQL. V takovém případě šifrování bude používat certifikát podepsaný svým držitelem serveru bez ověřování, pokud žádný ověřitelný certifikát zřízená na serveru.  
  
 Nastavení aplikace nelze snížit úroveň zabezpečení, které jsou nakonfigurované v systému SQL Server, ale můžete volitelně posílení. Aplikace může požádat o šifrování nastavením `TrustServerCertificate` a `Encrypt` klíčová slova pro `true`, která zaručí, že šifrování probíhá i v případě, že certifikát serveru ještě není zřízené a **vynucení šifrování protokolu**  není nakonfigurován pro klienta. Ale pokud `TrustServerCertificate` není povolena v konfiguraci klienta, je stále vyžadují certifikát zřízené serveru.  
  
 Následující tabulka popisuje všechny případy.  
  
|Nastavení vynucení šifrování protokolu klienta.|Důvěřovat certifikátu serveru nastavení klienta|Šifrování nebo používají šifrování pro atribut řetězce připojení dat|Vztah důvěryhodnosti atribut řetězce připojení certifikát serveru|Výsledek|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|Ne|Není k dispozici|Žádný (výchozí)|Ignorováno|Žádné šifrování probíhá.|  
|Ne|Není k dispozici|Ano|Žádný (výchozí)|Šifrování probíhá pouze v případě, že je ověřit certifikát serveru, jinak se nezdaří pokus o připojení.|  
|Ne|Není k dispozici|Ano|Ano|Šifrování probíhá pouze v případě, že je ověřit certifikát serveru, jinak se nezdaří pokus o připojení.|  
|Ano|Ne|Ignorováno|Ignorováno|Šifrování probíhá pouze v případě, že je ověřit certifikát serveru, jinak se nezdaří pokus o připojení.|  
|Ano|Ano|Žádný (výchozí)|Ignorováno|Šifrování probíhá pouze v případě, že je ověřit certifikát serveru, jinak se nezdaří pokus o připojení.|  
|Ano|Ano|Ano|Žádný (výchozí)|Šifrování probíhá pouze v případě, že je ověřit certifikát serveru, jinak se nezdaří pokus o připojení.|  
|Ano|Ano|Ano|Ano|Šifrování probíhá pouze v případě, že je ověřit certifikát serveru, jinak se nezdaří pokus o připojení.|  
  
 Další informace najdete v tématu [pomocí šifrování bez ověření](http://go.microsoft.com/fwlink/?LinkId=120500) v SQL Server Books Online.  
  
## <a name="oledb-connection-strings"></a>OleDb připojovací řetězce  
 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> Vlastnost <xref:System.Data.OleDb.OleDbConnection> umožňuje získat nebo nastavit připojovací řetězec pro zdroj dat OLE DB, jako je například Microsoft Access. Můžete taky vytvořit `OleDb` připojovací řetězec za běhu pomocí <xref:System.Data.OleDb.OleDbConnectionStringBuilder> třídy.  
  
### <a name="oledb-connection-string-syntax"></a>Syntaxi OleDb připojovacího řetězce  
 Musíte zadat název zprostředkovatele pro <xref:System.Data.OleDb.OleDbConnection> připojovací řetězec. Připojí se k databázi Microsoft Access pomocí zprostředkovatele Jet následující připojovací řetězec. Všimněte si, že `UserID` a `Password` klíčová slova jsou volitelné, pokud databáze je nezabezpečené (výchozí).  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;   
```  
  
 Pokud je databáze Jet zabezpečena pomocí zabezpečení na úrovni uživatele, je nutné zadat umístění z informačního souboru (MDW). Informačního souboru se používá k ověření přihlašovací údaje v připojovacím řetězci.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
>  Je možné poskytnout informace o připojení **OleDbConnection** v souboru Universal Data odkaz (UDL); ale neměli byste tak. Soubory UDL nejsou zašifrované a vystavit informace o připojovacím řetězci ve formátu prostého textu. Protože soubor UDL je externí prostředek založených na souborech do vaší aplikace, nelze zabezpečené, pomocí rozhraní .NET Framework. Soubory UDL nejsou podporovány pro **SqlClient**.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>Pomocí DataDirectory pro připojení k přístupu nebo Jet  
 `DataDirectory`není určena výhradně pro `SqlClient`. Můžete použít taky s <xref:System.Data.OleDb> a <xref:System.Data.Odbc> zprostředkovatele dat .NET. Následující ukázka <xref:System.Data.OleDb.OleDbConnection> řetězec ukazuje syntaxi požadované pro připojení k Northwind.mdb umístěný ve složce app_data. Systémové databáze (System.mdw) je také uloženo v tomto umístění.  
  
```  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
>  Určení umístění systémové databáze v připojovacím řetězci není vyžaduje, pokud databáze přístup/Jet není zabezpečená. Zabezpečení je vypnuté ve výchozím nastavení, s všichni uživatelé připojení jako integrované správce s prázdným heslem. I když zabezpečení na úrovni uživatele je implementovaná správně, zůstane Jet databáze bude zranitelný vůči útoku. Proto ukládání citlivých informací v databázi přístup/Jet se nedoporučuje kvůli vyplývajících slabinu systému jeho zabezpečení na základě souborů.  
  
### <a name="connecting-to-excel"></a>Připojení k aplikaci Excel  
 Zprostředkovatel Microsoft Jet se používá pro připojení k sešitu aplikace Excel. V následující připojovací řetězec `Extended Properties` – klíčové slovo nastaví vlastnosti, které jsou specifické pro aplikaci Excel. "Záhlaví = Yes;" znamená, že první řádek obsahuje názvy sloupců, ne data a "IMEX = 1;" ovladač vyzván k vždycky přečíst "míchán" datových sloupců jako text.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 Všimněte si, že znak dvojitých uvozovek požadované pro `Extended Properties` také musí být uzavřena v uvozovkách.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Syntaxi datový tvar zprostředkovatele připojovacího řetězce  
 Použití `Provider` a `Data Provider` klíčová slova při použití zprostředkovatele Microsoft datový tvar. Následující příklad používá zprostředkovatele tvar pro připojení k místní instanci systému SQL Server.  
  
```  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a>Připojovací řetězce rozhraní ODBC  
 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> Vlastnost <xref:System.Data.Odbc.OdbcConnection> umožňuje získat nebo nastavit připojovací řetězec pro zdroj dat OLE DB. ODBC připojovací řetězce jsou také podporovány pomocí <xref:System.Data.Odbc.OdbcConnectionStringBuilder>.  
  
 Následující připojovací řetězec používá ovladač pro Text.  
  
```  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Pomocí DataDirectory se připojit k Visual FoxPro  
 Následující <xref:System.Data.Odbc.OdbcConnection> připojovací řetězec příklad znázorňuje pomocí `DataDirectory` pro připojení k Microsoft Visual FoxPro souboru.  
  
```  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Oracle připojovací řetězce  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> Vlastnost <xref:System.Data.OracleClient.OracleConnection> umožňuje získat nebo nastavit připojovací řetězec pro zdroj dat OLE DB. Oracle připojovací řetězce jsou také podporovány pomocí <xref:System.Data.OracleClient.OracleConnectionStringBuilder> .  
  
```  
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 Další informace o syntaxi připojovacího řetězce ODBC najdete v tématu <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Připojovací řetězce](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
