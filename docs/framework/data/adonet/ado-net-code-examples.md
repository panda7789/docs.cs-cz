---
title: Příklady kódu
description: Tyto příklady ukazují .NET Framework programátory, jak načíst data z databáze pomocí zprostředkovatelů dat ADO.NET a ADO.NET Entity Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 54df0e253716c970cf23446434d96b104b8e9b03
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287165"
---
# <a name="adonet-code-examples"></a><span data-ttu-id="9e222-103">Příklady kódu ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9e222-103">ADO.NET code examples</span></span>

<span data-ttu-id="9e222-104">Výpisy kódu na této stránce ukazují, jak načíst data z databáze pomocí následujících ADO.NET technologií:</span><span class="sxs-lookup"><span data-stu-id="9e222-104">The code listings on this page demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="9e222-105">Poskytovatelé dat ADO.NET:</span><span class="sxs-lookup"><span data-stu-id="9e222-105">ADO.NET data providers:</span></span>

  - <span data-ttu-id="9e222-106">[SqlClient](#sqlclient) ( `System.Data.SqlClient` )</span><span class="sxs-lookup"><span data-stu-id="9e222-106">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="9e222-107">[OLEDB](#oledb) ( `System.Data.OleDb` )</span><span class="sxs-lookup"><span data-stu-id="9e222-107">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="9e222-108">[ODBC](#odbc) ( `System.Data.Odbc` )</span><span class="sxs-lookup"><span data-stu-id="9e222-108">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="9e222-109">[OracleClient](#oracleclient) ( `System.Data.OracleClient` )</span><span class="sxs-lookup"><span data-stu-id="9e222-109">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="9e222-110">ADO.NET Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="9e222-110">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="9e222-111">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9e222-111">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="9e222-112">Typové ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="9e222-112">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="9e222-113">[Zprostředkovatel EntityClient](#entityclient) ( `System.Data.EntityClient` )</span><span class="sxs-lookup"><span data-stu-id="9e222-113">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="9e222-114">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9e222-114">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="9e222-115">Příklady poskytovatele dat ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9e222-115">ADO.NET data provider examples</span></span>
<span data-ttu-id="9e222-116">Následující výpisy kódu ukazují, jak načíst data z databáze pomocí zprostředkovatelů dat ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="9e222-116">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="9e222-117">Data jsou vrácena v `DataReader` .</span><span class="sxs-lookup"><span data-stu-id="9e222-117">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="9e222-118">Další informace najdete v tématu [načtení dat pomocí objektu DataReader](retrieving-data-using-a-datareader.md).</span><span class="sxs-lookup"><span data-stu-id="9e222-118">For more information, see [Retrieving Data Using a DataReader](retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="9e222-119">SqlClient</span><span class="sxs-lookup"><span data-stu-id="9e222-119">SqlClient</span></span>
<span data-ttu-id="9e222-120">Kód v tomto příkladu předpokládá, že se můžete připojit k `Northwind` ukázkové databázi na Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9e222-120">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft SQL Server.</span></span> <span data-ttu-id="9e222-121">Kód vytvoří <xref:System.Data.SqlClient.SqlCommand> pro výběr řádků z tabulky Products, přidáním a <xref:System.Data.SqlClient.SqlParameter> omezí výsledky na řádky s jednotkou JednotkováCena větší, než je zadaná hodnota parametru, v tomto případě 5.</span><span class="sxs-lookup"><span data-stu-id="9e222-121">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="9e222-122"><xref:System.Data.SqlClient.SqlConnection>Je otevřen v rámci `using` bloku, který zajišťuje, že se prostředky zavřou a odstraní při ukončení kódu.</span><span class="sxs-lookup"><span data-stu-id="9e222-122">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="9e222-123">Kód spustí příkaz pomocí a <xref:System.Data.SqlClient.SqlDataReader> zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="9e222-123">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="9e222-124">OleDb</span><span class="sxs-lookup"><span data-stu-id="9e222-124">OleDb</span></span>
<span data-ttu-id="9e222-125">Kód v tomto příkladu předpokládá, že se můžete připojit k ukázkové databázi Northwind aplikace Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="9e222-125">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="9e222-126">Kód vytvoří <xref:System.Data.OleDb.OleDbCommand> pro výběr řádků z tabulky Products, přidáním a <xref:System.Data.OleDb.OleDbParameter> omezí výsledky na řádky s jednotkou JednotkováCena větší, než je zadaná hodnota parametru, v tomto případě 5.</span><span class="sxs-lookup"><span data-stu-id="9e222-126">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="9e222-127"><xref:System.Data.OleDb.OleDbConnection>Je otevřen uvnitř `using` bloku, který zajišťuje, že se prostředky zavřou a odstraní při ukončení kódu.</span><span class="sxs-lookup"><span data-stu-id="9e222-127">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="9e222-128">Kód spustí příkaz pomocí a <xref:System.Data.OleDb.OleDbDataReader> zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="9e222-128">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="9e222-129">ODBC</span><span class="sxs-lookup"><span data-stu-id="9e222-129">Odbc</span></span>
<span data-ttu-id="9e222-130">Kód v tomto příkladu předpokládá, že se můžete připojit k ukázkové databázi Northwind aplikace Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="9e222-130">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="9e222-131">Kód vytvoří <xref:System.Data.Odbc.OdbcCommand> pro výběr řádků z tabulky Products, přidáním a <xref:System.Data.Odbc.OdbcParameter> omezí výsledky na řádky s jednotkou JednotkováCena větší, než je zadaná hodnota parametru, v tomto případě 5.</span><span class="sxs-lookup"><span data-stu-id="9e222-131">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="9e222-132"><xref:System.Data.Odbc.OdbcConnection>Je otevřen v rámci `using` bloku, který zajišťuje, že se prostředky zavřou a odstraní při ukončení kódu.</span><span class="sxs-lookup"><span data-stu-id="9e222-132">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="9e222-133">Kód spustí příkaz pomocí a <xref:System.Data.Odbc.OdbcDataReader> zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="9e222-133">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)]
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)]

