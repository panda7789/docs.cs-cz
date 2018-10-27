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
# <a name="filestream-data"></a>FILESTREAM Data
Atribut úložiště FILESTREAM je binárních (objektů BLOB) data uložená v sloupce varbinary(max). Před FILESTREAM ukládání binárních dat vyžaduje speciální zacházení. Nestrukturovaných dat, jako jsou textové dokumenty, obrázky a videa, je často uložená mimo databázi kvůli tomu obtížné spravovat.  
  
> [!NOTE]
>  Musíte nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější) pro práci s daty FILESTREAM pomocí SqlClient.  
  
 Určení u sloupce varbinary(max) FILESTREAM atribut způsobí, že Server SQL pro ukládání dat v místním systému souborů NTFS místo v souboru databáze. I když se ukládají odděleně, můžete použít stejný [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy, které jsou podporovány pro práci s daty varbinary(max), který je uložen v databázi.  
  
## <a name="sqlclient-support-for-filestream"></a>Podpora klienta SqlClient pro FILESTREAM  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server, <xref:System.Data.SqlClient>, podporuje čtení a zápis do pomocí dat FILESTREAM <xref:System.Data.SqlTypes.SqlFileStream> třídy definované v <xref:System.Data.SqlTypes> oboru názvů. `SqlFileStream` dědí z <xref:System.IO.Stream> třídu, která poskytuje metody pro čtení a zápis do datových proudů. Čtení z datového proudu přenosu dat z datového proudu do datové struktury, jako například pole bajtů. Zápis přenáší data z strukturu dat do datového proudu.  
  
### <a name="creating-the-sql-server-table"></a>Vytváří se tabulka SQL serveru  
 Následující [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy vytvoří tabulku s názvem Zaměstnanci a vloží řádek s daty. Jakmile povolíte úložiště FILESTREAM, můžete použít tuto tabulku ve spojení s příklady kódu, které následují. Odkazy na zdroje v SQL Server Books Online jsou umístěny na konci tohoto tématu.  
  
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
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>Příklad: Pro čtení, přepsání a vkládání dat FILESTREAM  
 Následující příklad ukazuje, jak přečíst data z FILESTREAM. Kód získá logickou cestu k souboru nastavení `FileAccess` k `Read` a `FileOptions` k `SequentialScan`. Kód poté načte bajtů z SqlFileStream do vyrovnávací paměti. Bajty jsou pak zapsány do okna konzoly.  
  
 Ukázka také ukazuje, jak zapisovat data FILESTREAM, ve kterém všechna existující data přepsána. Kód získá logickou cestu k souboru a vytvoří `SqlFileStream`a nastavte `FileAccess` k `Write` a `FileOptions` k `SequentialScan`. Jeden bajt je zapsán do `SqlFileStream`, nahraďte všechna data v souboru.  
  
 Ukázka také ukazuje, jak zapsat data do FILESTREAM pomocí metody hledání pro připojení dat na konec souboru. Kód získá logickou cestu k souboru a vytvoří `SqlFileStream`a nastavte `FileAccess` k `ReadWrite` a `FileOptions` k `SequentialScan`. Tento kód použije metody Seek hledání na konci souboru, jeden bajt připojení k existujícímu souboru.  
  
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
  
 Další příklad naleznete v tématu [postupy při ukládání a načítání binárních dat do sloupce datového proudu souboru](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).  
  
## <a name="resources-in-sql-server-books-online"></a>Prostředky v Online knihách serveru SQL  
 Kompletní dokumentaci k FILESTREAM je umístěn v následujících částech v SQL Server Books Online.  
  
|Téma|Popis|  
|-----------|-----------------|  
|[FILESTREAM (SQL Server)](/sql/relational-databases/blob/filestream-sql-server)|Popisuje použití úložiště FILESTREAM a popisuje integraci této služby databázového stroje SQL Server pomocí systému souborů NTFS.|  
|[Vytvoření klientské aplikace pro FILESTREAM Data](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|Popisuje funkce rozhraní Win32 API pro práci s daty FILESTREAM.|  
|[FILESTREAM a další funkce SQL serveru](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|Obsahuje důležité informace, pokyny a omezení pro používání dat FILESTREAM s jinými funkcemi systému SQL Server.|  
  
## <a name="see-also"></a>Viz také  
 [Datové typy SQL Serveru a ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [Načítání a úpravy dat v ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Zabezpečení přístupu ke kódu a ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [Binární a vysoké hodnoty na SQL Serveru](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [Přehled ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)
