---
title: Navazování připojení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: 4606ecb370b7e85cf5ebd92754471f5253321251
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149658"
---
# <a name="establishing-the-connection"></a>Navazování připojení
Chcete-li se připojit k <xref:System.Data.SqlClient.SqlConnection> serveru Microsoft SQL Server, použijte objekt zprostředkovatele dat rozhraní .NET Framework pro sql server. Chcete-li se připojit ke zdroji <xref:System.Data.OleDb.OleDbConnection> dat technologie OLE DB, použijte objekt zprostředkovatele dat rozhraní .NET Framework pro prostředí OLE DB. Chcete-li se připojit ke zdroji <xref:System.Data.Odbc.OdbcConnection> dat ROZHRANÍ ODBC, použijte objekt zprostředkovatele dat rozhraní .NET Framework pro rozhraní ODBC. Chcete-li se připojit ke <xref:System.Data.OracleClient.OracleConnection> zdroji dat Oracle, použijte objekt zprostředkovatele dat rozhraní .NET Framework pro společnost Oracle. Informace o bezpečném ukládání a načítání připojovacích řetězců naleznete [v tématu Ochrana informací o připojení](protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Zavírání připojení  
 Doporučujeme vždy zavřít připojení po dokončení jeho použití, tak, aby připojení lze vrátit do fondu. Blok `Using` v jazyce Visual Basic nebo C# automaticky vyloží připojení při ukončení kódu bloku, i v případě neošetřené výjimky. Další informace najdete [v tématu Using Statement](../../../csharp/language-reference/keywords/using-statement.md) and Using [Statement.](../../../visual-basic/language-reference/statements/using-statement.md)  
  
 Můžete také použít `Close` `Dispose` metody nebo objektu připojení pro zprostředkovatele, který používáte. Připojení, která nejsou explicitně uzavřena, nemusí být přidána nebo vrácena do fondu. Například připojení, které přešlo mimo rozsah, ale které nebylo explicitně uzavřeno, bude vráceno do fondu připojení pouze v případě, že bylo dosaženo maximální velikosti fondu a připojení je stále platné. Další informace naleznete v [tématech OLE DB, ODBC a Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
> Nevolejte `Close` nebo `Dispose` na **připojení**, **DataReader**nebo jiný spravovaný objekt v metodě `Finalize` vaší třídy. Ve finalizační metodě uvolněte pouze nespravované prostředky, které přímo vlastní vaše třída. Pokud vaše třída nevlastní žádné nespravované prostředky, `Finalize` nezahrnujte metodu do definice třídy. Další informace naleznete v [tématu Garbage Collection](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
> Události přihlášení a odhlášení nebudou vyvolány na serveru při načtení připojení z fondu připojení nebo vrácené do fondu připojení, protože připojení není ve skutečnosti uzavřeno, když je vráceno do fondu připojení. Další informace naleznete v tématu [SQL Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>Připojení k serveru SQL Server  
 Zprostředkovatel dat rozhraní .NET Framework pro SQL Server podporuje formát připojovacího řetězce, který je podobný formátu připojovacího řetězce OLE DB (ADO). Platné názvy a hodnoty formátu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> řetězce <xref:System.Data.SqlClient.SqlConnection> naleznete ve vlastnosti objektu. Třídu <xref:System.Data.SqlClient.SqlConnectionStringBuilder> můžete také použít k vytvoření syntakticky platných připojovacích řetězců za běhu. Další informace naleznete v [tématu Connection String Builders](connection-string-builders.md).  
  
 Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení k databázi serveru SQL Server.  
  
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
 Integrované zabezpečení SQL Serveru (označované také jako důvěryhodná připojení) pomáhá poskytovat ochranu při připojování k serveru SQL Server, protože nezveřejňuje ID uživatele a heslo v připojovacím řetězci a je doporučenou metodou ověřování připojení. Integrované zabezpečení používá aktuální identitu zabezpečení nebo token vykonávajícího procesu. Pro desktopové aplikace se obvykle jedná o identitu aktuálně přihlášeného uživatele.  
  
 Identitu zabezpečení pro aplikace ASP.NET lze nastavit na jednu z několika různých možností. Chcete-li lépe porozumět identitě zabezpečení, kterou aplikace ASP.NET používá při připojování k serveru SQL Server, [přečtěte si ASP.NET zosobnění](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET ověřování](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100))a [postup: Přístup k serveru SQL Server pomocí integrovaného zabezpečení systému Windows](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).  
  
## <a name="connecting-to-an-ole-db-data-source"></a>Připojení ke zdroji dat technologie OLE DB  
 Zprostředkovatel dat rozhraní .NET Framework pro technologie OLE DB poskytuje připojení ke zdrojům dat vystaveným pomocí technologie OLE DB (prostřednictvím SQLOLEDB, zprostředkovatele OLE DB pro SQL Server), pomocí objektu **OleDbConnection.**  
  
 Pro zprostředkovatele dat rozhraní .NET Framework pro technologie OLE DB je formát připojovacího řetězce shodný s formátem připojovacího řetězce používaným v objektu ADO s následujícími výjimkami:  
  
- Je vyžadováno klíčové slovo **Zprostředkovatel.**  
  
- Klíčová slova **URL**, **Vzdáleného zprostředkovatele**a **Vzdáleného serveru** nejsou podporována.  
  
 Další informace o připojovacích <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> řetězcích TECHNOLOGIE OLE DB naleznete v tématu. Můžete také vytvořit <xref:System.Data.OleDb.OleDbConnectionStringBuilder> připojovací řetězce za běhu.  
  
> [!NOTE]
> Objekt **OleDbConnection** nepodporuje nastavení nebo načítání dynamických vlastností specifických pro zprostředkovatele TECHNOLOGIE OLE DB. Podporovány jsou pouze vlastnosti, které mohou být předány v připojovacím řetězci pro zprostředkovatele TECHNOLOGIE OLE DB.  
  
 Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení ke zdroji dat TECHNOLOGIE OLE DB.  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a>Nepoužívejte soubory univerzálního datového propojení  
 Je možné zadat informace o připojení pro **OleDbConnection** v souboru Univerzální datové spojení (UDL). nicméně byste se měli vyhnout tomu. UDL soubory nejsou šifrovány a vystavit informace o připojovacím řetězci ve prostém textu. Vzhledem k tomu, že soubor UDL je externí prostředek založený na souboru pro vaši aplikaci, nelze jej zabezpečit pomocí rozhraní .NET Framework.  
  
## <a name="connecting-to-an-odbc-data-source"></a>Připojení ke zdroji dat ODBC  
 Zprostředkovatel dat rozhraní .NET Framework pro rozhraní ODBC poskytuje připojení ke zdrojům dat vystaveným pomocí rozhraní ODBC pomocí objektu **OdbcConnection.**  
  
 Pro zprostředkovatele dat rozhraní .NET Framework pro rozhraní ODBC je formát připojovacího řetězce navržen tak, aby co nejvíce odpovídal formátu připojovacího řetězce ODBC. Můžete také zadat název zdroje dat ODBC (DSN). Další podrobnosti o **připojení OdbcConnection** naleznete v tématu <xref:System.Data.Odbc.OdbcConnection>.  
  
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
 Zprostředkovatel dat rozhraní .NET Framework pro oracle poskytuje připojení ke zdrojům dat Oracle pomocí objektu **OracleConnection.**  
  
 Pro zprostředkovatele dat rozhraní .NET Framework pro oracle je formát připojovacího řetězce navržen tak, aby co nejvíce odpovídal formátu připojovacího řetězce OLE DB Provider for Oracle (MSDAORA). Další podrobnosti o **řešení OracleConnection**naleznete v tématu <xref:System.Data.OracleClient.OracleConnection>.  
  
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
  
## <a name="see-also"></a>Viz také

- [Připojení ke zdroji dat](connecting-to-a-data-source.md)
- [Připojovací řetězce](connection-strings.md)
- [Sdružování připojení OLE DB, ODBC a Oracle](ole-db-odbc-and-oracle-connection-pooling.md)
- [Přehled ADO.NET](ado-net-overview.md)
