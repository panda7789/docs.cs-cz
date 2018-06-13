---
title: Asynchronní programování
ms.date: 03/30/2017
ms.assetid: 85da7447-7125-426e-aa5f-438a290d1f77
ms.openlocfilehash: 29324a07ffdaf99d1b7631ad8e94e773ed509fcc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759904"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="49fd6-102">Asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="49fd6-102">Asynchronous Programming</span></span>

<span data-ttu-id="49fd6-103">Toto téma popisuje podporu pro asynchronní programování v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server (SqlClient) včetně vylepšení pro podporu asynchronní programování funkcí, které se zavedly v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49fd6-103">This topic discusses support for asynchronous programming in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server (SqlClient) including enhancements made to support asynchronous programming functionality that was introduced in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="legacy-asynchronous-programming"></a><span data-ttu-id="49fd6-104">Starší verze asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="49fd6-104">Legacy Asynchronous Programming</span></span>  
 <span data-ttu-id="49fd6-105">Před verzí [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], asynchronní programování s SqlClient bylo provedeno pomocí následujících metod a `Asynchronous Processing=true` vlastnost připojení:</span><span class="sxs-lookup"><span data-stu-id="49fd6-105">Prior to [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], asynchronous programming with SqlClient was done with the following methods and the `Asynchronous Processing=true` connection property:</span></span>  
  
1.  <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="49fd6-106">Tato funkce zůstane v SqlClient v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49fd6-106">This functionality remains in SqlClient in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
 <span data-ttu-id="49fd6-107">Počínaje [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], už nebudou potřebovat tyto metody `Asynchronous Processing=true` v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="49fd6-107">Beginning in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], these methods no longer require `Asynchronous Processing=true` in the connection string.</span></span>  
  
## <a name="asynchronous-programming-features-added-in-includenetv45includesnet-v45-mdmd"></a><span data-ttu-id="49fd6-108">Asynchronní programování funkce přidané do [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49fd6-108">Asynchronous Programming Features Added in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]</span></span>  
 <span data-ttu-id="49fd6-109">Nový asynchronní programování funkce poskytuje jednoduché techniku, aby byl kód asynchronní.</span><span class="sxs-lookup"><span data-stu-id="49fd6-109">The new asynchronous programming feature provides a simple technique to make code asynchronous.</span></span>  
  
 <span data-ttu-id="49fd6-110">Další informace o asynchronní programování funkce, která byla zavedena v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], najdete v části:</span><span class="sxs-lookup"><span data-stu-id="49fd6-110">For more information about the asynchronous programming feature that was introduced in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], see:</span></span>  
  
