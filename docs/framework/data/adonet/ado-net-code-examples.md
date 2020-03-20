---
title: Příklady kódu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 8a0a7c6166bb4cfc8064faa20056fda16b593e81
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151764"
---
# <a name="adonet-code-examples"></a><span data-ttu-id="0ecc6-102">ADO.NET příklady kódu</span><span class="sxs-lookup"><span data-stu-id="0ecc6-102">ADO.NET code examples</span></span>
<span data-ttu-id="0ecc6-103">Výpisy kódu v tomto tématu ukazují, jak načíst data z databáze pomocí následujících technologií ADO.NET:</span><span class="sxs-lookup"><span data-stu-id="0ecc6-103">The code listings in this topic demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="0ecc6-104">ADO.NET poskytovatelé dat:</span><span class="sxs-lookup"><span data-stu-id="0ecc6-104">ADO.NET data providers:</span></span>

  - <span data-ttu-id="0ecc6-105">[SqlClient](#sqlclient) `System.Data.SqlClient`( )</span><span class="sxs-lookup"><span data-stu-id="0ecc6-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="0ecc6-106">[OleDb](#oledb) `System.Data.OleDb`( )</span><span class="sxs-lookup"><span data-stu-id="0ecc6-106">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="0ecc6-107">[Odbc](#odbc) `System.Data.Odbc`( )</span><span class="sxs-lookup"><span data-stu-id="0ecc6-107">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="0ecc6-108">[Klient](#oracleclient) Oracle`System.Data.OracleClient`( )</span><span class="sxs-lookup"><span data-stu-id="0ecc6-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="0ecc6-109">ADO.NET entity:</span><span class="sxs-lookup"><span data-stu-id="0ecc6-109">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="0ecc6-110">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0ecc6-110">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="0ecc6-111">Zadaný objektový dotaz</span><span class="sxs-lookup"><span data-stu-id="0ecc6-111">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="0ecc6-112">[EntityClient](#entityclient) `System.Data.EntityClient`( )</span><span class="sxs-lookup"><span data-stu-id="0ecc6-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="0ecc6-113">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0ecc6-113">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="0ecc6-114">ADO.NET příklady poskytovatelů dat</span><span class="sxs-lookup"><span data-stu-id="0ecc6-114">ADO.NET data provider examples</span></span>
<span data-ttu-id="0ecc6-115">Následující výpisy kódu ukazují, jak načíst data z databáze pomocí ADO.NET zprostředkovatelů dat.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-115">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="0ecc6-116">Data jsou vrácena `DataReader`v .</span><span class="sxs-lookup"><span data-stu-id="0ecc6-116">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="0ecc6-117">Další informace naleznete v [tématu Načítání dat pomocí datareader](retrieving-data-using-a-datareader.md).</span><span class="sxs-lookup"><span data-stu-id="0ecc6-117">For more information, see [Retrieving Data Using a DataReader](retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="0ecc6-118">Sqlclient</span><span class="sxs-lookup"><span data-stu-id="0ecc6-118">SqlClient</span></span>
<span data-ttu-id="0ecc6-119">Kód v tomto příkladu předpokládá, že `Northwind` se můžete připojit k ukázkové databázi na serveru Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-119">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft SQL Server.</span></span> <span data-ttu-id="0ecc6-120">Kód vytvoří <xref:System.Data.SqlClient.SqlCommand> pro výběr řádků z tabulky <xref:System.Data.SqlClient.SqlParameter> Produkty, přidáním a omezit výsledky na řádky s UnitPrice větší než zadaná hodnota parametru, v tomto případě 5.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-120">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="0ecc6-121">Je <xref:System.Data.SqlClient.SqlConnection> otevřen uvnitř `using` bloku, který zajišťuje, že prostředky jsou uzavřeny a uvolněny při ukončení kódu.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-121">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="0ecc6-122">Kód provede příkaz pomocí <xref:System.Data.SqlClient.SqlDataReader>aplikace a zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-122">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="0ecc6-123">OleDb</span><span class="sxs-lookup"><span data-stu-id="0ecc6-123">OleDb</span></span>
<span data-ttu-id="0ecc6-124">Kód v tomto příkladu předpokládá, že se můžete připojit k ukázkové databázi Aplikace Microsoft Access Northwind.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-124">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="0ecc6-125">Kód vytvoří <xref:System.Data.OleDb.OleDbCommand> pro výběr řádků z tabulky <xref:System.Data.OleDb.OleDbParameter> Produkty, přidáním a omezit výsledky na řádky s UnitPrice větší než zadaná hodnota parametru, v tomto případě 5.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-125">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="0ecc6-126">Je <xref:System.Data.OleDb.OleDbConnection> otevřen uvnitř `using` bloku, který zajišťuje, že prostředky jsou uzavřeny a uvolněny při ukončení kódu.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-126">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="0ecc6-127">Kód provede příkaz pomocí <xref:System.Data.OleDb.OleDbDataReader>aplikace a zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-127">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="0ecc6-128">Odbc</span><span class="sxs-lookup"><span data-stu-id="0ecc6-128">Odbc</span></span>
<span data-ttu-id="0ecc6-129">Kód v tomto příkladu předpokládá, že se můžete připojit k ukázkové databázi Aplikace Microsoft Access Northwind.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-129">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="0ecc6-130">Kód vytvoří <xref:System.Data.Odbc.OdbcCommand> pro výběr řádků z tabulky <xref:System.Data.Odbc.OdbcParameter> Produkty, přidáním a omezit výsledky na řádky s UnitPrice větší než zadaná hodnota parametru, v tomto případě 5.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-130">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="0ecc6-131">Je <xref:System.Data.Odbc.OdbcConnection> otevřen uvnitř `using` bloku, který zajišťuje, že prostředky jsou uzavřeny a uvolněny při ukončení kódu.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-131">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="0ecc6-132">Kód provede příkaz pomocí <xref:System.Data.Odbc.OdbcDataReader>aplikace a zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-132">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)]
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)]

