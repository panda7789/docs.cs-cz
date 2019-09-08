---
title: Data FILESTREAM
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: 87bed5dd345c240cc00b2c36aa976ec53fe63b93
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794092"
---
# <a name="filestream-data"></a>Data FILESTREAM

Atribut úložiště FILESTREAM je pro binární data (BLOB) uložená ve sloupci varbinary (max). Před FILESTREAM ukládá binární data požadovaná speciální zpracování. Nestrukturovaná data, jako jsou textové dokumenty, obrázky a videa, se často ukládají mimo databázi, což usnadňuje správu.

> [!NOTE]
> Abyste mohli pracovat s daty FILESTREAM pomocí SqlClient, musíte nainstalovat .NET Framework 3,5 SP1 (nebo novější).

Zadání atributu FILESTREAM u sloupce varbinary (max) způsobí, že SQL Server ukládat data do místního systému souborů NTFS místo do databázového souboru. I když je uložen samostatně, můžete použít stejné příkazy jazyka Transact-SQL, které jsou podporovány pro práci s daty varbinary (max) uloženými v databázi.

## <a name="sqlclient-support-for-filestream"></a>Podpora SqlClient pro FILESTREAM

Zprostředkovatel dat .NET Framework pro SQL Server, <xref:System.Data.SqlClient>podporuje čtení a zápis dat FILESTREAM <xref:System.Data.SqlTypes.SqlFileStream> pomocí třídy definované v <xref:System.Data.SqlTypes> oboru názvů. `SqlFileStream`dědí z <xref:System.IO.Stream> třídy, která poskytuje metody pro čtení a zápis do datových proudů. Čtení z datového proudu přenáší data z datového proudu do datové struktury, jako je například pole bajtů. Zápis přenáší data z datové struktury do datového proudu.

### <a name="creating-the-sql-server-table"></a>Vytvoření tabulky SQL Server

Následující příkazy jazyka Transact-SQL vytvoří tabulku s názvem zaměstnanci a vloží řádek dat. Po povolení úložiště FILESTREAM můžete tuto tabulku použít ve spojení s příklady kódu, které následují. Odkazy na prostředky v SQL Server Knihy online najdete na konci tohoto tématu.

```sql
CREATE TABLE employees
(
  EmployeeId INT  NOT NULL  PRIMARY KEY,
  Photo VARBINARY(MAX) FILESTREAM  NULL,
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL
  UNIQUE DEFAULT NEWID()
)
GO
Insert into employees
Values(1, 0x00, default)
GO
```

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>Příklad: Čtení, přepsání a vkládání dat FILESTREAM

Následující příklad ukazuje, jak číst data z FILESTREAM. Kód získá `FileAccess` logickou cestu k souboru, nastaví na `Read` a `FileOptions` `SequentialScan`hodnotu na. Kód pak přečte bajty z SqlFileStream do vyrovnávací paměti. Bajty se pak zapíší do okna konzoly.

Ukázka také ukazuje, jak zapisovat data do FILESTREAM, ve kterém jsou přepsána všechna stávající data. Kód Získá logickou cestu k souboru a vytvoří `SqlFileStream`, `FileAccess` nastaví `Write` na a `FileOptions` `SequentialScan`na. Do rozhraní `SqlFileStream`se zapíše jeden bajt, který nahradí všechna data v souboru.

Ukázka také ukazuje, jak zapisovat data do FILESTREAM pomocí metody Seek pro připojení dat na konec souboru. Kód Získá logickou cestu k souboru a vytvoří `SqlFileStream`, `FileAccess` nastaví `ReadWrite` na a `FileOptions` `SequentialScan`na. Kód používá metodu hledání k hledání na konec souboru a připojuje k existujícímu souboru jeden bajt.

```csharp
using System;
using System.Data.SqlClient;
using System.Data.SqlTypes;
using System.Data;
using System.IO;

namespace FileStreamTest
{
    class Program
    {
        static void Main(string[] args)
        {
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");
            ReadFileStream(builder);
            OverwriteFileStream(builder);
            InsertFileStream(builder);

            Console.WriteLine("Done");
        }

        private static void ReadFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for the file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Read the contents as bytes and write them to the console
                            for (long index = 0; index < fileStream.Length; index++)
                            {
                                Console.WriteLine(fileStream.ReadByte());
                            }
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void OverwriteFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Write a single byte to the file. This will
                            // replace any data in the file.
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void InsertFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.ReadWrite, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Seek to the end of the file
                            fileStream.Seek(0, SeekOrigin.End);

                            // Append a single byte
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }

        }
    }
}
```

Další ukázku najdete v tématu [jak ukládat a načítat binární data do sloupce datového proudu souborů](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).

## <a name="resources-in-sql-server-books-online"></a>Prostředky v SQL Server Knihy online

Kompletní dokumentace pro FILESTREAM je k dispozici v následujících částech SQL Server Knihy online.

|Téma|Popis|
|-----------|-----------------|
|[FILESTREAM (SQL Server)](/sql/relational-databases/blob/filestream-sql-server)|Popisuje, kdy použít úložiště FILESTREAM a jak integruje SQL Server databázový stroj se systémem souborů NTFS.|
|[Vytváření klientských aplikací pro data FILESTREAM](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|Popisuje funkce rozhraní Windows API pro práci s daty FILESTREAM.|
|[FILESTREAM a další SQL Server funkce](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|Obsahuje informace, pokyny a omezení pro používání dat FILESTREAM s jinými funkcemi SQL Server.|

## <a name="see-also"></a>Viz také:

- [Datové typy SQL Serveru a ADO.NET](sql-server-data-types.md)
- [Načítání a úpravy dat v ADO.NET](../retrieving-and-modifying-data.md)
- [Zabezpečení přístupu ke kódu a ADO.NET](../code-access-security.md)
- [Binární a vysoké hodnoty na SQL Serveru](sql-server-binary-and-large-value-data.md)
- [Přehled ADO.NET](../ado-net-overview.md)
