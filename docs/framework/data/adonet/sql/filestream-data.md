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
# <a name="filestream-data"></a><span data-ttu-id="351ef-102">Data FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="351ef-102">FILESTREAM Data</span></span>

<span data-ttu-id="351ef-103">Atribut úložiště FILESTREAM je pro binární data (BLOB) uložená ve sloupci varbinary (max).</span><span class="sxs-lookup"><span data-stu-id="351ef-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="351ef-104">Před FILESTREAM ukládá binární data požadovaná speciální zpracování.</span><span class="sxs-lookup"><span data-stu-id="351ef-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="351ef-105">Nestrukturovaná data, jako jsou textové dokumenty, obrázky a videa, se často ukládají mimo databázi, což usnadňuje správu.</span><span class="sxs-lookup"><span data-stu-id="351ef-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>

> [!NOTE]
> <span data-ttu-id="351ef-106">Abyste mohli pracovat s daty FILESTREAM pomocí SqlClient, musíte nainstalovat .NET Framework 3,5 SP1 (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="351ef-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>

<span data-ttu-id="351ef-107">Zadání atributu FILESTREAM u sloupce varbinary (max) způsobí, že SQL Server ukládat data do místního systému souborů NTFS místo do databázového souboru.</span><span class="sxs-lookup"><span data-stu-id="351ef-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="351ef-108">I když je uložen samostatně, můžete použít stejné příkazy jazyka Transact-SQL, které jsou podporovány pro práci s daty varbinary (max) uloženými v databázi.</span><span class="sxs-lookup"><span data-stu-id="351ef-108">Although it is stored separately, you can use the same Transact-SQL statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>

## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="351ef-109">Podpora SqlClient pro FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="351ef-109">SqlClient Support for FILESTREAM</span></span>

<span data-ttu-id="351ef-110">Zprostředkovatel dat .NET Framework pro SQL Server, <xref:System.Data.SqlClient>podporuje čtení a zápis dat FILESTREAM <xref:System.Data.SqlTypes.SqlFileStream> pomocí třídy definované v <xref:System.Data.SqlTypes> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="351ef-110">The .NET Framework Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="351ef-111">`SqlFileStream`dědí z <xref:System.IO.Stream> třídy, která poskytuje metody pro čtení a zápis do datových proudů.</span><span class="sxs-lookup"><span data-stu-id="351ef-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="351ef-112">Čtení z datového proudu přenáší data z datového proudu do datové struktury, jako je například pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="351ef-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="351ef-113">Zápis přenáší data z datové struktury do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="351ef-113">Writing transfers the data from the data structure into a stream.</span></span>

### <a name="creating-the-sql-server-table"></a><span data-ttu-id="351ef-114">Vytvoření tabulky SQL Server</span><span class="sxs-lookup"><span data-stu-id="351ef-114">Creating the SQL Server Table</span></span>

<span data-ttu-id="351ef-115">Následující příkazy jazyka Transact-SQL vytvoří tabulku s názvem zaměstnanci a vloží řádek dat.</span><span class="sxs-lookup"><span data-stu-id="351ef-115">The following Transact-SQL statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="351ef-116">Po povolení úložiště FILESTREAM můžete tuto tabulku použít ve spojení s příklady kódu, které následují.</span><span class="sxs-lookup"><span data-stu-id="351ef-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="351ef-117">Odkazy na prostředky v SQL Server Knihy online najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="351ef-117">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>

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

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="351ef-118">Příklad: Čtení, přepsání a vkládání dat FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="351ef-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>

<span data-ttu-id="351ef-119">Následující příklad ukazuje, jak číst data z FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="351ef-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="351ef-120">Kód získá `FileAccess` logickou cestu k souboru, nastaví na `Read` a `FileOptions` `SequentialScan`hodnotu na.</span><span class="sxs-lookup"><span data-stu-id="351ef-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="351ef-121">Kód pak přečte bajty z SqlFileStream do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="351ef-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="351ef-122">Bajty se pak zapíší do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="351ef-122">The bytes are then written to the console window.</span></span>

<span data-ttu-id="351ef-123">Ukázka také ukazuje, jak zapisovat data do FILESTREAM, ve kterém jsou přepsána všechna stávající data.</span><span class="sxs-lookup"><span data-stu-id="351ef-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="351ef-124">Kód Získá logickou cestu k souboru a vytvoří `SqlFileStream`, `FileAccess` nastaví `Write` na a `FileOptions` `SequentialScan`na.</span><span class="sxs-lookup"><span data-stu-id="351ef-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="351ef-125">Do rozhraní `SqlFileStream`se zapíše jeden bajt, který nahradí všechna data v souboru.</span><span class="sxs-lookup"><span data-stu-id="351ef-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>

<span data-ttu-id="351ef-126">Ukázka také ukazuje, jak zapisovat data do FILESTREAM pomocí metody Seek pro připojení dat na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="351ef-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="351ef-127">Kód Získá logickou cestu k souboru a vytvoří `SqlFileStream`, `FileAccess` nastaví `ReadWrite` na a `FileOptions` `SequentialScan`na.</span><span class="sxs-lookup"><span data-stu-id="351ef-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="351ef-128">Kód používá metodu hledání k hledání na konec souboru a připojuje k existujícímu souboru jeden bajt.</span><span class="sxs-lookup"><span data-stu-id="351ef-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>

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

<span data-ttu-id="351ef-129">Další ukázku najdete v tématu [jak ukládat a načítat binární data do sloupce datového proudu souborů](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="351ef-129">For another sample, see [How to store and fetch binary data into a file stream column](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>

## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="351ef-130">Prostředky v SQL Server Knihy online</span><span class="sxs-lookup"><span data-stu-id="351ef-130">Resources in SQL Server Books Online</span></span>

<span data-ttu-id="351ef-131">Kompletní dokumentace pro FILESTREAM je k dispozici v následujících částech SQL Server Knihy online.</span><span class="sxs-lookup"><span data-stu-id="351ef-131">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>

|<span data-ttu-id="351ef-132">Téma</span><span class="sxs-lookup"><span data-stu-id="351ef-132">Topic</span></span>|<span data-ttu-id="351ef-133">Popis</span><span class="sxs-lookup"><span data-stu-id="351ef-133">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="351ef-134">FILESTREAM (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="351ef-134">FILESTREAM (SQL Server)</span></span>](/sql/relational-databases/blob/filestream-sql-server)|<span data-ttu-id="351ef-135">Popisuje, kdy použít úložiště FILESTREAM a jak integruje SQL Server databázový stroj se systémem souborů NTFS.</span><span class="sxs-lookup"><span data-stu-id="351ef-135">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|
|[<span data-ttu-id="351ef-136">Vytváření klientských aplikací pro data FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="351ef-136">Create Client Applications for FILESTREAM Data</span></span>](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|<span data-ttu-id="351ef-137">Popisuje funkce rozhraní Windows API pro práci s daty FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="351ef-137">Describes the Windows API functions for working with FILESTREAM data.</span></span>|
|[<span data-ttu-id="351ef-138">FILESTREAM a další SQL Server funkce</span><span class="sxs-lookup"><span data-stu-id="351ef-138">FILESTREAM and Other SQL Server Features</span></span>](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|<span data-ttu-id="351ef-139">Obsahuje informace, pokyny a omezení pro používání dat FILESTREAM s jinými funkcemi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="351ef-139">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|

## <a name="see-also"></a><span data-ttu-id="351ef-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="351ef-140">See also</span></span>

- [<span data-ttu-id="351ef-141">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="351ef-141">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="351ef-142">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="351ef-142">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="351ef-143">Zabezpečení přístupu ke kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="351ef-143">Code Access Security and ADO.NET</span></span>](../code-access-security.md)
- [<span data-ttu-id="351ef-144">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="351ef-144">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="351ef-145">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="351ef-145">ADO.NET Overview</span></span>](../ado-net-overview.md)
