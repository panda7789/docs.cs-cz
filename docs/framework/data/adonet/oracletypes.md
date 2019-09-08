---
title: Typy Oracle
ms.date: 03/30/2017
ms.assetid: 18143304-d5c7-4c95-9995-678088d0c142
ms.openlocfilehash: 9caf30111fc8f856af69571d507c243efa549343
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783261"
---
# <a name="oracletypes"></a><span data-ttu-id="a49ae-102">Typy Oracle</span><span class="sxs-lookup"><span data-stu-id="a49ae-102">OracleTypes</span></span>
<span data-ttu-id="a49ae-103">Zprostředkovatel dat .NET Framework pro Oracle obsahuje několik struktur, které můžete použít pro práci s datovými typy Oracle.</span><span class="sxs-lookup"><span data-stu-id="a49ae-103">The .NET Framework Data Provider for Oracle includes several structures you can use to work with Oracle data types.</span></span> <span data-ttu-id="a49ae-104">Mezi ně <xref:System.Data.OracleClient.OracleNumber> patří <xref:System.Data.OracleClient.OracleString>a.</span><span class="sxs-lookup"><span data-stu-id="a49ae-104">These include <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a49ae-105">Úplný seznam těchto struktur naleznete v tématu <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="a49ae-105">For a complete list of these structures, see <xref:System.Data.OracleClient>.</span></span>  
  
 <span data-ttu-id="a49ae-106">Následující C# příklady:</span><span class="sxs-lookup"><span data-stu-id="a49ae-106">The following C# examples:</span></span>  
  
- <span data-ttu-id="a49ae-107">Vytvořte tabulku Oracle a načtěte ji s daty.</span><span class="sxs-lookup"><span data-stu-id="a49ae-107">Create an Oracle table and load it with data.</span></span>  
  
- <span data-ttu-id="a49ae-108">Použijte pro přístup k datům a použijte několik <xref:System.Data.OracleClient.OracleType> struktur k zobrazení dat. <xref:System.Data.OracleClient.OracleDataReader></span><span class="sxs-lookup"><span data-stu-id="a49ae-108">Use an <xref:System.Data.OracleClient.OracleDataReader> to access the data, and use several <xref:System.Data.OracleClient.OracleType> structures to display the data.</span></span>  
  
## <a name="creating-an-oracle-table"></a><span data-ttu-id="a49ae-109">Vytvoření tabulky Oracle</span><span class="sxs-lookup"><span data-stu-id="a49ae-109">Creating an Oracle Table</span></span>  
 <span data-ttu-id="a49ae-110">Tento příklad vytvoří tabulku Oracle a načte ji s daty.</span><span class="sxs-lookup"><span data-stu-id="a49ae-110">This example creates an Oracle table and loads it with data.</span></span> <span data-ttu-id="a49ae-111">Před spuštěním následujícího příkladu je nutné spustit tento příklad.</span><span class="sxs-lookup"><span data-stu-id="a49ae-111">You must run this example before running the next example.</span></span>  
  
```csharp  
public void Setup(string connectionString)  
   {  
   OracleConnection conn = new OracleConnection(connectionString);  
   try  
      {  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
      cmd.CommandText ="CREATE TABLE OracleTypesTable " +  
        "(MyVarchar2 varchar2(3000),MyNumber number(28,4) " +  
        "PRIMARY KEY ,MyDate date, MyRaw raw(255))";  
      cmd.ExecuteNonQuery();  
      cmd.CommandText ="INSERT INTO OracleTypesTable VALUES " +  
        "( 'test', 2, to_date('2000-01-11 12:54:01','yyyy-mm-dd " +  
        "hh24:mi:ss'), '0001020304' )";  
      cmd.ExecuteNonQuery();  
      }  
   catch(Exception)  
   {  
   }  
   finally  
   {  
      conn.Close();  
   }  
}  
```  
  
## <a name="retrieving-data-from-the-oracle-table"></a><span data-ttu-id="a49ae-112">Načítání dat z tabulky Oracle</span><span class="sxs-lookup"><span data-stu-id="a49ae-112">Retrieving Data from the Oracle Table</span></span>  
 <span data-ttu-id="a49ae-113">V tomto příkladu se pro přístup k datům používá **OracleDataReader** a k zobrazení dat používá několik struktur **OracleType** .</span><span class="sxs-lookup"><span data-stu-id="a49ae-113">This example uses an **OracleDataReader** to access the data, and uses several **OracleType** structures to display the data.</span></span>  
  
```csharp  
public void ReadOracleTypesExample(string connectionString)  
   {  
   OracleConnection myConnection =   
      new OracleConnection(connectionString);  
   myConnection.Open();  
   OracleCommand myCommand = myConnection.CreateCommand();  
  
   try  
      {  
      myCommand.CommandText = "SELECT * from OracleTypesTable";  
      OracleDataReader oracledatareader1 = myCommand.ExecuteReader();  
      oracledatareader1.Read();  
  
      //Using the oracle specific getters for each type is faster than  
      //using GetOracleValue.  
  
      //First column, MyVarchar2, is a VARCHAR2 data type in Oracle  
      //Server and maps to OracleString.  
      OracleString oraclestring1 =   
        oracledatareader1.GetOracleString(0);  
      Console.WriteLine("OracleString " + oraclestring1.ToString());  
  
      //Second column, MyNumber, is a NUMBER data type in Oracle Server  
      //and maps to OracleNumber.  
      OracleNumber oraclenumber1 =   
        oracledatareader1.GetOracleNumber(1);  
      Console.WriteLine("OracleNumber " + oraclenumber1.ToString());  
  
      //Third column, MyDate, is a DATA data type in Oracle Server  
      //and maps to OracleDateTime.  
      OracleDateTime oracledatetime1 =   
        oracledatareader1.GetOracleDateTime(2);  
      Console.WriteLine("OracleDateTime " + oracledatetime1.ToString());  
  
      //Fourth column, MyRaw, is a RAW data type in Oracle Server and  
      //maps to OracleBinary.  
      OracleBinary oraclebinary1 =   
        oracledatareader1.GetOracleBinary(3);  
      //Calling value on a null OracleBinary throws  
      //OracleNullValueException; therefore, check for a null value.  
      if (oraclebinary1.IsNull==false)  
      {  
         foreach(byte b in oraclebinary1.Value)  
         {  
            Console.WriteLine("byte " + b.ToString());  
         }  
      }  
      oracledatareader1.Close();  
   }  
   catch(Exception e)  
   {  
       Console.WriteLine(e.ToString());  
   }  
   finally  
   {  
       myConnection.Close();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a49ae-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a49ae-114">See also</span></span>

- [<span data-ttu-id="a49ae-115">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a49ae-115">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="a49ae-116">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a49ae-116">ADO.NET Overview</span></span>](ado-net-overview.md)
