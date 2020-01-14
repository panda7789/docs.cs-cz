---
title: Asynchronní programování
ms.date: 10/18/2018
ms.assetid: 85da7447-7125-426e-aa5f-438a290d1f77
ms.openlocfilehash: 7bf492e45a9ebabdd36caa8e21605739bb410695
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937581"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="f6b19-102">Asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="f6b19-102">Asynchronous Programming</span></span>

<span data-ttu-id="f6b19-103">Toto téma popisuje podporu asynchronního programování v .NET Framework Zprostředkovatel dat pro SQL Server (SqlClient), včetně vylepšení pro podporu funkcí asynchronního programování, které byly představeny v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="f6b19-103">This topic discusses support for asynchronous programming in the .NET Framework Data Provider for SQL Server (SqlClient) including enhancements made to support asynchronous programming functionality that was introduced in .NET Framework 4.5.</span></span>

## <a name="legacy-asynchronous-programming"></a><span data-ttu-id="f6b19-104">Starší verze asynchronního programování</span><span class="sxs-lookup"><span data-stu-id="f6b19-104">Legacy Asynchronous Programming</span></span>

<span data-ttu-id="f6b19-105">Před .NET Framework 4,5 bylo asynchronní programování s SqlClient provedeno s následujícími metodami a vlastností připojení `Asynchronous Processing=true`:</span><span class="sxs-lookup"><span data-stu-id="f6b19-105">Prior to .NET Framework 4.5, asynchronous programming with SqlClient was done with the following methods and the `Asynchronous Processing=true` connection property:</span></span>

1. <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A?displayProperty=nameWithType>

2. <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A?displayProperty=nameWithType>

3. <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A?displayProperty=nameWithType>

<span data-ttu-id="f6b19-106">Tato funkce zůstává v SqlClient v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="f6b19-106">This functionality remains in SqlClient in .NET Framework 4.5.</span></span>

> [!TIP]
> <span data-ttu-id="f6b19-107">Počínaje .NET Framework 4,5 tyto starší metody již nevyžadují `Asynchronous Processing=true` v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="f6b19-107">Beginning in the .NET Framework 4.5, these legacy methods no longer require `Asynchronous Processing=true` in the connection string.</span></span>

## <a name="asynchronous-programming-features-added-in-net-framework-45"></a><span data-ttu-id="f6b19-108">Funkce asynchronního programování přidané v .NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="f6b19-108">Asynchronous Programming Features Added in .NET Framework 4.5</span></span>

<span data-ttu-id="f6b19-109">Nová funkce asynchronního programování poskytuje jednoduchou techniku pro asynchronní vytváření kódu.</span><span class="sxs-lookup"><span data-stu-id="f6b19-109">The new asynchronous programming feature provides a simple technique to make code asynchronous.</span></span>

<span data-ttu-id="f6b19-110">Další informace o funkci asynchronního programování, která byla představena v .NET Framework 4,5, naleznete zde:</span><span class="sxs-lookup"><span data-stu-id="f6b19-110">For more information about the asynchronous programming feature that was introduced in .NET Framework 4.5, see:</span></span>

