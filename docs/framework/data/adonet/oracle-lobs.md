---
title: Objekty LOBs Oracle
ms.date: 03/30/2017
ms.assetid: 272e8e1e-a31f-475a-8c2a-ae8e1286bdab
ms.openlocfilehash: 04789b385d7a956b65b7cd99594fc92001183af3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758773"
---
# <a name="oracle-lobs"></a><span data-ttu-id="1ecfe-102">Objekty LOBs Oracle</span><span class="sxs-lookup"><span data-stu-id="1ecfe-102">Oracle LOBs</span></span>
<span data-ttu-id="1ecfe-103">Zprostředkovatel dat .NET Framework pro Oracle zahrnuje <xref:System.Data.OracleClient.OracleLob> třídy, která se používá pro práci s Oracle **obchodní** datové typy.</span><span class="sxs-lookup"><span data-stu-id="1ecfe-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle **LOB** data types.</span></span>  
  
 <span data-ttu-id="1ecfe-104">**OracleLob** může mít jednu z těchto <xref:System.Data.OracleClient.OracleType> datové typy:</span><span class="sxs-lookup"><span data-stu-id="1ecfe-104">An **OracleLob** may be one of these <xref:System.Data.OracleClient.OracleType> data types:</span></span>  
  
|<span data-ttu-id="1ecfe-105">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1ecfe-105">Data type</span></span>|<span data-ttu-id="1ecfe-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1ecfe-106">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ecfe-107">**Objekt BLOB**</span><span class="sxs-lookup"><span data-stu-id="1ecfe-107">**Blob**</span></span>|<span data-ttu-id="1ecfe-108">Oracle **BLOB** datový typ, který obsahuje binární data s maximální velikost 4 GB.</span><span class="sxs-lookup"><span data-stu-id="1ecfe-108">An Oracle **BLOB** data type that contains binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="1ecfe-109">To se mapuje **pole** typu **bajtů**.</span><span class="sxs-lookup"><span data-stu-id="1ecfe-109">This maps to an **Array** of type **Byte**.</span></span>|  
|<span data-ttu-id="1ecfe-110">**Datový typ CLOB**</span><span class="sxs-lookup"><span data-stu-id="1ecfe-110">**Clob**</span></span>|<span data-ttu-id="1ecfe-111">Oracle **datový typ CLOB** datový typ, který obsahuje znak data, v závislosti na výchozí znakovou nastavit na serveru, a maximální velikost 4 GB.</span><span class="sxs-lookup"><span data-stu-id="1ecfe-111">An Oracle **CLOB** data type that contains character data, based on the default character set on the server, with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="1ecfe-112">To se mapuje na **řetězec**.</span><span class="sxs-lookup"><span data-stu-id="1ecfe-112">This maps to **String**.</span></span>|  
|<span data-ttu-id="1ecfe-113">**NClob**</span><span class="sxs-lookup"><span data-stu-id="1ecfe-113">**NClob**</span></span>|<span data-ttu-id="1ecfe-114">Oracle **NCLOB** datový typ, který obsahuje znak data podle national znakovou sadu na serveru s maximální velikost 4 GB.</span><span class="sxs-lookup"><span data-stu-id="1ecfe-114">An Oracle **NCLOB** data type that contains character data, based on the national character set on the server with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="1ecfe-115">To se mapuje na **řetězec**.</span><span class="sxs-lookup"><span data-stu-id="1ecfe-115">This maps to **String**.</span></span>|  
  
 <span data-ttu-id="1ecfe-116">**OracleLob** se liší od <xref:System.Data.OracleClient.OracleBFile> že data jsou uložena na serveru místo v fyzický soubor v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="1ecfe-116">An **OracleLob** differs from an <xref:System.Data.OracleClient.OracleBFile> in that the data is stored on the server instead of in a physical file in the operating system.</span></span> <span data-ttu-id="1ecfe-117">Objekt pro čtení a zápis, může být také na rozdíl od **OracleBFile**, což je vždy jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="1ecfe-117">It can also be a read-write object, unlike an **OracleBFile**, which is always read-only.</span></span>  
  
