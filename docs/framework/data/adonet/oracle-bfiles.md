---
title: Soubory Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 07a7f28e08ed43672e94151cd9de88301069e1ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142386"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="8bf10-102">Soubory Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="8bf10-102">Oracle BFILEs</span></span>
<span data-ttu-id="8bf10-103">Zprostředkovatel dat .NET Framework pro Oracle se zahrnuje <xref:System.Data.OracleClient.OracleBFile> třídu, která se používá pro práci s Oracle <xref:System.Data.OracleClient.OracleType.BFile> datového typu.</span><span class="sxs-lookup"><span data-stu-id="8bf10-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="8bf10-104">Oracle **BFILE** je datový typ Oracle **LOB** datový typ, který obsahuje odkaz na binárních dat a maximální velikost 4 GB.</span><span class="sxs-lookup"><span data-stu-id="8bf10-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="8bf10-105">Oracle **BFILE** se liší od jiných Oracle **LOB** datové typy v tom, že jeho data se ukládají v fyzický soubor v operačním systému místo na serveru.</span><span class="sxs-lookup"><span data-stu-id="8bf10-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="8bf10-106">Všimněte si, **BFILE** datový typ poskytuje přístup jen pro čtení k datům.</span><span class="sxs-lookup"><span data-stu-id="8bf10-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="8bf10-107">Další vlastnosti **BFILE** datový typ, který odlišit od **LOB** se, že datový typ:</span><span class="sxs-lookup"><span data-stu-id="8bf10-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
-   <span data-ttu-id="8bf10-108">Obsahuje Nestrukturovaná data.</span><span class="sxs-lookup"><span data-stu-id="8bf10-108">Contains unstructured data.</span></span>  
  
-   <span data-ttu-id="8bf10-109">Podporuje bloků na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="8bf10-109">Supports server-side chunking.</span></span>  
  
-   <span data-ttu-id="8bf10-110">Odkazovat na používá sémantiku kopírování.</span><span class="sxs-lookup"><span data-stu-id="8bf10-110">Uses reference copy semantics.</span></span> <span data-ttu-id="8bf10-111">Například, pokud provádíte operaci kopírování na **BFILE**, pouze **BFILE** zkopíruje Lokátor (což je odkaz na soubor).</span><span class="sxs-lookup"><span data-stu-id="8bf10-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="8bf10-112">Data v souboru není zkopírován.</span><span class="sxs-lookup"><span data-stu-id="8bf10-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="8bf10-113">**BFILE** datový typ by měl použít pro odkazování na objekty LOBs, které jsou velké a proto není praktické ukládá do databáze.</span><span class="sxs-lookup"><span data-stu-id="8bf10-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="8bf10-114">Další režii klienta, server a komunikace je zahrnuta při použití **BFILE** datový typ ve srovnání s **LOB** datového typu.</span><span class="sxs-lookup"><span data-stu-id="8bf10-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="8bf10-115">Je mnohem efektivnější pro přístup k **BFILE** Pokud potřebujete získat malé množství dat.</span><span class="sxs-lookup"><span data-stu-id="8bf10-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="8bf10-116">To je mnohem efektivnější pro přístup k databázi rezidentní objekty LOBs, pokud je třeba získat celý objekt.</span><span class="sxs-lookup"><span data-stu-id="8bf10-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="8bf10-117">Každý NENULOVOU **OracleBFile** objekt je přidružený dvě entity, které definují umístění podkladový fyzický soubor:</span><span class="sxs-lookup"><span data-stu-id="8bf10-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1.  <span data-ttu-id="8bf10-118">Objekt adresáře Oracle, což je alias databáze pro adresář v systému souborů, a</span><span class="sxs-lookup"><span data-stu-id="8bf10-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2.  <span data-ttu-id="8bf10-119">Název souboru základního fyzického souboru, který je umístěn v adresáři přidružená k objektu adresáře.</span><span class="sxs-lookup"><span data-stu-id="8bf10-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bf10-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="8bf10-120">Example</span></span>  
 <span data-ttu-id="8bf10-121">Následující příklad jazyka C# ukazuje, jak můžete vytvořit **BFILE** Oracle tabulce a potom ho načíst ve formě **OracleBFile** objektu.</span><span class="sxs-lookup"><span data-stu-id="8bf10-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="8bf10-122">Tento příklad ukazuje použití <xref:System.Data.OracleClient.OracleDataReader> objektu a **OracleBFile** **Seek** a **čtení** metody.</span><span class="sxs-lookup"><span data-stu-id="8bf10-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="8bf10-123">Všimněte si, že chcete-li použít tento příklad, musíte nejprve vytvořit adresář s názvem "c:\\\bfiles" a soubor s názvem "MyFile.jpg" na serveru Oracle.</span><span class="sxs-lookup"><span data-stu-id="8bf10-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8bf10-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bf10-124">See also</span></span>

- [<span data-ttu-id="8bf10-125">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8bf10-125">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [<span data-ttu-id="8bf10-126">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="8bf10-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