- [<span data-ttu-id="f6b19-111">Asynchronní programování vC#</span><span class="sxs-lookup"><span data-stu-id="f6b19-111">Asynchronous programming in C#</span></span>](../../../csharp/async.md)

- [<span data-ttu-id="f6b19-112">Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6b19-112">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)

- [<span data-ttu-id="f6b19-113">Použití nových asynchronních metod SqlDataReader v rozhraní .NET 4,5 (část 1)</span><span class="sxs-lookup"><span data-stu-id="f6b19-113">Using SqlDataReader’s new async methods in .NET 4.5 (Part 1)</span></span>](https://docs.microsoft.com/archive/blogs/adonet/using-sqldatareaders-new-async-methods-in-net-4-5)

- [<span data-ttu-id="f6b19-114">Použití nových asynchronních metod SqlDataReader v rozhraní .NET 4,5 (část 2)</span><span class="sxs-lookup"><span data-stu-id="f6b19-114">Using SqlDataReader’s new async methods in .NET 4.5 (Part 2)</span></span>](https://docs.microsoft.com/archive/blogs/adonet/using-sqldatareaders-new-async-methods-in-net-4-5-part-2-examples)

<span data-ttu-id="f6b19-115">Pokud vaše uživatelské rozhraní nereaguje nebo váš server není škálovatelný, je pravděpodobně potřeba, abyste měli kód větší asynchronní.</span><span class="sxs-lookup"><span data-stu-id="f6b19-115">When your user interface is unresponsive or your server does not scale, it is likely that you need your code to be more asynchronous.</span></span> <span data-ttu-id="f6b19-116">Zápis asynchronního kódu tradičně zahrnuje instalaci zpětného volání (označovaného také jako pokračování), který vyjadřuje logiku, která nastane po dokončení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="f6b19-116">Writing asynchronous code has traditionally involved installing a callback (also called continuation) to express the logic that occurs after the asynchronous operation finishes.</span></span> <span data-ttu-id="f6b19-117">Tím se ztěžuje struktura asynchronního kódu v porovnání s synchronním kódem.</span><span class="sxs-lookup"><span data-stu-id="f6b19-117">This complicates the structure of asynchronous code as compared with synchronous code.</span></span>

<span data-ttu-id="f6b19-118">Nyní se můžete volat do asynchronních metod bez použití zpětných volání a bez rozdělení kódu napříč více metodami nebo lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="f6b19-118">You can now call into asynchronous methods without using callbacks, and without splitting your code across multiple methods or lambda expressions.</span></span>

<span data-ttu-id="f6b19-119">Modifikátor `async` určuje, že metoda je asynchronní.</span><span class="sxs-lookup"><span data-stu-id="f6b19-119">The `async` modifier specifies that a method is asynchronous.</span></span> <span data-ttu-id="f6b19-120">Při volání metody `async` je vrácen úkol.</span><span class="sxs-lookup"><span data-stu-id="f6b19-120">When calling an `async` method, a task is returned.</span></span> <span data-ttu-id="f6b19-121">Při použití operátoru `await` pro úlohu se aktuální metoda okamžitě ukončí.</span><span class="sxs-lookup"><span data-stu-id="f6b19-121">When the `await` operator is applied to a task, the current method exits immediately.</span></span> <span data-ttu-id="f6b19-122">Po dokončení úlohy se provádění pokračuje ve stejné metodě.</span><span class="sxs-lookup"><span data-stu-id="f6b19-122">When the task finishes, execution resumes in the same method.</span></span>

> [!WARNING]
> <span data-ttu-id="f6b19-123">Asynchronní volání nejsou podporovaná, pokud aplikace používá také klíčové slovo připojovacího řetězce `Context Connection`.</span><span class="sxs-lookup"><span data-stu-id="f6b19-123">Asynchronous calls are not supported if an application also uses the `Context Connection` connection string keyword.</span></span>

<span data-ttu-id="f6b19-124">Volání metody `async` nealokuje žádné další podprocesy.</span><span class="sxs-lookup"><span data-stu-id="f6b19-124">Calling an `async` method does not allocate any additional threads.</span></span> <span data-ttu-id="f6b19-125">Může na konci krátce použít stávající vlákno dokončení I/O.</span><span class="sxs-lookup"><span data-stu-id="f6b19-125">It may use the existing I/O completion thread briefly at the end.</span></span>

<span data-ttu-id="f6b19-126">V .NET Framework 4,5 byly přidány následující metody pro podporu asynchronního programování:</span><span class="sxs-lookup"><span data-stu-id="f6b19-126">The following methods were added in .NET Framework 4.5 to support asynchronous programming:</span></span>

- <xref:System.Data.Common.DbConnection.OpenAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbCommand.ExecuteDbDataReaderAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbCommand.ExecuteNonQueryAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbCommand.ExecuteReaderAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbCommand.ExecuteScalarAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbDataReader.GetFieldValueAsync%2A>

- <xref:System.Data.Common.DbDataReader.IsDBNullAsync%2A>

- <xref:System.Data.Common.DbDataReader.NextResultAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.Common.DbDataReader.ReadAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlConnection.OpenAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQueryAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlCommand.ExecuteReaderAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlCommand.ExecuteScalarAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlCommand.ExecuteXmlReaderAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlDataReader.NextResultAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlDataReader.ReadAsync%2A?displayProperty=nameWithType>

- <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>

 <span data-ttu-id="f6b19-127">Pro podporu [streamování SqlClient](sqlclient-streaming-support.md)byly přidány další asynchronní členy.</span><span class="sxs-lookup"><span data-stu-id="f6b19-127">Other asynchronous members were added to support [SqlClient Streaming Support](sqlclient-streaming-support.md).</span></span>

> [!TIP]
> <span data-ttu-id="f6b19-128">Nové asynchronní metody nevyžadují `Asynchronous Processing=true` v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="f6b19-128">The new asynchronous methods don't require `Asynchronous Processing=true` in the connection string.</span></span>

### <a name="synchronous-to-asynchronous-connection-open"></a><span data-ttu-id="f6b19-129">Synchronní s otevřeným asynchronním připojením</span><span class="sxs-lookup"><span data-stu-id="f6b19-129">Synchronous to Asynchronous Connection Open</span></span>

<span data-ttu-id="f6b19-130">Existující aplikaci můžete upgradovat, aby používala novou asynchronní funkci.</span><span class="sxs-lookup"><span data-stu-id="f6b19-130">You can upgrade an existing application to use the new asynchronous feature.</span></span> <span data-ttu-id="f6b19-131">Předpokládejme například, že aplikace má synchronní algoritmus připojení a blokuje vlákno uživatelského rozhraní pokaždé, když se připojí k databázi a po připojení aplikace volá uloženou proceduru, která signalizuje jiným uživatelům, kteří se právě přihlásili.</span><span class="sxs-lookup"><span data-stu-id="f6b19-131">For example, assume an application has a synchronous connection algorithm and blocks the UI thread every time it connects to the database and, once connected, the application calls a stored procedure that signals other users of the one who just signed in.</span></span>

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

<span data-ttu-id="f6b19-132">Při převodu na použití nové asynchronní funkce by program vypadal takto:</span><span class="sxs-lookup"><span data-stu-id="f6b19-132">When converted to use the new asynchronous functionality, the program would look like:</span></span>

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
            Console.WriteLine(reader[0]);
      }
   }
}
```

### <a name="adding-the-new-asynchronous-feature-in-an-existing-application-mixing-old-and-new-patterns"></a><span data-ttu-id="f6b19-133">Přidání nové asynchronní funkce do existující aplikace (kombinování starých a nových vzorů)</span><span class="sxs-lookup"><span data-stu-id="f6b19-133">Adding the New Asynchronous Feature in an Existing Application (Mixing Old and New Patterns)</span></span>

<span data-ttu-id="f6b19-134">Je také možné přidat novou asynchronní funkci (SqlConnection:: OpenAsync) beze změny stávající asynchronní logiky.</span><span class="sxs-lookup"><span data-stu-id="f6b19-134">It is also possible to add new asynchronous capability (SqlConnection::OpenAsync) without changing the existing asynchronous logic.</span></span> <span data-ttu-id="f6b19-135">Například pokud aplikace aktuálně používá:</span><span class="sxs-lookup"><span data-stu-id="f6b19-135">For example, if an application currently uses:</span></span>

```csharp
AsyncCallback productList = new AsyncCallback(ProductList);
SqlConnection conn = new SqlConnection("…");
conn.Open();
SqlCommand cmd = new SqlCommand("SELECT * FROM [Current Product List]", conn);
IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);
```

<span data-ttu-id="f6b19-136">Můžete začít používat nový asynchronní vzorek bez podstatné změny stávajícího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="f6b19-136">You can begin to use the new asynchronous pattern without substantially changing the existing algorithm.</span></span>

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

### <a name="using-the-base-provider-model-and-the-new-asynchronous-feature"></a><span data-ttu-id="f6b19-137">Použití základního modelu poskytovatele a nové asynchronní funkce</span><span class="sxs-lookup"><span data-stu-id="f6b19-137">Using the Base Provider Model and the New Asynchronous Feature</span></span>

<span data-ttu-id="f6b19-138">Možná budete muset vytvořit nástroj, který bude schopný připojit se k různým databázím a spouštět dotazy.</span><span class="sxs-lookup"><span data-stu-id="f6b19-138">You may need to create a tool that is able to connect to different databases and execute queries.</span></span> <span data-ttu-id="f6b19-139">Můžete použít základní model poskytovatele a novou asynchronní funkci.</span><span class="sxs-lookup"><span data-stu-id="f6b19-139">You can use the base provider model and the new asynchronous feature.</span></span>

<span data-ttu-id="f6b19-140">Aby bylo možné používat distribuované transakce, musí být na serveru povolená služba MS DTC (Microsoft Distributed Transaction Controller).</span><span class="sxs-lookup"><span data-stu-id="f6b19-140">The Microsoft Distributed Transaction Controller (MSDTC) must be enabled on the server to use distributed transactions.</span></span> <span data-ttu-id="f6b19-141">Informace o tom, jak povolit MSDTC, najdete v tématu [Jak povolit MSDTC na webovém serveru](https://docs.microsoft.com/previous-versions/commerce-server/dd327979(v=cs.90)).</span><span class="sxs-lookup"><span data-stu-id="f6b19-141">For information on how to enable MSDTC, see [How to Enable MSDTC on a Web Server](https://docs.microsoft.com/previous-versions/commerce-server/dd327979(v=cs.90)).</span></span>

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

### <a name="using-sql-transactions-and-the-new-asynchronous-feature"></a><span data-ttu-id="f6b19-142">Používání transakcí SQL a nové asynchronní funkce</span><span class="sxs-lookup"><span data-stu-id="f6b19-142">Using SQL Transactions and the New Asynchronous Feature</span></span>

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

### <a name="using-sql-transactions-and-the-new-asynchronous-feature"></a><span data-ttu-id="f6b19-143">Používání transakcí SQL a nové asynchronní funkce</span><span class="sxs-lookup"><span data-stu-id="f6b19-143">Using SQL Transactions and the New Asynchronous Feature</span></span>

<span data-ttu-id="f6b19-144">V podnikové aplikaci možná budete muset v některých scénářích přidat distribuované transakce, aby bylo možné povolit transakce mezi několika databázovými servery.</span><span class="sxs-lookup"><span data-stu-id="f6b19-144">In an enterprise application, you may need to add distributed transactions in some scenarios, to enable transactions between multiple database servers.</span></span> <span data-ttu-id="f6b19-145">Obor názvů System. Transactions a příkaz k zařazení distribuované transakce lze použít následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f6b19-145">You can use the System.Transactions namespace and enlist a distributed transaction, as follows:</span></span>

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

### <a name="cancelling-an-asynchronous-operation"></a><span data-ttu-id="f6b19-146">Zrušení asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="f6b19-146">Cancelling an Asynchronous Operation</span></span>

<span data-ttu-id="f6b19-147">Asynchronní požadavek můžete zrušit pomocí <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="f6b19-147">You can cancel an asynchronous request by using the <xref:System.Threading.CancellationToken>.</span></span>

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

### <a name="asynchronous-operations-with-sqlbulkcopy"></a><span data-ttu-id="f6b19-148">Asynchronní operace s SqlBulkCopy</span><span class="sxs-lookup"><span data-stu-id="f6b19-148">Asynchronous Operations with SqlBulkCopy</span></span>

<span data-ttu-id="f6b19-149">Do <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType> s <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>se přidaly taky asynchronní možnosti.</span><span class="sxs-lookup"><span data-stu-id="f6b19-149">Asynchronous capabilities were also added to <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType> with <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>.</span></span>

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
      static string selectStatement = "SELECT * FROM [pubs].[dbo].[titles]";
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
            using (SqlCommand cmd = new SqlCommand(selectStatement, conn)) {
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

      // 3.1.2 Asynchronous bulk copy in .NET 4.5
      private static async Task AsyncSqlBulkCopy() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            DataTable dt = new DataTable();
            using (SqlCommand cmd = new SqlCommand(selectStatement, conn)) {
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

      // 3.2 Add new Async.NET capabilities in an existing application (Mixing synchronous and asynchronous calls)
      private static async Task MixSyncAsyncSqlBulkCopy() {
         using (OdbcConnection odbcconn = new OdbcConnection(odbcConnectionString)) {
            odbcconn.Open();
            using (OdbcCommand odbccmd = new OdbcCommand(selectStatement, odbcconn)) {
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
            using (SqlCommand cmd = new SqlCommand(selectStatement, conn)) {
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
            using (SqlCommand cmd = new SqlCommand(selectStatement, conn)) {
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
      //      using (SqlCommand srcCmd = new SqlCommand(selectStatement, srcConn)) {
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
      //      using (SqlCommand srcCmd = new SqlCommand(selectStatement, srcConn)) {
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

## <a name="asynchronously-using-multiple-commands-with-mars"></a><span data-ttu-id="f6b19-150">Asynchronní použití více příkazů s MARS</span><span class="sxs-lookup"><span data-stu-id="f6b19-150">Asynchronously Using Multiple Commands with MARS</span></span>

<span data-ttu-id="f6b19-151">V tomto příkladu se otevře jedno připojení k databázi **AdventureWorks** .</span><span class="sxs-lookup"><span data-stu-id="f6b19-151">The example opens a single connection to the **AdventureWorks** database.</span></span> <span data-ttu-id="f6b19-152">Při použití objektu <xref:System.Data.SqlClient.SqlCommand> se vytvoří <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="f6b19-152">Using a <xref:System.Data.SqlClient.SqlCommand> object, a <xref:System.Data.SqlClient.SqlDataReader> is created.</span></span> <span data-ttu-id="f6b19-153">Při použití čtecího modulu je otevřen druhý <xref:System.Data.SqlClient.SqlDataReader>, který používá data z první <xref:System.Data.SqlClient.SqlDataReader> jako vstup do klauzule WHERE pro druhý čtecí modul.</span><span class="sxs-lookup"><span data-stu-id="f6b19-153">As the reader is used, a second <xref:System.Data.SqlClient.SqlDataReader> is opened, using data from the first <xref:System.Data.SqlClient.SqlDataReader> as input to the WHERE clause for the second reader.</span></span>

> [!NOTE]
> <span data-ttu-id="f6b19-154">Následující příklad používá ukázkovou databázi **AdventureWorks** , která je součástí SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f6b19-154">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="f6b19-155">Připojovací řetězec uvedený v ukázkovém kódu předpokládá, že je databáze nainstalována a je k dispozici v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="f6b19-155">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="f6b19-156">Upravte připojovací řetězec podle potřeby pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="f6b19-156">Modify the connection string as necessary for your environment.</span></span>

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
      // To avoid storing the connection string in your code, you can retrieve it from a configuration file.
      return "Data Source=(local);Integrated Security=SSPI;Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";
   }
}
```

