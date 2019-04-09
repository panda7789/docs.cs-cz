---
title: Syntaxe připojovacího řetězce
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 4c5ed5000f075fb637915dc40e122a9337176e36
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084952"
---
# <a name="connection-string-syntax"></a>Syntaxe připojovacího řetězce
Každý poskytovatel dat rozhraní .NET Framework má `Connection` objekt, který dědí z <xref:System.Data.Common.DbConnection> a také konkrétního zprostředkovatele <xref:System.Data.Common.DbConnection.ConnectionString%2A> vlastnost. Syntaxe specifické připojovacího řetězce pro každého zprostředkovatele je popsána v jeho `ConnectionString` vlastnost. V následující tabulce jsou uvedeny zprostředkovatelé čtyři dat, které jsou zahrnuty v rozhraní .NET Framework.  
  
|Zprostředkovatel dat .NET framework|Popis|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Poskytuje přístup k datům pro Microsoft SQL Server. Další informace o syntaxe připojovacího řetězce, naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.|  
|<xref:System.Data.OleDb>|Poskytuje přístup k datům pro zdroje dat přístupné přes OLE DB. Další informace o syntaxe připojovacího řetězce, naleznete v tématu <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.|  
|<xref:System.Data.Odbc>|Poskytuje přístup k datům pro zdroje dat přístupné přes rozhraní ODBC. Další informace o syntaxe připojovacího řetězce, naleznete v tématu <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.|  
|<xref:System.Data.OracleClient>|Poskytuje přístup k datům pro Oracle version 8.1.7 nebo vyšší. Další informace o syntaxe připojovacího řetězce, naleznete v tématu <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.|  
  
## <a name="connection-string-builders"></a>Tvůrci připojovacích řetězců  
 ADO.NET 2.0 zavedeny následující tvůrci připojovacích řetězců pro zprostředkovatele dat .NET Framework.  
  
-   <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
-   <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
-   <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
-   <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Tvůrci připojovacích řetězců umožňuje vytvářet syntakticky správný připojovací řetězce v době běhu, takže není potřeba ručně zřetězit hodnoty připojovacího řetězce v kódu. Další informace najdete v tématu [tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md).  

## <a name="windows-authentication"></a>Ověřování systému Windows  
 Doporučujeme používat ověřování Windows (někdy označovány jako *integrované zabezpečení*) pro připojení ke zdrojům dat, které ho podporují. Syntaxe použijí v připojovacím řetězci se liší od poskytovatele. Následující tabulka ukazuje syntaxi ověřování Windows pomocí zprostředkovatele dat .NET Framework.  
  
|Poskytovatel|Syntaxe|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
>  `Integrated Security=true` vyvolá výjimku při použití s `OleDb` zprostředkovatele.  
  
## <a name="sqlclient-connection-strings"></a>SqlClient připojovacích řetězců  
Syntaxe <xref:System.Data.SqlClient.SqlConnection> připojovací řetězec je popsána v <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> vlastnost. Můžete použít <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> vlastnost k získání nebo nastavení připojovacího řetězce pro databázi serveru SQL Server. Pokud budete muset připojit ke starší verzi systému SQL Server, musíte použít zprostředkovatele dat .NET Framework pro OleDb (<xref:System.Data.OleDb>). Většinu klíčových slov připojovací řetězec k vlastnostem v také namapovat <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  

> [!IMPORTANT]
>  Ve výchozím nastavení `Persist Security Info` – klíčové slovo je `false`. Nastavení na `true` nebo `yes` umožňuje zabezpečené informace, včetně ID uživatele a heslo, chcete-li získat z připojení po otevření připojení. Zachovat `Persist Security Info` nastavena na `false` zajistit, že nedůvěryhodného zdroje nemá přístup k citlivým připojovacího řetězce.  

### <a name="windows-authentication-with-sqlclient"></a>Ověřování Windows pomocí SqlClient 
 Každá z těchto forem syntaxi používá ověřování Windows pro připojení k **AdventureWorks** databáze na místním serveru.  
  
```  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>Ověřování SQL serveru s SqlClient   
 Ověřování Windows je upřednostňována pro připojení k serveru SQL Server. Nicméně pokud je požadováno ověřování serveru SQL, použijte následující syntaxi k zadání uživatelského jména a hesla. V tomto příkladu jsou hvězdičky z obou stran používá k reprezentování platné uživatelské jméno a heslo.  
  
```  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

Při připojení ke službě Azure SQL Database nebo Azure SQL Data Warehouse a zadejte přihlašovací údaje ve formátu `user@servername`, ujistěte se, že `servername` v přihlášení odpovídá hodnotě zadané pro `Server=`.

> [!NOTE]
>  Ověřování Windows má přednost před přihlášení serveru SQL Server. Pokud zadáte obě Integrated Security = true i uživatelské jméno a heslo, bude ignorovat uživatelské jméno a heslo a použije ověřování Windows.  

