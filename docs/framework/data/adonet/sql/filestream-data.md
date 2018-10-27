---
title: FILESTREAM Data
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: 843aa890ba80ab2816af0726170eacb77f419d50
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50047979"
---
# <a name="filestream-data"></a><span data-ttu-id="ca290-102">FILESTREAM Data</span><span class="sxs-lookup"><span data-stu-id="ca290-102">FILESTREAM Data</span></span>
<span data-ttu-id="ca290-103">Atribut úložiště FILESTREAM je binárních (objektů BLOB) data uložená v sloupce varbinary(max).</span><span class="sxs-lookup"><span data-stu-id="ca290-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="ca290-104">Před FILESTREAM ukládání binárních dat vyžaduje speciální zacházení.</span><span class="sxs-lookup"><span data-stu-id="ca290-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="ca290-105">Nestrukturovaných dat, jako jsou textové dokumenty, obrázky a videa, je často uložená mimo databázi kvůli tomu obtížné spravovat.</span><span class="sxs-lookup"><span data-stu-id="ca290-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca290-106">Musíte nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější) pro práci s daty FILESTREAM pomocí SqlClient.</span><span class="sxs-lookup"><span data-stu-id="ca290-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>  
  
 <span data-ttu-id="ca290-107">Určení u sloupce varbinary(max) FILESTREAM atribut způsobí, že Server SQL pro ukládání dat v místním systému souborů NTFS místo v souboru databáze.</span><span class="sxs-lookup"><span data-stu-id="ca290-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="ca290-108">I když se ukládají odděleně, můžete použít stejný [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy, které jsou podporovány pro práci s daty varbinary(max), který je uložen v databázi.</span><span class="sxs-lookup"><span data-stu-id="ca290-108">Although it is stored separately, you can use the same [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>  
  
## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="ca290-109">Podpora klienta SqlClient pro FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="ca290-109">SqlClient Support for FILESTREAM</span></span>  
 <span data-ttu-id="ca290-110">[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server, <xref:System.Data.SqlClient>, podporuje čtení a zápis do pomocí dat FILESTREAM <xref:System.Data.SqlTypes.SqlFileStream> třídy definované v <xref:System.Data.SqlTypes> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ca290-110">The [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="ca290-111">`SqlFileStream` dědí z <xref:System.IO.Stream> třídu, která poskytuje metody pro čtení a zápis do datových proudů.</span><span class="sxs-lookup"><span data-stu-id="ca290-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="ca290-112">Čtení z datového proudu přenosu dat z datového proudu do datové struktury, jako například pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="ca290-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="ca290-113">Zápis přenáší data z strukturu dat do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="ca290-113">Writing transfers the data from the data structure into a stream.</span></span>  
  
### <a name="creating-the-sql-server-table"></a><span data-ttu-id="ca290-114">Vytváří se tabulka SQL serveru</span><span class="sxs-lookup"><span data-stu-id="ca290-114">Creating the SQL Server Table</span></span>  
 <span data-ttu-id="ca290-115">Následující [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy vytvoří tabulku s názvem Zaměstnanci a vloží řádek s daty.</span><span class="sxs-lookup"><span data-stu-id="ca290-115">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="ca290-116">Jakmile povolíte úložiště FILESTREAM, můžete použít tuto tabulku ve spojení s příklady kódu, které následují.</span><span class="sxs-lookup"><span data-stu-id="ca290-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="ca290-117">Odkazy na zdroje v SQL Server Books Online jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ca290-117">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>  
  
```  
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
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="ca290-118">Příklad: Pro čtení, přepsání a vkládání dat FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="ca290-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>  
 <span data-ttu-id="ca290-119">Následující příklad ukazuje, jak přečíst data z FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="ca290-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="ca290-120">Kód získá logickou cestu k souboru nastavení `FileAccess` k `Read` a `FileOptions` k `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="ca290-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="ca290-121">Kód poté načte bajtů z SqlFileStream do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ca290-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="ca290-122">Bajty jsou pak zapsány do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="ca290-122">The bytes are then written to the console window.</span></span>  
  
 <span data-ttu-id="ca290-123">Ukázka také ukazuje, jak zapisovat data FILESTREAM, ve kterém všechna existující data přepsána.</span><span class="sxs-lookup"><span data-stu-id="ca290-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="ca290-124">Kód získá logickou cestu k souboru a vytvoří `SqlFileStream`a nastavte `FileAccess` k `Write` a `FileOptions` k `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="ca290-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="ca290-125">Jeden bajt je zapsán do `SqlFileStream`, nahraďte všechna data v souboru.</span><span class="sxs-lookup"><span data-stu-id="ca290-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>  
  
 <span data-ttu-id="ca290-126">Ukázka také ukazuje, jak zapsat data do FILESTREAM pomocí metody hledání pro připojení dat na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="ca290-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="ca290-127">Kód získá logickou cestu k souboru a vytvoří `SqlFileStream`a nastavte `FileAccess` k `ReadWrite` a `FileOptions` k `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="ca290-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="ca290-128">Tento kód použije metody Seek hledání na konci souboru, jeden bajt připojení k existujícímu souboru.</span><span class="sxs-lookup"><span data-stu-id="ca290-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>  
  
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
            ReadFilestream(builder);  
            OverwriteFilestream(builder);  
            InsertFilestream(builder);  
  
            Console.WriteLine("Done");  
        }  
  
        private static void ReadFilestream(SqlConnectionStringBuilder connStringBuilder)  
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
  
        private static void OverwriteFilestream(SqlConnectionStringBuilder connStringBuilder)  
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
  
        private static void InsertFilestream(SqlConnectionStringBuilder connStringBuilder)  
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
  
 <span data-ttu-id="ca290-129">Další příklad naleznete v tématu [postupy při ukládání a načítání binárních dat do sloupce datového proudu souboru](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="ca290-129">For another sample, see [How to store and fetch binary data into a file stream column](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>  
  
## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="ca290-130">Prostředky v Online knihách serveru SQL</span><span class="sxs-lookup"><span data-stu-id="ca290-130">Resources in SQL Server Books Online</span></span>  
 <span data-ttu-id="ca290-131">Kompletní dokumentaci k FILESTREAM je umístěn v následujících částech v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="ca290-131">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>  
  
|<span data-ttu-id="ca290-132">Téma</span><span class="sxs-lookup"><span data-stu-id="ca290-132">Topic</span></span>|<span data-ttu-id="ca290-133">Popis</span><span class="sxs-lookup"><span data-stu-id="ca290-133">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ca290-134">FILESTREAM (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ca290-134">FILESTREAM (SQL Server)</span></span>](/sql/relational-databases/blob/filestream-sql-server)|<span data-ttu-id="ca290-135">Popisuje použití úložiště FILESTREAM a popisuje integraci této služby databázového stroje SQL Server pomocí systému souborů NTFS.</span><span class="sxs-lookup"><span data-stu-id="ca290-135">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|  
|[<span data-ttu-id="ca290-136">Vytvoření klientské aplikace pro FILESTREAM Data</span><span class="sxs-lookup"><span data-stu-id="ca290-136">Create Client Applications for FILESTREAM Data</span></span>](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|<span data-ttu-id="ca290-137">Popisuje funkce rozhraní Win32 API pro práci s daty FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="ca290-137">Describes the Win32 API functions for working with FILESTREAM data.</span></span>|  
|[<span data-ttu-id="ca290-138">FILESTREAM a další funkce SQL serveru</span><span class="sxs-lookup"><span data-stu-id="ca290-138">FILESTREAM and Other SQL Server Features</span></span>](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|<span data-ttu-id="ca290-139">Obsahuje důležité informace, pokyny a omezení pro používání dat FILESTREAM s jinými funkcemi systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ca290-139">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca290-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca290-140">See Also</span></span>  
 [<span data-ttu-id="ca290-141">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ca290-141">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="ca290-142">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ca290-142">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="ca290-143">Zabezpečení přístupu ke kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ca290-143">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [<span data-ttu-id="ca290-144">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="ca290-144">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="ca290-145">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ca290-145">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)
