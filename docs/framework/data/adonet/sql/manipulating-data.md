---
title: Manipulace s daty
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 51096a2e-8b38-4c4d-a523-799bfdb7ec69
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4870e5f3a71f51cb788eae1aa2a1884f5084ad40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="manipulating-data"></a><span data-ttu-id="25bfd-102">Manipulace s daty</span><span class="sxs-lookup"><span data-stu-id="25bfd-102">Manipulating Data</span></span>
<span data-ttu-id="25bfd-103">Před zavedením z více Active výsledek sady (MARS) vývojáři bylo nutné použít více připojení nebo kurzory na straně serveru k řešení určité scénáře.</span><span class="sxs-lookup"><span data-stu-id="25bfd-103">Before the introduction of Multiple Active Result Sets (MARS), developers had to use either multiple connections or server-side cursors to solve certain scenarios.</span></span> <span data-ttu-id="25bfd-104">Kromě toho, když v situaci, transakční používaly více připojení, vázaný připojení (s **proceduru sp_getbindtoken** a **procedury sp_bindsession**) nebyly potřeba.</span><span class="sxs-lookup"><span data-stu-id="25bfd-104">In addition, when multiple connections were used in a transactional situation, bound connections (with **sp_getbindtoken** and **sp_bindsession**) were required.</span></span> <span data-ttu-id="25bfd-105">Následující scénáře ukazují, jak používat připojení s MARS místo více připojení.</span><span class="sxs-lookup"><span data-stu-id="25bfd-105">The following scenarios show how to use a MARS-enabled connection instead of multiple connections.</span></span>  
  
## <a name="using-multiple-commands-with-mars"></a><span data-ttu-id="25bfd-106">Použití více příkazů s MARS</span><span class="sxs-lookup"><span data-stu-id="25bfd-106">Using Multiple Commands with MARS</span></span>  
 <span data-ttu-id="25bfd-107">Následující aplikace konzoly ukazuje, jak používat dvě <xref:System.Data.SqlClient.SqlDataReader> objekty se dvěma <xref:System.Data.SqlClient.SqlCommand> objektů a jeden <xref:System.Data.SqlClient.SqlConnection> objekt s MARS povolena.</span><span class="sxs-lookup"><span data-stu-id="25bfd-107">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with two <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span>  
  
