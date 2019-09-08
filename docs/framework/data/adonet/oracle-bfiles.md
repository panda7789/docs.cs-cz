---
title: Soubory Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 214140bb8fcf43154b014ea3db609d355a27af7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794625"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="702b3-102">Soubory Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="702b3-102">Oracle BFILEs</span></span>
<span data-ttu-id="702b3-103">Zprostředkovatel dat .NET Framework pro Oracle obsahuje <xref:System.Data.OracleClient.OracleBFile> třídu, která se používá pro práci s datovým typem Oracle. <xref:System.Data.OracleClient.OracleType.BFile></span><span class="sxs-lookup"><span data-stu-id="702b3-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="702b3-104">Datový typ Oracle **BFILE** je typ dat **LOB** Oracle, který obsahuje odkaz na binární data s maximální velikostí 4 gigabajtů.</span><span class="sxs-lookup"><span data-stu-id="702b3-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="702b3-105">Oracle **BFILE** se liší od jiných datových typů typu Oracle **LOB** v tom, že jeho data se ukládají do fyzického souboru v operačním systému místo na serveru.</span><span class="sxs-lookup"><span data-stu-id="702b3-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="702b3-106">Všimněte si, že datový typ **BFILE** poskytuje přístup k datům jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="702b3-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="702b3-107">Další vlastnosti datového typu **BFILE** , které ho odlišují od datového typu **LOB** , jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="702b3-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
- <span data-ttu-id="702b3-108">Obsahuje nestrukturovaná data.</span><span class="sxs-lookup"><span data-stu-id="702b3-108">Contains unstructured data.</span></span>  
  
- <span data-ttu-id="702b3-109">Podporuje rozblokování na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="702b3-109">Supports server-side chunking.</span></span>  
  
- <span data-ttu-id="702b3-110">Používá sémantiku kopírování odkazů.</span><span class="sxs-lookup"><span data-stu-id="702b3-110">Uses reference copy semantics.</span></span> <span data-ttu-id="702b3-111">Například při provádění operace kopírování na **BFILE**se zkopíruje pouze **BFILE** Lokátor (což je odkaz na soubor).</span><span class="sxs-lookup"><span data-stu-id="702b3-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="702b3-112">Data v souboru se nekopírují.</span><span class="sxs-lookup"><span data-stu-id="702b3-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="702b3-113">Datový typ **BFILE** by se měl používat pro odkazování na objekty LOBs sy, které jsou velké velikosti, a proto není praktické ukládat do databáze.</span><span class="sxs-lookup"><span data-stu-id="702b3-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="702b3-114">Při použití datového typu **BFILE** v porovnání s datovým typem **LOB** je zapojená další režie klienta, serveru a komunikace.</span><span class="sxs-lookup"><span data-stu-id="702b3-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="702b3-115">Přístup k **BFILE** je efektivnější, jenom když potřebujete získat jen malé množství dat.</span><span class="sxs-lookup"><span data-stu-id="702b3-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="702b3-116">Přístup k objekty LOBs s rezidentu v databázi je efektivnější, pokud potřebujete získat celý objekt.</span><span class="sxs-lookup"><span data-stu-id="702b3-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="702b3-117">Každý objekt **OracleBFile** , který nemá hodnotu null, je přidružen ke dvěma entitám, které definují umístění podkladového fyzického souboru:</span><span class="sxs-lookup"><span data-stu-id="702b3-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1. <span data-ttu-id="702b3-118">Objekt adresáře Oracle, který je aliasem databáze pro adresář v systému souborů a</span><span class="sxs-lookup"><span data-stu-id="702b3-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2. <span data-ttu-id="702b3-119">Název souboru podkladového fyzického souboru, který je umístěn v adresáři přidruženém k objektu adresáře.</span><span class="sxs-lookup"><span data-stu-id="702b3-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="702b3-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="702b3-120">Example</span></span>  
 <span data-ttu-id="702b3-121">Následující C# příklad ukazuje, jak můžete vytvořit **BFILE** v tabulce Oracle a pak ho načíst ve formě objektu **OracleBFile** .</span><span class="sxs-lookup"><span data-stu-id="702b3-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="702b3-122">Příklad ukazuje použití <xref:System.Data.OracleClient.OracleDataReader> objektu a metod **hledání** a **čtení** **OracleBFile** .</span><span class="sxs-lookup"><span data-stu-id="702b3-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="702b3-123">Všimněte si, že aby bylo možné tuto ukázku použít, musíte nejprve na serveru Oracle vytvořit adresář s\\názvem "c: \bfiles" a souborem s názvem "MyFile. jpg".</span><span class="sxs-lookup"><span data-stu-id="702b3-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="702b3-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="702b3-124">See also</span></span>

- [<span data-ttu-id="702b3-125">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="702b3-125">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="702b3-126">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="702b3-126">ADO.NET Overview</span></span>](ado-net-overview.md)
