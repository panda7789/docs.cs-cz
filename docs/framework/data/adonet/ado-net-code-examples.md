---
title: "Příklady kódu pro technologii ADO.NET"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-ado
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fcdfee8486b089456d294d983c09dc6246bd8ac2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="adonet-code-examples"></a><span data-ttu-id="46b1c-102">Příklady kódu pro technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="46b1c-102">ADO.NET code examples</span></span>
<span data-ttu-id="46b1c-103">Příklady kódu v tomto tématu ukazují, jak načíst data z databáze pomocí následující technologie ADO.NET:</span><span class="sxs-lookup"><span data-stu-id="46b1c-103">The code listings in this topic demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="46b1c-104">Zprostředkovatelé dat ADO.NET:</span><span class="sxs-lookup"><span data-stu-id="46b1c-104">ADO.NET data providers:</span></span>

  - <span data-ttu-id="46b1c-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span><span class="sxs-lookup"><span data-stu-id="46b1c-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="46b1c-106">[OleDb](#oledb) (`System.Data.OleDb`)</span><span class="sxs-lookup"><span data-stu-id="46b1c-106">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="46b1c-107">[ODBC](#odbc) (`System.Data.Odbc`)</span><span class="sxs-lookup"><span data-stu-id="46b1c-107">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="46b1c-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span><span class="sxs-lookup"><span data-stu-id="46b1c-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="46b1c-109">ADO.NET Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="46b1c-109">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="46b1c-110">Technologie LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="46b1c-110">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="46b1c-111">Zadaný objekt ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="46b1c-111">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="46b1c-112">[Zprostředkovatel EntityClient](#entityclient) (`System.Data.EntityClient`)</span><span class="sxs-lookup"><span data-stu-id="46b1c-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="46b1c-113">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="46b1c-113">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="46b1c-114">Příklady zprostředkovatele dat ADO.NET</span><span class="sxs-lookup"><span data-stu-id="46b1c-114">ADO.NET data provider examples</span></span>
<span data-ttu-id="46b1c-115">Následující příklady kódu ukazují, jak k načtení dat z databáze pomocí zprostředkovatele dat ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="46b1c-115">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="46b1c-116">Data jsou vrácena v `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="46b1c-116">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="46b1c-117">Další informace najdete v tématu [načítání dat pomocí DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).</span><span class="sxs-lookup"><span data-stu-id="46b1c-117">For more information, see [Retrieving Data Using a DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="46b1c-118">SqlClient</span><span class="sxs-lookup"><span data-stu-id="46b1c-118">SqlClient</span></span>
<span data-ttu-id="46b1c-119">Kód v tomto příkladu se předpokládá, že se může připojit k `Northwind` ukázkovou databázi na Microsoft [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46b1c-119">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="46b1c-120">Kód vytvoří <xref:System.Data.SqlClient.SqlCommand> pro výběr řádků z tabulky produktů, přidávání <xref:System.Data.SqlClient.SqlParameter> omezit výsledky na řádky s UnitPrice větší než je zadaná hodnota parametru, v takovém případě 5.</span><span class="sxs-lookup"><span data-stu-id="46b1c-120">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="46b1c-121"><xref:System.Data.SqlClient.SqlConnection> Je otevřen uvnitř `using` blok, který zajišťuje, že jsou prostředky uzavřený a uvolněno při ukončení kód.</span><span class="sxs-lookup"><span data-stu-id="46b1c-121">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="46b1c-122">Kód spustí příkaz pomocí <xref:System.Data.SqlClient.SqlDataReader>a zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="46b1c-122">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="46b1c-123">OleDb</span><span class="sxs-lookup"><span data-stu-id="46b1c-123">OleDb</span></span>
<span data-ttu-id="46b1c-124">Kód v tomto příkladu se předpokládá, zda se můžete připojit k ukázkové databázi Northwind přístup společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="46b1c-124">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="46b1c-125">Kód vytvoří <xref:System.Data.OleDb.OleDbCommand> pro výběr řádků z tabulky produktů, přidávání <xref:System.Data.OleDb.OleDbParameter> omezit výsledky na řádky s UnitPrice větší než je zadaná hodnota parametru, v takovém případě 5.</span><span class="sxs-lookup"><span data-stu-id="46b1c-125">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="46b1c-126"><xref:System.Data.OleDb.OleDbConnection> Je otevřen uvnitř `using` blok, který zajišťuje, že jsou prostředky uzavřený a uvolněno při ukončení kód.</span><span class="sxs-lookup"><span data-stu-id="46b1c-126">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="46b1c-127">Kód spustí příkaz pomocí <xref:System.Data.OleDb.OleDbDataReader>a zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="46b1c-127">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="46b1c-128">Rozhraní ODBC</span><span class="sxs-lookup"><span data-stu-id="46b1c-128">Odbc</span></span>
<span data-ttu-id="46b1c-129">Kód v tomto příkladu se předpokládá, zda se můžete připojit k ukázkové databázi Northwind přístup společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="46b1c-129">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="46b1c-130">Kód vytvoří <xref:System.Data.Odbc.OdbcCommand> pro výběr řádků z tabulky produktů, přidávání <xref:System.Data.Odbc.OdbcParameter> omezit výsledky na řádky s UnitPrice větší než je zadaná hodnota parametru, v takovém případě 5.</span><span class="sxs-lookup"><span data-stu-id="46b1c-130">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="46b1c-131"><xref:System.Data.Odbc.OdbcConnection> Je otevřen uvnitř `using` blok, který zajišťuje, že jsou prostředky uzavřený a uvolněno při ukončení kód.</span><span class="sxs-lookup"><span data-stu-id="46b1c-131">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="46b1c-132">Kód spustí příkaz pomocí <xref:System.Data.Odbc.OdbcDataReader>a zobrazí výsledky v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="46b1c-132">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)] 
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)] 

### <a name="oracleclient"></a><span data-ttu-id="46b1c-133">OracleClient</span><span class="sxs-lookup"><span data-stu-id="46b1c-133">OracleClient</span></span>
<span data-ttu-id="46b1c-134">Kód v tomto příkladu se předpokládá připojení k UKÁZCE. Zákazník na serveru Oracle.</span><span class="sxs-lookup"><span data-stu-id="46b1c-134">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="46b1c-135">Musíte taky přidat odkaz na System.Data.OracleClient.dll.</span><span class="sxs-lookup"><span data-stu-id="46b1c-135">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="46b1c-136">Kód vrátí data v <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="46b1c-136">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="46b1c-137">Příklady Entity Framework</span><span class="sxs-lookup"><span data-stu-id="46b1c-137">Entity Framework examples</span></span>
<span data-ttu-id="46b1c-138">Následující příklady kódu ukazují, jak načíst data ze zdroje dat pomocí dotazu na entity v Entity Data Model (EDM).</span><span class="sxs-lookup"><span data-stu-id="46b1c-138">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="46b1c-139">Pomocí těchto příkladech [Northwind modelu](http://msdn.microsoft.com/74521f8c-e974-48cb-8858-c08deff52638).</span><span class="sxs-lookup"><span data-stu-id="46b1c-139">These examples use the [Northwind model](http://msdn.microsoft.com/74521f8c-e974-48cb-8858-c08deff52638).</span></span> <span data-ttu-id="46b1c-140">Další informace najdete v tématu [Entity Framework přehled](../../../../docs/framework/data/adonet/ef/overview.md).</span><span class="sxs-lookup"><span data-stu-id="46b1c-140">For more information, see [Entity Framework Overview](../../../../docs/framework/data/adonet/ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="46b1c-141">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="46b1c-141">LINQ to Entities</span></span>
<span data-ttu-id="46b1c-142">Kód v tomto příkladu používá dotaz LINQ jako kategorie objekty, které jsou k projekci jako anonymní typ, který obsahuje pouze vlastnosti CategoryID a CategoryName vrátit data.</span><span class="sxs-lookup"><span data-stu-id="46b1c-142">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="46b1c-143">Další informace najdete v tématu [technologie LINQ to Entities přehled](http://msdn.microsoft.com/86d87a27-c17a-45ac-b28d-72c8500333c6).</span><span class="sxs-lookup"><span data-stu-id="46b1c-143">For more information, see [LINQ to Entities Overview](http://msdn.microsoft.com/86d87a27-c17a-45ac-b28d-72c8500333c6).</span></span>

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

Imports System
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

### <a name="typed-objectquery"></a><span data-ttu-id="46b1c-144">Zadaný objekt ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="46b1c-144">Typed ObjectQuery</span></span>
<span data-ttu-id="46b1c-145">Kód v tomto příkladu používá <xref:System.Data.Objects.ObjectQuery%601> vrátit data jako objekty kategorií.</span><span class="sxs-lookup"><span data-stu-id="46b1c-145">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="46b1c-146">Další informace najdete v tématu [objekt dotazy](http://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276).</span><span class="sxs-lookup"><span data-stu-id="46b1c-146">For more information, see [Object Queries](http://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276).</span></span>

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

Imports System
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

### <a name="entityclient"></a><span data-ttu-id="46b1c-147">Zprostředkovatel EntityClient</span><span class="sxs-lookup"><span data-stu-id="46b1c-147">EntityClient</span></span>
<span data-ttu-id="46b1c-148">Kód v tomto příkladu používá <xref:System.Data.EntityClient.EntityCommand> k provedení příkazu jazyka Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="46b1c-148">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="46b1c-149">Tento dotaz vrací seznam záznamů, které představují instance kategorie typu entity.</span><span class="sxs-lookup"><span data-stu-id="46b1c-149">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="46b1c-150"><xref:System.Data.EntityClient.EntityDataReader> Se používá pro přístup k datové záznamy v sadě výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="46b1c-150">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="46b1c-151">Další informace najdete v tématu [zprostředkovatel EntityClient rozhraní Entity Framework](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="46b1c-151">For more information, see [EntityClient Provider for the Entity Framework](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>

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

Imports System
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

## <a name="linq-to-sql"></a><span data-ttu-id="46b1c-152">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="46b1c-152">LINQ to SQL</span></span>
<span data-ttu-id="46b1c-153">Kód v tomto příkladu používá dotaz LINQ jako kategorie objekty, které jsou k projekci jako anonymní typ, který obsahuje pouze vlastnosti CategoryID a CategoryName vrátit data.</span><span class="sxs-lookup"><span data-stu-id="46b1c-153">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="46b1c-154">Tento příklad vychází kontext Northwind data.</span><span class="sxs-lookup"><span data-stu-id="46b1c-154">This example is based on the Northwind data context.</span></span> <span data-ttu-id="46b1c-155">Další informace najdete v tématu [Začínáme](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="46b1c-155">For more information, see [Getting Started](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).</span></span>

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

Imports System
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

## <a name="see-also"></a><span data-ttu-id="46b1c-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="46b1c-156">See also</span></span>
 [<span data-ttu-id="46b1c-157">ADO.NET – přehled</span><span class="sxs-lookup"><span data-stu-id="46b1c-157">ADO.NET Overview</span></span>](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [<span data-ttu-id="46b1c-158">Načítání a upravovat Data v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="46b1c-158">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="46b1c-159">Vytváření datových aplikací</span><span class="sxs-lookup"><span data-stu-id="46b1c-159">Creating Data Applications</span></span>](http://msdn.microsoft.com/library/ab334d5f-4f49-4346-bce0-3325d6130b3e)  
 [<span data-ttu-id="46b1c-160">Dotaz na datový Model Entity (úlohy Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="46b1c-160">Querying an Entity Data Model (Entity Framework Tasks)</span></span>](http://msdn.microsoft.com/187f1caa-e4d3-4e31-bd99-5d5c2b329c77)  
 [<span data-ttu-id="46b1c-161">Postup: provedení dotazu, který vrátí objekty anonymního typu</span><span class="sxs-lookup"><span data-stu-id="46b1c-161">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](http://msdn.microsoft.com/3b264025-e911-4d73-90ce-992d2b9d189d)  
 [<span data-ttu-id="46b1c-162">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="46b1c-162">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)  