### <a name="example"></a><span data-ttu-id="25bfd-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="25bfd-108">Example</span></span>  
 <span data-ttu-id="25bfd-109">V příkladu otevře jednoho připojení k **AdventureWorks** databáze.</span><span class="sxs-lookup"><span data-stu-id="25bfd-109">The example opens a single connection to the **AdventureWorks** database.</span></span> <span data-ttu-id="25bfd-110">Použití <xref:System.Data.SqlClient.SqlCommand> objekt, <xref:System.Data.SqlClient.SqlDataReader> je vytvořena.</span><span class="sxs-lookup"><span data-stu-id="25bfd-110">Using a <xref:System.Data.SqlClient.SqlCommand> object, a <xref:System.Data.SqlClient.SqlDataReader> is created.</span></span> <span data-ttu-id="25bfd-111">Jak se používá program pro čtení, a druhé <xref:System.Data.SqlClient.SqlDataReader> je otevřen pomocí dat z první <xref:System.Data.SqlClient.SqlDataReader> jako vstup do klauzule WHERE pro druhý čtečku.</span><span class="sxs-lookup"><span data-stu-id="25bfd-111">As the reader is used, a second <xref:System.Data.SqlClient.SqlDataReader> is opened, using data from the first <xref:System.Data.SqlClient.SqlDataReader> as input to the WHERE clause for the second reader.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25bfd-112">Následující příklad používá vzorku **AdventureWorks** databáze součástí [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25bfd-112">The following example uses the sample **AdventureWorks** database included with [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="25bfd-113">V ukázkovém kódu v zadaném připojovacím řetězci předpokládá, že databáze je nainstalovaná a k dispozici v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="25bfd-113">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="25bfd-114">Upravte připojovací řetězec v případě potřeby pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="25bfd-114">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
Option Explicit On  
  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Module Module1  
  Sub Main()  
    ' By default, MARS is disabled when connecting  
    ' to a MARS-enabled host.  
    ' It must be enabled in the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Dim vendorID As Integer  
  
    Dim vendorCmd As SqlCommand  
    Dim productCmd As SqlCommand  
    Dim productReader As SqlDataReader  
  
    Dim vendorSQL As String = & _   
      "SELECT VendorId, Name FROM Purchasing.Vendor"  
    Dim productSQL As String = _  
        "SELECT Production.Product.Name FROM Production.Product " & _  
        "INNER JOIN Purchasing.ProductVendor " & _  
        "ON Production.Product.ProductID = " & _  
        "Purchasing.ProductVendor.ProductID " & _  
        "WHERE Purchasing.ProductVendor.VendorID = @VendorId"  
  
    Using awConnection As New SqlConnection(connectionString)  
      vendorCmd = New SqlCommand(vendorSQL, awConnection)  
      productCmd = New SqlCommand(productSQL, awConnection)  
      productCmd.Parameters.Add("@VendorId", SqlDbType.Int)  
  
      awConnection.Open()  
      Using vendorReader As SqlDataReader = vendorCmd.ExecuteReader()  
        While vendorReader.Read()  
          Console.WriteLine(vendorReader("Name"))  
  
          vendorID = CInt(vendorReader("VendorId"))  
  
          productCmd.Parameters("@VendorId").Value = vendorID  
  
          ' The following line of code requires  
          ' a MARS-enabled connection.  
          productReader = productCmd.ExecuteReader()  
          Using productReader  
            While productReader.Read()  
              Console.WriteLine("  " & CStr(productReader("Name")))  
            End While  
          End Using  
        End While  
      End Using  
    End Using  
  
    Console.WriteLine("Press any key to continue")  
    Console.ReadLine()  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrive it from a configuration file.  
    Return "Data Source=(local);Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks; MultipleActiveResultSets=True"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  int vendorID;  
  SqlDataReader productReader = null;  
  string vendorSQL =   
    "SELECT VendorId, Name FROM Purchasing.Vendor";  
  string productSQL =   
    "SELECT Production.Product.Name FROM Production.Product " +  
    "INNER JOIN Purchasing.ProductVendor " +  
    "ON Production.Product.ProductID = " +   
    "Purchasing.ProductVendor.ProductID " +  
    "WHERE Purchasing.ProductVendor.VendorID = @VendorId";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    SqlCommand productCmd =   
      new SqlCommand(productSQL, awConnection);  
  
    productCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    awConnection.Open();  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int)vendorReader["VendorId"];  
  
        productCmd.Parameters["@VendorId"].Value = vendorID;  
        // The following line of code requires  
        // a MARS-enabled connection.  
        productReader = productCmd.ExecuteReader();  
        using (productReader)  
        {  
          while (productReader.Read())  
          {  
            Console.WriteLine("  " +  
              productReader["Name"].ToString());  
          }  
        }  
      }  
  }  
      Console.WriteLine("Press any key to continue");  
      Console.ReadLine();  
    }  
  }  
  private static string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,  
    // you can retrive it from a configuration file.  
    return "Data Source=(local);Integrated Security=SSPI;" +   
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="reading-and-updating-data-with-mars"></a><span data-ttu-id="25bfd-115">Čtení a aktualizace dat pomocí MARS</span><span class="sxs-lookup"><span data-stu-id="25bfd-115">Reading and Updating Data with MARS</span></span>  
 <span data-ttu-id="25bfd-116">MARS umožňuje připojení, který se má použít pro obě operace a data manipulaci jazyk (DML) operací čtení s více než jedno čekající operace.</span><span class="sxs-lookup"><span data-stu-id="25bfd-116">MARS allows a connection to be used for both read operations and data manipulation language (DML) operations with more than one pending operation.</span></span> <span data-ttu-id="25bfd-117">Tato funkce eliminuje potřebu aplikace k řešení chyb zaneprázdněných připojení.</span><span class="sxs-lookup"><span data-stu-id="25bfd-117">This feature eliminates the need for an application to deal with connection-busy errors.</span></span> <span data-ttu-id="25bfd-118">Kromě toho můžete MARS nahradit uživatel kurzory na straně serveru, které obecně spotřebují více prostředků.</span><span class="sxs-lookup"><span data-stu-id="25bfd-118">In addition, MARS can replace the user of server-side cursors, which generally consume more resources.</span></span> <span data-ttu-id="25bfd-119">Nakonec, protože více operací může být použita u jednoho připojení, mohou sdílet stejné transakce kontextu, což eliminuje nutnost používat **proceduru sp_getbindtoken** a **procedury sp_bindsession** systémové uložené postupy.</span><span class="sxs-lookup"><span data-stu-id="25bfd-119">Finally, because multiple operations can operate on a single connection, they can share the same transaction context, eliminating the need to use **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span>  
  