## <a name="creating-retrieving-and-writing-to-a-lob"></a><span data-ttu-id="1ecfe-118">Vytváření, načítání a zápisu do objektu LOB</span><span class="sxs-lookup"><span data-stu-id="1ecfe-118">Creating, Retrieving, and Writing to a LOB</span></span>  
 <span data-ttu-id="1ecfe-119">Následující příklad jazyka C# ukazuje, jak můžete vytvořit objekty LOBs v tabulce Oracle a pak načtení a zápis do nich ve formě **OracleLob** objekty.</span><span class="sxs-lookup"><span data-stu-id="1ecfe-119">The following C# example demonstrates how you can create LOBs in an Oracle table, and then retrieve and write to them in the form of **OracleLob** objects.</span></span> <span data-ttu-id="1ecfe-120">Tento příklad ukazuje, jak pomocí <xref:System.Data.OracleClient.OracleDataReader> objektu a **OracleLob** **čtení** a **zápisu** metody.</span><span class="sxs-lookup"><span data-stu-id="1ecfe-120">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleLob** **Read** and **Write** methods.</span></span> <span data-ttu-id="1ecfe-121">Tento příklad používá Oracle **BLOB**, **datový typ CLOB**, a **NCLOB** datové typy.</span><span class="sxs-lookup"><span data-stu-id="1ecfe-121">The example uses Oracle **BLOB**, **CLOB**, and **NCLOB** data types.</span></span>  
  
```csharp  
using System;  
using System.IO;              
using System.Text;             
using System.Data;              
using System.Data.OracleClient;  
  
// LobExample  
public class LobExample  
{  
   public static int Main(string[] args)  
   {  
      //Create a connection.  
      OracleConnection conn = new OracleConnection(  
         "Data Source=Oracle8i;Integrated Security=yes");  
      using(conn)  
      {  
         //Open a connection.  
         conn.Open();  
         OracleCommand cmd = conn.CreateCommand();  
  
         //Create the table and schema.  
         CreateTable(cmd);  
  
         //Read example.  
         ReadLobExample(cmd);  
  
         //Write example  
         WriteLobExample(cmd);  
      }  
  
      return 1;  
   }  
  
   // ReadLobExample  
   public static void ReadLobExample(OracleCommand cmd)  
   {  
      int actual = 0;  
  
      // Table Schema:  
      // "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      // "INSERT INTO tablewithlobs values (1, 'AA', 'AAA', N'AAAA')";  
      // Select some data.  
      cmd.CommandText = "SELECT * FROM tablewithlobs";  
      OracleDataReader reader = cmd.ExecuteReader();  
      using(reader)  
      {  
         //Obtain the first row of data.  
         reader.Read();  
  
         //Obtain the LOBs (all 3 varieties).  
         OracleLob blob = reader.GetOracleLob(1);  
         OracleLob clob = reader.GetOracleLob(2);  
         OracleLob nclob = reader.GetOracleLob(3);  
  
         //Example - Reading binary data (in chunks).  
         byte[] buffer = new byte[100];  
         while((actual = blob.Read(buffer, 0, buffer.Length)) >0)  
            Console.WriteLine(blob.LobType + ".Read(" + buffer + ", " +   
              buffer.Length + ") => " + actual);  
  
         // Example - Reading CLOB/NCLOB data (in chunks).  
         // Note: You can read character data as raw Unicode bytes   
         // (using OracleLob.Read as in the above example).  
         // However, because the OracleLob object inherits directly   
         // from the .Net stream object,   
         // all the existing classes that manipluate streams can   
         // also be used. For example, the   
         // .Net StreamReader makes it easier to convert the raw bytes   
         // into actual characters.  
         StreamReader streamreader =   
           new StreamReader(clob, Encoding.Unicode);  
         char[] cbuffer = new char[100];  
         while((actual = streamreader.Read(cbuffer,   
           0, cbuffer.Length)) >0)  
            Console.WriteLine(clob.LobType + ".Read(  
              " + new string(cbuffer, 0, actual) + ", " +   
              cbuffer.Length + ") => " + actual);  
  
         // Example - Reading data (all at once).  
         // You could use StreamReader.ReadToEnd to obtain   
         // all the string data, or simply  
         // call OracleLob.Value to obtain a contiguous allocation   
         // of all the data.  
         Console.WriteLine(nclob.LobType + ".Value => " + nclob.Value);  
      }  
   }  
  
   // WriteLobExample  
   public static void WriteLobExample(OracleCommand cmd)  
   {  
      //Note: Updating LOB data requires a transaction.  
      cmd.Transaction = cmd.Connection.BeginTransaction();  
  
      // Select some data.  
      // Table Schema:  
      // "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      // "INSERT INTO tablewithlobs values (1, 'AA', 'AAA', N'AAAA')";  
      cmd.CommandText = "SELECT * FROM tablewithlobs FOR UPDATE";  
      OracleDataReader reader = cmd.ExecuteReader();  
      using(reader)  
      {  
         // Obtain the first row of data.  
         reader.Read();  
  
         // Obtain a LOB.  
         OracleLob blob = reader.GetOracleLob(1/*0:based ordinal*/);  
  
         // Perform any desired operations on the LOB   
         // (read, position, and so on).  
  
         // Example - Writing binary data (directly to the backend).  
         // To write, you can use any of the stream classes, or write  
         // raw binary data using   
         // the OracleLob write method. Writing character vs. binary   
         // is the same;  
         // however note that character is always in terms of   
         // Unicode byte counts  
         // (for example, even number of bytes - 2 bytes for every  
         // Unicode character).  
         byte[] buffer = new byte[100];  
         buffer[0] = 0xCC;  
         buffer[1] = 0xDD;  
         blob.Write(buffer, 0, 2);  
         blob.Position = 0;  
         Console.WriteLine(blob.LobType + ".Write(  
           " + buffer + ", 0, 2) => " + blob.Value);  
  
         // Example - Obtaining a temp LOB and copying data   
         // into it from another LOB.  
         OracleLob templob = CreateTempLob(cmd, blob.LobType);  
         long actual = blob.CopyTo(templob);  
         Console.WriteLine(blob.LobType + ".CopyTo(  
            " + templob.Value + ") => " + actual);  
  
         // Commit the transaction now that everything succeeded.  
         // Note: On error, Transaction.Dispose is called   
         // (from the using statement)  
         // and will automatically roll back the pending transaction.  
         cmd.Transaction.Commit();  
      }  
   }  
  
   // CreateTempLob  
   public static OracleLob CreateTempLob(  
     OracleCommand cmd, OracleType lobtype)  
   {  
      //Oracle server syntax to obtain a temporary LOB.  
      cmd.CommandText = "DECLARE A " + lobtype + "; "+  
                     "BEGIN "+  
                        "DBMS_LOB.CREATETEMPORARY(A, FALSE); "+  
                        ":LOC := A; "+  
                     "END;";  
  
      //Bind the LOB as an output parameter.  
      OracleParameter p = cmd.Parameters.Add("LOC", lobtype);  
      p.Direction = ParameterDirection.Output;  
  
      //Execute (to receive the output temporary LOB).  
      cmd.ExecuteNonQuery();  
  
      //Return the temporary LOB.  
      return (OracleLob)p.Value;  
   }  
  
   // CreateTable  
   public static void CreateTable(OracleCommand cmd)  
   {  
      // Table Schema:  
      // "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      // "INSERT INTO tablewithlobs VALUES (1, 'AA', 'AAA', N'AAAA')";  
      try  
      {  
         cmd.CommandText   = "DROP TABLE tablewithlobs";  
         cmd.ExecuteNonQuery();  
      }  
      catch(Exception)  
      {  
      }  
  
      cmd.CommandText =   
        "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      cmd.ExecuteNonQuery();  
      cmd.CommandText =   
        "INSERT INTO tablewithlobs VALUES (1, 'AA', 'AAA', N'AAAA')";  
      cmd.ExecuteNonQuery();  
   }  
}  
```  
  
