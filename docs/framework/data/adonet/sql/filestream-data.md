---
title: FILESTREAM Data
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: 782674cb38669c400bd5d730c2fd0c144778a985
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357768"
---
# <a name="filestream-data"></a><span data-ttu-id="b0704-102">FILESTREAM Data</span><span class="sxs-lookup"><span data-stu-id="b0704-102">FILESTREAM Data</span></span>
<span data-ttu-id="b0704-103">Atribut úložiště FILESTREAM je binární (binární rozsáhlý OBJEKT) data uložená v sloupce varbinary(max).</span><span class="sxs-lookup"><span data-stu-id="b0704-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="b0704-104">Před FILESTREAM ukládání binárních dat vyžadují speciální zacházení.</span><span class="sxs-lookup"><span data-stu-id="b0704-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="b0704-105">Nestrukturovaná data, jako jsou dokumenty text, obrázky a videa, je často uložené mimo databázi, a může ztížit správu.</span><span class="sxs-lookup"><span data-stu-id="b0704-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0704-106">Musíte nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější) pro práci s daty FILESTREAM pomocí SqlClient.</span><span class="sxs-lookup"><span data-stu-id="b0704-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>  
  
 <span data-ttu-id="b0704-107">Určení atributem FILESTREAM u sloupce varbinary(max) způsobí, že Server SQL pro ukládání dat v místním systému souborů NTFS místo v souboru databáze.</span><span class="sxs-lookup"><span data-stu-id="b0704-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="b0704-108">I když je uložen samostatně, můžete použít stejné [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy, které jsou podporovány pro práci s daty varbinary(max), který je uložen v databázi.</span><span class="sxs-lookup"><span data-stu-id="b0704-108">Although it is stored separately, you can use the same [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>  
  
## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="b0704-109">Podpora SqlClient FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="b0704-109">SqlClient Support for FILESTREAM</span></span>  
 <span data-ttu-id="b0704-110">[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server, <xref:System.Data.SqlClient>, podporuje čtení a zápis do FILESTREAM dat pomocí <xref:System.Data.SqlTypes.SqlFileStream> třídy definované v <xref:System.Data.SqlTypes> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b0704-110">The [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="b0704-111">`SqlFileStream` dědí z <xref:System.IO.Stream> třídy, která poskytuje metody pro čtení a zápis do datových proudů.</span><span class="sxs-lookup"><span data-stu-id="b0704-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="b0704-112">Čtení z datového proudu přenáší data z datového proudu do struktury dat, jako je například pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="b0704-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="b0704-113">Zápis přenáší data z strukturu dat do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="b0704-113">Writing transfers the data from the data structure into a stream.</span></span>  
  
### <a name="creating-the-sql-server-table"></a><span data-ttu-id="b0704-114">Vytvoření tabulky serveru SQL</span><span class="sxs-lookup"><span data-stu-id="b0704-114">Creating the SQL Server Table</span></span>  
 <span data-ttu-id="b0704-115">Následující [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy vytvoří tabulku s názvem Zaměstnanci a vloží řádek s daty.</span><span class="sxs-lookup"><span data-stu-id="b0704-115">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="b0704-116">Jakmile povolíte úložiště FILESTREAM, můžete pomocí této tabulky ve spojení s příklady kódu, které následují.</span><span class="sxs-lookup"><span data-stu-id="b0704-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="b0704-117">Odkazy na zdroje informací v Online knihách SQL Server jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b0704-117">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>  
  
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
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="b0704-118">Příklad: Čtení, přepsání a vkládání dat FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="b0704-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>  
 <span data-ttu-id="b0704-119">Následující příklad ukazuje, jak číst data z FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="b0704-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="b0704-120">Kód získá logickou cestu k souboru, nastavení `FileAccess` k `Read` a `FileOptions` k `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="b0704-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="b0704-121">Kód pak přečte bajtů z SqlFileStream do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b0704-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="b0704-122">Počet bajtů se pak zapisují do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="b0704-122">The bytes are then written to the console window.</span></span>  
  
 <span data-ttu-id="b0704-123">Ukázka také ukazuje, jak zapsat data do FILESTREAM, ve kterém se přepíše všechna existující data.</span><span class="sxs-lookup"><span data-stu-id="b0704-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="b0704-124">Kód získá logickou cestu k souboru a vytvoří `SqlFileStream`, nastavení `FileAccess` k `Write` a `FileOptions` k `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="b0704-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="b0704-125">Jeden bajt je zapsán do `SqlFileStream`, nahraďte všechna data v souboru.</span><span class="sxs-lookup"><span data-stu-id="b0704-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>  
  
 <span data-ttu-id="b0704-126">Ukázka také ukazuje, jak zapsat data do FILESTREAM pomocí metody Seek pro připojení dat na konci souboru.</span><span class="sxs-lookup"><span data-stu-id="b0704-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="b0704-127">Kód získá logickou cestu k souboru a vytvoří `SqlFileStream`, nastavení `FileAccess` k `ReadWrite` a `FileOptions` k `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="b0704-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="b0704-128">Kód používá metodu Seek k vyhledání na konec souboru připojením byl jediný bajt ke stávajícímu souboru.</span><span class="sxs-lookup"><span data-stu-id="b0704-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>  
  
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
  
 <span data-ttu-id="b0704-129">Jiný příklad naleznete v tématu [uložení a načtení binární data do sloupce datového proudu souboru](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="b0704-129">For another sample, see [How to store and fetch binary data into a file stream column](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>  
  
## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="b0704-130">Prostředky v Online knihách serveru SQL</span><span class="sxs-lookup"><span data-stu-id="b0704-130">Resources in SQL Server Books Online</span></span>  
 <span data-ttu-id="b0704-131">Kompletní dokumentaci pro FILESTREAM se nachází v následujících částech v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="b0704-131">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>  
  
|<span data-ttu-id="b0704-132">Téma</span><span class="sxs-lookup"><span data-stu-id="b0704-132">Topic</span></span>|<span data-ttu-id="b0704-133">Popis</span><span class="sxs-lookup"><span data-stu-id="b0704-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b0704-134">[Navrhování a implementace úložiště FILESTREAM](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b0704-134">[Designing and Implementing FILESTREAM Storage](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)</span></span>|<span data-ttu-id="b0704-135">Obsahuje odkazy na dokumentaci FILESTREAM a související témata.</span><span class="sxs-lookup"><span data-stu-id="b0704-135">Provides links to FILESTREAM documentation and related topics.</span></span>|  
|<span data-ttu-id="b0704-136">[Přehled FILESTREAM](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b0704-136">[FILESTREAM Overview](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)</span></span>|<span data-ttu-id="b0704-137">Popisuje použití úložiště FILESTREAM a jak se integruje se službou databázového stroje SQL Server pomocí systému souborů NTFS.</span><span class="sxs-lookup"><span data-stu-id="b0704-137">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|  
|<span data-ttu-id="b0704-138">[Začínáme s úložištěm FILESTREAM](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b0704-138">[Getting Started with FILESTREAM Storage](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)</span></span>|<span data-ttu-id="b0704-139">Popisuje, jak povolit FILESTREAM v instanci systému SQL Server, vytvořte databázi a tabulku pro uložených dat FILESTREAM a manipulace s řádky obsahující FILESTREAM data.</span><span class="sxs-lookup"><span data-stu-id="b0704-139">Describes how to enable FILESTREAM on an instance of SQL Server, how to create a database and a table to stored FILESTREAM data, and how to manipulate rows containing FILESTREAM data.</span></span>|  
|<span data-ttu-id="b0704-140">[Pomocí úložiště FILESTREAM v klientských aplikacích](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b0704-140">[Using FILESTREAM Storage in Client Applications](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)</span></span>|<span data-ttu-id="b0704-141">Popisuje funkce Win32 API pro práci s daty FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="b0704-141">Describes the Win32 API functions for working with FILESTREAM data.</span></span>|  
|<span data-ttu-id="b0704-142">[FILESTREAM a další funkce SQL Server](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b0704-142">[FILESTREAM and Other SQL Server Features](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)</span></span>|<span data-ttu-id="b0704-143">Poskytuje důležité informace, pokyny a omezení pro používání FILESTREAM data s jinými funkcemi systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b0704-143">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0704-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0704-144">See Also</span></span>  
 [<span data-ttu-id="b0704-145">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b0704-145">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="b0704-146">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b0704-146">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="b0704-147">Zabezpečení přístupu ke kódu a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b0704-147">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [<span data-ttu-id="b0704-148">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="b0704-148">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="b0704-149">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="b0704-149">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
