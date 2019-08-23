---
title: Navazování připojení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: b4a61306cd9b61f84eff16ffaac302317b6dfe44
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959181"
---
# <a name="establishing-the-connection"></a>Navazování připojení
Chcete-li se připojit k Microsoft SQL Server <xref:System.Data.SqlClient.SqlConnection> , použijte pro SQL Server objekt zprostředkovatel dat .NET Framework. Chcete-li se připojit k OLE DB zdroji dat, <xref:System.Data.OleDb.OleDbConnection> použijte pro OLE DB objekt zprostředkovatel dat .NET Framework. Chcete-li se připojit ke zdroji dat ODBC, <xref:System.Data.Odbc.OdbcConnection> použijte objekt zprostředkovatel dat .NET Framework pro rozhraní ODBC. Chcete-li se připojit ke zdroji dat Oracle, <xref:System.Data.OracleClient.OracleConnection> použijte objekt zprostředkovatel dat .NET Framework pro Oracle. Informace o bezpečném ukládání a načítání připojovacích řetězců najdete v tématu [ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Uzavírání připojení  
 Doporučujeme, abyste připojení vždy zavřeli, až ho budete používat, aby bylo možné připojení vrátit do fondu. Blok v Visual Basic nebo C# automaticky odstraní připojení, když kód ukončí blok, i v případě neošetřené výjimky. `Using` Další informace naleznete v tématu [using Statement](../../../csharp/language-reference/keywords/using-statement.md) a [using příkaz using](../../../visual-basic/language-reference/statements/using-statement.md) .  
  
 Můžete také použít `Close` metody nebo `Dispose` objektu Connection pro poskytovatele, kterého používáte. Nemusejí být do fondu přidány ani vráceny připojení, která nejsou explicitně zavřena. Například připojení, které se odchází z oboru, ale které nebylo explicitně uzavřeno, bude vráceno do fondu připojení pouze v případě, že byla dosažena maximální velikost fondu a připojení je stále platné. Další informace najdete v tématu [sdružování připojení OLE DB, ODBC a Oracle](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
> Nevolejte `Close` ani `Dispose` na **připojení**, objekt DataReadernebo žádný jiný spravovaný objekt v `Finalize` metodě vaší třídy. V finalizační metodě pouze uvolní nespravované prostředky, které vaše třída vlastní. Pokud vaše třída nevlastní žádné nespravované prostředky, `Finalize` nezahrnujte metodu do definice třídy. Další informace najdete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
> Události přihlášení a odhlášení nebudou na serveru vyvolány, když je připojení načteno z nebo vráceno do fondu připojení, protože připojení není ve skutečnosti při návratu do fondu připojení ukončeno. Další informace najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>Připojování k SQL Server  
 Zprostředkovatel dat .NET Framework pro SQL Server podporuje formát připojovacího řetězce, který se podobá formátu připojovacího řetězce OLE DB (ADO). Platný název a hodnoty formátu řetězce naleznete <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> v vlastnosti <xref:System.Data.SqlClient.SqlConnection> objektu. Můžete také použít <xref:System.Data.SqlClient.SqlConnectionStringBuilder> třídu k vytvoření syntakticky platných připojovacích řetězců za běhu. Další informace najdete v tématu [tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení k databázi SQL Server.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
### <a name="integrated-security-and-aspnet"></a>Integrované zabezpečení a ASP.NET  
 SQL Server integrované zabezpečení (označované také jako důvěryhodná připojení) pomáhá zajistit ochranu při připojení k SQL Server, protože nezveřejňuje ID uživatele a heslo v připojovacím řetězci a je doporučenou metodou pro ověřování připojení. Integrované zabezpečení používá aktuální identitu zabezpečení nebo token spuštěného procesu. U aplikací klasické pracovní plochy se obvykle jedná o identitu aktuálně přihlášeného uživatele.  
  
 Identita zabezpečení pro aplikace ASP.NET může být nastavená na jednu z několika různých možností. Pro lepší pochopení identity zabezpečení, kterou aplikace ASP.NET používá při připojování k SQL Server, přečtěte si téma [ASP.NET Impersonation](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100))a [How to: Přístup k SQL Server s využitím](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100))integrovaného zabezpečení systému Windows.  
  
## <a name="connecting-to-an-ole-db-data-source"></a>Připojení k OLE DBmu zdroji dat  
 Zprostředkovatel dat .NET Framework pro OLE DB poskytuje připojení ke zdrojům dat vystaveným pomocí OLE DB (prostřednictvím SQLOLEDB, poskytovatele OLE DB pro SQL Server) pomocí objektu **OleDbConnection** .  
  
 Pro .NET Framework Zprostředkovatel dat pro OLE DB je formát připojovacího řetězce totožný s formátem připojovacího řetězce používaným v objektech ADO, s následujícími výjimkami:  
  
- Klíčové slovo **Provider** je povinné.  
  
- Klíčová slova **URL**, **vzdálený zprostředkovatel**a **vzdálené servery** nejsou podporovaná.  
  
 Další informace o OLE DB připojovacích řetězcích naleznete <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> v tématu. Můžete také použít <xref:System.Data.OleDb.OleDbConnectionStringBuilder> k vytvoření připojovacích řetězců v době běhu.  
  
> [!NOTE]
> Objekt **OleDbConnection** nepodporuje nastavení nebo načítání dynamických vlastností specifických pro poskytovatele OLE DB. Jsou podporovány pouze vlastnosti, které lze předat v připojovacím řetězci pro poskytovatele OLE DB.  
  
 Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení k OLE DBmu zdroji dat.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OleDbConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OleDbConnection connection =   
  new OleDbConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="do-not-use-universal-data-link-files"></a>Nepoužívejte soubory Universal Data Link  
 V souboru UDL (Universal Data Link) je možné zadávat informace o připojení pro **OleDbConnection** . měli byste se ale vyhnout. Soubory UDL nejsou zašifrované a zveřejňují informace připojovacího řetězce ve formátu prostého textu. Vzhledem k tomu, že soubor UDL je externí prostředek založený na souboru, nelze jej zabezpečit pomocí .NET Framework.  
  
## <a name="connecting-to-an-odbc-data-source"></a>Připojení ke zdroji dat ODBC  
 Zprostředkovatel dat .NET Framework pro rozhraní ODBC poskytuje připojení ke zdrojům dat vystaveným pomocí rozhraní ODBC pomocí objektu **OdbcConnection** .  
  
 Pro Zprostředkovatel dat .NET Framework pro rozhraní ODBC je formát připojovacího řetězce navržen tak, aby co nejpřesněji odpovídal formátu připojovacího řetězce ODBC. Můžete také uvést název zdroje dat ODBC (DSN). Další podrobnosti o **OdbcConnection** najdete v tématu <xref:System.Data.Odbc.OdbcConnection>.  
  
 Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení ke zdroji dat ODBC.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OdbcConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OdbcConnection connection =   
  new OdbcConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="connecting-to-an-oracle-data-source"></a>Připojení ke zdroji dat Oracle  
 Zprostředkovatel dat .NET Framework pro Oracle poskytuje připojení ke zdrojům dat Oracle pomocí objektu **OracleConnection** .  
  
 Pro Zprostředkovatel dat .NET Framework pro Oracle je formát připojovacího řetězce navržený tak, aby co nejpřesněji odpovídal formátu připojovacího řetězce Oracle (MADAORA) poskytovatele OLE DB. Další podrobnosti o **OracleConnection**najdete v tématu <xref:System.Data.OracleClient.OracleConnection>.  
  
 Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení ke zdroji dat Oracle.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OracleConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OracleConnection connection =   
  new OracleConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
OracleConnection nwindConn = new OracleConnection("Data Source=MyOracleServer;Integrated Security=yes;");  
nwindConn.Open();  
```  
  
## <a name="see-also"></a>Viz také:

- [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Připojovací řetězce](../../../../docs/framework/data/adonet/connection-strings.md)
- [Sdružování připojení OLE DB, ODBC a Oracle](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