## <a name="asynchronously-reading-and-updating-data-with-mars"></a><span data-ttu-id="f6b19-157">Asynchronní čtení a aktualizace dat pomocí MARS</span><span class="sxs-lookup"><span data-stu-id="f6b19-157">Asynchronously Reading and Updating Data with MARS</span></span>

<span data-ttu-id="f6b19-158">MARS umožňuje, aby se připojení používalo pro operace čtení i operace jazyka DML (data remanipulace Language) s více než jednou probíhající operací.</span><span class="sxs-lookup"><span data-stu-id="f6b19-158">MARS allows a connection to be used for both read operations and data manipulation language (DML) operations with more than one pending operation.</span></span> <span data-ttu-id="f6b19-159">Tato funkce eliminuje nutnost zabývat se chybami zaneprázdněnými připojením aplikace.</span><span class="sxs-lookup"><span data-stu-id="f6b19-159">This feature eliminates the need for an application to deal with connection-busy errors.</span></span> <span data-ttu-id="f6b19-160">MARS navíc může nahradit uživatele koncových ukazatelů na straně serveru, což obecně spotřebovává víc prostředků.</span><span class="sxs-lookup"><span data-stu-id="f6b19-160">In addition, MARS can replace the user of server-side cursors, which generally consume more resources.</span></span> <span data-ttu-id="f6b19-161">Vzhledem k tomu, že více operací může pracovat s jedním připojením, může sdílet stejný kontext transakce, což eliminuje nutnost použít **sp_getbindtoken** a **sp_bindsession** systémových uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="f6b19-161">Finally, because multiple operations can operate on a single connection, they can share the same transaction context, eliminating the need to use **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span>