## <a name="creating-a-temporary-lob"></a><span data-ttu-id="1ecfe-122">Vytváření dočasných LOB</span><span class="sxs-lookup"><span data-stu-id="1ecfe-122">Creating a Temporary LOB</span></span>  
 <span data-ttu-id="1ecfe-123">Následující příklad jazyka C# ukazuje, jak vytvořit dočasný OBJEKT.</span><span class="sxs-lookup"><span data-stu-id="1ecfe-123">The following C# example demonstrates how to create a temporary LOB.</span></span>  
  
```csharp  
OracleConnection conn = new OracleConnection(  
  "server=test8172; integrated security=yes;");  
conn.Open();  
  
OracleTransaction tx = conn.BeginTransaction();  
  
OracleCommand cmd = conn.CreateCommand();  
cmd.Transaction = tx;  
cmd.CommandText =   
  "declare xx blob; begin dbms_lob.createtemporary(  
  xx, false, 0); :tempblob := xx; end;";  
cmd.Parameters.Add(new OracleParameter("tempblob",  
  OracleType.Blob)).Direction = ParameterDirection.Output;  
cmd.ExecuteNonQuery();  
OracleLob tempLob = (OracleLob)cmd.Parameters[0].Value;  
tempLob.BeginBatch(OracleLobOpenMode.ReadWrite);  
tempLob.Write(tempbuff,0,tempbuff.Length);  
tempLob.EndBatch();  
cmd.Parameters.Clear();  
cmd.CommandText = "myTable.myProc";  
cmd.CommandType = CommandType.StoredProcedure;    
cmd.Parameters.Add(new OracleParameter(  
  "ImportDoc", OracleType.Blob)).Value = tempLob;  
cmd.ExecuteNonQuery();  
  
tx.Commit();  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ecfe-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ecfe-124">See Also</span></span>  
 [<span data-ttu-id="1ecfe-125">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1ecfe-125">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="1ecfe-126">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="1ecfe-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
