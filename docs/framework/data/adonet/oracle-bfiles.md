---
title: Oracle BFILEs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 585245464ce3a2ef4b1da6ec2a7e2770af187876
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="oracle-bfiles"></a><span data-ttu-id="829ae-102">Oracle BFILEs</span><span class="sxs-lookup"><span data-stu-id="829ae-102">Oracle BFILEs</span></span>
<span data-ttu-id="829ae-103">Zprostředkovatel dat .NET Framework pro Oracle zahrnuje <xref:System.Data.OracleClient.OracleBFile> třídy, která se používá pro práci s Oracle <xref:System.Data.OracleClient.OracleType.BFile> datového typu.</span><span class="sxs-lookup"><span data-stu-id="829ae-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="829ae-104">Oracle **BFILE** datový typ je Oracle **obchodní** datový typ, který obsahuje odkaz na binární data s maximální velikost 4 GB.</span><span class="sxs-lookup"><span data-stu-id="829ae-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="829ae-105">Oracle **BFILE** se liší od jiných Oracle **obchodní** datové typy, že data jsou uložena v fyzického souboru operačního systému místo na serveru.</span><span class="sxs-lookup"><span data-stu-id="829ae-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="829ae-106">Všimněte si, že **BFILE** datový typ poskytuje přístup jen pro čtení k datům.</span><span class="sxs-lookup"><span data-stu-id="829ae-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="829ae-107">Další vlastnosti **BFILE** datový typ, který odlišující jej od **obchodní** datový typ jsou to:</span><span class="sxs-lookup"><span data-stu-id="829ae-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
-   <span data-ttu-id="829ae-108">Obsahuje Nestrukturovaná data.</span><span class="sxs-lookup"><span data-stu-id="829ae-108">Contains unstructured data.</span></span>  
  
-   <span data-ttu-id="829ae-109">Podporuje rozdělování na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="829ae-109">Supports server-side chunking.</span></span>  
  
-   <span data-ttu-id="829ae-110">Používá referenční sémantiku kopírování.</span><span class="sxs-lookup"><span data-stu-id="829ae-110">Uses reference copy semantics.</span></span> <span data-ttu-id="829ae-111">Například, pokud provádíte na operace kopírování **BFILE**, jenom **BFILE** zkopíruje Lokátor (což je odkaz na soubor).</span><span class="sxs-lookup"><span data-stu-id="829ae-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="829ae-112">Data v souboru není zkopírována.</span><span class="sxs-lookup"><span data-stu-id="829ae-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="829ae-113">**BFILE** datový typ měli použít pro odkazování na objekty LOBs, které jsou velké a proto není potřeba ukládat v databázi.</span><span class="sxs-lookup"><span data-stu-id="829ae-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="829ae-114">Další režii klienta, komunikace a server je zahrnuta při použití **BFILE** datový typ ve srovnání s **obchodní** datového typu.</span><span class="sxs-lookup"><span data-stu-id="829ae-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="829ae-115">Přístup je efektivnější **BFILE** Pokud potřebujete získat malé množství dat.</span><span class="sxs-lookup"><span data-stu-id="829ae-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="829ae-116">Je efektivnější k přístupu k databázi rezidentní objekty LOBs, pokud je nutné získat celý objekt.</span><span class="sxs-lookup"><span data-stu-id="829ae-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="829ae-117">Každý NENULOVOU **OracleBFile** objekt je přidružený ke dvě entity, které definují umístění základní fyzický soubor:</span><span class="sxs-lookup"><span data-stu-id="829ae-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1.  <span data-ttu-id="829ae-118">Objekt Oracle adresář, který je alias databáze pro adresář v systému souborů, a</span><span class="sxs-lookup"><span data-stu-id="829ae-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2.  <span data-ttu-id="829ae-119">Název souboru základní fyzického souboru, který je umístěný v adresáři přidružená k objektu adresáře.</span><span class="sxs-lookup"><span data-stu-id="829ae-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="829ae-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="829ae-120">Example</span></span>  
 <span data-ttu-id="829ae-121">Následující příklad jazyka C# ukazuje, jak můžete vytvořit **BFILE** v Oracle tabulky a následně načíst ve formě **OracleBFile** objektu.</span><span class="sxs-lookup"><span data-stu-id="829ae-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="829ae-122">Tento příklad ukazuje, jak pomocí <xref:System.Data.OracleClient.OracleDataReader> objektu a **OracleBFile** **Seek** a **čtení** metody.</span><span class="sxs-lookup"><span data-stu-id="829ae-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="829ae-123">Všimněte si, že chcete-li použít tuto ukázku, musíte nejprve vytvořit adresář s názvem "c:\\\bfiles" a soubor s názvem "MyFile.jpg" na serveru Oracle.</span><span class="sxs-lookup"><span data-stu-id="829ae-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =   
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =   
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="829ae-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="829ae-124">See Also</span></span>  
 [<span data-ttu-id="829ae-125">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="829ae-125">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="829ae-126">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="829ae-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
