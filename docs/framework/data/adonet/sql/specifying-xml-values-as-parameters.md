---
title: "Zadání hodnoty XML jako parametry"
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
ms.assetid: 2c4d08b8-fc29-4614-97fa-29c8ff7ca5b3
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7514d2d19b6691fc5a25e17e7ad483d108fe4aa2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="specifying-xml-values-as-parameters"></a><span data-ttu-id="5649c-102">Zadání hodnoty XML jako parametry</span><span class="sxs-lookup"><span data-stu-id="5649c-102">Specifying XML Values as Parameters</span></span>
<span data-ttu-id="5649c-103">Pokud dotaz vyžaduje parametr, jehož hodnota je řetězec v kódu XML, vývojáři mohou zadat tuto hodnotu pomocí instance **SqlXml** datového typu.</span><span class="sxs-lookup"><span data-stu-id="5649c-103">If a query requires a parameter whose value is an XML string, developers can supply that value using an instance of the **SqlXml** data type.</span></span> <span data-ttu-id="5649c-104">Neexistují žádné triky; skutečně Sloupce XML v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] přijmout parametr hodnoty stejným způsobem jako jiné datové typy.</span><span class="sxs-lookup"><span data-stu-id="5649c-104">There really are no tricks; XML columns in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] accept parameter values in exactly the same way as other data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5649c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="5649c-105">Example</span></span>  
 <span data-ttu-id="5649c-106">Následující konzolové aplikace vytvoří novou tabulku v **AdventureWorks** databáze.</span><span class="sxs-lookup"><span data-stu-id="5649c-106">The following console application creates a new table in the **AdventureWorks** database.</span></span> <span data-ttu-id="5649c-107">Nová tabulka obsahuje sloupec s názvem **SalesID** a sloupec XML s názvem **SalesInfo**.</span><span class="sxs-lookup"><span data-stu-id="5649c-107">The new table includes a column named **SalesID** and an XML column named **SalesInfo**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5649c-108">**AdventureWorks** ukázkové databáze není nainstalována ve výchozím nastavení při instalaci [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5649c-108">The **AdventureWorks** sample database is not installed by default when you install [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5649c-109">Můžete ho nainstalovat tak, že spustíte instalační program SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="5649c-109">You can install it by running SQL Server Setup.</span></span>  
  
 <span data-ttu-id="5649c-110">V příkladu připraví <xref:System.Data.SqlClient.SqlCommand> objekt vložit řádek do nové tabulky.</span><span class="sxs-lookup"><span data-stu-id="5649c-110">The example prepares a <xref:System.Data.SqlClient.SqlCommand> object to insert a row in the new table.</span></span> <span data-ttu-id="5649c-111">Poskytuje XML data potřebná pro uloženého souboru **SalesInfo** sloupce.</span><span class="sxs-lookup"><span data-stu-id="5649c-111">A saved file provides the XML data needed for the **SalesInfo** column.</span></span>  
  
 <span data-ttu-id="5649c-112">K vytvoření souboru potřebné pro spuštění ukázky, vytvořte nový textový soubor ve stejné složce jako projektu.</span><span class="sxs-lookup"><span data-stu-id="5649c-112">To create the file needed for the example to run, create a new text file in the same folder as your project.</span></span> <span data-ttu-id="5649c-113">Název souboru MyTestStoreData.xml.</span><span class="sxs-lookup"><span data-stu-id="5649c-113">Name the file MyTestStoreData.xml.</span></span> <span data-ttu-id="5649c-114">Otevřete soubor v programu Poznámkový blok a zkopírujte a vložte následující text:</span><span class="sxs-lookup"><span data-stu-id="5649c-114">Open the file in Notepad and copy and paste the following text:</span></span>  
  
```xml  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>International Bank</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1970</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>7000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>T1</Internet>  
  <NumberEmployees>2</NumberEmployees>  
</StoreSurvey>  
```  
  
```vb  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Xml  
  
Module Module1  
    Sub Main()  
  
        Using connection As SqlConnection = New SqlConnection(GetConnectionString())  
        connection.Open()  
  
        ' Create a sample table (dropping first if it already  
        ' exists.)  
        Dim commandNewTable As String = _  
         "IF EXISTS (SELECT * FROM dbo.sysobjects " & _  
         "WHERE id = object_id(N'[dbo].[XmlDataTypeSample]') " & _  
         "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " & _  
         "DROP TABLE [dbo].[XmlDataTypeSample];" & _  
         "CREATE TABLE [dbo].[XmlDataTypeSample](" & _  
         "[SalesID] [int] IDENTITY(1,1) NOT NULL, " & _  
         "[SalesInfo] [xml])"  
  
        Dim commandAdd As New _  
         SqlCommand(commandNewTable, connection)  
        commandAdd.ExecuteNonQuery()  
  
        Dim commandText As String = _  
         "INSERT INTO [dbo].[XmlDataTypeSample] " & _  
           "([SalesInfo] ) " & _  
           "VALUES(@xmlParameter )"  
  
        Dim command As New SqlCommand(commandText, connection)  
  
        ' Read the saved XML document as a   
        ' SqlXml-data typed variable.  
        Dim newXml As SqlXml = _  
         New SqlXml(New XmlTextReader("MyTestStoreData.xml"))  
  
        ' Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml)  
  
        Dim result As Integer = command.ExecuteNonQuery()  
        Console.WriteLine(result & " row was added.")  
        Console.WriteLine("Press Enter to continue.")  
        Console.ReadLine()  
    End Using  
End Sub  
  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,              
        ' you can retrieve it from a configuration file.   
        Return "Data Source=(local);Integrated Security=SSPI;" & _  
          "Initial Catalog=AdventureWorks"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Xml;  
using System.Data.SqlTypes;  
  
class Class1  
{  
    static void Main()  
    {  
        using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
       {  
        connection.Open();  
        //  Create a sample table (dropping first if it already  
        //  exists.)  
  
        string commandNewTable =   
            "IF EXISTS (SELECT * FROM dbo.sysobjects " +   
            "WHERE id = " +  
                  "object_id(N'[dbo].[XmlDataTypeSample]') " +   
            "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " +   
            "DROP TABLE [dbo].[XmlDataTypeSample];" +   
            "CREATE TABLE [dbo].[XmlDataTypeSample](" +   
            "[SalesID] [int] IDENTITY(1,1) NOT NULL, " +   
            "[SalesInfo] [xml])";  
        SqlCommand commandAdd =   
                   new SqlCommand(commandNewTable, connection);  
        commandAdd.ExecuteNonQuery();  
        string commandText =   
            "INSERT INTO [dbo].[XmlDataTypeSample] " +   
            "([SalesInfo] ) " +   
            "VALUES(@xmlParameter )";  
        SqlCommand command =   
                  new SqlCommand(commandText, connection);  
  
        //  Read the saved XML document as a   
        //  SqlXml-data typed variable.  
        SqlXml newXml =   
            new SqlXml(new XmlTextReader("MyTestStoreData.xml"));  
  
        //  Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml);  
  
        int result = command.ExecuteNonQuery();  
        Console.WriteLine(result + " row was added.");  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,              
        // you can retrieve it from a configuration file.   
        return "Data Source=(local);Integrated Security=true;" +  
        "Initial Catalog=AdventureWorks; ";  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5649c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="5649c-115">See Also</span></span>  
 <xref:System.Data.SqlTypes.SqlXml>  
 [<span data-ttu-id="5649c-116">Data XML na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="5649c-116">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [<span data-ttu-id="5649c-117">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="5649c-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
