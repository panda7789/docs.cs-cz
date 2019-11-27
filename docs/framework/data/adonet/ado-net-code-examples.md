---
title: Příklady kódu ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: a66ae2b2b8bed95fd38b71a39682a2a7f42be218
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430803"
---
# <a name="adonet-code-examples"></a><span data-ttu-id="89923-102">Příklady kódu ADO.NET</span><span class="sxs-lookup"><span data-stu-id="89923-102">ADO.NET code examples</span></span>
<span data-ttu-id="89923-103">Výpisy kódu v tomto tématu demonstrují, jak načíst data z databáze pomocí následujících ADO.NET technologií:</span><span class="sxs-lookup"><span data-stu-id="89923-103">The code listings in this topic demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="89923-104">Poskytovatelé dat ADO.NET:</span><span class="sxs-lookup"><span data-stu-id="89923-104">ADO.NET data providers:</span></span>

  - <span data-ttu-id="89923-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span><span class="sxs-lookup"><span data-stu-id="89923-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="89923-106">[OLEDB](#oledb) (`System.Data.OleDb`)</span><span class="sxs-lookup"><span data-stu-id="89923-106">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="89923-107">[ODBC](#odbc) (`System.Data.Odbc`)</span><span class="sxs-lookup"><span data-stu-id="89923-107">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="89923-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span><span class="sxs-lookup"><span data-stu-id="89923-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="89923-109">ADO.NET Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="89923-109">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="89923-110">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="89923-110">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="89923-111">Typové ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="89923-111">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="89923-112">[Zprostředkovatel EntityClient](#entityclient) (`System.Data.EntityClient`)</span><span class="sxs-lookup"><span data-stu-id="89923-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="89923-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="89923-113">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="89923-114">Příklady poskytovatele dat ADO.NET</span><span class="sxs-lookup"><span data-stu-id="89923-114">ADO.NET data provider examples</span></span>
<span data-ttu-id="89923-115">Následující výpisy kódu ukazují, jak načíst data z databáze pomocí zprostředkovatelů dat ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="89923-115">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="89923-116">Data jsou vrácena v `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="89923-116">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="89923-117">Další informace najdete v tématu [načtení dat pomocí objektu DataReader](retrieving-data-using-a-datareader.md).</span><span class="sxs-lookup"><span data-stu-id="89923-117">For more information, see [Retrieving Data Using a DataReader](retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="89923-118">SqlClient</span><span class="sxs-lookup"><span data-stu-id="89923-118">SqlClient</span></span>
<span data-ttu-id="89923-119">Kód v tomto příkladu předpokládá, že se můžete připojit k ukázkové databázi `Northwind` v Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="89923-119">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft SQL Server.</span></span> <span data-ttu-id="89923-120">Kód vytvoří <xref:System.Data.SqlClient.SqlCommand> pro výběr řádků z tabulky Products a přidání <xref:System.Data.SqlClient.SqlParameter> k omezení výsledků na řádky s jednotkou JednotkováCena větší, než je zadaná hodnota parametru, v tomto případě 5.</span><span class="sxs-lookup"><span data-stu-id="89923-120">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="89923-121"><xref:System.Data.SqlClient.SqlConnection> se otevírá v bloku `using`, který zajišťuje, že se prostředky zavřou a odstraní při ukončení kódu.</span><span class="sxs-lookup"><span data-stu-id="89923-121">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="89923-122">Kód spustí příkaz pomocí <xref:System.Data.SqlClient.SqlDataReader>a zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="89923-122">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="89923-123">Povolí</span><span class="sxs-lookup"><span data-stu-id="89923-123">OleDb</span></span>
<span data-ttu-id="89923-124">Kód v tomto příkladu předpokládá, že se můžete připojit k ukázkové databázi Northwind aplikace Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="89923-124">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="89923-125">Kód vytvoří <xref:System.Data.OleDb.OleDbCommand> pro výběr řádků z tabulky Products a přidání <xref:System.Data.OleDb.OleDbParameter> k omezení výsledků na řádky s jednotkou JednotkováCena větší, než je zadaná hodnota parametru, v tomto případě 5.</span><span class="sxs-lookup"><span data-stu-id="89923-125">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="89923-126"><xref:System.Data.OleDb.OleDbConnection> se otevírá v bloku `using`, který zajišťuje, že se prostředky při ukončení kódu zavřou a odstraní.</span><span class="sxs-lookup"><span data-stu-id="89923-126">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="89923-127">Kód spustí příkaz pomocí <xref:System.Data.OleDb.OleDbDataReader>a zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="89923-127">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="89923-128">Odbc</span><span class="sxs-lookup"><span data-stu-id="89923-128">Odbc</span></span>
<span data-ttu-id="89923-129">Kód v tomto příkladu předpokládá, že se můžete připojit k ukázkové databázi Northwind aplikace Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="89923-129">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="89923-130">Kód vytvoří <xref:System.Data.Odbc.OdbcCommand> pro výběr řádků z tabulky Products a přidání <xref:System.Data.Odbc.OdbcParameter> k omezení výsledků na řádky s jednotkou JednotkováCena větší, než je zadaná hodnota parametru, v tomto případě 5.</span><span class="sxs-lookup"><span data-stu-id="89923-130">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="89923-131"><xref:System.Data.Odbc.OdbcConnection> se otevírá v bloku `using`, který zajišťuje, že se prostředky zavřou a odstraní při ukončení kódu.</span><span class="sxs-lookup"><span data-stu-id="89923-131">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="89923-132">Kód spustí příkaz pomocí <xref:System.Data.Odbc.OdbcDataReader>a zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="89923-132">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)] 
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)] 

### <a name="oracleclient"></a><span data-ttu-id="89923-133">OracleClient</span><span class="sxs-lookup"><span data-stu-id="89923-133">OracleClient</span></span>
<span data-ttu-id="89923-134">Kód v tomto příkladu předpokládá připojení k UKÁZCE. ZÁKAZNÍK na serveru Oracle.</span><span class="sxs-lookup"><span data-stu-id="89923-134">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="89923-135">Musíte také přidat odkaz na System. data. OracleClient. dll.</span><span class="sxs-lookup"><span data-stu-id="89923-135">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="89923-136">Kód vrátí data v <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="89923-136">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="89923-137">Příklady Entity Framework</span><span class="sxs-lookup"><span data-stu-id="89923-137">Entity Framework examples</span></span>
<span data-ttu-id="89923-138">Následující výpisy kódu ukazují, jak načíst data ze zdroje dat pomocí dotazu na entity v model EDM (Entity Data Model) (EDM).</span><span class="sxs-lookup"><span data-stu-id="89923-138">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="89923-139">V těchto příkladech se používá model založený na ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="89923-139">These examples use a model based on the Northwind sample database.</span></span> <span data-ttu-id="89923-140">Další informace o Entity Framework najdete v tématu [Entity Framework Overview](./ef/overview.md).</span><span class="sxs-lookup"><span data-stu-id="89923-140">For more information about Entity Framework, see [Entity Framework Overview](./ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="89923-141">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="89923-141">LINQ to Entities</span></span>
<span data-ttu-id="89923-142">Kód v tomto příkladu používá dotaz LINQ, který vrací data jako objekty kategorií, které jsou probíhají jako anonymní typ, který obsahuje pouze vlastnosti CategoryID a CategoryName.</span><span class="sxs-lookup"><span data-stu-id="89923-142">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="89923-143">Další informace najdete v tématu [přehled LINQ to Entities](./ef/language-reference/linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="89923-143">For more information, see [LINQ to Entities Overview](./ef/language-reference/linq-to-entities.md).</span></span>

```csharp
using System;
using System.Linq;
using System.Data.Objects;
using NorthwindModel;

class LinqSample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            try
            {
                var query = from category in context.Categories
                            select new
                            {
                                categoryID = category.CategoryID,
                                categoryName = category.CategoryName
                            };

                foreach (var categoryInfo in query)
                {
                    Console.WriteLine("\t{0}\t{1}",
                        categoryInfo.categoryID, categoryInfo.categoryName);
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Linq
Imports System.Data.Objects
Imports NorthwindModel

Class LinqSample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Try
                Dim query = From category In context.Categories _
                            Select New With _
                            { _
                                .categoryID = category.CategoryID, _
                                .categoryName = category.CategoryName _
                            }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                        categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using
    End Sub
End Class
```

### <a name="typed-objectquery"></a><span data-ttu-id="89923-144">Typové ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="89923-144">Typed ObjectQuery</span></span>
<span data-ttu-id="89923-145">Kód v tomto příkladu používá <xref:System.Data.Objects.ObjectQuery%601> k vrácení dat jako objektů kategorií.</span><span class="sxs-lookup"><span data-stu-id="89923-145">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="89923-146">Další informace najdete v tématu [dotazy na objekty](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="89923-146">For more information, see [Object Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span></span>

```csharp
using System;
using System.Data.Objects;
using NorthwindModel;

class ObjectQuerySample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            ObjectQuery<Categories> categoryQuery = context.Categories;

            foreach (Categories category in 
                categoryQuery.Execute(MergeOption.AppendOnly))
            {
                Console.WriteLine("\t{0}\t{1}",
                    category.CategoryID, category.CategoryName);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Data.Objects
Imports NorthwindModel

Class ObjectQuerySample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Dim categoryQuery As ObjectQuery(Of Categories) = context.Categories

            For Each category As Categories In _
                categoryQuery.Execute(MergeOption.AppendOnly)
                Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                    category.CategoryID, category.CategoryName)
            Next
        End Using
    End Sub
End Class
```

### <a name="entityclient"></a><span data-ttu-id="89923-147">EntityClient</span><span class="sxs-lookup"><span data-stu-id="89923-147">EntityClient</span></span>
<span data-ttu-id="89923-148">Kód v tomto příkladu používá <xref:System.Data.EntityClient.EntityCommand> ke spuštění dotazu Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="89923-148">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="89923-149">Tento dotaz vrátí seznam záznamů, které reprezentují instance typu entity categories (kategorie).</span><span class="sxs-lookup"><span data-stu-id="89923-149">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="89923-150">Pro přístup k datovým záznamům v sadě výsledků se používá <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="89923-150">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="89923-151">Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="89923-151">For more information, see [EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).</span></span>

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.EntityClient;
using NorthwindModel;

class EntityClientSample
{
    public static void ExecuteQuery()
    {
        string queryString =
            @"SELECT c.CategoryID, c.CategoryName 
                FROM NorthwindEntities.Categories AS c";

        using (EntityConnection conn =
            new EntityConnection("name=NorthwindEntities"))
        {
            try
            {
                conn.Open();
                using (EntityCommand query = new EntityCommand(queryString, conn))
                {
                    using (DbDataReader rdr = 
                        query.ExecuteReader(CommandBehavior.SequentialAccess))
                    {
                        while (rdr.Read())
                        {
                            Console.WriteLine("\t{0}\t{1}", rdr[0], rdr[1]);
                        }
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Data
Imports System.Data.Common
Imports System.Data.EntityClient
Imports NorthwindModel

Class EntityClientSample
    Public Shared Sub ExecuteQuery()
        Dim queryString As String = _
            "SELECT c.CategoryID, c.CategoryName " & _
                "FROM NorthwindEntities.Categories AS c"

        Using conn As EntityConnection = _
            New EntityConnection("name=NorthwindEntities")

            Try
                conn.Open()
                Using query As EntityCommand = _
                New EntityCommand(queryString, conn)
                    Using rdr As DbDataReader = _
                        query.ExecuteReader(CommandBehavior.SequentialAccess)
                        While rdr.Read()
                            Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                                              rdr(0), rdr(1))
                        End While
                    End Using
                End Using
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using 
    End Sub
End Class
```

## <a name="linq-to-sql"></a><span data-ttu-id="89923-152">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="89923-152">LINQ to SQL</span></span>
<span data-ttu-id="89923-153">Kód v tomto příkladu používá dotaz LINQ, který vrací data jako objekty kategorií, které jsou probíhají jako anonymní typ, který obsahuje pouze vlastnosti CategoryID a CategoryName.</span><span class="sxs-lookup"><span data-stu-id="89923-153">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="89923-154">Tento příklad je založen na kontextu dat Northwind.</span><span class="sxs-lookup"><span data-stu-id="89923-154">This example is based on the Northwind data context.</span></span> <span data-ttu-id="89923-155">Další informace najdete v tématu [Začínáme](./sql/linq/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="89923-155">For more information, see [Getting Started](./sql/linq/getting-started.md).</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Northwind;

    class LinqSqlSample
    {
        public static void ExecuteQuery()
        {
            using (NorthwindDataContext db = new NorthwindDataContext())
            {
                try
                {
                    var query = from category in db.Categories
                                select new
                                {
                                    categoryID = category.CategoryID,
                                    categoryName = category.CategoryName
                                };

                    foreach (var categoryInfo in query)
                    {
                        Console.WriteLine("vbTab {0} vbTab {1}",
                            categoryInfo.categoryID, categoryInfo.categoryName);
                    }
                }
                catch (Exception ex)
                {
                    Console.WriteLine(ex.Message);
                }
            }
        }
    }
```

```vb
Option Explicit On
Option Strict On

Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports Northwind

Class LinqSqlSample
    Public Shared Sub ExecuteQuery()
        Using db As NorthwindDataContext = New NorthwindDataContext()
            Try
                Dim query = From category In db.Categories _
                                Select New With _
                                { _
                                    .categoryID = category.CategoryID, _
                                    .categoryName = category.CategoryName _
                                }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                            categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
            End Using 
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="89923-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89923-156">See also</span></span>

- [<span data-ttu-id="89923-157">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="89923-157">ADO.NET Overview</span></span>](ado-net-overview.md)
- [<span data-ttu-id="89923-158">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="89923-158">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- <span data-ttu-id="89923-159">[Vytváření datových aplikací](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="89923-159">[Creating Data Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span></span>
- <span data-ttu-id="89923-160">[Dotazování na model EDM (Entity Data Model) (úlohy Entity Framework)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="89923-160">[Querying an Entity Data Model (Entity Framework Tasks)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span></span>
- <span data-ttu-id="89923-161">[Postupy: provedení dotazu, který vrací objekty anonymního typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="89923-161">[How to: Execute a Query that Returns Anonymous Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>
