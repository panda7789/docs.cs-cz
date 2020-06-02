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
# <a name="adonet-code-examples"></a>Příklady kódu ADO.NET

Výpisy kódu na této stránce ukazují, jak načíst data z databáze pomocí následujících ADO.NET technologií:

- Poskytovatelé dat ADO.NET:

  - [SqlClient](#sqlclient) ( `System.Data.SqlClient` )

  - [OLEDB](#oledb) ( `System.Data.OleDb` )

  - [ODBC](#odbc) ( `System.Data.Odbc` )

  - [OracleClient](#oracleclient) ( `System.Data.OracleClient` )

- ADO.NET Entity Framework:

  - [LINQ to Entities](#linq-to-entities)

  - [Typové ObjectQuery](#typed-objectquery)

  - [Zprostředkovatel EntityClient](#entityclient) ( `System.Data.EntityClient` )

- [Technologie LINQ to SQL](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a>Příklady poskytovatele dat ADO.NET
Následující výpisy kódu ukazují, jak načíst data z databáze pomocí zprostředkovatelů dat ADO.NET. Data jsou vrácena v `DataReader` . Další informace najdete v tématu [načtení dat pomocí objektu DataReader](retrieving-data-using-a-datareader.md).

### <a name="sqlclient"></a>SqlClient
Kód v tomto příkladu předpokládá, že se můžete připojit k `Northwind` ukázkové databázi na Microsoft SQL Server. Kód vytvoří <xref:System.Data.SqlClient.SqlCommand> pro výběr řádků z tabulky Products, přidáním a <xref:System.Data.SqlClient.SqlParameter> omezí výsledky na řádky s jednotkou JednotkováCena větší, než je zadaná hodnota parametru, v tomto případě 5. <xref:System.Data.SqlClient.SqlConnection>Je otevřen v rámci `using` bloku, který zajišťuje, že se prostředky zavřou a odstraní při ukončení kódu. Kód spustí příkaz pomocí a <xref:System.Data.SqlClient.SqlDataReader> zobrazí výsledky v okně konzoly.

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a>OleDb
Kód v tomto příkladu předpokládá, že se můžete připojit k ukázkové databázi Northwind aplikace Microsoft Access. Kód vytvoří <xref:System.Data.OleDb.OleDbCommand> pro výběr řádků z tabulky Products, přidáním a <xref:System.Data.OleDb.OleDbParameter> omezí výsledky na řádky s jednotkou JednotkováCena větší, než je zadaná hodnota parametru, v tomto případě 5. <xref:System.Data.OleDb.OleDbConnection>Je otevřen uvnitř `using` bloku, který zajišťuje, že se prostředky zavřou a odstraní při ukončení kódu. Kód spustí příkaz pomocí a <xref:System.Data.OleDb.OleDbDataReader> zobrazí výsledky v okně konzoly.

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a>ODBC
Kód v tomto příkladu předpokládá, že se můžete připojit k ukázkové databázi Northwind aplikace Microsoft Access. Kód vytvoří <xref:System.Data.Odbc.OdbcCommand> pro výběr řádků z tabulky Products, přidáním a <xref:System.Data.Odbc.OdbcParameter> omezí výsledky na řádky s jednotkou JednotkováCena větší, než je zadaná hodnota parametru, v tomto případě 5. <xref:System.Data.Odbc.OdbcConnection>Je otevřen v rámci `using` bloku, který zajišťuje, že se prostředky zavřou a odstraní při ukončení kódu. Kód spustí příkaz pomocí a <xref:System.Data.Odbc.OdbcDataReader> zobrazí výsledky v okně konzoly.

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)]
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)]

### <a name="oracleclient"></a>OracleClient
Kód v tomto příkladu předpokládá připojení k UKÁZCE. ZÁKAZNÍK na serveru Oracle. Musíte také přidat odkaz na System. data. OracleClient. dll. Kód vrátí data v <xref:System.Data.OracleClient.OracleDataReader> .

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a>Příklady Entity Framework
Následující výpisy kódu ukazují, jak načíst data ze zdroje dat pomocí dotazu na entity v model EDM (Entity Data Model) (EDM). V těchto příkladech se používá model založený na ukázkové databázi Northwind. Další informace o Entity Framework najdete v tématu [Entity Framework Overview](./ef/overview.md).

### <a name="linq-to-entities"></a>LINQ to Entities
Kód v tomto příkladu používá dotaz LINQ, který vrací data jako objekty kategorií, které jsou probíhají jako anonymní typ, který obsahuje pouze vlastnosti CategoryID a CategoryName. Další informace najdete v tématu [přehled LINQ to Entities](./ef/language-reference/linq-to-entities.md).

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

### <a name="typed-objectquery"></a>Typové ObjectQuery
Kód v tomto příkladě používá <xref:System.Data.Objects.ObjectQuery%601> k vrácení dat jako objektů kategorií. Další informace najdete v tématu [dotazy na objekty](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).

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

### <a name="entityclient"></a>EntityClient
Kód v tomto příkladu používá <xref:System.Data.EntityClient.EntityCommand> ke spuštění dotazu Entity SQL. Tento dotaz vrátí seznam záznamů, které reprezentují instance typu entity categories (kategorie). <xref:System.Data.EntityClient.EntityDataReader>Slouží k přístupu k datovým záznamům v sadě výsledků. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).

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

## <a name="linq-to-sql"></a>Technologie LINQ to SQL
Kód v tomto příkladu používá dotaz LINQ, který vrací data jako objekty kategorií, které jsou probíhají jako anonymní typ, který obsahuje pouze vlastnosti CategoryID a CategoryName. Tento příklad je založen na kontextu dat Northwind. Další informace najdete v tématu [Začínáme](./sql/linq/getting-started.md).

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

## <a name="see-also"></a>Viz také

- [Přehled ADO.NET](ado-net-overview.md)
- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)
- [Vytváření datových aplikací](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))
- [Dotazování na model EDM (Entity Data Model) (úlohy Entity Framework)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))
- [Postupy: provedení dotazu, který vrací objekty anonymního typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))