<span data-ttu-id="f6b19-162">Následující aplikace konzoly ukazuje, jak použít dva objekty <xref:System.Data.SqlClient.SqlDataReader> se třemi objekty <xref:System.Data.SqlClient.SqlCommand> a jeden objekt <xref:System.Data.SqlClient.SqlConnection> s povoleným MARS.</span><span class="sxs-lookup"><span data-stu-id="f6b19-162">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with three <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span> <span data-ttu-id="f6b19-163">První objekt příkazu načte seznam dodavatelů, jejichž kreditní hodnocení je 5.</span><span class="sxs-lookup"><span data-stu-id="f6b19-163">The first command object retrieves a list of vendors whose credit rating is 5.</span></span> <span data-ttu-id="f6b19-164">Druhý objekt příkazu používá ID dodavatele poskytnuté z <xref:System.Data.SqlClient.SqlDataReader> k načtení druhého <xref:System.Data.SqlClient.SqlDataReader> se všemi produkty pro konkrétního dodavatele.</span><span class="sxs-lookup"><span data-stu-id="f6b19-164">The second command object uses the vendor ID provided from a <xref:System.Data.SqlClient.SqlDataReader> to load the second <xref:System.Data.SqlClient.SqlDataReader> with all of the products for the particular vendor.</span></span> <span data-ttu-id="f6b19-165">Druhý <xref:System.Data.SqlClient.SqlDataReader>navštíví každý záznam produktu.</span><span class="sxs-lookup"><span data-stu-id="f6b19-165">Each product record is visited by the second <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="f6b19-166">Provede se výpočet, který určí, co by mělo být nového v rámci **OrderQty** .</span><span class="sxs-lookup"><span data-stu-id="f6b19-166">A calculation is performed to determine what the new **OnOrderQty** should be.</span></span> <span data-ttu-id="f6b19-167">Třetí objekt příkazu se pak použije k aktualizaci tabulky **ProductVendor** s novou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="f6b19-167">The third command object is then used to update the **ProductVendor** table with the new value.</span></span> <span data-ttu-id="f6b19-168">Celý proces probíhá v rámci jedné transakce, která je vrácena zpět na konci.</span><span class="sxs-lookup"><span data-stu-id="f6b19-168">This entire process takes place within a single transaction, which is rolled back at the end.</span></span>

> [!NOTE]
> <span data-ttu-id="f6b19-169">Následující příklad používá ukázkovou databázi **AdventureWorks** , která je součástí SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f6b19-169">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="f6b19-170">Připojovací řetězec uvedený v ukázkovém kódu předpokládá, že je databáze nainstalována a je k dispozici v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="f6b19-170">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="f6b19-171">Upravte připojovací řetězec podle potřeby pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="f6b19-171">Modify the connection string as necessary for your environment.</span></span>

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
      // To avoid storing the connection string in your code, you can retrieve it from a configuration file.
      return "Data Source=(local);Integrated Security=SSPI;Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";
   }
}
```

## <a name="see-also"></a><span data-ttu-id="f6b19-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6b19-172">See also</span></span>

- [<span data-ttu-id="f6b19-173">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f6b19-173">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