### <a name="oracleclient"></a><span data-ttu-id="0ecc6-133">Klient Oracle</span><span class="sxs-lookup"><span data-stu-id="0ecc6-133">OracleClient</span></span>
<span data-ttu-id="0ecc6-134">Kód v tomto příkladu předpokládá připojení k DEMO. zákazníka na serveru Oracle.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-134">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="0ecc6-135">Je také nutné přidat odkaz na soubor System.Data.OracleClient.dll.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-135">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="0ecc6-136">Kód vrátí data v <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-136">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="0ecc6-137">Příklady rámce entit</span><span class="sxs-lookup"><span data-stu-id="0ecc6-137">Entity Framework examples</span></span>
<span data-ttu-id="0ecc6-138">Následující výpisy kódu ukazují, jak načíst data ze zdroje dat dotazováním entit v datovém modelu entity (EDM).</span><span class="sxs-lookup"><span data-stu-id="0ecc6-138">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="0ecc6-139">Tyto příklady používají model založený na ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-139">These examples use a model based on the Northwind sample database.</span></span> <span data-ttu-id="0ecc6-140">Další informace o rozhraní Entity Framework naleznete v [tématu Přehled rozhraní entity](./ef/overview.md).</span><span class="sxs-lookup"><span data-stu-id="0ecc6-140">For more information about Entity Framework, see [Entity Framework Overview](./ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="0ecc6-141">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0ecc6-141">LINQ to Entities</span></span>
<span data-ttu-id="0ecc6-142">Kód v tomto příkladu používá dotaz LINQ k vrácení dat jako objekty Categories, které jsou promítány jako anonymní typ, který obsahuje pouze vlastnosti CategoryID a CategoryName.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-142">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="0ecc6-143">Další informace naleznete v tématu [LINQ to Entities Overview](./ef/language-reference/linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="0ecc6-143">For more information, see [LINQ to Entities Overview](./ef/language-reference/linq-to-entities.md).</span></span>

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

### <a name="typed-objectquery"></a><span data-ttu-id="0ecc6-144">Zadaný objektový dotaz</span><span class="sxs-lookup"><span data-stu-id="0ecc6-144">Typed ObjectQuery</span></span>
<span data-ttu-id="0ecc6-145">Kód v tomto příkladu používá k <xref:System.Data.Objects.ObjectQuery%601> vrácení dat jako kategorie objekty.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-145">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="0ecc6-146">Další informace naleznete v [tématu Objektové dotazy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0ecc6-146">For more information, see [Object Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span></span>

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

### <a name="entityclient"></a><span data-ttu-id="0ecc6-147">EntitaKlient</span><span class="sxs-lookup"><span data-stu-id="0ecc6-147">EntityClient</span></span>
<span data-ttu-id="0ecc6-148">Kód v tomto příkladu používá an <xref:System.Data.EntityClient.EntityCommand> ke spuštění dotazu SQL entity.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-148">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="0ecc6-149">Tento dotaz vrátí seznam záznamů, které představují instance typu entity Kategorie.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-149">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="0ecc6-150">A <xref:System.Data.EntityClient.EntityDataReader> slouží k přístupu k datovým záznamům v sadě výsledků.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-150">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="0ecc6-151">Další informace naleznete [v tématu EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="0ecc6-151">For more information, see [EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).</span></span>

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

## <a name="linq-to-sql"></a><span data-ttu-id="0ecc6-152">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0ecc6-152">LINQ to SQL</span></span>
<span data-ttu-id="0ecc6-153">Kód v tomto příkladu používá dotaz LINQ k vrácení dat jako objekty Categories, které jsou promítány jako anonymní typ, který obsahuje pouze vlastnosti CategoryID a CategoryName.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-153">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="0ecc6-154">Tento příklad je založen na kontextu dat Northwind.</span><span class="sxs-lookup"><span data-stu-id="0ecc6-154">This example is based on the Northwind data context.</span></span> <span data-ttu-id="0ecc6-155">Další informace naleznete v [tématu Začínáme](./sql/linq/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="0ecc6-155">For more information, see [Getting Started](./sql/linq/getting-started.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0ecc6-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ecc6-156">See also</span></span>

- [<span data-ttu-id="0ecc6-157">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0ecc6-157">ADO.NET Overview</span></span>](ado-net-overview.md)
- [<span data-ttu-id="0ecc6-158">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0ecc6-158">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- <span data-ttu-id="0ecc6-159">[Vytváření datových aplikací](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="0ecc6-159">[Creating Data Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span></span>
- <span data-ttu-id="0ecc6-160">[Dotazování datového modelu entity (úlohy architektury entit)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0ecc6-160">[Querying an Entity Data Model (Entity Framework Tasks)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span></span>
- <span data-ttu-id="0ecc6-161">[Postup: Spuštění dotazu, který vrací anonymní objekty typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0ecc6-161">[How to: Execute a Query that Returns Anonymous Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>
