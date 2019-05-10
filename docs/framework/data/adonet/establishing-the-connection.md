---
title: Navazování připojení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: 50cf5011376576d371dba558a602187201395bd0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599593"
---
# <a name="establishing-the-connection"></a>Navazování připojení
Pro připojení k serveru Microsoft SQL Server, použijte <xref:System.Data.SqlClient.SqlConnection> objektu zprostředkovatele dat .NET Framework pro SQL Server. Pro připojení ke zdroji dat OLE DB, použijte <xref:System.Data.OleDb.OleDbConnection> objektu zprostředkovatele dat .NET Framework pro OLE DB. Chcete-li se připojit ke zdroji dat rozhraní ODBC, použijte <xref:System.Data.Odbc.OdbcConnection> objektu zprostředkovatele dat .NET Framework pro ODBC. Chcete-li se připojit ke zdroji dat Oracle, použijte <xref:System.Data.OracleClient.OracleConnection> objektu zprostředkovatele dat .NET Framework pro Oracle. Bezpečné ukládání a načítání připojovacích řetězců najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Zavření připojení  
 Doporučujeme, abyste po dokončení jeho použití, takže připojení může být vrácen do fondu vždy ukončení připojení. `Using` Blokovat v jazyce Visual Basic nebo C# automaticky uvolní připojení při kód ukončení bloku i v případě neošetřené výjimce. Zobrazit [příkaz using](~/docs/csharp/language-reference/keywords/using-statement.md) a [příkazu Using](~/docs/visual-basic/language-reference/statements/using-statement.md) Další informace.  
  
 Můžete také použít `Close` nebo `Dispose` metody objektu připojení pro poskytovatele, který používáte. Připojení, které nebyly uzavřeny explicitně nemusí přidali nebo vrácen do fondu. Například připojení, který má nepřejdou mimo rozsah, ale který ještě nebyl uzavřen explicitně pouze vrátí se do fondu připojení Pokud bylo dosaženo maximální velikosti fondu připojení je stále platný. Další informace najdete v tématu [OLE DB, ODBC a Oracle sdružování připojení](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
>  Nevolejte `Close` nebo `Dispose` na **připojení**, **DataReader**, nebo jakýkoli jiný spravovaný objekt v `Finalize` metoda vaší třídy. V finalizační metodu jenom uvolnění nespravovaných prostředků, které vaše třída vlastní přímo. Pokud vaše třída není vlastníkem jakýchkoliv nespravovaných prostředků, nezahrnujte `Finalize` metoda v definici třídy. Další informace najdete v tématu [uvolňování](../../../../docs/standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Přihlášení a odhlášení události nebudou vyvolány na serveru při připojení je načtena z nebo vrácen do fondu připojení, protože připojení není ukončeno ve skutečnosti, pokud je vrácen do fondu připojení. Další informace najdete v tématu [SQL sdružování připojení serveru (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>Připojení k SQL serveru  
 Zprostředkovatel dat .NET Framework pro SQL Server podporuje formát připojovacího řetězce, který je podobný formátu OLE DB (ADO) připojovacího řetězce. Platný řetězec formátu názvy a hodnoty, najdete v článku <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> vlastnost <xref:System.Data.SqlClient.SqlConnection> objektu. Můžete také použít <xref:System.Data.SqlClient.SqlConnectionStringBuilder> třídy za účelem vytvoření syntakticky správný připojovací řetězce v době běhu. Další informace najdete v tématu [tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
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
 Integrované zabezpečení (označované také jako důvěryhodná připojení) pomáhá zajistit ochranu při připojování k serveru SQL Server jako jeho systému SQL Server nemůže vystavovat ID uživatele a heslo v připojovacím řetězci a je doporučenou metodou pro ověřování připojení. Integrované zabezpečení používá aktuální identita zabezpečení, nebo token spuštěného procesu. Pro desktopové aplikace je to obvykle identitu aktuálně přihlášeného uživatele.  
  
 Identita zabezpečení pro aplikace ASP.NET můžete nastavit na jedno z několika různých možností. Abyste lépe pochopili identita zabezpečení, který používá aplikace ASP.NET při připojování k serveru SQL Server, naleznete v tématu [zosobnění technologie ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ověřování ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), a [jak: Přístup k SQL serveru pomocí Windows integrované zabezpečení](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).  
  
## <a name="connecting-to-an-ole-db-data-source"></a>Připojení ke zdroji dat OLE DB  
 Zprostředkovatel dat .NET Framework pro OLE DB poskytuje připojení ke zdrojům dat, které jsou přístupné přes OLE DB (pomocí SQLOLEDB, OLE DB Provider pro SQL Server), pomocí **OleDbConnection –** objektu.  
  
 Formát připojovacího řetězce pro zprostředkovatele dat .NET Framework pro OLE DB, je stejný jako formát připojovacího řetězce používán ADO, s následujícími výjimkami:  
  
- **Poskytovatele** – klíčové slovo je povinný.  
  
- **URL**, **vzdáleného poskytovatele**, a **vzdálený Server** klíčová slova nejsou podporovány.  
  
 Další informace o připojovacích řetězcích OLE DB, najdete v článku <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> tématu. Můžete také použít <xref:System.Data.OleDb.OleDbConnectionStringBuilder> vytvoření připojovací řetězce v době běhu.  
  
> [!NOTE]
>  **OleDbConnection –** objekt nepodporuje nastavení nebo načtení dynamické vlastnosti specifické pro zprostředkovatele OLE DB. Jsou podporovány pouze vlastnosti, které lze předat v připojovacím řetězci pro zprostředkovatele OLE DB.  
  
 Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení ke zdroji dat OLE DB.  
  
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
 Je možné zadat informace o připojení **OleDbConnection –** v souboru univerzální datové propojení (UDL); ale měli byste se vyhnout tím. Soubory UDL nejsou šifrované a zveřejnit informace o připojovacím řetězci ve formátu prostého textu. Vzhledem k tomu, že je soubor UDL externí souborových prostředků do vaší aplikace, nemůže být zabezpečená, pomocí rozhraní .NET Framework.  
  
## <a name="connecting-to-an-odbc-data-source"></a>Připojení ke zdroji dat rozhraní ODBC  
 Zprostředkovatel dat .NET Framework pro ODBC poskytuje připojení ke zdrojům dat, které jsou přístupné přes rozhraní ODBC použitím **ODBC** objektu.  
  
 Pro .NET Framework Data Provider pro rozhraní ODBC formát připojovacího řetězce je navržená tak, aby odpovídaly formát připojovacího řetězce ODBC co nejpřesněji. Může také poskytnout název zdroje dat ODBC (DSN). Další podrobnosti o **ODBC** , najdete v článku <xref:System.Data.Odbc.OdbcConnection>.  
  
 Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení ke zdroji dat rozhraní ODBC.  
  
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
 Poskytuje připojení ke zdrojům dat Oracle pomocí zprostředkovatele dat .NET Framework pro Oracle **Objekt OracleConnection** objektu.  
  
 Pro .NET Framework Data Provider pro Oracle formát připojovacího řetězce je navržená tak, aby odpovídala zprostředkovatele OLE DB pro Oracle (MSDAORA) formát připojovacího řetězce co nejpřesněji. Další podrobnosti o **Objekt OracleConnection**, najdete v článku <xref:System.Data.OracleClient.OracleConnection>.  
  
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
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