### <a name="oracleclient"></a><span data-ttu-id="9e222-134">OracleClient</span><span class="sxs-lookup"><span data-stu-id="9e222-134">OracleClient</span></span>
<span data-ttu-id="9e222-135">Kód v tomto příkladu předpokládá připojení k UKÁZCE. ZÁKAZNÍK na serveru Oracle.</span><span class="sxs-lookup"><span data-stu-id="9e222-135">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="9e222-136">Musíte také přidat odkaz na System. data. OracleClient. dll.</span><span class="sxs-lookup"><span data-stu-id="9e222-136">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="9e222-137">Kód vrátí data v <xref:System.Data.OracleClient.OracleDataReader> .</span><span class="sxs-lookup"><span data-stu-id="9e222-137">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="9e222-138">Příklady Entity Framework</span><span class="sxs-lookup"><span data-stu-id="9e222-138">Entity Framework examples</span></span>
<span data-ttu-id="9e222-139">Následující výpisy kódu ukazují, jak načíst data ze zdroje dat pomocí dotazu na entity v model EDM (Entity Data Model) (EDM).</span><span class="sxs-lookup"><span data-stu-id="9e222-139">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="9e222-140">V těchto příkladech se používá model založený na ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="9e222-140">These examples use a model based on the Northwind sample database.</span></span> <span data-ttu-id="9e222-141">Další informace o Entity Framework najdete v tématu [Entity Framework Overview](./ef/overview.md).</span><span class="sxs-lookup"><span data-stu-id="9e222-141">For more information about Entity Framework, see [Entity Framework Overview](./ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="9e222-142">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9e222-142">LINQ to Entities</span></span>
<span data-ttu-id="9e222-143">Kód v tomto příkladu používá dotaz LINQ, který vrací data jako objekty kategorií, které jsou probíhají jako anonymní typ, který obsahuje pouze vlastnosti CategoryID a CategoryName.</span><span class="sxs-lookup"><span data-stu-id="9e222-143">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="9e222-144">Další informace najdete v tématu [přehled LINQ to Entities](./ef/language-reference/linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="9e222-144">For more information, see [LINQ to Entities Overview](./ef/language-reference/linq-to-entities.md).</span></span>

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

### <a name="typed-objectquery"></a><span data-ttu-id="9e222-145">Typové ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="9e222-145">Typed ObjectQuery</span></span>
<span data-ttu-id="9e222-146">Kód v tomto příkladě používá <xref:System.Data.Objects.ObjectQuery%601> k vrácení dat jako objektů kategorií.</span><span class="sxs-lookup"><span data-stu-id="9e222-146">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="9e222-147">Další informace najdete v tématu [dotazy na objekty](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9e222-147">For more information, see [Object Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span></span>

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

### <a name="entityclient"></a><span data-ttu-id="9e222-148">EntityClient</span><span class="sxs-lookup"><span data-stu-id="9e222-148">EntityClient</span></span>
<span data-ttu-id="9e222-149">Kód v tomto příkladu používá <xref:System.Data.EntityClient.EntityCommand> ke spuštění dotazu Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="9e222-149">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="9e222-150">Tento dotaz vrátí seznam záznamů, které reprezentují instance typu entity categories (kategorie).</span><span class="sxs-lookup"><span data-stu-id="9e222-150">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="9e222-151"><xref:System.Data.EntityClient.EntityDataReader>Slouží k přístupu k datovým záznamům v sadě výsledků.</span><span class="sxs-lookup"><span data-stu-id="9e222-151">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="9e222-152">Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="9e222-152">For more information, see [EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).</span></span>

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

## <a name="linq-to-sql"></a><span data-ttu-id="9e222-153">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9e222-153">LINQ to SQL</span></span>
<span data-ttu-id="9e222-154">Kód v tomto příkladu používá dotaz LINQ, který vrací data jako objekty kategorií, které jsou probíhají jako anonymní typ, který obsahuje pouze vlastnosti CategoryID a CategoryName.</span><span class="sxs-lookup"><span data-stu-id="9e222-154">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="9e222-155">Tento příklad je založen na kontextu dat Northwind.</span><span class="sxs-lookup"><span data-stu-id="9e222-155">This example is based on the Northwind data context.</span></span> <span data-ttu-id="9e222-156">Další informace najdete v tématu [Začínáme](./sql/linq/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="9e222-156">For more information, see [Getting Started](./sql/linq/getting-started.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9e222-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e222-157">See also</span></span>

- [<span data-ttu-id="9e222-158">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9e222-158">ADO.NET Overview</span></span>](ado-net-overview.md)
- [<span data-ttu-id="9e222-159">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9e222-159">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- <span data-ttu-id="9e222-160">[Vytváření datových aplikací](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="9e222-160">[Creating Data Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span></span>
- <span data-ttu-id="9e222-161">[Dotazování na model EDM (Entity Data Model) (úlohy Entity Framework)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9e222-161">[Querying an Entity Data Model (Entity Framework Tasks)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span></span>
- <span data-ttu-id="9e222-162">[Postupy: provedení dotazu, který vrací objekty anonymního typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9e222-162">[How to: Execute a Query that Returns Anonymous Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>
