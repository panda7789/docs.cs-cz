---
title: Navazování připojení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: c4e782b670bfc74a651ce38457c05d9acfcf0e8c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783907"
---
# <a name="establishing-the-connection"></a><span data-ttu-id="39c38-102">Navazování připojení</span><span class="sxs-lookup"><span data-stu-id="39c38-102">Establishing the Connection</span></span>
<span data-ttu-id="39c38-103">Chcete-li se připojit k Microsoft SQL Server <xref:System.Data.SqlClient.SqlConnection> , použijte pro SQL Server objekt zprostředkovatel dat .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39c38-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="39c38-104">Chcete-li se připojit k OLE DB zdroji dat, <xref:System.Data.OleDb.OleDbConnection> použijte pro OLE DB objekt zprostředkovatel dat .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39c38-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="39c38-105">Chcete-li se připojit ke zdroji dat ODBC, <xref:System.Data.Odbc.OdbcConnection> použijte objekt zprostředkovatel dat .NET Framework pro rozhraní ODBC.</span><span class="sxs-lookup"><span data-stu-id="39c38-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="39c38-106">Chcete-li se připojit ke zdroji dat Oracle, <xref:System.Data.OracleClient.OracleConnection> použijte objekt zprostředkovatel dat .NET Framework pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="39c38-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="39c38-107">Informace o bezpečném ukládání a načítání připojovacích řetězců najdete v tématu [ochrana informací o připojení](protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="39c38-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="39c38-108">Uzavírání připojení</span><span class="sxs-lookup"><span data-stu-id="39c38-108">Closing Connections</span></span>  
 <span data-ttu-id="39c38-109">Doporučujeme, abyste připojení vždy zavřeli, až ho budete používat, aby bylo možné připojení vrátit do fondu.</span><span class="sxs-lookup"><span data-stu-id="39c38-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="39c38-110">Blok v Visual Basic nebo C# automaticky odstraní připojení, když kód ukončí blok, i v případě neošetřené výjimky. `Using`</span><span class="sxs-lookup"><span data-stu-id="39c38-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="39c38-111">Další informace naleznete v tématu [using Statement](../../../csharp/language-reference/keywords/using-statement.md) a [using příkaz using](../../../visual-basic/language-reference/statements/using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="39c38-111">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) and [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="39c38-112">Můžete také použít `Close` metody nebo `Dispose` objektu Connection pro poskytovatele, kterého používáte.</span><span class="sxs-lookup"><span data-stu-id="39c38-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="39c38-113">Nemusejí být do fondu přidány ani vráceny připojení, která nejsou explicitně zavřena.</span><span class="sxs-lookup"><span data-stu-id="39c38-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="39c38-114">Například připojení, které se odchází z oboru, ale které nebylo explicitně uzavřeno, bude vráceno do fondu připojení pouze v případě, že byla dosažena maximální velikost fondu a připojení je stále platné.</span><span class="sxs-lookup"><span data-stu-id="39c38-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="39c38-115">Další informace najdete v tématu [sdružování připojení OLE DB, ODBC a Oracle](ole-db-odbc-and-oracle-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="39c38-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39c38-116">Nevolejte `Close` ani `Dispose` na **připojení**, objekt **DataReader**nebo žádný jiný spravovaný objekt v `Finalize` metodě vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="39c38-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="39c38-117">V finalizační metodě pouze uvolní nespravované prostředky, které vaše třída vlastní.</span><span class="sxs-lookup"><span data-stu-id="39c38-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="39c38-118">Pokud vaše třída nevlastní žádné nespravované prostředky, `Finalize` nezahrnujte metodu do definice třídy.</span><span class="sxs-lookup"><span data-stu-id="39c38-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="39c38-119">Další informace najdete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="39c38-119">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39c38-120">Události přihlášení a odhlášení nebudou na serveru vyvolány, když je připojení načteno z nebo vráceno do fondu připojení, protože připojení není ve skutečnosti při návratu do fondu připojení ukončeno.</span><span class="sxs-lookup"><span data-stu-id="39c38-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="39c38-121">Další informace najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="39c38-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="39c38-122">Připojování k SQL Server</span><span class="sxs-lookup"><span data-stu-id="39c38-122">Connecting to SQL Server</span></span>  
 <span data-ttu-id="39c38-123">Zprostředkovatel dat .NET Framework pro SQL Server podporuje formát připojovacího řetězce, který se podobá formátu připojovacího řetězce OLE DB (ADO).</span><span class="sxs-lookup"><span data-stu-id="39c38-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="39c38-124">Platný název a hodnoty formátu řetězce naleznete <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> v vlastnosti <xref:System.Data.SqlClient.SqlConnection> objektu.</span><span class="sxs-lookup"><span data-stu-id="39c38-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="39c38-125">Můžete také použít <xref:System.Data.SqlClient.SqlConnectionStringBuilder> třídu k vytvoření syntakticky platných připojovacích řetězců za běhu.</span><span class="sxs-lookup"><span data-stu-id="39c38-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="39c38-126">Další informace najdete v tématu [tvůrci připojovacích řetězců](connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="39c38-126">For more information, see [Connection String Builders](connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="39c38-127">Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení k databázi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="39c38-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
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
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="39c38-128">Integrované zabezpečení a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="39c38-128">Integrated Security and ASP.NET</span></span>  
 <span data-ttu-id="39c38-129">SQL Server integrované zabezpečení (označované také jako důvěryhodná připojení) pomáhá zajistit ochranu při připojení k SQL Server, protože nezveřejňuje ID uživatele a heslo v připojovacím řetězci a je doporučenou metodou pro ověřování připojení.</span><span class="sxs-lookup"><span data-stu-id="39c38-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="39c38-130">Integrované zabezpečení používá aktuální identitu zabezpečení nebo token spuštěného procesu.</span><span class="sxs-lookup"><span data-stu-id="39c38-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="39c38-131">U aplikací klasické pracovní plochy se obvykle jedná o identitu aktuálně přihlášeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="39c38-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="39c38-132">Identita zabezpečení pro aplikace ASP.NET může být nastavená na jednu z několika různých možností.</span><span class="sxs-lookup"><span data-stu-id="39c38-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="39c38-133">Pro lepší pochopení identity zabezpečení, kterou aplikace ASP.NET používá při připojování k SQL Server, přečtěte si téma [ASP.NET Impersonation](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100))a [How to: Přístup k SQL Server s využitím](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100))integrovaného zabezpečení systému Windows.</span><span class="sxs-lookup"><span data-stu-id="39c38-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), and [How to: Access SQL Server Using Windows Integrated Security](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="39c38-134">Připojení k OLE DBmu zdroji dat</span><span class="sxs-lookup"><span data-stu-id="39c38-134">Connecting to an OLE DB Data Source</span></span>  
 <span data-ttu-id="39c38-135">Zprostředkovatel dat .NET Framework pro OLE DB poskytuje připojení ke zdrojům dat vystaveným pomocí OLE DB (prostřednictvím SQLOLEDB, poskytovatele OLE DB pro SQL Server) pomocí objektu **OleDbConnection** .</span><span class="sxs-lookup"><span data-stu-id="39c38-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="39c38-136">Pro .NET Framework Zprostředkovatel dat pro OLE DB je formát připojovacího řetězce totožný s formátem připojovacího řetězce používaným v objektech ADO, s následujícími výjimkami:</span><span class="sxs-lookup"><span data-stu-id="39c38-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