### <a name="connect-to-a-named-instance-of-sql-server"></a>Připojení k pojmenované instanci systému SQL Server
Pro připojení k pojmenované instanci systému SQL Server, použijte *název počítače\název instance serveru* syntaxe.  
  
```  
Data Source=MySqlServer\MSSQL1;"  
```  
 
Můžete také nastavit <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> vlastnost `SqlConnectionStringBuilder` k názvu instance při sestavování připojovací řetězec. <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> Vlastnost <xref:System.Data.SqlClient.SqlConnection> objekt je jen pro čtení.  
  
### <a name="type-system-version-changes"></a>Typ změny verze systému  
 `Type System Version` – Klíčové slovo v <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> určuje reprezentace typů systému SQL Server na straně klienta. Zobrazit <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> Další informace o `Type System Version` – klíčové slovo.  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>Připojení a připojení k serveru SQL Server Express uživatelské instance  
 Uživatelské instance jsou funkce v systému SQL Server Express. Povolit uživatele běžící na nejnižší úrovní oprávnění místní účet Windows pro připojení a spuštění databáze SQL serveru bez nutnosti oprávnění správce. Uživatelskou instanci provádí pomocí přihlašovacích údajů Windows uživatele, ne jako službu.  
  
 Další informace o práci s uživatelské instance, naleznete v tématu [instance SQL serveru Express uživatele](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>Pomocí TrustServerCertificate  
 `TrustServerCertificate` – Klíčové slovo je platná pouze v případě, že připojení k instanci systému SQL Server pomocí platného certifikátu. Když `TrustServerCertificate` je nastavena na `true`, přenosové vrstvy budou používat protokol SSL pro šifrování kanálu a obejít walking řetěz certifikátů pro ověření vztahu důvěryhodnosti.  
  
```  
"TrustServerCertificate=true;"   
```  
  
> [!NOTE]
>  Pokud `TrustServerCertificate` je nastavena na `true` a šifrování je zapnuté, úrovně šifrování zadaných na serveru se použijí i v případě `Encrypt` je nastavena na `false` v připojovacím řetězci. Připojení v opačném případě se nezdaří.  
  
### <a name="enabling-encryption"></a>Povolení šifrování  
 Povolit šifrování certifikát nebyla zřízena na serveru, **vynucení šifrování protokolu** a **důvěřovat certifikátu serveru** možnosti musí být nastavena v SQL Server Configuration Manager. V takovém případě šifrování použije certifikát podepsaný svým držitelem serveru bez ověřování, pokud žádný ověřit certifikát zřízení na serveru.  
  
 Nastavení aplikace nelze snížit úroveň zabezpečení, které jsou nakonfigurované v systému SQL Server, ale můžete volitelně lépe. Může aplikace vyžadovat šifrování tak, že nastavíte `TrustServerCertificate` a `Encrypt` klíčových slov pro `true`, zajištění, že šifrování probíhá i v případě, že se nezřídil certifikát serveru a **vynucení šifrování protokolu**  nebyl nakonfigurován pro klienta. Nicméně pokud `TrustServerCertificate` není povolená v konfiguraci klienta, je nutné použít certifikát zřízené serveru.  
  
 Následující tabulka popisuje všechny případy.  
  
|Vynutit šifrování protokolem nastavení klienta|Důvěřovat certifikátu serveru nastavení klienta|Šifrování a použití šifrování pro atribut řetězce připojení dat|Důvěřovat certifikátu serveru atribut připojovacího řetězce /|Výsledek|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|Ne|Není k dispozici|Ne (výchozí)|Ignorováno|Nastane, bez šifrování.|  
|Ne|Není k dispozici|Ano|Ne (výchozí)|Šifrování dojde pouze v případě, že se ověřit certifikát serveru, jinak se nezdaří pokus o připojení.|  
|Ne|Není k dispozici|Ano|Ano|Šifrování vždy vyvolá se, ale může používat certifikát podepsaný svým držitelem serveru.|  
|Ano|Ne|Ignorováno|Ignorováno|Šifrování dojde pouze v případě, že je certifikát ověřit server; v opačném případě se nezdaří pokus o připojení.|  
|Ano|Ano|Ne (výchozí)|Ignorováno|Šifrování vždy vyvolá se, ale může používat certifikát podepsaný svým držitelem serveru.|  
|Ano|Ano|Ano|Ne (výchozí)|Šifrování dojde pouze v případě, že je certifikát ověřit server; v opačném případě se nezdaří pokus o připojení.|  
|Ano|Ano|Ano|Ano|Šifrování vždy vyvolá se, ale může používat certifikát podepsaný svým držitelem serveru.|  
  
 Další informace najdete v tématu [pomocí šifrování bez ověření](/sql/relational-databases/native-client/features/using-encryption-without-validation).
  
## <a name="oledb-connection-strings"></a>Řetězce připojení OleDb  
 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> Vlastnost <xref:System.Data.OleDb.OleDbConnection> umožňuje získat nebo nastavit připojovací řetězec pro zdroj dat OLE DB, jako je například aplikace Microsoft Access. Můžete taky vytvořit `OleDb` připojovací řetězec za běhu pomocí <xref:System.Data.OleDb.OleDbConnectionStringBuilder> třídy.  
  
### <a name="oledb-connection-string-syntax"></a>Syntaxe připojovacího řetězce OleDb  
 Musíte zadat název zprostředkovatele pro <xref:System.Data.OleDb.OleDbConnection> připojovací řetězec. Následující připojovací řetězec připojení k databázi aplikace Microsoft Access pomocí zprostředkovatele Jet. Všimněte si, `User ID` a `Password` klíčová slova jsou volitelné při připojení k databázi je nezabezpečené (výchozí).  
  
```   
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;   
```  
  
 Pokud databáze Jet je zabezpečený pomocí zabezpečení na úrovni uživatele, musíte zadat umístění informační soubor pracovní skupiny (MDW). Informační soubor pracovní skupiny slouží k ověření přihlašovací údaje v připojovacím řetězci.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
>  Je možné zadat informace o připojení **OleDbConnection –** v souboru univerzální datové propojení (UDL); ale měli byste se vyhnout tím. Soubory UDL nejsou šifrované a zveřejnit informace o připojovacím řetězci ve formátu prostého textu. Vzhledem k tomu, že je soubor UDL externí souborových prostředků do vaší aplikace, nemůže být zabezpečená, pomocí rozhraní .NET Framework. Soubory UDL nejsou podporovány pro **SqlClient**.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>Použití DataDirectory pro připojení k přístupu nebo Jet  
 `DataDirectory` není výhradně pro `SqlClient`. Můžete použít také s <xref:System.Data.OleDb> a <xref:System.Data.Odbc> zprostředkovatele dat .NET. Následující ukázka <xref:System.Data.OleDb.OleDbConnection> řetězec znázorňuje syntaxe požadované pro připojení k Northwind.mdb umístěný ve složce app_data aplikace. Systémovou databázi (System.mdw) je také uložena v dané oblasti.  
  
```  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
>  Určení umístění systémové databáze v připojovacím řetězci není vyžadován, pokud databáze aplikace Access/Jet není zabezpečená. Zabezpečení je vypnuto ve výchozím nastavení, se všemi uživateli připojení podle uživatele s rolí správce integrované s prázdným heslem. I v případě, že je správně implementované zabezpečení na úrovni uživatele, zůstávají snadno napadnutelný databáze Jet. Proto ukládání citlivých informací v databázi aplikace Access/Jet se nedoporučuje kvůli inherentní slabinu její schéma zabezpečení na základě souboru.  
  
### <a name="connecting-to-excel"></a>Připojení k Excelu  
 Zprostředkovatel Microsoft Jet slouží k připojení k Excelovému sešitu. V následující připojovací řetězec `Extended Properties` – klíčové slovo nastaví vlastnosti, které jsou specifické pro aplikaci Excel. "HDR = Ano." znamená, že první řádek obsahuje názvy sloupců, nikoli data, a "IMEX = 1," říká ovladač vždy číst "míchán" datových sloupců jako text.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 Všimněte si, že znak dvojité uvozovky vyžadované pro `Extended Properties` také musí být uzavřen do dvojitých uvozovek.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Syntaxe připojovacího řetězce datového tvaru poskytovatele  
 Použít `Provider` a `Data Provider` klíčová slova při použití zprostředkovatele Microsoft Data obrazce. Následující příklad používá zprostředkovatele tvar pro připojení k místní instanci systému SQL Server.  
  
```  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a>Připojovací řetězce ODBC  
 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> Vlastnost <xref:System.Data.Odbc.OdbcConnection> umožňuje získat nebo nastavit připojovací řetězec pro zdroj dat OLE DB. Řetězce připojení rozhraní ODBC jsou také podporovány <xref:System.Data.Odbc.OdbcConnectionStringBuilder>.  
  
 Následující připojovací řetězec používá ovladač Microsoft Text.  
  
```  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Použití DataDirectory pro připojení k Visual FoxPro  
 Následující <xref:System.Data.Odbc.OdbcConnection> ukázka připojovací řetězec znázorňuje použití `DataDirectory` pro připojení k Microsoft Visual FoxPro souboru.  
  
```  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Oracle připojovacích řetězců  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> Vlastnost <xref:System.Data.OracleClient.OracleConnection> umožňuje získat nebo nastavit připojovací řetězec pro zdroj dat OLE DB. Oracle připojovací řetězce jsou podporovány také <xref:System.Data.OracleClient.OracleConnectionStringBuilder> .  
  
```  
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 Další informace o rozhraní ODBC syntaxe připojovacího řetězce, naleznete v tématu <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Připojovací řetězce](../../../../docs/framework/data/adonet/connection-strings.md)
- [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