### <a name="example"></a><span data-ttu-id="25bfd-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="25bfd-120">Example</span></span>  
 <span data-ttu-id="25bfd-121">Následující aplikace konzoly ukazuje, jak používat dvě <xref:System.Data.SqlClient.SqlDataReader> objekty s třemi <xref:System.Data.SqlClient.SqlCommand> objektů a jeden <xref:System.Data.SqlClient.SqlConnection> objekt s MARS povolena.</span><span class="sxs-lookup"><span data-stu-id="25bfd-121">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with three <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span> <span data-ttu-id="25bfd-122">První objekt příkazu načte seznam dodavatelů, jejichž platební hodnocení je 5.</span><span class="sxs-lookup"><span data-stu-id="25bfd-122">The first command object retrieves a list of vendors whose credit rating is 5.</span></span> <span data-ttu-id="25bfd-123">Druhý objekt příkazu používá zadáno ID od dodavatele <xref:System.Data.SqlClient.SqlDataReader> načíst druhý <xref:System.Data.SqlClient.SqlDataReader> se všemi produktů pro konkrétní dodavatele.</span><span class="sxs-lookup"><span data-stu-id="25bfd-123">The second command object uses the vendor ID provided from a <xref:System.Data.SqlClient.SqlDataReader> to load the second <xref:System.Data.SqlClient.SqlDataReader> with all of the products for the particular vendor.</span></span> <span data-ttu-id="25bfd-124">Každý záznam produktu je navštívené druhou <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="25bfd-124">Each product record is visited by the second <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="25bfd-125">Provádění výpočtu určit, jaké nové **OnOrderQty** by měl být.</span><span class="sxs-lookup"><span data-stu-id="25bfd-125">A calculation is performed to determine what the new **OnOrderQty** should be.</span></span> <span data-ttu-id="25bfd-126">Třetí objekt příkazu se pak používá k aktualizaci **ProductVendor** tabulku s novou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="25bfd-126">The third command object is then used to update the **ProductVendor** table with the new value.</span></span> <span data-ttu-id="25bfd-127">Tento celý proces probíhá v rámci jedné transakce, která je vrácena zpět na konci.</span><span class="sxs-lookup"><span data-stu-id="25bfd-127">This entire process takes place within a single transaction, which is rolled back at the end.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25bfd-128">Následující příklad používá vzorku **AdventureWorks** databáze součástí [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25bfd-128">The following example uses the sample **AdventureWorks** database included with [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="25bfd-129">V ukázkovém kódu v zadaném připojovacím řetězci předpokládá, že databáze je nainstalovaná a k dispozici v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="25bfd-129">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="25bfd-130">Upravte připojovací řetězec v případě potřeby pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="25bfd-130">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
Option Explicit On  
  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    ' By default, MARS is disabled when connecting  
    ' to a MARS-enabled host.  
    ' It must be enabled in the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Dim updateTx As SqlTransaction  
    Dim vendorCmd As SqlCommand  
    Dim prodVendCmd As SqlCommand  
    Dim updateCmd As SqlCommand  
  
    Dim prodVendReader As SqlDataReader  
  
    Dim vendorID As Integer  
    Dim productID As Integer  
    Dim minOrderQty As Integer  
    Dim maxOrderQty As Integer  
    Dim onOrderQty As Integer  
    Dim recordsUpdated As Integer  
    Dim totalRecordsUpdated As Integer  
  
    Dim vendorSQL As String = _  
        "SELECT VendorID, Name FROM Purchasing.Vendor " & _  
        "WHERE CreditRating = 5"  
    Dim prodVendSQL As String = _  
        "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " & _  
        "FROM Purchasing.ProductVendor " & _  
        "WHERE VendorID = @VendorID"  
    Dim updateSQL As String = _  
        "UPDATE Purchasing.ProductVendor " & _   
        "SET OnOrderQty = @OrderQty " & _  
        "WHERE ProductID = @ProductID AND VendorID = @VendorID"  
  
    Using awConnection As New SqlConnection(connectionString)  
      awConnection.Open()  
      updateTx = awConnection.BeginTransaction()  
  
      vendorCmd = New SqlCommand(vendorSQL, awConnection)  
      vendorCmd.Transaction = updateTx  
  
      prodVendCmd = New SqlCommand(prodVendSQL, awConnection)  
      prodVendCmd.Transaction = updateTx  
      prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int)  
  
      updateCmd = New SqlCommand(updateSQL, awConnection)  
      updateCmd.Transaction = updateTx  
      updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int)  
      updateCmd.Parameters.Add("@ProductID", SqlDbType.Int)  
      updateCmd.Parameters.Add("@VendorID", SqlDbType.Int)  
  
      Using vendorReader As SqlDataReader = vendorCmd.ExecuteReader()  
        While vendorReader.Read()  
          Console.WriteLine(vendorReader("Name"))  
  
          vendorID = CInt(vendorReader("VendorID"))  
          prodVendCmd.Parameters("@VendorID").Value = vendorID  
          prodVendReader = prodVendCmd.ExecuteReader()  
  
          Using prodVendReader  
            While (prodVendReader.Read)  
              productID = CInt(prodVendReader("ProductID"))  
  
              If IsDBNull(prodVendReader("OnOrderQty")) Then  
                minOrderQty = CInt(prodVendReader("MinOrderQty"))  
                onOrderQty = minOrderQty  
              Else  
                maxOrderQty = CInt(prodVendReader("MaxOrderQty"))  
                onOrderQty = CInt(maxOrderQty / 2)  
              End If  
  
              updateCmd.Parameters("@OrderQty").Value = onOrderQty  
              updateCmd.Parameters("@ProductID").Value = productID  
              updateCmd.Parameters("@VendorID").Value = vendorID  
  
              recordsUpdated = updateCmd.ExecuteNonQuery()  
              totalRecordsUpdated += recordsUpdated  
            End While  
          End Using  
        End While  
      End Using  
  
      Console.WriteLine("Total Records Updated: " & _   
        CStr(totalRecordsUpdated))  
      updateTx.Rollback()  
      Console.WriteLine("Transaction Rolled Back")  
    End Using  
  
    Console.WriteLine("Press any key to continue")  
    Console.ReadLine()  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrive it from a configuration file.  
    Return "Data Source=(local);Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  SqlTransaction updateTx = null;  
  SqlCommand vendorCmd = null;  
  SqlCommand prodVendCmd = null;  
  SqlCommand updateCmd = null;  
  
  SqlDataReader prodVendReader = null;  
  
  int vendorID = 0;  
  int productID = 0;  
  int minOrderQty = 0;  
  int maxOrderQty = 0;  
  int onOrderQty = 0;  
  int recordsUpdated = 0;  
  int totalRecordsUpdated = 0;  
  
  string vendorSQL =  
      "SELECT VendorID, Name FROM Purchasing.Vendor " +   
      "WHERE CreditRating = 5";  
  string prodVendSQL =  
      "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +  
      "FROM Purchasing.ProductVendor " +   
      "WHERE VendorID = @VendorID";  
  string updateSQL =  
      "UPDATE Purchasing.ProductVendor " +   
      "SET OnOrderQty = @OrderQty " +  
      "WHERE ProductID = @ProductID AND VendorID = @VendorID";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    awConnection.Open();  
    updateTx = awConnection.BeginTransaction();  
  
    vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    vendorCmd.Transaction = updateTx;  
  
    prodVendCmd = new SqlCommand(prodVendSQL, awConnection);  
    prodVendCmd.Transaction = updateTx;  
    prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    updateCmd = new SqlCommand(updateSQL, awConnection);  
    updateCmd.Transaction = updateTx;  
    updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);  
    updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);  
    updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);  
  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int) vendorReader["VendorID"];  
        prodVendCmd.Parameters["@VendorID"].Value = vendorID;  
        prodVendReader = prodVendCmd.ExecuteReader();  
  
        using (prodVendReader)  
        {  
          while (prodVendReader.Read())  
          {  
            productID = (int) prodVendReader["ProductID"];  
  
            if (prodVendReader["OnOrderQty"] == DBNull.Value)  
            {  
              minOrderQty = (int) prodVendReader["MinOrderQty"];  
              onOrderQty = minOrderQty;  
            }  
            else  
            {  
              maxOrderQty = (int) prodVendReader["MaxOrderQty"];  
              onOrderQty = (int)(maxOrderQty / 2);  
            }  
  
            updateCmd.Parameters["@OrderQty"].Value = onOrderQty;  
            updateCmd.Parameters["@ProductID"].Value = productID;  
            updateCmd.Parameters["@VendorID"].Value = vendorID;  
  
            recordsUpdated = updateCmd.ExecuteNonQuery();  
            totalRecordsUpdated += recordsUpdated;  
          }  
        }  
      }  
    }  
    Console.WriteLine("Total Records Updated: " +   
      totalRecordsUpdated.ToString());  
    updateTx.Rollback();  
    Console.WriteLine("Transaction Rolled Back");  
  }  
  
  Console.WriteLine("Press any key to continue");  
  Console.ReadLine();  
}  
private static string GetConnectionString()  
{  
  // To avoid storing the connection string in your code,  
  // you can retrive it from a configuration file.  
  return "Data Source=(local);Integrated Security=SSPI;" +   
    "Initial Catalog=AdventureWorks;" +   
    "MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="25bfd-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="25bfd-131">See Also</span></span>  
 [<span data-ttu-id="25bfd-132">Více aktivních sad výsledků (MARS)</span><span class="sxs-lookup"><span data-stu-id="25bfd-132">Multiple Active Result Sets (MARS)</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 [<span data-ttu-id="25bfd-133">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="25bfd-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
