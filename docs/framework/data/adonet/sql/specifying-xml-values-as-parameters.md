---
title: Zadání hodnot XML jako parametry
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2c4d08b8-fc29-4614-97fa-29c8ff7ca5b3
ms.openlocfilehash: 0003e6c5e9499c066f47202a6dd03fc86268d679
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180667"
---
# <a name="specifying-xml-values-as-parameters"></a><span data-ttu-id="3a0e0-102">Zadání hodnot XML jako parametry</span><span class="sxs-lookup"><span data-stu-id="3a0e0-102">Specifying XML Values as Parameters</span></span>
<span data-ttu-id="3a0e0-103">Pokud dotaz vyžaduje parametr, jehož hodnota je řetězec XML, vývojáři můžete zadat tuto hodnotu pomocí instance **SqlXml** datového typu.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-103">If a query requires a parameter whose value is an XML string, developers can supply that value using an instance of the **SqlXml** data type.</span></span> <span data-ttu-id="3a0e0-104">Neexistují žádné triky; ve skutečnosti Sloupce XML v systému SQL Server přijmout hodnoty parametrů v přesně stejným způsobem jako jiné datové typy.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-104">There really are no tricks; XML columns in SQL Server accept parameter values in exactly the same way as other data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a0e0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a0e0-105">Example</span></span>  
 <span data-ttu-id="3a0e0-106">Vytvoří novou tabulku v následujících konzolovou aplikaci **AdventureWorks** databáze.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-106">The following console application creates a new table in the **AdventureWorks** database.</span></span> <span data-ttu-id="3a0e0-107">Nová tabulka obsahuje sloupec s názvem **SalesID** a sloupec XML s názvem **SalesInfo**.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-107">The new table includes a column named **SalesID** and an XML column named **SalesInfo**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a0e0-108">**AdventureWorks** ukázkovou databázi není nainstalovaný ve výchozím nastavení při instalaci systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-108">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="3a0e0-109">Můžete ho nainstalovat spuštěním instalační program systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-109">You can install it by running SQL Server Setup.</span></span>  
  
 <span data-ttu-id="3a0e0-110">V příkladu připraví <xref:System.Data.SqlClient.SqlCommand> objekt vložit řádek do nové tabulky.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-110">The example prepares a <xref:System.Data.SqlClient.SqlCommand> object to insert a row in the new table.</span></span> <span data-ttu-id="3a0e0-111">Uložený soubor obsahuje data XML, třeba **SalesInfo** sloupce.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-111">A saved file provides the XML data needed for the **SalesInfo** column.</span></span>  
  
 <span data-ttu-id="3a0e0-112">K vytvoření souboru potřebné pro spuštění ukázky vytvořte nový textový soubor ve stejné složce jako projekt.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-112">To create the file needed for the example to run, create a new text file in the same folder as your project.</span></span> <span data-ttu-id="3a0e0-113">Název souboru MyTestStoreData.xml.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-113">Name the file MyTestStoreData.xml.</span></span> <span data-ttu-id="3a0e0-114">Otevřete soubor v poznámkovém bloku a zkopírujte a vložte následující text:</span><span class="sxs-lookup"><span data-stu-id="3a0e0-114">Open the file in Notepad and copy and paste the following text:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a0e0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a0e0-115">See Also</span></span>  
 <xref:System.Data.SqlTypes.SqlXml>  
 [<span data-ttu-id="3a0e0-116">Data XML na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="3a0e0-116">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [<span data-ttu-id="3a0e0-117">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="3a0e0-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
