---
title: Syntaxe připojovacího řetězce
description: Seznamte se s syntaxí připojovacích řetězců v ADO.NET. Syntaxe pro každého poskytovatele je dokumentována ve vlastnosti ConnectionString.
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: bb29365a4729e731ddeffc7cfa61e379c3144a46
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287048"
---
# <a name="connection-string-syntax"></a>Syntaxe připojovacího řetězce
Každý zprostředkovatel dat .NET Framework má `Connection` objekt, který dědí z, <xref:System.Data.Common.DbConnection> a také vlastnost specifickou pro poskytovatele <xref:System.Data.Common.DbConnection.ConnectionString%2A> . Konkrétní syntaxi připojovacího řetězce pro každého poskytovatele je popsána v jeho `ConnectionString` Vlastnosti. V následující tabulce jsou uvedeny čtyři poskytovatelé dat, kteří jsou součástí .NET Framework.  
  
|Poskytovatel dat .NET Framework|Popis|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Poskytuje přístup k datům pro Microsoft SQL Server. Další informace o syntaxi připojovacího řetězce naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> .|  
|<xref:System.Data.OleDb>|Poskytuje přístup k datům pro zdroje dat, které jsou vystaveny pomocí OLE DB. Další informace o syntaxi připojovacího řetězce naleznete v tématu <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> .|  
|<xref:System.Data.Odbc>|Poskytuje přístup k datům pro zdroje dat, které jsou vystaveny pomocí rozhraní ODBC. Další informace o syntaxi připojovacího řetězce naleznete v tématu <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> .|  
|<xref:System.Data.OracleClient>|Poskytuje přístup k datům pro Oracle verze 8.1.7 nebo novější. Další informace o syntaxi připojovacího řetězce naleznete v tématu <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> .|  
  
## <a name="connection-string-builders"></a>Tvůrci připojovacích řetězců  
 ADO.NET 2,0 představil následující tvůrci připojovacích řetězců pro poskytovatele .NET Framework dat.  
  
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
- <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
- <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
- <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Tvůrci připojovacích řetězců umožňují vytvořit syntakticky platné připojovací řetězce za běhu, takže není nutné ručně zřetězit hodnoty připojovacího řetězce v kódu. Další informace najdete v tématu [tvůrci připojovacích řetězců](connection-string-builders.md).  

## <a name="windows-authentication"></a>Ověřování systému Windows  
 Pro připojení ke zdrojům dat, které ji podporují, doporučujeme použít ověřování systému Windows (někdy označované jako *integrované zabezpečení*). Syntaxe, která je zaměstnána v připojovacím řetězci, se liší podle poskytovatele. V následující tabulce jsou uvedeny syntaxe ověřování systému Windows používané s poskytovateli dat .NET Framework.  
  
|Poskytovatel|Syntaxe|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
> `Integrated Security=true`vyvolá výjimku při použití se `OleDb` zprostředkovatelem.  
  
## <a name="sqlclient-connection-strings"></a>Připojovací řetězce SqlClient  
Syntaxe <xref:System.Data.SqlClient.SqlConnection> připojovacího řetězce je dokumentována ve <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> Vlastnosti. Vlastnost můžete použít <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> k získání nebo nastavení připojovacího řetězce pro databázi SQL Server. Pokud se potřebujete připojit k dřívější verzi SQL Server, je nutné použít Zprostředkovatel dat .NET Framework pro OleDb ( <xref:System.Data.OleDb> ). Většina klíčových slov řetězce připojení se také mapuje na vlastnosti v <xref:System.Data.SqlClient.SqlConnectionStringBuilder> .  

> [!IMPORTANT]
> Výchozí nastavení pro `Persist Security Info` klíčové slovo je `false` . Nastavení `true` nebo `yes` umožňuje získat informace citlivé na zabezpečení, včetně ID a hesla uživatele, aby bylo možné získat připojení po otevření připojení. `Persist Security Info`Nastavte na `false` , aby se zajistilo, že nedůvěryhodný zdroj nemá přístup k informacím citlivého připojovacího řetězce.  

### <a name="windows-authentication-with-sqlclient"></a>Ověřování systému Windows s použitím SqlClient
 Každá z následujících forem syntaxe používá ověřování systému Windows pro připojení k databázi **AdventureWorks** na místním serveru.  
  
```csharp  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>Ověřování SQL Server s použitím SqlClient
 Pro připojení k SQL Server se upřednostňuje ověřování systému Windows. Pokud se ale vyžaduje ověření SQL Server, použijte k zadání uživatelského jména a hesla následující syntaxi. V tomto příkladu se hvězdičky používají k vyjádření platného uživatelského jména a hesla.  
  
```csharp  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

Když se připojíte k Azure SQL Database nebo Azure SQL Data Warehouse a zadáte přihlašovací údaje ve formátu `user@servername` , ujistěte se, že `servername` hodnota v přihlašovacích údajích odpovídá hodnotě zadané pro `Server=` .

> [!NOTE]
> Ověřování systému Windows má před SQL Server přihlášení přednost. Pokud zadáte obě integrované zabezpečení = true i uživatelské jméno a heslo, bude se ignorovat uživatelské jméno a heslo a použije se ověřování systému Windows.  