- [<span data-ttu-id="49fd6-111">Asynchronní programování v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="49fd6-111">Asynchronous programming in C#</span></span>](../../../csharp/async.md)

- [<span data-ttu-id="49fd6-112">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49fd6-112">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)

- [<span data-ttu-id="49fd6-113">Použití SqlDataReader na nový asynchronní metody v rozhraní .net 4.5 (část 1)</span><span class="sxs-lookup"><span data-stu-id="49fd6-113">Using SqlDataReader’s new async methods in .Net 4.5 (Part 1)</span></span>](https://blogs.msdn.microsoft.com/adonet/2012/04/20/using-sqldatareaders-new-async-methods-in-net-4-5/)

- [<span data-ttu-id="49fd6-114">Použití SqlDataReader na nový asynchronní metody v rozhraní .net 4.5 (část 2)</span><span class="sxs-lookup"><span data-stu-id="49fd6-114">Using SqlDataReader’s new async methods in .Net 4.5 (Part 2)</span></span>](https://blogs.msdn.microsoft.com/adonet/2012/07/15/using-sqldatareaders-new-async-methods-in-net-4-5-part-2-examples/)
 
 <span data-ttu-id="49fd6-115">Pokud vaše uživatelské rozhraní je reagovat nebo váš server není škálování, je pravděpodobné, je nutné, aby váš kód více asynchronní.</span><span class="sxs-lookup"><span data-stu-id="49fd6-115">When your user interface is unresponsive or your server does not scale, it is likely that you need your code to be more asynchronous.</span></span>  <span data-ttu-id="49fd6-116">Psaní kódu asynchronní má tradičně podílejí instalaci zpětné volání (také nazývané pokračování) express logiky, která nastane po dokončení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="49fd6-116">Writing asynchronous code has traditionally involved installing a callback (also called continuation) to express the logic that occurs after the asynchronous operation finishes.</span></span> <span data-ttu-id="49fd6-117">To komplikuje struktury asynchronní kódu ve srovnání s synchronní kódu.</span><span class="sxs-lookup"><span data-stu-id="49fd6-117">This complicates the structure of asynchronous code as compared with synchronous code.</span></span>  
  
 <span data-ttu-id="49fd6-118">Můžete teď volání do asynchronní metody bez použití zpětná volání a bez rozdělení kódu mezi více metod nebo výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="49fd6-118">You can now call into asynchronous methods without using callbacks, and without splitting your code across multiple methods or lambda expressions.</span></span>  
  
 <span data-ttu-id="49fd6-119">`async` Modifikátor Určuje, že je asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="49fd6-119">The `async` modifier specifies that a method is asynchronous.</span></span> <span data-ttu-id="49fd6-120">Při volání metody `async` metoda, je vrácen úlohu.</span><span class="sxs-lookup"><span data-stu-id="49fd6-120">When calling an `async` method, a task is returned.</span></span> <span data-ttu-id="49fd6-121">Když `await` operátor se použije pro úlohu, aktuální metoda se okamžitě ukončí.</span><span class="sxs-lookup"><span data-stu-id="49fd6-121">When the `await` operator is applied to a task, the current method exits immediately.</span></span> <span data-ttu-id="49fd6-122">Po dokončení této úlohy, provádění pokračuje v stejnou metodu.</span><span class="sxs-lookup"><span data-stu-id="49fd6-122">When the task finishes, execution resumes in the same method.</span></span>
  
> [!WARNING]
>  <span data-ttu-id="49fd6-123">Asynchronní volání nejsou podporovány, pokud aplikace používá také `Context Connection` klíčové slovo připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="49fd6-123">Asynchronous calls are not supported if an application also uses the `Context Connection` connection string keyword.</span></span>  
  
 <span data-ttu-id="49fd6-124">Volání metody `async` metoda nepřidělí žádné další podprocesy.</span><span class="sxs-lookup"><span data-stu-id="49fd6-124">Calling an `async` method does not allocate any additional threads.</span></span> <span data-ttu-id="49fd6-125">Existující vlákno dokončení vstupně-výstupní operace se může používat stručně na konci.</span><span class="sxs-lookup"><span data-stu-id="49fd6-125">It may use the existing I/O completion thread briefly at the end.</span></span>  
  
 <span data-ttu-id="49fd6-126">Byly přidány následující metody v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] pro podporu asynchronní programování:</span><span class="sxs-lookup"><span data-stu-id="49fd6-126">The following methods were added in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] to support asynchronous programming:</span></span>  
  
-   <xref:System.Data.Common.DbConnection.OpenAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbCommand.ExecuteDbDataReaderAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbCommand.ExecuteNonQueryAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbCommand.ExecuteReaderAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbCommand.ExecuteScalarAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbDataReader.GetFieldValueAsync%2A>  
  
-   <xref:System.Data.Common.DbDataReader.IsDBNullAsync%2A>  
  
-   <xref:System.Data.Common.DbDataReader.NextResultAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbDataReader.ReadAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlConnection.OpenAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQueryAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlCommand.ExecuteReaderAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlCommand.ExecuteScalarAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlCommand.ExecuteXmlReaderAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.NextResultAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.ReadAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="49fd6-127">Jiní členové asynchronní byly přidány k podpoře [streamování podporují SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md).</span><span class="sxs-lookup"><span data-stu-id="49fd6-127">Other asynchronous members were added to support [SqlClient Streaming Support](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md).</span></span>  
  
### <a name="synchronous-to-asynchronous-connection-open"></a><span data-ttu-id="49fd6-128">Synchronní a asynchronní připojení otevřete</span><span class="sxs-lookup"><span data-stu-id="49fd6-128">Synchronous to Asynchronous Connection Open</span></span>  
 <span data-ttu-id="49fd6-129">Můžete upgradovat stávající aplikace do používal novou funkci asynchronní.</span><span class="sxs-lookup"><span data-stu-id="49fd6-129">You can upgrade an existing application to use the new asynchronous feature.</span></span> <span data-ttu-id="49fd6-130">Předpokládejme například, aplikace má synchronní připojení algoritmus a blokuje vlákna uživatelského rozhraní pokaždé, když se připojuje k databázi, a po připojení aplikace volání uložené procedury, jež signály jiných uživatelů k tomu, který právě přihlášení.</span><span class="sxs-lookup"><span data-stu-id="49fd6-130">For example, assume an application has a synchronous connection algorithm and blocks the UI thread every time it connects to the database and, once connected, the application calls a stored procedure that signals other users of the one who just signed in.</span></span>  
  
```csharp
using SqlConnection conn = new SqlConnection("…");  
{  
   conn.Open();  
   using (SqlCommand cmd = new SqlCommand("StoredProcedure_Logon", conn))  
   {  
      cmd.ExecuteNonQuery();  
   }  
}  
```  
  
 <span data-ttu-id="49fd6-131">Při převodu používat nové funkce, asynchronní, bude vypadat program:</span><span class="sxs-lookup"><span data-stu-id="49fd6-131">When converted to use the new asynchronous functionality, the program would look like:</span></span>  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class A {  
  
   static async Task<int> Method(SqlConnection conn, SqlCommand cmd) {  
      await conn.OpenAsync();  
      await cmd.ExecuteNonQueryAsync();  
      return 1;  
   }  
  
   public static void Main() {  
      using (SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI")) {  
         SqlCommand command = new SqlCommand("select top 2 * from orders", conn);  
  
         int result = A.Method(conn, command).Result;  
  
         SqlDataReader reader = command.ExecuteReader();  
         while (reader.Read())  
            Console.WriteLine(String.Format("{0}", reader[0]));  
      }  
   }  
}  
```  
  
### <a name="adding-the-new-asynchronous-feature-in-an-existing-application-mixing-old-and-new-patterns"></a><span data-ttu-id="49fd6-132">Přidání nové asynchronní funkce do stávající aplikace (kombinací staré a nové vzory)</span><span class="sxs-lookup"><span data-stu-id="49fd6-132">Adding the New Asynchronous Feature in an Existing Application (Mixing Old and New Patterns)</span></span>  
 <span data-ttu-id="49fd6-133">Je také možné přidat novou funkci asynchronní (SqlConnection::OpenAsync) beze změny existujícího asynchronní logiku.</span><span class="sxs-lookup"><span data-stu-id="49fd6-133">It is also possible to add new asynchronous capability (SqlConnection::OpenAsync) without changing the existing asynchronous logic.</span></span> <span data-ttu-id="49fd6-134">Například pokud aplikace v současné době používá:</span><span class="sxs-lookup"><span data-stu-id="49fd6-134">For example, if an application currently uses:</span></span>  
  
```csharp
AsyncCallback productList = new AsyncCallback(ProductList);  
SqlConnection conn = new SqlConnection("…");  
conn.Open();  
SqlCommand cmd = new SqlCommand("SELECT * FROM [Current Product List]", conn);  
IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);  
```  
  
 <span data-ttu-id="49fd6-135">Můžete začít používat nový asynchronní vzor bez podstatně Změna existující algoritmus.</span><span class="sxs-lookup"><span data-stu-id="49fd6-135">You can begin to use the new asynchronous pattern without substantially changing the existing algorithm.</span></span>  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class A {  
   static void ProductList(IAsyncResult result) { }  
  
   public static void Main() {  
      // AsyncCallback productList = new AsyncCallback(ProductList);  
      // SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI");  
      // conn.Open();  
      // SqlCommand cmd = new SqlCommand("select top 2 * from orders", conn);  
      // IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);  
  
      AsyncCallback productList = new AsyncCallback(ProductList);  
      SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI");  
      conn.OpenAsync().ContinueWith((task) => {  
         SqlCommand cmd = new SqlCommand("select top 2 * from orders", conn);  
         IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);  
      }, TaskContinuationOptions.OnlyOnRanToCompletion);  
   }  
}  
```  
  
### <a name="using-the-base-provider-model-and-the-new-asynchronous-feature"></a><span data-ttu-id="49fd6-136">Pomocí modelu základní zprostředkovatel a nový asynchronní funkce</span><span class="sxs-lookup"><span data-stu-id="49fd6-136">Using the Base Provider Model and the New Asynchronous Feature</span></span>  
 <span data-ttu-id="49fd6-137">Musíte vytvořit nástroj, který je možné připojit do různých databází a spouštět dotazy.</span><span class="sxs-lookup"><span data-stu-id="49fd6-137">You may need to create a tool that is able to connect to different databases and execute queries.</span></span> <span data-ttu-id="49fd6-138">Můžete použít v modelu základní zprostředkovatel a nová funkce pro asynchronní.</span><span class="sxs-lookup"><span data-stu-id="49fd6-138">You can use the base provider model and the new asynchronous feature.</span></span>  
  
 <span data-ttu-id="49fd6-139">Microsoft řadiče pro distribuované transakce (MSDTC) musí na serveru povolený distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="49fd6-139">The Microsoft Distributed Transaction Controller (MSDTC) must be enabled on the server to use distributed transactions.</span></span> <span data-ttu-id="49fd6-140">Informace o tom, jak povolit služby MSDTC najdete v tématu [postup povolení služby MSDTC na webovém serveru](http://msdn.microsoft.com/library/dd327979.aspx).</span><span class="sxs-lookup"><span data-stu-id="49fd6-140">For information on how to enable MSDTC, see [How to Enable MSDTC on a Web Server](http://msdn.microsoft.com/library/dd327979.aspx).</span></span>  
  
```csharp
using System;  
using System.Data.Common;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class A {  
   static async Task PerformDBOperationsUsingProviderModel(string connectionString, string providerName) {  
      DbProviderFactory factory = DbProviderFactories.GetFactory(providerName);  
      using (DbConnection connection = factory.CreateConnection()) {  
         connection.ConnectionString = connectionString;  
         await connection.OpenAsync();  
  
         DbCommand command = connection.CreateCommand();  
         command.CommandText = "SELECT * FROM AUTHORS";  
  
         using (DbDataReader reader = await command.ExecuteReaderAsync()) {  
            while (await reader.ReadAsync()) {  
               for (int i = 0; i < reader.FieldCount; i++) {  
                  // Process each column as appropriate  
                  object obj = await reader.GetFieldValueAsync<object>(i);  
                  Console.WriteLine(obj);  
               }  
            }  
         }  
      }  
   }  
  
   public static void Main()   
   {  
       SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder();  
       // replace these with your own values  
       builder.DataSource = "your_server";  
       builder.InitialCatalog = "pubs";  
       builder.IntegratedSecurity = true;  
       string provider = "System.Data.SqlClient";  
  
       Task task = PerformDBOperationsUsingProviderModel(builder.ConnectionString, provider);  
       task.Wait();  
   }  
}  
```  
  
### <a name="using-sql-transactions-and-the-new-asynchronous-feature"></a><span data-ttu-id="49fd6-141">Použití transakcí SQL a nový asynchronní funkce</span><span class="sxs-lookup"><span data-stu-id="49fd6-141">Using SQL Transactions and the New Asynchronous Feature</span></span>  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class Program {  
   static void Main() {  
      string connectionString =  
          "Persist Security Info=False;Integrated Security=SSPI;database=Northwind;server=(local)";  
      Task task = ExecuteSqlTransaction(connectionString);  
      task.Wait();  
   }  
  
   static async Task ExecuteSqlTransaction(string connectionString) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         await connection.OpenAsync();  
  
         SqlCommand command = connection.CreateCommand();  
         SqlTransaction transaction = null;  
  
         // Start a local transaction.  
         transaction = await Task.Run<SqlTransaction>(  
             () => connection.BeginTransaction("SampleTransaction")  
             );  
  
         // Must assign both transaction object and connection  
         // to Command object for a pending local transaction  
         command.Connection = connection;  
         command.Transaction = transaction;  
  
         try {  
            command.CommandText =  
                "Insert into Region (RegionID, RegionDescription) VALUES (555, 'Description')";  
            await command.ExecuteNonQueryAsync();  
  
            command.CommandText =  
                "Insert into Region (RegionID, RegionDescription) VALUES (556, 'Description')";  
            await command.ExecuteNonQueryAsync();  
  
            // Attempt to commit the transaction.  
            await Task.Run(() => transaction.Commit());  
            Console.WriteLine("Both records are written to database.");  
         }  
         catch (Exception ex) {  
            Console.WriteLine("Commit Exception Type: {0}", ex.GetType());  
            Console.WriteLine("  Message: {0}", ex.Message);  
  
            // Attempt to roll back the transaction.  
            try {  
               transaction.Rollback();  
            }  
            catch (Exception ex2) {  
               // This catch block will handle any errors that may have occurred  
               // on the server that would cause the rollback to fail, such as  
               // a closed connection.  
               Console.WriteLine("Rollback Exception Type: {0}", ex2.GetType());  
               Console.WriteLine("  Message: {0}", ex2.Message);  
            }  
         }  
      }  
   }  
}  
```  
  
### <a name="using-sql-transactions-and-the-new-asynchronous-feature"></a><span data-ttu-id="49fd6-142">Použití transakcí SQL a nový asynchronní funkce</span><span class="sxs-lookup"><span data-stu-id="49fd6-142">Using SQL Transactions and the New Asynchronous Feature</span></span>  
 <span data-ttu-id="49fd6-143">V podniková aplikace musíte přidat distribuovaných transakcí v některých scénářích, chcete-li povolit transakce mezi více servery databáze.</span><span class="sxs-lookup"><span data-stu-id="49fd6-143">In an enterprise application, you may need to add distributed transactions in some scenarios, to enable transactions between multiple database servers.</span></span> <span data-ttu-id="49fd6-144">Můžete použít System.Transactions – obor názvů a zařazení distribuované transakce, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="49fd6-144">You can use the System.Transactions namespace and enlist a distributed transaction, as follows:</span></span>  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
using System.Transactions;  
  
class Program {  
   public static void Main()   
   {  
       SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder();  
       // replace these with your own values  
       builder.DataSource = "your_server";  
       builder.InitialCatalog = "your_data_source";  
       builder.IntegratedSecurity = true;  
  
       Task task = ExecuteDistributedTransaction(builder.ConnectionString, builder.ConnectionString);  
       task.Wait();  
   }  
  
   static async Task ExecuteDistributedTransaction(string connectionString1, string connectionString2) {  
      using (SqlConnection connection1 = new SqlConnection(connectionString1))  
      using (SqlConnection connection2 = new SqlConnection(connectionString2)) {  
         using (CommittableTransaction transaction = new CommittableTransaction()) {  
            await connection1.OpenAsync();  
            connection1.EnlistTransaction(transaction);  
  
            await connection2.OpenAsync();  
            connection2.EnlistTransaction(transaction);  
  
            try {  
               SqlCommand command1 = connection1.CreateCommand();  
               command1.CommandText = "Insert into RegionTable1 (RegionID, RegionDescription) VALUES (100, 'Description')";  
               await command1.ExecuteNonQueryAsync();  
  
               SqlCommand command2 = connection2.CreateCommand();  
               command2.CommandText = "Insert into RegionTable2 (RegionID, RegionDescription) VALUES (100, 'Description')";  
               await command2.ExecuteNonQueryAsync();  
  
               transaction.Commit();  
            }  
            catch (Exception ex) {  
               Console.WriteLine("Exception Type: {0}", ex.GetType());  
               Console.WriteLine("  Message: {0}", ex.Message);  
  
               try {  
                  transaction.Rollback();  
               }  
               catch (Exception ex2) {  
                  Console.WriteLine("Rollback Exception Type: {0}", ex2.GetType());  
                  Console.WriteLine("  Message: {0}", ex2.Message);  
               }  
            }  
         }  
      }  
   }  
}  
```  
  
