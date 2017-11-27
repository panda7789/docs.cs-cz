---
title: FILESTREAM Data
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2fde543187d1904da93be255878d6c7a99de6bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="filestream-data"></a>FILESTREAM Data
Atribut úložiště FILESTREAM je binární (binární rozsáhlý OBJEKT) data uložená v sloupce varbinary(max). Před FILESTREAM ukládání binárních dat vyžadují speciální zacházení. Nestrukturovaná data, jako jsou dokumenty text, obrázky a videa, je často uložené mimo databázi, a může ztížit správu.  
  
> [!NOTE]
>  Musíte nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější) pro práci s daty FILESTREAM pomocí SqlClient.  
  
 Určení atributem FILESTREAM u sloupce varbinary(max) způsobí, že [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] k uložení dat v místním systému souborů NTFS místo v souboru databáze. I když je uložen samostatně, můžete použít stejné [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy, které jsou podporovány pro práci s daty varbinary(max), který je uložen v databázi.  
  
## <a name="sqlclient-support-for-filestream"></a>Podpora SqlClient FILESTREAM  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], <xref:System.Data.SqlClient>, podporuje čtení a zápis do FILESTREAM dat pomocí <xref:System.Data.SqlTypes.SqlFileStream> třídy definované v <xref:System.Data.SqlTypes> oboru názvů. `SqlFileStream`dědí z <xref:System.IO.Stream> třídy, která poskytuje metody pro čtení a zápis do datových proudů. Čtení z datového proudu přenáší data z datového proudu do struktury dat, jako je například pole bajtů. Zápis přenáší data z strukturu dat do datového proudu.  
  
### <a name="creating-the-includessnoversionincludesssnoversion-mdmd-table"></a>Vytváření [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] tabulky  
 Následující [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy vytvoří tabulku s názvem Zaměstnanci a vloží řádek s daty. Jakmile povolíte úložiště FILESTREAM, můžete pomocí této tabulky ve spojení s příklady kódu, které následují. Odkazy na zdroje informací v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] na webu knihy Online jsou umístěné na konci tohoto tématu.  
  
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
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>Příklad: Čtení, přepsání a vkládání dat FILESTREAM  
 Následující příklad ukazuje, jak číst data z FILESTREAM. Kód získá logickou cestu k souboru, nastavení `FileAccess` k `Read` a `FileOptions` k `SequentialScan`. Kód pak přečte bajtů z SqlFileStream do vyrovnávací paměti. Počet bajtů se pak zapisují do okna konzoly.  
  
 Ukázka také ukazuje, jak zapsat data do FILESTREAM, ve kterém se přepíše všechna existující data. Kód získá logickou cestu k souboru a vytvoří `SqlFileStream`, nastavení `FileAccess` k `Write` a `FileOptions` k `SequentialScan`. Jeden bajt je zapsán do `SqlFileStream`, nahraďte všechna data v souboru.  
  
 Ukázka také ukazuje, jak zapsat data do FILESTREAM pomocí metody Seek pro připojení dat na konci souboru. Kód získá logickou cestu k souboru a vytvoří `SqlFileStream`, nastavení `FileAccess` k `ReadWrite` a `FileOptions` k `SequentialScan`. Kód používá metodu Seek k vyhledání na konec souboru připojením byl jediný bajt ke stávajícímu souboru.  
  
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
  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))  
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
} using (SqlConnection connection = new SqlConnection(  
    connStringBuilder.ToString()))  
{  
    connection.Open();  
  
    SqlCommand command = new SqlCommand("", connection);  
    command.CommandText = "select Top(1) Photo.PathName(), "  
    + "GET_FILESTREAM_TRANSACTION_CONTEXT () from employees";  
  
    SqlTransaction tran = connection.BeginTransaction(  
        System.Data.IsolationLevel.ReadCommitted);  
    command.Transaction = tran;  
  
    using (SqlDataReader reader = command.ExecuteReader())  
    {  
        while (reader.Read())  
        {  
            // Get the pointer for file  
            string path = reader.GetString(0);  
            byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
            FileStream fileStream = new SqlFileStream(path,  
                (byte[])reader.GetValue(1),  
                FileAccess.ReadWrite,  
                FileOptions.SequentialScan, 0);  
  
            // Seek to the end of the file  
            fs.Seek(0, SeekOrigin.End);  
  
            // Append a single byte   
            fileStream.WriteByte(0x01);  
            fileStream.Close();  
        }  
    }  
    tran.Commit();  
}  
```  
  
 Jiný příklad naleznete v tématu [uložení a načtení binární data do sloupce datového proudu souboru](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).  
  
## <a name="resources-in-includessnoversionincludesssnoversion-mdmd-books-online"></a>Prostředky v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] zarezervuje Online  
 Kompletní dokumentaci pro FILESTREAM je umístěný v následující části [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] na webu knihy Online.  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Navrhování a implementace úložiště FILESTREAM](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)|Obsahuje odkazy na dokumentaci FILESTREAM a související témata.|  
|[Přehled FILESTREAM](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)|Popisuje použití úložiště FILESTREAM a jak se integruje se službou databázového stroje SQL Server pomocí systému souborů NTFS.|  
|[Začínáme s úložištěm FILESTREAM](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)|Popisuje, jak povolit FILESTREAM v instanci systému SQL Server, vytvořte databázi a tabulku pro uložených dat FILESTREAM a manipulace s řádky obsahující FILESTREAM data.|  
|[Pomocí úložiště FILESTREAM v klientských aplikacích](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)|Popisuje funkce Win32 API pro práci s daty FILESTREAM.|  
|[FILESTREAM a další funkce SQL Server](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)|Poskytuje důležité informace, pokyny a omezení pro používání FILESTREAM data s jinými funkcemi systému SQL Server.|  
  
## <a name="see-also"></a>Viz také  
 [Data serveru SQL typy a ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [Načítání a upravovat Data v technologii ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Zabezpečení přístupu kódu a ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [Binární a velké hodnoty dat systému SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
