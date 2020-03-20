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
# <a name="establishing-the-connection"></a><span data-ttu-id="3dd0d-102">Navazování připojení</span><span class="sxs-lookup"><span data-stu-id="3dd0d-102">Establishing the Connection</span></span>
<span data-ttu-id="3dd0d-103">Chcete-li se připojit k <xref:System.Data.SqlClient.SqlConnection> serveru Microsoft SQL Server, použijte objekt zprostředkovatele dat rozhraní .NET Framework pro sql server.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="3dd0d-104">Chcete-li se připojit ke zdroji <xref:System.Data.OleDb.OleDbConnection> dat technologie OLE DB, použijte objekt zprostředkovatele dat rozhraní .NET Framework pro prostředí OLE DB.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="3dd0d-105">Chcete-li se připojit ke zdroji <xref:System.Data.Odbc.OdbcConnection> dat ROZHRANÍ ODBC, použijte objekt zprostředkovatele dat rozhraní .NET Framework pro rozhraní ODBC.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="3dd0d-106">Chcete-li se připojit ke <xref:System.Data.OracleClient.OracleConnection> zdroji dat Oracle, použijte objekt zprostředkovatele dat rozhraní .NET Framework pro společnost Oracle.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="3dd0d-107">Informace o bezpečném ukládání a načítání připojovacích řetězců naleznete [v tématu Ochrana informací o připojení](protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="3dd0d-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="3dd0d-108">Zavírání připojení</span><span class="sxs-lookup"><span data-stu-id="3dd0d-108">Closing Connections</span></span>  
 <span data-ttu-id="3dd0d-109">Doporučujeme vždy zavřít připojení po dokončení jeho použití, tak, aby připojení lze vrátit do fondu.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="3dd0d-110">Blok `Using` v jazyce Visual Basic nebo C# automaticky vyloží připojení při ukončení kódu bloku, i v případě neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="3dd0d-111">Další informace najdete [v tématu Using Statement](../../../csharp/language-reference/keywords/using-statement.md) and Using [Statement.](../../../visual-basic/language-reference/statements/using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="3dd0d-111">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) and [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="3dd0d-112">Můžete také použít `Close` `Dispose` metody nebo objektu připojení pro zprostředkovatele, který používáte.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="3dd0d-113">Připojení, která nejsou explicitně uzavřena, nemusí být přidána nebo vrácena do fondu.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="3dd0d-114">Například připojení, které přešlo mimo rozsah, ale které nebylo explicitně uzavřeno, bude vráceno do fondu připojení pouze v případě, že bylo dosaženo maximální velikosti fondu a připojení je stále platné.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="3dd0d-115">Další informace naleznete v [tématech OLE DB, ODBC a Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="3dd0d-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3dd0d-116">Nevolejte `Close` nebo `Dispose` na **připojení**, **DataReader**nebo jiný spravovaný objekt v metodě `Finalize` vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="3dd0d-117">Ve finalizační metodě uvolněte pouze nespravované prostředky, které přímo vlastní vaše třída.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="3dd0d-118">Pokud vaše třída nevlastní žádné nespravované prostředky, `Finalize` nezahrnujte metodu do definice třídy.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="3dd0d-119">Další informace naleznete v [tématu Garbage Collection](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="3dd0d-119">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3dd0d-120">Události přihlášení a odhlášení nebudou vyvolány na serveru při načtení připojení z fondu připojení nebo vrácené do fondu připojení, protože připojení není ve skutečnosti uzavřeno, když je vráceno do fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="3dd0d-121">Další informace naleznete v tématu [SQL Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="3dd0d-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="3dd0d-122">Připojení k serveru SQL Server</span><span class="sxs-lookup"><span data-stu-id="3dd0d-122">Connecting to SQL Server</span></span>  
 <span data-ttu-id="3dd0d-123">Zprostředkovatel dat rozhraní .NET Framework pro SQL Server podporuje formát připojovacího řetězce, který je podobný formátu připojovacího řetězce OLE DB (ADO).</span><span class="sxs-lookup"><span data-stu-id="3dd0d-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="3dd0d-124">Platné názvy a hodnoty formátu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> řetězce <xref:System.Data.SqlClient.SqlConnection> naleznete ve vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="3dd0d-125">Třídu <xref:System.Data.SqlClient.SqlConnectionStringBuilder> můžete také použít k vytvoření syntakticky platných připojovacích řetězců za běhu.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="3dd0d-126">Další informace naleznete v [tématu Connection String Builders](connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="3dd0d-126">For more information, see [Connection String Builders](connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="3dd0d-127">Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení k databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
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
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="3dd0d-128">Integrované zabezpečení a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3dd0d-128">Integrated Security and ASP.NET</span></span>  
 <span data-ttu-id="3dd0d-129">Integrované zabezpečení SQL Serveru (označované také jako důvěryhodná připojení) pomáhá poskytovat ochranu při připojování k serveru SQL Server, protože nezveřejňuje ID uživatele a heslo v připojovacím řetězci a je doporučenou metodou ověřování připojení.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="3dd0d-130">Integrované zabezpečení používá aktuální identitu zabezpečení nebo token vykonávajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="3dd0d-131">Pro desktopové aplikace se obvykle jedná o identitu aktuálně přihlášeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="3dd0d-132">Identitu zabezpečení pro aplikace ASP.NET lze nastavit na jednu z několika různých možností.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="3dd0d-133">Chcete-li lépe porozumět identitě zabezpečení, kterou aplikace ASP.NET používá při připojování k serveru SQL Server, [přečtěte si ASP.NET zosobnění](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET ověřování](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100))a [postup: Přístup k serveru SQL Server pomocí integrovaného zabezpečení systému Windows](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3dd0d-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), and [How to: Access SQL Server Using Windows Integrated Security](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="3dd0d-134">Připojení ke zdroji dat technologie OLE DB</span><span class="sxs-lookup"><span data-stu-id="3dd0d-134">Connecting to an OLE DB Data Source</span></span>  
 <span data-ttu-id="3dd0d-135">Zprostředkovatel dat rozhraní .NET Framework pro technologie OLE DB poskytuje připojení ke zdrojům dat vystaveným pomocí technologie OLE DB (prostřednictvím SQLOLEDB, zprostředkovatele OLE DB pro SQL Server), pomocí objektu **OleDbConnection.**</span><span class="sxs-lookup"><span data-stu-id="3dd0d-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="3dd0d-136">Pro zprostředkovatele dat rozhraní .NET Framework pro technologie OLE DB je formát připojovacího řetězce shodný s formátem připojovacího řetězce používaným v objektu ADO s následujícími výjimkami:</span><span class="sxs-lookup"><span data-stu-id="3dd0d-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
- <span data-ttu-id="3dd0d-137">Je vyžadováno klíčové slovo **Zprostředkovatel.**</span><span class="sxs-lookup"><span data-stu-id="3dd0d-137">The **Provider** keyword is required.</span></span>  
  
- <span data-ttu-id="3dd0d-138">Klíčová slova **URL**, **Vzdáleného zprostředkovatele**a **Vzdáleného serveru** nejsou podporována.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="3dd0d-139">Další informace o připojovacích <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> řetězcích TECHNOLOGIE OLE DB naleznete v tématu.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="3dd0d-140">Můžete také vytvořit <xref:System.Data.OleDb.OleDbConnectionStringBuilder> připojovací řetězce za běhu.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3dd0d-141">Objekt **OleDbConnection** nepodporuje nastavení nebo načítání dynamických vlastností specifických pro zprostředkovatele TECHNOLOGIE OLE DB.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="3dd0d-142">Podporovány jsou pouze vlastnosti, které mohou být předány v připojovacím řetězci pro zprostředkovatele TECHNOLOGIE OLE DB.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="3dd0d-143">Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení ke zdroji dat TECHNOLOGIE OLE DB.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="3dd0d-144">Nepoužívejte soubory univerzálního datového propojení</span><span class="sxs-lookup"><span data-stu-id="3dd0d-144">Do Not Use Universal Data Link Files</span></span>  
 <span data-ttu-id="3dd0d-145">Je možné zadat informace o připojení pro **OleDbConnection** v souboru Univerzální datové spojení (UDL). nicméně byste se měli vyhnout tomu.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="3dd0d-146">UDL soubory nejsou šifrovány a vystavit informace o připojovacím řetězci ve prostém textu.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="3dd0d-147">Vzhledem k tomu, že soubor UDL je externí prostředek založený na souboru pro vaši aplikaci, nelze jej zabezpečit pomocí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="3dd0d-148">Připojení ke zdroji dat ODBC</span><span class="sxs-lookup"><span data-stu-id="3dd0d-148">Connecting to an ODBC Data Source</span></span>  
 <span data-ttu-id="3dd0d-149">Zprostředkovatel dat rozhraní .NET Framework pro rozhraní ODBC poskytuje připojení ke zdrojům dat vystaveným pomocí rozhraní ODBC pomocí objektu **OdbcConnection.**</span><span class="sxs-lookup"><span data-stu-id="3dd0d-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="3dd0d-150">Pro zprostředkovatele dat rozhraní .NET Framework pro rozhraní ODBC je formát připojovacího řetězce navržen tak, aby co nejvíce odpovídal formátu připojovacího řetězce ODBC.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="3dd0d-151">Můžete také zadat název zdroje dat ODBC (DSN).</span><span class="sxs-lookup"><span data-stu-id="3dd0d-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="3dd0d-152">Další podrobnosti o **připojení OdbcConnection** naleznete v tématu <xref:System.Data.Odbc.OdbcConnection>.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="3dd0d-153">Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení ke zdroji dat ODBC.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="3dd0d-154">Připojení ke zdroji dat Oracle</span><span class="sxs-lookup"><span data-stu-id="3dd0d-154">Connecting to an Oracle Data Source</span></span>  
 <span data-ttu-id="3dd0d-155">Zprostředkovatel dat rozhraní .NET Framework pro oracle poskytuje připojení ke zdrojům dat Oracle pomocí objektu **OracleConnection.**</span><span class="sxs-lookup"><span data-stu-id="3dd0d-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="3dd0d-156">Pro zprostředkovatele dat rozhraní .NET Framework pro oracle je formát připojovacího řetězce navržen tak, aby co nejvíce odpovídal formátu připojovacího řetězce OLE DB Provider for Oracle (MSDAORA).</span><span class="sxs-lookup"><span data-stu-id="3dd0d-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="3dd0d-157">Další podrobnosti o **řešení OracleConnection**naleznete v tématu <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="3dd0d-158">Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení ke zdroji dat Oracle.</span><span class="sxs-lookup"><span data-stu-id="3dd0d-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3dd0d-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="3dd0d-159">See also</span></span>

- [<span data-ttu-id="3dd0d-160">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="3dd0d-160">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="3dd0d-161">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="3dd0d-161">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="3dd0d-162">Sdružování připojení OLE DB, ODBC a Oracle</span><span class="sxs-lookup"><span data-stu-id="3dd0d-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- [<span data-ttu-id="3dd0d-163">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3dd0d-163">ADO.NET Overview</span></span>](ado-net-overview.md)