### <a name="connect-to-a-named-instance-of-sql-server"></a>Připojení k pojmenované instanci SQL Server
Pro připojení k pojmenované instanci SQL Server použijte syntaxi *název serveru \* .  
  
```csharp  
"Data Source=MySqlServer\MSSQL1;"  
```  

Můžete také nastavit <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> vlastnost `SqlConnectionStringBuilder` na název instance při sestavování připojovacího řetězce. <xref:System.Data.SqlClient.SqlConnection.DataSource%2A>Vlastnost <xref:System.Data.SqlClient.SqlConnection> objektu je určena jen pro čtení.  
  
### <a name="type-system-version-changes"></a>Změny typu systémové verze  
 `Type System Version`Klíčové slovo v typu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> určuje reprezentace SQL serverch typů na straně klienta. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>Další informace o `Type System Version` klíčovém slově naleznete v tématu.  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>Připojení a připojení k SQL Server Express uživatelské instance  
 Uživatelské instance jsou funkcí v SQL Server Express. Umožňují uživateli, který běží na místním účtu systému Windows s minimálními oprávněními pro připojení a spuštění databáze SQL Server bez nutnosti oprávnění správce. Uživatelská instance se spustí s přihlašovacími údaji uživatele Windows, ne jako službou.  
  
 Další informace o práci s uživatelskými instancemi najdete v tématu [SQL Server Express uživatelské instance](./sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>Použití TrustServerCertificate  
 `TrustServerCertificate`Klíčové slovo je platné pouze při připojení k instanci SQL Server s platným certifikátem. Pokud `TrustServerCertificate` je nastavená na `true` , transportní vrstva bude používat protokol SSL k šifrování kanálu a obejít procházení řetězu certifikátů za účelem ověření vztahu důvěryhodnosti.  
  
```csharp  
"TrustServerCertificate=true;"
```  
  
> [!NOTE]
> Pokud `TrustServerCertificate` je nastavená na `true` a je zapnuté šifrování, použije se úroveň šifrování zadaná na serveru i v případě, že `Encrypt` je `false` v připojovacím řetězci nastavená na. V opačném případě se připojení nezdaří.  
  
### <a name="enabling-encryption"></a>Povolení šifrování  
 Pokud chcete povolit šifrování, když se na serveru nezřídí certifikát, musí být v SQL Server Configuration Manager nastavená možnost **Vynutit šifrování protokolu** a **certifikát důvěryhodného serveru** . V takovém případě bude šifrování používat certifikát serveru podepsaný svým držitelem bez ověření, pokud se na serveru nezřídí žádný ověřitelný certifikát.  
  
 Nastavení aplikace nemůže snížit úroveň zabezpečení nakonfigurovanou v SQL Server, ale může ji případně posílit. Aplikace může vyžádat šifrování tím, že `TrustServerCertificate` nastaví `Encrypt` klíčová slova a, aby se `true` zajistilo, že šifrování proběhne i v případě, že nebyl zřízen certifikát serveru a nenakonfigurovalo se **šifrování protokolu** pro klienta. Pokud ale `TrustServerCertificate` v konfiguraci klienta není povolený, je certifikát zřízeného serveru stále povinný.  
  
 V následující tabulce jsou popsány všechny případy.  
  
|Vynutit nastavení klienta šifrování protokolu|Důvěřovat klientskému nastavení certifikátu serveru|Šifrovat/použít šifrování pro datový připojovací řetězec/atribut|Důvěřovat připojovacímu řetězci certifikátu serveru nebo atributu|Výsledek|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|No|–|Ne (výchozí)|Ignorováno|Nedochází k žádnému šifrování.|  
|No|–|Ano|Ne (výchozí)|K šifrování dochází pouze v případě, že existuje ověřitelný certifikát serveru, jinak pokus o připojení selže.|  
|No|–|Ano|Ano|K šifrování vždy dojde, ale může používat certifikát serveru podepsaný svým držitelem.|  
|Ano|Ne|Ignorováno|Ignorováno|K šifrování dochází pouze v případě, že existuje ověřitelný certifikát serveru. v opačném případě se pokus o připojení nezdaří.|  
|Ano|Ano|Ne (výchozí)|Ignorováno|K šifrování vždy dojde, ale může používat certifikát serveru podepsaný svým držitelem.|  
|Ano|Ano|Ano|Ne (výchozí)|K šifrování dochází pouze v případě, že existuje ověřitelný certifikát serveru. v opačném případě se pokus o připojení nezdaří.|  
|Ano|Ano|Ano|Ano|K šifrování vždy dojde, ale může používat certifikát serveru podepsaný svým držitelem.|  
  
 Další informace najdete v tématu [použití šifrování bez ověření](/sql/relational-databases/native-client/features/using-encryption-without-validation).
  
## <a name="oledb-connection-strings"></a>Připojovací řetězce OleDb  
 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>Vlastnost <xref:System.Data.OleDb.OleDbConnection> umožňuje získat nebo nastavit připojovací řetězec pro zdroj dat OLE DB, jako je například Microsoft Access. Připojovací řetězec můžete vytvořit také `OleDb` v době běhu pomocí <xref:System.Data.OleDb.OleDbConnectionStringBuilder> třídy.  
  
### <a name="oledb-connection-string-syntax"></a>Syntaxe připojovacího řetězce OleDb  
 Je nutné zadat název zprostředkovatele <xref:System.Data.OleDb.OleDbConnection> připojovacího řetězce. Následující připojovací řetězec se připojí k databázi aplikace Microsoft Access pomocí poskytovatele jet. Všimněte si, `User ID` že `Password` klíčová slova a jsou volitelná, pokud není databáze zabezpečená (výchozí).  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;
```  
  
 Pokud je databáze Jet zabezpečená pomocí zabezpečení na úrovni uživatele, musíte zadat umístění informačního souboru pracovní skupiny (. mdw). Informační soubor pracovní skupiny slouží k ověření přihlašovacích údajů prezentovaných v připojovacím řetězci.  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
> V souboru UDL (Universal Data Link) je možné zadávat informace o připojení pro **OleDbConnection** . měli byste se ale vyhnout. Soubory UDL nejsou zašifrované a zveřejňují informace připojovacího řetězce ve formátu prostého textu. Vzhledem k tomu, že soubor UDL je externí prostředek založený na souboru, nelze jej zabezpečit pomocí .NET Framework. Soubory UDL nejsou podporovány pro **SqlClient**.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>Použití DataDirectory pro připojení k přístupu/jet  
 `DataDirectory`není výhradně pro `SqlClient` . Můžete ji také použít s <xref:System.Data.OleDb> <xref:System.Data.Odbc> poskytovateli dat a .NET. Následující vzorový <xref:System.Data.OleDb.OleDbConnection> řetězec ukazuje syntaxi nutnou k připojení k souboru Northwind. mdb umístěnému ve složce App_Data aplikace. Systémová databáze (System. mdw) je také uložena v tomto umístění.  
  
```csharp  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
> Určení umístění systémové databáze v připojovacím řetězci není vyžadováno, pokud databáze Access/Jet není zabezpečená. Zabezpečení je ve výchozím nastavení vypnuté a všichni uživatelé se připojují jako předdefinovaný správce s prázdným heslem. I když je zabezpečení na úrovni uživatele správně implementované, zůstane databáze Jet zranitelná vůči útokům. Proto se nedoporučuje ukládání citlivých informací v databázi Accessu nebo databázi Jet na základní slabiny svého schématu zabezpečení založeného na souborech.  
  
### <a name="connecting-to-excel"></a>Připojení k Excelu  
 Zprostředkovatel Microsoft Jet slouží k připojení k sešitu aplikace Excel. V následujícím připojovacím řetězci `Extended Properties` Nastaví klíčové slovo vlastnosti, které jsou specifické pro aplikaci Excel. "HDR = Yes;" označuje, že první řádek obsahuje názvy sloupců, ne data a "IMEX = 1;" oznamuje ovladači, aby se jako text vždy četly sloupce s mezismíšenými daty.  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 Všimněte si, že znak dvojité uvozovky vyžadovaný pro `Extended Properties` musí být také uzavřen v uvozovkách.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Syntaxe připojovacího řetězce zprostředkovatele datových tvarů  
 `Provider` `Data Provider` Při použití poskytovatele datových tvarů společnosti Microsoft použijte klíčová slova a. Následující příklad používá poskytovatele tvaru pro připojení k místní instanci SQL Server.  
  
```csharp  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"
```  
  
## <a name="odbc-connection-strings"></a>Připojovací řetězce ODBC  
 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>Vlastnost <xref:System.Data.Odbc.OdbcConnection> umožňuje získat nebo nastavit připojovací řetězec pro zdroj dat OLE DB. Připojovací řetězce ODBC jsou podporovány také v <xref:System.Data.Odbc.OdbcConnectionStringBuilder> .  
  
 Následující připojovací řetězec používá ovladač pro text společnosti Microsoft.  
  
```csharp  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Použití DataDirectory pro připojení k Visual FoxPro  
 Následující <xref:System.Data.Odbc.OdbcConnection> Ukázka připojovacího řetězce ukazuje použití nástroje `DataDirectory` pro připojení k souboru Microsoft Visual FoxPro.  
  
```csharp  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Připojovací řetězce Oracle  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>Vlastnost <xref:System.Data.OracleClient.OracleConnection> umožňuje získat nebo nastavit připojovací řetězec pro zdroj dat OLE DB. Připojovací řetězce Oracle jsou podporovány také v <xref:System.Data.OracleClient.OracleConnectionStringBuilder> .  
  
```csharp
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 Další informace o syntaxi připojovacího řetězce ODBC naleznete v tématu <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> .  
  
## <a name="see-also"></a>Viz také

- [Připojovací řetězce](connection-strings.md)
- [Připojení ke zdroji dat](connecting-to-a-data-source.md)
- [Přehled ADO.NET](ado-net-overview.md)
