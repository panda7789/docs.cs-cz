---
title: Soubory Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 40060a7ea8576e08140d972072d086606d640366
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149437"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="64555-102">Soubory Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="64555-102">Oracle BFILEs</span></span>
<span data-ttu-id="64555-103">Zprostředkovatel dat rozhraní .NET Framework <xref:System.Data.OracleClient.OracleBFile> pro oracle zahrnuje třídu, <xref:System.Data.OracleClient.OracleType.BFile> která se používá pro práci s datovým typem Oracle.</span><span class="sxs-lookup"><span data-stu-id="64555-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="64555-104">Datový typ Oracle **BFILE** je datový typ Oracle **LOB,** který obsahuje odkaz na binární data s maximální velikostí 4 gigabajty.</span><span class="sxs-lookup"><span data-stu-id="64555-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="64555-105">Oracle **BFILE** se liší od ostatních datových typů Oracle **LOB** v tom, že jeho data jsou uložena ve fyzickém souboru v operačním systému namísto na serveru.</span><span class="sxs-lookup"><span data-stu-id="64555-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="64555-106">Všimněte si, že datový typ **BFILE** poskytuje přístup jen pro čtení k datům.</span><span class="sxs-lookup"><span data-stu-id="64555-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="64555-107">Další charakteristiky datového typu **BFILE,** které jej odlišují od datového typu **LOB,** jsou, že:</span><span class="sxs-lookup"><span data-stu-id="64555-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
- <span data-ttu-id="64555-108">Obsahuje nestrukturovaná data.</span><span class="sxs-lookup"><span data-stu-id="64555-108">Contains unstructured data.</span></span>  
  
- <span data-ttu-id="64555-109">Podporuje bloků na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="64555-109">Supports server-side chunking.</span></span>  
  
- <span data-ttu-id="64555-110">Používá sémantiku referenční kopie.</span><span class="sxs-lookup"><span data-stu-id="64555-110">Uses reference copy semantics.</span></span> <span data-ttu-id="64555-111">Pokud například provedete operaci kopírování na **BFILE**, zkopíruje se pouze lokátor **BFILE** (což je odkaz na soubor).</span><span class="sxs-lookup"><span data-stu-id="64555-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="64555-112">Data v souboru nejsou zkopírována.</span><span class="sxs-lookup"><span data-stu-id="64555-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="64555-113">Datový typ **BFILE** by měl být použit pro odkazování na loby, které jsou velké velikosti a proto není praktické ukládat v databázi.</span><span class="sxs-lookup"><span data-stu-id="64555-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="64555-114">Při použití datového typu **BFILE** ve srovnání s datovým typem **LOB** se jedná o další režii klienta, serveru a komunikace.</span><span class="sxs-lookup"><span data-stu-id="64555-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="64555-115">Je efektivnější přístup k **BFILE,** pokud potřebujete pouze získat malé množství dat.</span><span class="sxs-lookup"><span data-stu-id="64555-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="64555-116">Je efektivnější přístup k databázi rezidentní LOBs, pokud potřebujete získat celý objekt.</span><span class="sxs-lookup"><span data-stu-id="64555-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="64555-117">Každý objekt **OracleBFile,** který není null, je přidružen ke dvěma entitam, které definují umístění základního fyzického souboru:</span><span class="sxs-lookup"><span data-stu-id="64555-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1. <span data-ttu-id="64555-118">Objekt Oracle DIRECTORY, který je aliasem databáze pro adresář v systému souborů, a</span><span class="sxs-lookup"><span data-stu-id="64555-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2. <span data-ttu-id="64555-119">Název souboru podkladového fyzického souboru, který je umístěn v adresáři přidruženém k objektu DIRECTORY.</span><span class="sxs-lookup"><span data-stu-id="64555-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64555-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="64555-120">Example</span></span>  
 <span data-ttu-id="64555-121">Následující příklad jazyka C# ukazuje, jak můžete vytvořit **BFILE** v tabulce Oracle a pak jej načíst ve formě objektu **OracleBFile.**</span><span class="sxs-lookup"><span data-stu-id="64555-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="64555-122">Příklad ukazuje použití <xref:System.Data.OracleClient.OracleDataReader> objektu a **metody OracleBFile** **Seek** a **Read.**</span><span class="sxs-lookup"><span data-stu-id="64555-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="64555-123">Všimněte si, že chcete-li použít tuto ukázku,\\musíte nejprve vytvořit adresář s názvem "c: \bfiles" a soubor s názvem "MyFile.jpg" na serveru Oracle.</span><span class="sxs-lookup"><span data-stu-id="64555-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="64555-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="64555-124">See also</span></span>

- [<span data-ttu-id="64555-125">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="64555-125">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="64555-126">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="64555-126">ADO.NET Overview</span></span>](ado-net-overview.md)
