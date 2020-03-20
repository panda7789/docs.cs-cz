---
title: Syntaxe připojovacího řetězce
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 3df97419391fe17ef77a3b8f24c4f0689a04602f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151647"
---
# <a name="connection-string-syntax"></a>Syntaxe připojovacího řetězce
Každý zprostředkovatel dat rozhraní `Connection` .NET Framework <xref:System.Data.Common.DbConnection> má objekt, který <xref:System.Data.Common.DbConnection.ConnectionString%2A> dědí z, stejně jako vlastnost specifická pro zprostředkovatele. Konkrétní syntaxe připojovacího řetězce `ConnectionString` pro každého zprostředkovatele je popsána v jeho vlastnosti. V následující tabulce jsou uvedeny čtyři zprostředkovatelé dat, které jsou zahrnuty v rozhraní .NET Framework.  
  
|Zprostředkovatel dat rozhraní .NET Framework|Popis|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Poskytuje přístup k datům pro server Microsoft SQL Server. Další informace o syntaxi <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>připojovacího řetězce naleznete v tématu .|  
|<xref:System.Data.OleDb>|Poskytuje přístup k datům pro zdroje dat vystavené pomocí technologie OLE DB. Další informace o syntaxi <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>připojovacího řetězce naleznete v tématu .|  
|<xref:System.Data.Odbc>|Poskytuje přístup k datům pro zdroje dat vystavené pomocí rozhraní ODBC. Další informace o syntaxi <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>připojovacího řetězce naleznete v tématu .|  
|<xref:System.Data.OracleClient>|Poskytuje přístup k datům pro verzi Oracle verze 8.1.7 nebo novější. Další informace o syntaxi <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>připojovacího řetězce naleznete v tématu .|  
  
## <a name="connection-string-builders"></a>Tvůrci připojovacích řetězců  
 ADO.NET 2.0 zavedla následující tvůrce připojovacího řetězce pro poskytovatele dat rozhraní .NET Framework.  
  
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
- <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
- <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
- <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Tvůrce připojovacího řetězce umožňují vytvářet syntakticky platné připojovací řetězce za běhu, takže není nutné ručně zřetězit hodnoty připojovacího řetězce v kódu. Další informace naleznete v [tématu Connection String Builders](connection-string-builders.md).  

## <a name="windows-authentication"></a>Ověřování systému Windows  
 Doporučujeme používat ověřování systému Windows (někdy označované jako *integrované zabezpečení)* pro připojení ke zdrojům dat, které jej podporují. Syntaxe použitá v připojovacím řetězci se liší podle zprostředkovatele. V následující tabulce je uvedena syntaxe ověřování systému Windows použitá s poskytovateli dat rozhraní .NET Framework.  
  
|Poskytovatel|Syntaxe|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
> `Integrated Security=true`vyvolá výjimku při použití `OleDb` s poskytovatelem.  
  
## <a name="sqlclient-connection-strings"></a>Připojovací řetězce sqlclient  
Syntaxe připojovacího <xref:System.Data.SqlClient.SqlConnection> řetězce <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> je popsána ve vlastnosti. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Vlastnost můžete použít k získání nebo nastavení připojovacího řetězce pro databázi serveru SQL Server. Pokud se potřebujete připojit k dřívější verzi serveru SQL Server, musíte použít zprostředkovatele dat rozhraní .NET Framework pro OleDb (<xref:System.Data.OleDb>). Většina klíčových slov připojovacího řetězce také mapuje na vlastnosti v rozhraní <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  

> [!IMPORTANT]
> Výchozí nastavení klíčového `Persist Security Info` `false`slova je . Nastavení `true` nebo `yes` umožňuje informace citlivé na zabezpečení, včetně ID uživatele a hesla, získat z připojení po otevření připojení. Chcete-li `false` zajistit, aby nedůvěryhodný zdroj neměl přístup k citlivým informacím o připojovacím řetězci, nastavte `Persist Security Info` ji.  

### <a name="windows-authentication-with-sqlclient"></a>Ověřování systému Windows pomocí služby SqlClient
 Každá z následujících forem syntaxe používá ověřování systému Windows pro připojení k databázi **AdventureWorks** na místním serveru.  
  
```csharp  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>Ověřování serveru SQL Server pomocí služby SQLClient
 Ověřování systému Windows je upřednostňováno pro připojení k serveru SQL Server. Pokud je však vyžadováno ověřování serveru SQL Server, zadejte uživatelské jméno a heslo pomocí následující syntaxe. V tomto příkladu hvězdičky představují platné uživatelské jméno a heslo.  
  
```csharp  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

Když se připojíte k Azure SQL Database nebo K Azure `user@servername`SQL Data `servername` Warehouse a zadáte přihlášení ve `Server=`formátu , ujistěte se, že hodnota v přihlášení odpovídá hodnotě stanovené pro .

> [!NOTE]
> Ověřování systému Windows má přednost před přihlášením serveru SQL Server. Pokud zadáte integrované zabezpečení = true, stejně jako uživatelské jméno a heslo, uživatelské jméno a heslo budou ignorovány a bude použito ověřování systému Windows.  

