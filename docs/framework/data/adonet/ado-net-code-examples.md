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
# <a name="adonet-code-examples"></a>ADO.NET příklady kódu
Výpisy kódu v tomto tématu ukazují, jak načíst data z databáze pomocí následujících technologií ADO.NET:

- ADO.NET poskytovatelé dat:

  - [SqlClient](#sqlclient) `System.Data.SqlClient`( )

  - [OleDb](#oledb) `System.Data.OleDb`( )

  - [Odbc](#odbc) `System.Data.Odbc`( )

  - [Klient](#oracleclient) Oracle`System.Data.OracleClient`( )

- ADO.NET entity:

  - [LINQ to Entities](#linq-to-entities)

  - [Zadaný objektový dotaz](#typed-objectquery)

  - [EntityClient](#entityclient) `System.Data.EntityClient`( )

- [Technologie LINQ to SQL](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a>ADO.NET příklady poskytovatelů dat
Následující výpisy kódu ukazují, jak načíst data z databáze pomocí ADO.NET zprostředkovatelů dat. Data jsou vrácena `DataReader`v . Další informace naleznete v [tématu Načítání dat pomocí datareader](retrieving-data-using-a-datareader.md).

### <a name="sqlclient"></a>Sqlclient
Kód v tomto příkladu předpokládá, že `Northwind` se můžete připojit k ukázkové databázi na serveru Microsoft SQL Server. Kód vytvoří <xref:System.Data.SqlClient.SqlCommand> pro výběr řádků z tabulky <xref:System.Data.SqlClient.SqlParameter> Produkty, přidáním a omezit výsledky na řádky s UnitPrice větší než zadaná hodnota parametru, v tomto případě 5. Je <xref:System.Data.SqlClient.SqlConnection> otevřen uvnitř `using` bloku, který zajišťuje, že prostředky jsou uzavřeny a uvolněny při ukončení kódu. Kód provede příkaz pomocí <xref:System.Data.SqlClient.SqlDataReader>aplikace a zobrazí výsledky v okně konzoly.

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a>OleDb
Kód v tomto příkladu předpokládá, že se můžete připojit k ukázkové databázi Aplikace Microsoft Access Northwind. Kód vytvoří <xref:System.Data.OleDb.OleDbCommand> pro výběr řádků z tabulky <xref:System.Data.OleDb.OleDbParameter> Produkty, přidáním a omezit výsledky na řádky s UnitPrice větší než zadaná hodnota parametru, v tomto případě 5. Je <xref:System.Data.OleDb.OleDbConnection> otevřen uvnitř `using` bloku, který zajišťuje, že prostředky jsou uzavřeny a uvolněny při ukončení kódu. Kód provede příkaz pomocí <xref:System.Data.OleDb.OleDbDataReader>aplikace a zobrazí výsledky v okně konzoly.

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a>Odbc
Kód v tomto příkladu předpokládá, že se můžete připojit k ukázkové databázi Aplikace Microsoft Access Northwind. Kód vytvoří <xref:System.Data.Odbc.OdbcCommand> pro výběr řádků z tabulky <xref:System.Data.Odbc.OdbcParameter> Produkty, přidáním a omezit výsledky na řádky s UnitPrice větší než zadaná hodnota parametru, v tomto případě 5. Je <xref:System.Data.Odbc.OdbcConnection> otevřen uvnitř `using` bloku, který zajišťuje, že prostředky jsou uzavřeny a uvolněny při ukončení kódu. Kód provede příkaz pomocí <xref:System.Data.Odbc.OdbcDataReader>aplikace a zobrazí výsledky v okně konzoly.

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)]
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)]

### <a name="oracleclient"></a>Klient Oracle
Kód v tomto příkladu předpokládá připojení k DEMO. zákazníka na serveru Oracle. Je také nutné přidat odkaz na soubor System.Data.OracleClient.dll. Kód vrátí data v <xref:System.Data.OracleClient.OracleDataReader>.

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a>Příklady rámce entit
Následující výpisy kódu ukazují, jak načíst data ze zdroje dat dotazováním entit v datovém modelu entity (EDM). Tyto příklady používají model založený na ukázkové databázi Northwind. Další informace o rozhraní Entity Framework naleznete v [tématu Přehled rozhraní entity](./ef/overview.md).

### <a name="linq-to-entities"></a>LINQ to Entities
Kód v tomto příkladu používá dotaz LINQ k vrácení dat jako objekty Categories, které jsou promítány jako anonymní typ, který obsahuje pouze vlastnosti CategoryID a CategoryName. Další informace naleznete v tématu [LINQ to Entities Overview](./ef/language-reference/linq-to-entities.md).

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

### <a name="typed-objectquery"></a>Zadaný objektový dotaz
Kód v tomto příkladu používá k <xref:System.Data.Objects.ObjectQuery%601> vrácení dat jako kategorie objekty. Další informace naleznete v [tématu Objektové dotazy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).

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

### <a name="entityclient"></a>EntitaKlient
Kód v tomto příkladu používá an <xref:System.Data.EntityClient.EntityCommand> ke spuštění dotazu SQL entity. Tento dotaz vrátí seznam záznamů, které představují instance typu entity Kategorie. A <xref:System.Data.EntityClient.EntityDataReader> slouží k přístupu k datovým záznamům v sadě výsledků. Další informace naleznete [v tématu EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).

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
Kód v tomto příkladu používá dotaz LINQ k vrácení dat jako objekty Categories, které jsou promítány jako anonymní typ, který obsahuje pouze vlastnosti CategoryID a CategoryName. Tento příklad je založen na kontextu dat Northwind. Další informace naleznete v [tématu Začínáme](./sql/linq/getting-started.md).

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
- [Dotazování datového modelu entity (úlohy architektury entit)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))
- [Postup: Spuštění dotazu, který vrací anonymní objekty typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))
