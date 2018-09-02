---
title: Navazování připojení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: 29db884a88f5150cd93571ba8fa7bf72be2b8c69
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423673"
---
# <a name="establishing-the-connection"></a><span data-ttu-id="45a28-102">Navazování připojení</span><span class="sxs-lookup"><span data-stu-id="45a28-102">Establishing the Connection</span></span>
<span data-ttu-id="45a28-103">Pro připojení k serveru Microsoft SQL Server, použijte <xref:System.Data.SqlClient.SqlConnection> objektu zprostředkovatele dat .NET Framework pro SQL Server.</span><span class="sxs-lookup"><span data-stu-id="45a28-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="45a28-104">Pro připojení ke zdroji dat OLE DB, použijte <xref:System.Data.OleDb.OleDbConnection> objektu zprostředkovatele dat .NET Framework pro OLE DB.</span><span class="sxs-lookup"><span data-stu-id="45a28-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="45a28-105">Chcete-li se připojit ke zdroji dat rozhraní ODBC, použijte <xref:System.Data.Odbc.OdbcConnection> objektu zprostředkovatele dat .NET Framework pro ODBC.</span><span class="sxs-lookup"><span data-stu-id="45a28-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="45a28-106">Chcete-li se připojit ke zdroji dat Oracle, použijte <xref:System.Data.OracleClient.OracleConnection> objektu zprostředkovatele dat .NET Framework pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="45a28-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="45a28-107">Bezpečné ukládání a načítání připojovacích řetězců najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="45a28-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="45a28-108">Zavření připojení</span><span class="sxs-lookup"><span data-stu-id="45a28-108">Closing Connections</span></span>  
 <span data-ttu-id="45a28-109">Doporučujeme, abyste po dokončení jeho použití, takže připojení může být vrácen do fondu vždy ukončení připojení.</span><span class="sxs-lookup"><span data-stu-id="45a28-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="45a28-110">`Using` Blokovat v jazyce Visual Basic nebo C# automaticky uvolní připojení při kód ukončení bloku i v případě neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="45a28-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="45a28-111">Zobrazit [příkaz using](~/docs/csharp/language-reference/keywords/using-statement.md) a [příkazu Using](~/docs/visual-basic/language-reference/statements/using-statement.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="45a28-111">See [using Statement](~/docs/csharp/language-reference/keywords/using-statement.md) and [Using Statement](~/docs/visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="45a28-112">Můžete také použít `Close` nebo `Dispose` metody objektu připojení pro poskytovatele, který používáte.</span><span class="sxs-lookup"><span data-stu-id="45a28-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="45a28-113">Připojení, které nebyly uzavřeny explicitně nemusí přidali nebo vrácen do fondu.</span><span class="sxs-lookup"><span data-stu-id="45a28-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="45a28-114">Například připojení, který má nepřejdou mimo rozsah, ale který ještě nebyl uzavřen explicitně pouze vrátí se do fondu připojení Pokud bylo dosaženo maximální velikosti fondu připojení je stále platný.</span><span class="sxs-lookup"><span data-stu-id="45a28-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="45a28-115">Další informace najdete v tématu [OLE DB, ODBC a Oracle sdružování připojení](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="45a28-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45a28-116">Nevolejte `Close` nebo `Dispose` na **připojení**, **DataReader**, nebo jakýkoli jiný spravovaný objekt v `Finalize` metoda vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="45a28-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="45a28-117">V finalizační metodu jenom uvolnění nespravovaných prostředků, které vaše třída vlastní přímo.</span><span class="sxs-lookup"><span data-stu-id="45a28-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="45a28-118">Pokud vaše třída není vlastníkem jakýchkoliv nespravovaných prostředků, nezahrnujte `Finalize` metoda v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="45a28-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="45a28-119">Další informace najdete v tématu [uvolňování](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="45a28-119">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45a28-120">Přihlášení a odhlášení události nebudou vyvolány na serveru při připojení je načtena z nebo vrácen do fondu připojení, protože připojení není ukončeno ve skutečnosti, pokud je vrácen do fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="45a28-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="45a28-121">Další informace najdete v tématu [SQL sdružování připojení serveru (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="45a28-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="45a28-122">Připojení k SQL serveru</span><span class="sxs-lookup"><span data-stu-id="45a28-122">Connecting to SQL Server</span></span>  
 <span data-ttu-id="45a28-123">Zprostředkovatel dat .NET Framework pro SQL Server podporuje formát připojovacího řetězce, který je podobný formátu OLE DB (ADO) připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="45a28-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="45a28-124">Platný řetězec formátu názvy a hodnoty, najdete v článku <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> vlastnost <xref:System.Data.SqlClient.SqlConnection> objektu.</span><span class="sxs-lookup"><span data-stu-id="45a28-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="45a28-125">Můžete také použít <xref:System.Data.SqlClient.SqlConnectionStringBuilder> třídy za účelem vytvoření syntakticky správný připojovací řetězce v době běhu.</span><span class="sxs-lookup"><span data-stu-id="45a28-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="45a28-126">Další informace najdete v tématu [tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="45a28-126">For more information, see [Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="45a28-127">Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení k databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="45a28-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
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
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="45a28-128">Integrované zabezpečení a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="45a28-128">Integrated Security and ASP.NET</span></span>  
 <span data-ttu-id="45a28-129">Integrované zabezpečení (označované také jako důvěryhodná připojení) pomáhá zajistit ochranu při připojování k serveru SQL Server jako jeho systému SQL Server nemůže vystavovat ID uživatele a heslo v připojovacím řetězci a je doporučenou metodou pro ověřování připojení.</span><span class="sxs-lookup"><span data-stu-id="45a28-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="45a28-130">Integrované zabezpečení používá aktuální identita zabezpečení, nebo token spuštěného procesu.</span><span class="sxs-lookup"><span data-stu-id="45a28-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="45a28-131">Pro desktopové aplikace je to obvykle identitu aktuálně přihlášeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="45a28-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="45a28-132">Identita zabezpečení pro aplikace ASP.NET můžete nastavit na jedno z několika různých možností.</span><span class="sxs-lookup"><span data-stu-id="45a28-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="45a28-133">Abyste lépe pochopili identita zabezpečení, který používá aplikace ASP.NET při připojování k serveru SQL Server, naleznete v tématu [zosobnění technologie ASP.NET](https://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d), [ověřování ASP.NET](https://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1), a [postupy: přístup k SQL Integrované zabezpečení serveru pomocí Windows](https://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5).</span><span class="sxs-lookup"><span data-stu-id="45a28-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](https://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d), [ASP.NET Authentication](https://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1), and [How to: Access SQL Server Using Windows Integrated Security](https://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="45a28-134">Připojení ke zdroji dat OLE DB</span><span class="sxs-lookup"><span data-stu-id="45a28-134">Connecting to an OLE DB Data Source</span></span>  
 <span data-ttu-id="45a28-135">Zprostředkovatel dat .NET Framework pro OLE DB poskytuje připojení ke zdrojům dat, které jsou přístupné přes OLE DB (pomocí SQLOLEDB, OLE DB Provider pro SQL Server), pomocí **OleDbConnection –** objektu.</span><span class="sxs-lookup"><span data-stu-id="45a28-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="45a28-136">Formát připojovacího řetězce pro zprostředkovatele dat .NET Framework pro OLE DB, je stejný jako formát připojovacího řetězce používán ADO, s následujícími výjimkami:</span><span class="sxs-lookup"><span data-stu-id="45a28-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="45a28-137">**Poskytovatele** – klíčové slovo je povinný.</span><span class="sxs-lookup"><span data-stu-id="45a28-137">The **Provider** keyword is required.</span></span>  
  
-   <span data-ttu-id="45a28-138">**URL**, **vzdáleného poskytovatele**, a **vzdálený Server** klíčová slova nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="45a28-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="45a28-139">Další informace o připojovacích řetězcích OLE DB, najdete v článku <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> tématu.</span><span class="sxs-lookup"><span data-stu-id="45a28-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="45a28-140">Můžete také použít <xref:System.Data.OleDb.OleDbConnectionStringBuilder> vytvoření připojovací řetězce v době běhu.</span><span class="sxs-lookup"><span data-stu-id="45a28-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45a28-141">**OleDbConnection –** objekt nepodporuje nastavení nebo načtení dynamické vlastnosti specifické pro zprostředkovatele OLE DB.</span><span class="sxs-lookup"><span data-stu-id="45a28-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="45a28-142">Jsou podporovány pouze vlastnosti, které lze předat v připojovacím řetězci pro zprostředkovatele OLE DB.</span><span class="sxs-lookup"><span data-stu-id="45a28-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="45a28-143">Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení ke zdroji dat OLE DB.</span><span class="sxs-lookup"><span data-stu-id="45a28-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="45a28-144">Nepoužívejte soubory univerzálního datového propojení</span><span class="sxs-lookup"><span data-stu-id="45a28-144">Do Not Use Universal Data Link Files</span></span>  
 <span data-ttu-id="45a28-145">Je možné zadat informace o připojení **OleDbConnection –** v souboru univerzální datové propojení (UDL); ale měli byste se vyhnout tím.</span><span class="sxs-lookup"><span data-stu-id="45a28-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="45a28-146">Soubory UDL nejsou šifrované a zveřejnit informace o připojovacím řetězci ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="45a28-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="45a28-147">Vzhledem k tomu, že je soubor UDL externí souborových prostředků do vaší aplikace, nemůže být zabezpečená, pomocí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45a28-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="45a28-148">Připojení ke zdroji dat rozhraní ODBC</span><span class="sxs-lookup"><span data-stu-id="45a28-148">Connecting to an ODBC Data Source</span></span>  
 <span data-ttu-id="45a28-149">Zprostředkovatel dat .NET Framework pro ODBC poskytuje připojení ke zdrojům dat, které jsou přístupné přes rozhraní ODBC použitím **ODBC** objektu.</span><span class="sxs-lookup"><span data-stu-id="45a28-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="45a28-150">Pro .NET Framework Data Provider pro rozhraní ODBC formát připojovacího řetězce je navržená tak, aby odpovídaly formát připojovacího řetězce ODBC co nejpřesněji.</span><span class="sxs-lookup"><span data-stu-id="45a28-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="45a28-151">Může také poskytnout název zdroje dat ODBC (DSN).</span><span class="sxs-lookup"><span data-stu-id="45a28-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="45a28-152">Další podrobnosti o **ODBC** , najdete v článku <xref:System.Data.Odbc.OdbcConnection>.</span><span class="sxs-lookup"><span data-stu-id="45a28-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="45a28-153">Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení ke zdroji dat rozhraní ODBC.</span><span class="sxs-lookup"><span data-stu-id="45a28-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="45a28-154">Připojení ke zdroji dat Oracle</span><span class="sxs-lookup"><span data-stu-id="45a28-154">Connecting to an Oracle Data Source</span></span>  
 <span data-ttu-id="45a28-155">Poskytuje připojení ke zdrojům dat Oracle pomocí zprostředkovatele dat .NET Framework pro Oracle **Objekt OracleConnection** objektu.</span><span class="sxs-lookup"><span data-stu-id="45a28-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="45a28-156">Pro .NET Framework Data Provider pro Oracle formát připojovacího řetězce je navržená tak, aby odpovídala zprostředkovatele OLE DB pro Oracle (MSDAORA) formát připojovacího řetězce co nejpřesněji.</span><span class="sxs-lookup"><span data-stu-id="45a28-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="45a28-157">Další podrobnosti o **Objekt OracleConnection**, najdete v článku <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="45a28-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="45a28-158">Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení ke zdroji dat Oracle.</span><span class="sxs-lookup"><span data-stu-id="45a28-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="45a28-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="45a28-159">See Also</span></span>  
 [<span data-ttu-id="45a28-160">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="45a28-160">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="45a28-161">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="45a28-161">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="45a28-162">Sdružování připojení OLE DB, ODBC a Oracle</span><span class="sxs-lookup"><span data-stu-id="45a28-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [<span data-ttu-id="45a28-163">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="45a28-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