### <a name="cancelling-an-asynchronous-operation"></a><span data-ttu-id="49fd6-145">Zrušení asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="49fd6-145">Cancelling an Asynchronous Operation</span></span>  
 <span data-ttu-id="49fd6-146">Asynchronní požadavek můžete zrušit pomocí <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="49fd6-146">You can cancel an asynchronous request by using the <xref:System.Threading.CancellationToken>.</span></span>  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading;  
using System.Threading.Tasks;  
  
namespace Samples {  
   class CancellationSample {  
      public static void Main(string[] args) {  
         CancellationTokenSource source = new CancellationTokenSource();  
         source.CancelAfter(2000); // give up after 2 seconds  
         try {  
            Task result = CancellingAsynchronousOperations(source.Token);  
            result.Wait();  
         }  
         catch (AggregateException exception) {  
            if (exception.InnerException is SqlException) {  
               Console.WriteLine("Operation canceled");  
            }  
            else {  
               throw;  
            }  
         }  
      }  
  
      static async Task CancellingAsynchronousOperations(CancellationToken cancellationToken) {  
         using (SqlConnection connection = new SqlConnection("Server=(local);Integrated Security=true")) {  
            await connection.OpenAsync(cancellationToken);  
  
            SqlCommand command = new SqlCommand("WAITFOR DELAY '00:10:00'", connection);  
            await command.ExecuteNonQueryAsync(cancellationToken);  
         }  
      }  
   }  
}  
```  
  
### <a name="asynchronous-operations-with-sqlbulkcopy"></a><span data-ttu-id="49fd6-147">Asynchronní operace s SqlBulkCopy.</span><span class="sxs-lookup"><span data-stu-id="49fd6-147">Asynchronous Operations with SqlBulkCopy</span></span>  
 <span data-ttu-id="49fd6-148">Asynchronní funkce byly také přidány do <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType> s <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="49fd6-148">Asynchronous capabilities were also added to <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType> with <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.Odbc;  
using System.Data.SqlClient;  
using System.Linq;  
using System.Text;  
using System.Threading;  
using System.Threading.Tasks;  
  
namespace SqlBulkCopyAsyncCodeSample {  
   class Program {  
      static string selectStatment = "SELECT * FROM [pubs].[dbo].[titles]";  
      static string createDestTableStatement =  
          @"CREATE TABLE {0} (  
            [title_id] [varchar](6) NOT NULL,  
            [title] [varchar](80) NOT NULL,  
            [type] [char](12) NOT NULL,  
            [pub_id] [char](4) NULL,  
            [price] [money] NULL,  
            [advance] [money] NULL,  
            [royalty] [int] NULL,  
            [ytd_sales] [int] NULL,  
            [notes] [varchar](200) NULL,  
            [pubdate] [datetime] NOT NULL)";  
  
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo;Integrated Security=true"  
      // static string connectionString = @"Server=(localdb)\V11.0;Database=Demo";  
      static string connectionString = @"Server=(local);Database=Demo;Integrated Security=true";  
  
      // static string odbcConnectionString = @"Driver={SQL Server};Server=(localdb)\V11.0;UID=oledb;Pwd=1Password!;Database=Demo";  
      static string odbcConnectionString = @"Driver={SQL Server};Server=(local);Database=Demo;Integrated Security=true";  
  
      // static string marsConnectionString = @"Server=(localdb)\V11.0;Database=Demo;MultipleActiveResultSets=true;";  
      static string marsConnectionString = @"Server=(local);Database=Demo;MultipleActiveResultSets=true;Integrated Security=true";  
  
      // Replace the Server name with your actual sql azure server name and User ID/Password  
      static string azureConnectionString = @"Server=SqlAzure;User ID=myUserID;Password=myPassword;Database=Demo";  
  
      static void Main(string[] args) {  
         SynchronousSqlBulkCopy();  
         AsyncSqlBulkCopy().Wait();  
         MixSyncAsyncSqlBulkCopy().Wait();  
         AsyncSqlBulkCopyNotifyAfter().Wait();  
         AsyncSqlBulkCopyDataRows().Wait();  
         // AsyncSqlBulkCopySqlServerToSqlAzure().Wait();  
         // AsyncSqlBulkCopyCancel().Wait();  
         AsyncSqlBulkCopyMARS().Wait();  
      }  
  
      // 3.1.1 Synchronous bulk copy in .NET 4.5  
      private static void SynchronousSqlBulkCopy() {  
         using (SqlConnection conn = new SqlConnection(connectionString)) {  
            conn.Open();  
            DataTable dt = new DataTable();  
            using (SqlCommand cmd = new SqlCommand(selectStatment, conn)) {  
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);  
               adapter.Fill(dt);  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               cmd.CommandText = string.Format(createDestTableStatement, temptable);  
               cmd.ExecuteNonQuery();  
  
               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                  bcp.DestinationTableName = temptable;  
                  bcp.WriteToServer(dt);  
               }  
            }  
         }  
  
      }  
  
      // 3.1.2 Asynchrounous bulk copy in .NET 4.5  
      private static async Task AsyncSqlBulkCopy() {  
         using (SqlConnection conn = new SqlConnection(connectionString)) {  
            await conn.OpenAsync();  
            DataTable dt = new DataTable();  
            using (SqlCommand cmd = new SqlCommand(selectStatment, conn)) {  
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);  
               adapter.Fill(dt);  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               cmd.CommandText = string.Format(createDestTableStatement, temptable);  
               await cmd.ExecuteNonQueryAsync();  
  
               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                  bcp.DestinationTableName = temptable;  
                  await bcp.WriteToServerAsync(dt);  
               }  
            }  
         }  
      }  
  
      // 3.2 Add new Async.NET capabilities in an existing application (Mixing synchronous and asynchornous calls)  
      private static async Task MixSyncAsyncSqlBulkCopy() {  
         using (OdbcConnection odbcconn = new OdbcConnection(odbcConnectionString)) {  
            odbcconn.Open();  
            using (OdbcCommand odbccmd = new OdbcCommand(selectStatment, odbcconn)) {  
               using (OdbcDataReader odbcreader = odbccmd.ExecuteReader()) {  
                  using (SqlConnection conn = new SqlConnection(connectionString)) {  
                     await conn.OpenAsync();  
                     string temptable = "temptable";//"[#" + Guid.NewGuid().ToString("N") + "]";  
                     SqlCommand createCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), conn);  
                     await createCmd.ExecuteNonQueryAsync();  
                     using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                        bcp.DestinationTableName = temptable;  
                        await bcp.WriteToServerAsync(odbcreader);  
                     }  
                  }  
               }  
            }  
         }  
      }  
  
      // 3.3 Using the NotifyAfter property  
      private static async Task AsyncSqlBulkCopyNotifyAfter() {  
         using (SqlConnection conn = new SqlConnection(connectionString)) {  
            await conn.OpenAsync();  
            DataTable dt = new DataTable();  
            using (SqlCommand cmd = new SqlCommand(selectStatment, conn)) {  
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);  
               adapter.Fill(dt);  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               cmd.CommandText = string.Format(createDestTableStatement, temptable);  
               await cmd.ExecuteNonQueryAsync();  
  
               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                  bcp.DestinationTableName = temptable;  
                  bcp.NotifyAfter = 5;  
                  bcp.SqlRowsCopied += new SqlRowsCopiedEventHandler(OnSqlRowsCopied);  
                  await bcp.WriteToServerAsync(dt);  
               }  
            }  
         }  
      }  
  
      private static void OnSqlRowsCopied(object sender, SqlRowsCopiedEventArgs e) {  
         Console.WriteLine("Copied {0} so far...", e.RowsCopied);  
      }  
  
      // 3.4 Using the new SqlBulkCopy Async.NET capabilities with DataRow[]  
      private static async Task AsyncSqlBulkCopyDataRows() {  
         using (SqlConnection conn = new SqlConnection(connectionString)) {  
            await conn.OpenAsync();  
            DataTable dt = new DataTable();  
            using (SqlCommand cmd = new SqlCommand(selectStatment, conn)) {  
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);  
               adapter.Fill(dt);  
               DataRow[] rows = dt.Select();  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               cmd.CommandText = string.Format(createDestTableStatement, temptable);  
               await cmd.ExecuteNonQueryAsync();  
  
               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                  bcp.DestinationTableName = temptable;  
                  await bcp.WriteToServerAsync(rows);  
               }  
            }  
         }  
      }  
  
      // 3.5 Copying data from SQL Server to SQL Azure in .NET 4.5  
      //private static async Task AsyncSqlBulkCopySqlServerToSqlAzure() {  
      //   using (SqlConnection srcConn = new SqlConnection(connectionString))  
      //   using (SqlConnection destConn = new SqlConnection(azureConnectionString)) {  
      //      await srcConn.OpenAsync();  
      //      await destConn.OpenAsync();  
      //      using (SqlCommand srcCmd = new SqlCommand(selectStatment, srcConn)) {  
      //         using (SqlDataReader reader = await srcCmd.ExecuteReaderAsync()) {  
      //            string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
      //            using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {  
      //               await destCmd.ExecuteNonQueryAsync();  
      //               using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {  
      //                  bcp.DestinationTableName = temptable;  
      //                  await bcp.WriteToServerAsync(reader);  
      //               }  
      //            }  
      //         }  
      //      }  
      //   }  
      //}  
  
      // 3.6 Cancelling an Asynchronous Operation to SQL Azure  
      //private static async Task AsyncSqlBulkCopyCancel() {  
      //   CancellationTokenSource cts = new CancellationTokenSource();  
      //   using (SqlConnection srcConn = new SqlConnection(connectionString))  
      //   using (SqlConnection destConn = new SqlConnection(azureConnectionString)) {  
      //      await srcConn.OpenAsync(cts.Token);  
      //      await destConn.OpenAsync(cts.Token);  
      //      using (SqlCommand srcCmd = new SqlCommand(selectStatment, srcConn)) {  
      //         using (SqlDataReader reader = await srcCmd.ExecuteReaderAsync(cts.Token)) {  
      //            string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
      //            using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {  
      //               await destCmd.ExecuteNonQueryAsync(cts.Token);  
      //               using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {  
      //                  bcp.DestinationTableName = temptable;  
      //                  await bcp.WriteToServerAsync(reader, cts.Token);  
      //                  //Cancel Async SqlBulCopy Operation after 200 ms  
      //                  cts.CancelAfter(200);  
      //               }  
      //            }  
      //         }  
      //      }  
      //   }  
      //}  
  
      // 3.7 Using Async.Net and MARS  
      private static async Task AsyncSqlBulkCopyMARS() {  
         using (SqlConnection marsConn = new SqlConnection(marsConnectionString)) {  
            await marsConn.OpenAsync();  
  
            SqlCommand titlesCmd = new SqlCommand("SELECT * FROM [pubs].[dbo].[titles]", marsConn);  
            SqlCommand authorsCmd = new SqlCommand("SELECT * FROM [pubs].[dbo].[authors]", marsConn);  
            //With MARS we can have multiple active results sets on the same connection  
            using (SqlDataReader titlesReader = await titlesCmd.ExecuteReaderAsync())  
            using (SqlDataReader authorsReader = await authorsCmd.ExecuteReaderAsync()) {  
               await authorsReader.ReadAsync();  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               using (SqlConnection destConn = new SqlConnection(connectionString)) {  
                  await destConn.OpenAsync();  
                  using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {  
                     await destCmd.ExecuteNonQueryAsync();  
                     using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {  
                        bcp.DestinationTableName = temptable;  
                        await bcp.WriteToServerAsync(titlesReader);  
                     }  
                  }  
               }  
            }  
         }  
      }  
   }  
}  
```  
  
