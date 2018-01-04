---
title: "Navazování připojení"
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
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 416d89aef35fef5dd0ac2bca92fb8a90d757a2d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="establishing-the-connection"></a>Navazování připojení
Pro připojení k serveru Microsoft SQL Server, použijte <xref:System.Data.SqlClient.SqlConnection> objektu zprostředkovatele dat .NET Framework pro SQL Server. Chcete-li se připojit ke zdroji dat OLE DB, použijte <xref:System.Data.OleDb.OleDbConnection> objekt zprostředkovatel dat .NET Framework pro OLE DB. Chcete-li se připojit ke zdroji dat rozhraní ODBC, použijte <xref:System.Data.Odbc.OdbcConnection> objekt zprostředkovatel dat .NET Framework pro ODBC. Chcete-li se připojit ke zdroji dat Oracle, použijte <xref:System.Data.OracleClient.OracleConnection> objekt zprostředkovatel dat .NET Framework pro Oracle. Bezpečného ukládání a načítání připojovacích řetězců najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Ukončením připojení  
 Doporučujeme, abyste po dokončení pomocí, tak, aby připojení se může vracet do fondu vždy ukončení připojení. `Using` Blokování v jazyce Visual Basic nebo C# automaticky odstraňuje připojení při kód ukončení bloku, i v případě neošetřené výjimce. V tématu [pomocí příkazu](~/docs/csharp/language-reference/keywords/using-statement.md) a [příkazu Using](~/docs/visual-basic/language-reference/statements/using-statement.md) Další informace.  
  
 Můžete také `Close` nebo `Dispose` metody objekt připojení pro poskytovatele, který používáte. Připojení, které nejsou výslovně nemusí přidat nebo vrátí do fondu. Například připojení, která byla mimo rozsah, ale který ještě nebyl uzavřen explicitně pouze vrátí do fondu připojení Pokud byl dosažen maximální počet a připojení je stále platný. Další informace najdete v tématu [OLE DB, rozhraní ODBC a sdružování připojení Oracle](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
>  Nevolejte `Close` nebo `Dispose` na **připojení**, **DataReader –**, nebo jiné spravovaného objektu v `Finalize` metoda vaší třídy. V finalizační metodu vydání pouze nespravovaných prostředků, které vlastní třídu přímo. Pokud vaše třída nevlastní žádné nespravovaných prostředků, nezahrnujte `Finalize` metoda v definici vaší třídy. Další informace najdete v tématu [uvolňování paměti](../../../../docs/standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Události přihlášení a odhlášení nebudou vyvolávat na serveru při připojení je načtena z nebo vrátí do fondu připojení, protože připojení není uzavřený ve skutečnosti, pokud se vrátí do fondu připojení. Další informace najdete v tématu [SQL sdružování připojení serveru (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>Připojení k SQL serveru  
 Zprostředkovatel dat .NET Framework pro SQL Server podporuje formátu řetězce připojení, který je podobný formátu řetězce připojení OLE DB (ADO). Platný řetězec formátu názvy a hodnoty, najdete v článku <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> vlastnost <xref:System.Data.SqlClient.SqlConnection> objektu. Můžete také <xref:System.Data.SqlClient.SqlConnectionStringBuilder> třídy za účelem vytvoření syntakticky připojovací řetězce v době běhu. Další informace najdete v tématu [Tvůrci řetězců pro připojení](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení k databázi systému SQL Server.  
  
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
 Integrované zabezpečení (také označované jako důvěryhodná připojení) pomáhá zajistit ochranu při připojování k systému SQL Server, jako je SQL Server nevystavuje ID uživatele a heslo v připojovacím řetězci a patří mezi doporučené metody pro ověřování připojení. Integrované zabezpečení používá aktuální identitu zabezpečení nebo token, provádění procesu. U aplikací klasické pracovní plochy je to obvykle identitu aktuálně přihlášeného uživatele.  
  
 Identity zabezpečení pro aplikace ASP.NET můžete nastavit na jedno z několika různých možností. Abyste lépe pochopili identity zabezpečení, která aplikace ASP.NET používá při připojování k systému SQL Server, najdete v části [zosobnění technologie ASP.NET](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d), [ověřování pomocí technologie ASP.NET](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1), a [postupy: přístup SQL Server Windows pomocí integrované zabezpečení](http://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5).  
  
## <a name="connecting-to-an-ole-db-data-source"></a>Připojení ke zdroji dat OLE DB  
 Zprostředkovatel dat .NET Framework pro OLE DB zajišťuje připojení ke zdrojům dat, které jsou vystavené pomocí OLE DB (prostřednictvím SQLOLEDB, zprostředkovatele OLE DB pro SQL Server), pomocí **OleDbConnection** objektu.  
  
 Pro rozhraní .NET Framework dat zprostředkovatele pro OLE DB formátu řetězce připojení je stejná jako formátu řetězce připojení, který se používá v ADO, s následujícími výjimkami:  
  
-   **Zprostředkovatele** je požadováno klíčové slovo.  
  
-   **URL**, **vzdáleného poskytovatele**, a **vzdáleného serveru** klíčová slova nejsou podporovány.  
  
 Další informace o OLE DB-řetězce připojení najdete v tématu <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> tématu. Můžete také <xref:System.Data.OleDb.OleDbConnectionStringBuilder> vytvořit připojovací řetězce v době běhu.  
  
> [!NOTE]
>  **OleDbConnection** objekt nepodporuje nastavení nebo načtení dynamické vlastnosti, které jsou specifické pro zprostředkovatele OLE DB. Jsou podporovány pouze vlastnosti, které lze předat v připojovacím řetězci pro zprostředkovatele OLE DB.  
  
 Následující příklad kódu ukazuje, jak vytvořit a otevřete připojení ke zdroji dat OLE DB.  
  
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
 Je možné poskytnout informace o připojení **OleDbConnection** v souboru Universal Data odkaz (UDL); ale neměli byste tak. Soubory UDL nejsou zašifrované a vystavit informace o připojovacím řetězci ve formátu prostého textu. Protože soubor UDL je externí prostředek založených na souborech do vaší aplikace, nelze zabezpečené, pomocí rozhraní .NET Framework.  
  
## <a name="connecting-to-an-odbc-data-source"></a>Připojení ke zdroji dat rozhraní ODBC  
 Zprostředkovatel dat .NET Framework pro ODBC poskytuje připojení ke zdrojům dat, které jsou vystavené pomocí pomocí rozhraní ODBC **ODBC** objektu.  
  
 Pro rozhraní .NET Framework dat zprostředkovatele pro rozhraní ODBC formátu řetězce připojení slouží k co nejvíce odpovídají formátu řetězce připojení ODBC. Může taky poskytovat název zdroje dat ODBC (DSN). Další podrobnosti o **ODBC** , najdete v článku <xref:System.Data.Odbc.OdbcConnection>.  
  
 Následující příklad kódu ukazuje, jak vytvořit a otevřete připojení ke zdroji dat rozhraní ODBC.  
  
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
 Zprostředkovatel dat .NET Framework pro Oracle zajišťuje připojení ke zdrojům dat Oracle pomocí **Objekt OracleConnection** objektu.  
  
 Pro rozhraní .NET Framework Data Provider pro Oracle formátu řetězce připojení slouží k co nejvíce odpovídají zprostředkovatele OLE DB pro Oracle (MSDAORA) formátu řetězce připojení. Další podrobnosti o **Objekt OracleConnection**, najdete v článku <xref:System.Data.OracleClient.OracleConnection>.  
  
 Následující příklad kódu ukazuje, jak vytvořit a otevřete připojení ke zdroji dat Oracle.  
  
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
 [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Připojovací řetězce](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Sdružování připojení OLE DB, ODBC a Oracle](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