### <a name="connect-to-a-named-instance-of-sql-server"></a>Připojení k pojmenované instanci serveru SQL Server
Chcete-li se připojit k pojmenované instanci serveru SQL Server, použijte syntaxi *názvu_serveru\název instance.*  
  
```csharp  
"Data Source=MySqlServer\MSSQL1;"  
```  

Můžete také nastavit <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> vlastnost `SqlConnectionStringBuilder` název instance při vytváření připojovacího řetězce. Vlastnost <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> objektu <xref:System.Data.SqlClient.SqlConnection> je jen pro čtení.  
  
### <a name="type-system-version-changes"></a>Změny verze systému typu  
 Klíčové `Type System Version` slovo <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> v a určuje reprezentaci typů serveru SQL Server na straně klienta. Další <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> informace o `Type System Version` klíčovém slově naleznete v tématu.  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>Připojení a připojení k uživatelským instancím SQL Server Express  
 Uživatelské instance jsou funkcí v sql server express. Umožňují uživateli s nejméně privilegovaným místním účtem systému Windows připojit a spustit databázi serveru SQL Server bez nutnosti oprávnění správce. Instance uživatele se spustí s pověřeními uživatele systému Windows, nikoli jako služba.  
  
 Další informace o práci s instancemi uživatelů naleznete v tématu [SQL Server Express User Instances](./sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>Použití certifikátu TrustServerCertificate  
 Klíčové `TrustServerCertificate` slovo je platné pouze při připojování k instanci serveru SQL Server s platným certifikátem. Pokud `TrustServerCertificate` je `true`nastavena na , bude transportní vrstva používat SSL k šifrování kanálu a obejít chůzi řetězce certifikátů k ověření důvěryhodnosti.  
  
```csharp  
"TrustServerCertificate=true;"
```  
  
> [!NOTE]
> Pokud `TrustServerCertificate` je `true` nastavena na a šifrování je zapnuto, úroveň šifrování `Encrypt` zadaná na serveru bude použita i v případě, že je nastavena na `false` v připojovacím řetězci. Připojení se jinak nezdaří.  
  
### <a name="enabling-encryption"></a>Povolení šifrování  
 Chcete-li povolit šifrování v případě, že certifikát nebyl na serveru zřízen, musí být v nástroji SQL Server Configuration Manager nastaveny možnosti **Force Protocol Encryption** a Certificate serveru **Trust.** V takovém případě bude šifrování používat certifikát serveru podepsaný svým držitelem bez ověření, pokud na serveru nebyl zřízen žádný ověřitelný certifikát.  
  
 Nastavení aplikace nemůže snížit úroveň zabezpečení nakonfigurované ho sql server, ale může volitelně posílit. Aplikace může požádat o `TrustServerCertificate` `Encrypt` šifrování nastavením a klíčová slova na `true`, zaručující, že šifrování probíhá i v případě, že certifikát serveru nebyl zřízen a šifrování force **protocol** nebylo nakonfigurováno pro klienta. Pokud `TrustServerCertificate` však není v konfiguraci klienta povolena, je stále vyžadován zřízený certifikát serveru.  
  
 Následující tabulka popisuje všechny případy.  
  
|Nastavení klienta force protocol encryption|Nastavení klienta certifikátu důvěryhodného serveru|Šifrovat/používat šifrování pro datový připojovací řetězec/atribut|Připojovací řetězec/atribut certifikátu důvěryhodného serveru|Výsledek|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|Ne|Není dostupné.|Ne (výchozí)|Ignorováno|Nedojde k žádnému šifrování.|  
|Ne|Není dostupné.|Ano|Ne (výchozí)|K šifrování dochází pouze v případě, že existuje ověřitelný certifikát serveru, jinak se pokus o připojení nezdaří.|  
|Ne|Není dostupné.|Ano|Ano|Šifrování vždy dochází, ale může použít certifikát serveru podepsaný svým držitelem.|  
|Ano|Ne|Ignorováno|Ignorováno|K šifrování dochází pouze v případě, že existuje ověřitelný serverový certifikát. v opačném případě se pokus o připojení nezdaří.|  
|Ano|Ano|Ne (výchozí)|Ignorováno|Šifrování vždy dochází, ale může použít certifikát serveru podepsaný svým držitelem.|  
|Ano|Ano|Ano|Ne (výchozí)|K šifrování dochází pouze v případě, že existuje ověřitelný serverový certifikát. v opačném případě se pokus o připojení nezdaří.|  
|Ano|Ano|Ano|Ano|Šifrování vždy dochází, ale může použít certifikát serveru podepsaný svým držitelem.|  
  
 Další informace naleznete [v tématu Použití šifrování bez ověření](/sql/relational-databases/native-client/features/using-encryption-without-validation).
  
## <a name="oledb-connection-strings"></a>Připojovací řetězce OleDb  
 Vlastnost <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> <xref:System.Data.OleDb.OleDbConnection> umožňuje získat nebo nastavit připojovací řetězec pro zdroj dat TECHNOLOGIE OLE DB, například aplikaci Microsoft Access. Můžete také vytvořit `OleDb` připojovací řetězec <xref:System.Data.OleDb.OleDbConnectionStringBuilder> za běhu pomocí třídy.  
  
### <a name="oledb-connection-string-syntax"></a>Syntaxe připojovacího řetězce OleDb  
 Je nutné zadat název <xref:System.Data.OleDb.OleDbConnection> zprostředkovatele pro připojovací řetězec. Následující připojovací řetězec se připojuje k databázi aplikace Microsoft Access pomocí zprostředkovatele Jet. Všimněte `User ID` si, že a `Password` klíčová slova jsou volitelné, pokud databáze není zabezpečená (výchozí).  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;
```  
  
 Pokud je databáze Jet zabezpečena pomocí zabezpečení na úrovni uživatele, je nutné zadat umístění informačního souboru pracovní skupiny (.mdw). Informační soubor pracovní skupiny se používá k ověření pověření uvedených v připojovacím řetězci.  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
> Je možné zadat informace o připojení pro **OleDbConnection** v souboru Univerzální datové spojení (UDL). nicméně byste se měli vyhnout tomu. UDL soubory nejsou šifrovány a vystavit informace o připojovacím řetězci ve prostém textu. Vzhledem k tomu, že soubor UDL je externí prostředek založený na souboru pro vaši aplikaci, nelze jej zabezpečit pomocí rozhraní .NET Framework. Soubory UDL nejsou podporovány pro **sqlclient**.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>Připojení k přístupu/jetu pomocí služby DataDirectory  
 `DataDirectory`není výlučně `SqlClient`. Lze jej také použít <xref:System.Data.OleDb> <xref:System.Data.Odbc> s poskytovateli dat a .NET. Následující ukázkový <xref:System.Data.OleDb.OleDbConnection> řetězec ukazuje syntaxi potřebnou pro připojení k souboru Northwind.mdb umístěného ve složce app_data aplikace. Systémová databáze (System.mdw) je také uložena v tomto umístění.  
  
```csharp  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
> Určení umístění systémové databáze v připojovacím řetězci není vyžadováno, pokud databáze Access/Jet není zabezpečená. Zabezpečení je ve výchozím nastavení vypnuto a všichni uživatelé se připojují jako vestavěný uživatel správce s prázdným heslem. I v případě, že je správně implementováno zabezpečení na úrovni uživatele, databáze Jet zůstává zranitelná vůči útoku. Proto ukládání citlivých informací v databázi Access/Jet se nedoporučuje z důvodu vlastní slabiny jeho schéma zabezpečení založené na souborech.  
  
### <a name="connecting-to-excel"></a>Připojení k Excelu  
 Zprostředkovatel Microsoft Jet se používá k připojení k sešitu aplikace Excel. V následujícím připojovacím řetězci `Extended Properties` klíčové slovo nastaví vlastnosti, které jsou specifické pro aplikaci Excel. "HDR=Ano;" označuje, že první řádek obsahuje názvy sloupců, nikoli data, a "IMEX=1;" říká řidiči, aby vždy četl "smíšené" datové sloupce jako text.  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 Všimněte si, že znak `Extended Properties` dvojité nabídky požadovaný pro musí být také uzavřen v uvozovkách.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Syntaxe připojovacího řetězce zprostředkovatele datového obrazce  
 Při použití `Provider` zprostředkovatele obrazce Microsoft Data Shape použijte `Data Provider` klíčová slova i klíčová slova. Následující příklad používá zprostředkovatele shape pro připojení k místní instanci serveru SQL Server.  
  
```csharp  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"
```  
  
## <a name="odbc-connection-strings"></a>Připojovací řetězce Odbc  
 Vlastnost <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> <xref:System.Data.Odbc.OdbcConnection> umožňuje získat nebo nastavit připojovací řetězec pro zdroj dat TECHNOLOGIE OLE DB. Připojovací řetězce Odbc <xref:System.Data.Odbc.OdbcConnectionStringBuilder>jsou také podporovány rozhraním .  
  
 Následující připojovací řetězec používá textový ovladač společnosti Microsoft.  
  
```csharp  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Připojení k aplikaci Visual FoxPro pomocí služby DataDirectory  
 Následující <xref:System.Data.Odbc.OdbcConnection> ukázka připojovacího řetězce ukazuje použití `DataDirectory` připojení k souboru Microsoft Visual FoxPro.  
  
```csharp  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Připojovací řetězce Oracle  
 Vlastnost <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> <xref:System.Data.OracleClient.OracleConnection> umožňuje získat nebo nastavit připojovací řetězec pro zdroj dat TECHNOLOGIE OLE DB. Připojovací řetězce Oracle <xref:System.Data.OracleClient.OracleConnectionStringBuilder> jsou také podporovány .  
  
```csharp
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 Další informace o syntaxi připojovacího řetězce ROZHRANÍ ODBC naleznete v tématu <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.  
  
## <a name="see-also"></a>Viz také

- [Připojovací řetězce](connection-strings.md)
- [Připojení ke zdroji dat](connecting-to-a-data-source.md)
- [Přehled ADO.NET](ado-net-overview.md)