## <a name="asynchronously-using-multiple-commands-with-mars"></a><span data-ttu-id="49fd6-149">Asynchronně pomocí MARS více příkazů</span><span class="sxs-lookup"><span data-stu-id="49fd6-149">Asynchronously Using Multiple Commands with MARS</span></span>  
 <span data-ttu-id="49fd6-150">V příkladu otevře jednoho připojení k **AdventureWorks** databáze.</span><span class="sxs-lookup"><span data-stu-id="49fd6-150">The example opens a single connection to the **AdventureWorks** database.</span></span> <span data-ttu-id="49fd6-151">Použití <xref:System.Data.SqlClient.SqlCommand> objekt, <xref:System.Data.SqlClient.SqlDataReader> je vytvořena.</span><span class="sxs-lookup"><span data-stu-id="49fd6-151">Using a <xref:System.Data.SqlClient.SqlCommand> object, a <xref:System.Data.SqlClient.SqlDataReader> is created.</span></span> <span data-ttu-id="49fd6-152">Jak se používá program pro čtení, a druhé <xref:System.Data.SqlClient.SqlDataReader> je otevřen pomocí dat z první <xref:System.Data.SqlClient.SqlDataReader> jako vstup do klauzule WHERE pro druhý čtečku.</span><span class="sxs-lookup"><span data-stu-id="49fd6-152">As the reader is used, a second <xref:System.Data.SqlClient.SqlDataReader> is opened, using data from the first <xref:System.Data.SqlClient.SqlDataReader> as input to the WHERE clause for the second reader.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49fd6-153">Následující příklad používá vzorku **AdventureWorks** databáze je součástí systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="49fd6-153">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="49fd6-154">V ukázkovém kódu v zadaném připojovacím řetězci předpokládá, že databáze je nainstalovaná a k dispozici v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="49fd6-154">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="49fd6-155">Upravte připojovací řetězec v případě potřeby pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="49fd6-155">Modify the connection string as necessary for your environment.</span></span>  
  