- <span data-ttu-id="39c38-137">Klíčové slovo **Provider** je povinné.</span><span class="sxs-lookup"><span data-stu-id="39c38-137">The **Provider** keyword is required.</span></span>  
  
- <span data-ttu-id="39c38-138">Klíčová slova **URL**, **vzdálený zprostředkovatel**a **vzdálené servery** nejsou podporovaná.</span><span class="sxs-lookup"><span data-stu-id="39c38-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="39c38-139">Další informace o OLE DB připojovacích řetězcích naleznete <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> v tématu.</span><span class="sxs-lookup"><span data-stu-id="39c38-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="39c38-140">Můžete také použít <xref:System.Data.OleDb.OleDbConnectionStringBuilder> k vytvoření připojovacích řetězců v době běhu.</span><span class="sxs-lookup"><span data-stu-id="39c38-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39c38-141">Objekt **OleDbConnection** nepodporuje nastavení nebo načítání dynamických vlastností specifických pro poskytovatele OLE DB.</span><span class="sxs-lookup"><span data-stu-id="39c38-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="39c38-142">Jsou podporovány pouze vlastnosti, které lze předat v připojovacím řetězci pro poskytovatele OLE DB.</span><span class="sxs-lookup"><span data-stu-id="39c38-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="39c38-143">Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení k OLE DBmu zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="39c38-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="39c38-144">Nepoužívejte soubory Universal Data Link</span><span class="sxs-lookup"><span data-stu-id="39c38-144">Do Not Use Universal Data Link Files</span></span>  
 <span data-ttu-id="39c38-145">V souboru UDL (Universal Data Link) je možné zadávat informace o připojení pro **OleDbConnection** . měli byste se ale vyhnout.</span><span class="sxs-lookup"><span data-stu-id="39c38-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="39c38-146">Soubory UDL nejsou zašifrované a zveřejňují informace připojovacího řetězce ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="39c38-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="39c38-147">Vzhledem k tomu, že soubor UDL je externí prostředek založený na souboru, nelze jej zabezpečit pomocí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39c38-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="39c38-148">Připojení ke zdroji dat ODBC</span><span class="sxs-lookup"><span data-stu-id="39c38-148">Connecting to an ODBC Data Source</span></span>  
 <span data-ttu-id="39c38-149">Zprostředkovatel dat .NET Framework pro rozhraní ODBC poskytuje připojení ke zdrojům dat vystaveným pomocí rozhraní ODBC pomocí objektu **OdbcConnection** .</span><span class="sxs-lookup"><span data-stu-id="39c38-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="39c38-150">Pro Zprostředkovatel dat .NET Framework pro rozhraní ODBC je formát připojovacího řetězce navržen tak, aby co nejpřesněji odpovídal formátu připojovacího řetězce ODBC.</span><span class="sxs-lookup"><span data-stu-id="39c38-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="39c38-151">Můžete také uvést název zdroje dat ODBC (DSN).</span><span class="sxs-lookup"><span data-stu-id="39c38-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="39c38-152">Další podrobnosti o **OdbcConnection** najdete v tématu <xref:System.Data.Odbc.OdbcConnection>.</span><span class="sxs-lookup"><span data-stu-id="39c38-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="39c38-153">Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení ke zdroji dat ODBC.</span><span class="sxs-lookup"><span data-stu-id="39c38-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="39c38-154">Připojení ke zdroji dat Oracle</span><span class="sxs-lookup"><span data-stu-id="39c38-154">Connecting to an Oracle Data Source</span></span>  
 <span data-ttu-id="39c38-155">Zprostředkovatel dat .NET Framework pro Oracle poskytuje připojení ke zdrojům dat Oracle pomocí objektu **OracleConnection** .</span><span class="sxs-lookup"><span data-stu-id="39c38-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="39c38-156">Pro Zprostředkovatel dat .NET Framework pro Oracle je formát připojovacího řetězce navržený tak, aby co nejpřesněji odpovídal formátu připojovacího řetězce Oracle (MADAORA) poskytovatele OLE DB.</span><span class="sxs-lookup"><span data-stu-id="39c38-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="39c38-157">Další podrobnosti o **OracleConnection**najdete v tématu <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="39c38-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="39c38-158">Následující příklad kódu ukazuje, jak vytvořit a otevřít připojení ke zdroji dat Oracle.</span><span class="sxs-lookup"><span data-stu-id="39c38-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39c38-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39c38-159">See also</span></span>

- [<span data-ttu-id="39c38-160">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="39c38-160">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="39c38-161">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="39c38-161">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="39c38-162">Sdružování připojení OLE DB, ODBC a Oracle</span><span class="sxs-lookup"><span data-stu-id="39c38-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- [<span data-ttu-id="39c38-163">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="39c38-163">ADO.NET Overview</span></span>](ado-net-overview.md)