```csharp
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class Class1 {  
   static void Main() {  
      Task task = MultipleCommands();  
      task.Wait();  
   }  
  
   static async Task MultipleCommands() {  
      // By default, MARS is disabled when connecting to a MARS-enabled.  
      // It must be enabled in the connection string.  
      string connectionString = GetConnectionString();  
  
      int vendorID;  
      SqlDataReader productReader = null;  
      string vendorSQL =  
        "SELECT VendorId, Name FROM Purchasing.Vendor";  
      string productSQL =  
        "SELECT Production.Product.Name FROM Production.Product " +  
        "INNER JOIN Purchasing.ProductVendor " +  
        "ON Production.Product.ProductID = " +  
        "Purchasing.ProductVendor.ProductID " +  
        "WHERE Purchasing.ProductVendor.VendorID = @VendorId";  
  
      using (SqlConnection awConnection =  
        new SqlConnection(connectionString)) {  
         SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);  
         SqlCommand productCmd =  
           new SqlCommand(productSQL, awConnection);  
  
         productCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
         await awConnection.OpenAsync();  
         using (SqlDataReader vendorReader = await vendorCmd.ExecuteReaderAsync()) {  
            while (await vendorReader.ReadAsync()) {  
               Console.WriteLine(vendorReader["Name"]);  
  
               vendorID = (int)vendorReader["VendorId"];  
  
               productCmd.Parameters["@VendorId"].Value = vendorID;  
               // The following line of code requires a MARS-enabled connection.  
               productReader = await productCmd.ExecuteReaderAsync();  
               using (productReader) {  
                  while (await productReader.ReadAsync()) {  
                     Console.WriteLine("  " +  
                       productReader["Name"].ToString());  
                  }  
               }  
            }  
         }  
      }  
   }  
  
   private static string GetConnectionString() {  
      // To avoid storing the connection string in your code, you can retrive it from a configuration file.  
      return "Data Source=(local);Integrated Security=SSPI;Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
   }  
}  
```  
  
## <a name="asynchronously-reading-and-updating-data-with-mars"></a><span data-ttu-id="49fd6-156">Asynchronně čtení a aktualizace dat pomocí MARS</span><span class="sxs-lookup"><span data-stu-id="49fd6-156">Asynchronously Reading and Updating Data with MARS</span></span>  
 <span data-ttu-id="49fd6-157">MARS umožňuje připojení, který se má použít pro obě operace a data manipulaci jazyk (DML) operací čtení s více než jedno čekající operace.</span><span class="sxs-lookup"><span data-stu-id="49fd6-157">MARS allows a connection to be used for both read operations and data manipulation language (DML) operations with more than one pending operation.</span></span> <span data-ttu-id="49fd6-158">Tato funkce eliminuje potřebu aplikace k řešení chyb zaneprázdněných připojení.</span><span class="sxs-lookup"><span data-stu-id="49fd6-158">This feature eliminates the need for an application to deal with connection-busy errors.</span></span> <span data-ttu-id="49fd6-159">Kromě toho můžete MARS nahradit uživatel kurzory na straně serveru, které obecně spotřebují více prostředků.</span><span class="sxs-lookup"><span data-stu-id="49fd6-159">In addition, MARS can replace the user of server-side cursors, which generally consume more resources.</span></span> <span data-ttu-id="49fd6-160">Nakonec, protože více operací může být použita u jednoho připojení, mohou sdílet stejné transakce kontextu, což eliminuje nutnost používat **proceduru sp_getbindtoken** a **procedury sp_bindsession** systémové uložené postupy.</span><span class="sxs-lookup"><span data-stu-id="49fd6-160">Finally, because multiple operations can operate on a single connection, they can share the same transaction context, eliminating the need to use **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span>  
  
 <span data-ttu-id="49fd6-161">Následující aplikace konzoly ukazuje, jak používat dvě <xref:System.Data.SqlClient.SqlDataReader> objekty s třemi <xref:System.Data.SqlClient.SqlCommand> objektů a jeden <xref:System.Data.SqlClient.SqlConnection> objekt s MARS povolena.</span><span class="sxs-lookup"><span data-stu-id="49fd6-161">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with three <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span> <span data-ttu-id="49fd6-162">První objekt příkazu načte seznam dodavatelů, jejichž platební hodnocení je 5.</span><span class="sxs-lookup"><span data-stu-id="49fd6-162">The first command object retrieves a list of vendors whose credit rating is 5.</span></span> <span data-ttu-id="49fd6-163">Druhý objekt příkazu používá zadáno ID od dodavatele <xref:System.Data.SqlClient.SqlDataReader> načíst druhý <xref:System.Data.SqlClient.SqlDataReader> se všemi produktů pro konkrétní dodavatele.</span><span class="sxs-lookup"><span data-stu-id="49fd6-163">The second command object uses the vendor ID provided from a <xref:System.Data.SqlClient.SqlDataReader> to load the second <xref:System.Data.SqlClient.SqlDataReader> with all of the products for the particular vendor.</span></span> <span data-ttu-id="49fd6-164">Každý záznam produktu je navštívené druhou <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="49fd6-164">Each product record is visited by the second <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="49fd6-165">Provádění výpočtu určit, jaké nové **OnOrderQty** by měl být.</span><span class="sxs-lookup"><span data-stu-id="49fd6-165">A calculation is performed to determine what the new **OnOrderQty** should be.</span></span> <span data-ttu-id="49fd6-166">Třetí objekt příkazu se pak používá k aktualizaci **ProductVendor** tabulku s novou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="49fd6-166">The third command object is then used to update the **ProductVendor** table with the new value.</span></span> <span data-ttu-id="49fd6-167">Tento celý proces probíhá v rámci jedné transakce, která je vrácena zpět na konci.</span><span class="sxs-lookup"><span data-stu-id="49fd6-167">This entire process takes place within a single transaction, which is rolled back at the end.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49fd6-168">Následující příklad používá vzorku **AdventureWorks** databáze je součástí systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="49fd6-168">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="49fd6-169">V ukázkovém kódu v zadaném připojovacím řetězci předpokládá, že databáze je nainstalovaná a k dispozici v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="49fd6-169">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="49fd6-170">Upravte připojovací řetězec v případě potřeby pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="49fd6-170">Modify the connection string as necessary for your environment.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class Program {  
   static void Main() {  
      Task task = ReadingAndUpdatingData();  
      task.Wait();  
   }  
  
   static async Task ReadingAndUpdatingData() {  
      // By default, MARS is disabled when connecting to a MARS-enabled host.  
      // It must be enabled in the connection string.  
      string connectionString = GetConnectionString();  
  
      SqlTransaction updateTx = null;  
      SqlCommand vendorCmd = null;  
      SqlCommand prodVendCmd = null;  
      SqlCommand updateCmd = null;  
  
      SqlDataReader prodVendReader = null;  
  
      int vendorID = 0;  
      int productID = 0;  
      int minOrderQty = 0;  
      int maxOrderQty = 0;  
      int onOrderQty = 0;  
      int recordsUpdated = 0;  
      int totalRecordsUpdated = 0;  
  
      string vendorSQL =  
          "SELECT VendorID, Name FROM Purchasing.Vendor " +  
          "WHERE CreditRating = 5";  
      string prodVendSQL =  
          "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +  
          "FROM Purchasing.ProductVendor " +  
          "WHERE VendorID = @VendorID";  
      string updateSQL =  
          "UPDATE Purchasing.ProductVendor " +  
          "SET OnOrderQty = @OrderQty " +  
          "WHERE ProductID = @ProductID AND VendorID = @VendorID";  
  
      using (SqlConnection awConnection =  
        new SqlConnection(connectionString)) {  
         await awConnection.OpenAsync();  
         updateTx = await Task.Run(() => awConnection.BeginTransaction());  
  
         vendorCmd = new SqlCommand(vendorSQL, awConnection);  
         vendorCmd.Transaction = updateTx;  
  
         prodVendCmd = new SqlCommand(prodVendSQL, awConnection);  
         prodVendCmd.Transaction = updateTx;  
         prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
         updateCmd = new SqlCommand(updateSQL, awConnection);  
         updateCmd.Transaction = updateTx;  
         updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);  
         updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);  
         updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);  
  
         using (SqlDataReader vendorReader = await vendorCmd.ExecuteReaderAsync()) {  
            while (await vendorReader.ReadAsync()) {  
               Console.WriteLine(vendorReader["Name"]);  
  
               vendorID = (int)vendorReader["VendorID"];  
               prodVendCmd.Parameters["@VendorID"].Value = vendorID;  
               prodVendReader = await prodVendCmd.ExecuteReaderAsync();  
  
               using (prodVendReader) {  
                  while (await prodVendReader.ReadAsync()) {  
                     productID = (int)prodVendReader["ProductID"];  
  
                     if (prodVendReader["OnOrderQty"] == DBNull.Value) {  
                        minOrderQty = (int)prodVendReader["MinOrderQty"];  
                        onOrderQty = minOrderQty;  
                     }  
                     else {  
                        maxOrderQty = (int)prodVendReader["MaxOrderQty"];  
                        onOrderQty = (int)(maxOrderQty / 2);  
                     }  
  
                     updateCmd.Parameters["@OrderQty"].Value = onOrderQty;  
                     updateCmd.Parameters["@ProductID"].Value = productID;  
                     updateCmd.Parameters["@VendorID"].Value = vendorID;  
  
                     recordsUpdated = await updateCmd.ExecuteNonQueryAsync();  
                     totalRecordsUpdated += recordsUpdated;  
                  }  
               }  
            }  
         }  
         Console.WriteLine("Total Records Updated: ", totalRecordsUpdated.ToString());  
         await Task.Run(() => updateTx.Rollback());  
         Console.WriteLine("Transaction Rolled Back");  
      }  
   }  
  
   private static string GetConnectionString() {  
      // To avoid storing the connection string in your code, you can retrive it from a configuration file.  
      return "Data Source=(local);Integrated Security=SSPI;Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="49fd6-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="49fd6-171">See Also</span></span>  
 [<span data-ttu-id="49fd6-172">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="49fd6-172">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
