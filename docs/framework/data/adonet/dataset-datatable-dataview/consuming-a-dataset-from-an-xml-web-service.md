---
title: Spotřebování datové sady z webové služby XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: 5f28179b43cb0af2d75e9e5b13783bc7287c8886
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784781"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="156e0-102">Spotřebování datové sady z webové služby XML</span><span class="sxs-lookup"><span data-stu-id="156e0-102">Consuming a DataSet from an XML Web Service</span></span>
<span data-ttu-id="156e0-103"><xref:System.Data.DataSet> Bylo navrženo s odpojeným návrhem, v rámci kterého se usnadnil pohodlný přenos dat přes Internet.</span><span class="sxs-lookup"><span data-stu-id="156e0-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="156e0-104">**Datová sada** je "serializovatelný" v tom, že ji lze zadat jako vstup nebo výstup z webových služeb XML bez jakéhokoli dalšího kódování požadovaného pro streamování obsahu **datové sady** z webové služby XML do klienta a zpět.</span><span class="sxs-lookup"><span data-stu-id="156e0-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="156e0-105">**Datová sada** je implicitně převedena na datový proud XML pomocí formátu DiffGram, který je odeslán přes síť a následně znovu sestaven z datového proudu XML jako **datová sada** na přijímacím konci.</span><span class="sxs-lookup"><span data-stu-id="156e0-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="156e0-106">Získáte tak velmi jednoduchou a flexibilní metodu pro přenášení a vracení relačních dat pomocí webových služeb XML.</span><span class="sxs-lookup"><span data-stu-id="156e0-106">This gives you a very simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="156e0-107">Další informace o formátu formátu DiffGram naleznete v tématu [DiffGram](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="156e0-107">For more information about the DiffGram format, see [DiffGrams](diffgrams.md).</span></span>  
  
 <span data-ttu-id="156e0-108">Následující příklad ukazuje, jak vytvořit webovou službu XML a klienta, které používají **datovou sadu** pro přenos relačních dat (včetně upravených dat) a řešení všech aktualizací zpátky do původního zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="156e0-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="156e0-109">Doporučujeme vždy vzít v úvahu důsledky zabezpečení při vytváření webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="156e0-109">We recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="156e0-110">Informace o zabezpečení webové služby XML najdete v tématu [zabezpečení webových služeb XML vytvořených pomocí ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="156e0-110">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span></span>  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a><span data-ttu-id="156e0-111">Vytvoření webové služby XML, která vrací a spotřebovává datovou sadu</span><span class="sxs-lookup"><span data-stu-id="156e0-111">To create an XML Web service that returns and consumes a DataSet</span></span>  
  
1. <span data-ttu-id="156e0-112">Vytvořte webovou službu XML.</span><span class="sxs-lookup"><span data-stu-id="156e0-112">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="156e0-113">V tomto příkladu je vytvořena webová služba XML, která vrací data, v tomto případě seznam zákazníků z databáze **Northwind** a obdrží **datovou sadu** s aktualizacemi dat, které webová služba XML překládá zpět na původní zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="156e0-113">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="156e0-114">Webová služba XML zpřístupňuje dvě metody: **GetCustomers**, pokud chcete vrátit seznam zákazníků a **UpdateCustomers**a vyřešit aktualizace zpět do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="156e0-114">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="156e0-115">Webová služba XML je uložena v souboru na webovém serveru s názvem DataSetSample. asmx.</span><span class="sxs-lookup"><span data-stu-id="156e0-115">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="156e0-116">Následující kód popisuje obsah DataSetSample. asmx.</span><span class="sxs-lookup"><span data-stu-id="156e0-116">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
    ```vb  
    <% @ WebService Language = "vb" Class = "Sample" %>  
    Imports System  
    Imports System.Data  
    Imports System.Data.SqlClient  
    Imports System.Web.Services  
  
    <WebService(Namespace:="http://microsoft.com/webservices/")> _  
    Public Class Sample  
  
    Public connection As SqlConnection = New SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind")  
  
      <WebMethod( Description := "Returns Northwind Customers", EnableSession := False )> _  
      Public Function GetCustomers() As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
          "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
        Dim custDS As DataSet = New DataSet()  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
        adapter.Fill(custDS, "Customers")  
  
        Return custDS  
      End Function  
  
      <WebMethod( Description := "Updates Northwind Customers", EnableSession := False )> _  
      Public Function UpdateCustomers(custDS As DataSet) As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter()  
  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Customers (CustomerID, CompanyName) " & _  
          "Values(@CustomerID, @CompanyName)", connection)  
        adapter.InsertCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.InsertCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Customers Set CustomerID = @CustomerID, " & _  
          "CompanyName = @CompanyName WHERE CustomerID = " & _  
          @OldCustomerID", connection)  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        Dim parameter As SqlParameter = _  
          adapter.UpdateCommand.Parameters.Add( _  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Customers WHERE CustomerID = @CustomerID", _  
          connection)  
        parameter = adapter.DeleteCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.Update(custDS, "Customers")  
  
        Return custDS  
      End Function  
    End Class  
    ```  
  
    ```csharp  
    <% @ WebService Language = "C#" Class = "Sample" %>  
    using System;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Web.Services;  
  
    [WebService(Namespace="http://microsoft.com/webservices/")]  
    public class Sample  
    {  
      public SqlConnection connection = new SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind");  
  
      [WebMethod( Description = "Returns Northwind Customers", EnableSession = false )]  
      public DataSet GetCustomers()  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter(  
          "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
        DataSet custDS = new DataSet();  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
        adapter.Fill(custDS, "Customers");  
  
        return custDS;  
      }  
  
      [WebMethod( Description = "Updates Northwind Customers",  
        EnableSession = false )]  
      public DataSet UpdateCustomers(DataSet custDS)  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        adapter.InsertCommand = new SqlCommand(  
          "INSERT INTO Customers (CustomerID, CompanyName) " +  
          "Values(@CustomerID, @CompanyName)", connection);  
        adapter.InsertCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.InsertCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
  
        adapter.UpdateCommand = new SqlCommand(  
          "UPDATE Customers Set CustomerID = @CustomerID, " +  
          "CompanyName = @CompanyName WHERE CustomerID = " +  
          "@OldCustomerID", connection);  
        adapter.UpdateCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.UpdateCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
        SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.DeleteCommand = new SqlCommand(  
        "DELETE FROM Customers WHERE CustomerID = @CustomerID",  
         connection);  
        parameter = adapter.DeleteCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.Update(custDS, "Customers");  
  
        return custDS;  
      }  
    }  
    ```  
  
     <span data-ttu-id="156e0-117">V typickém scénáři by byla metoda **UpdateCustomers** zapsána k zachycení optimistického narušení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="156e0-117">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="156e0-118">Pro zjednodušení tento příklad nezahrnuje.</span><span class="sxs-lookup"><span data-stu-id="156e0-118">For simplicity, the example does not include this.</span></span> <span data-ttu-id="156e0-119">Další informace o optimistické souběžnosti naleznete v tématu [Optimistická souběžnost](../optimistic-concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="156e0-119">For more information about optimistic concurrency, see [Optimistic Concurrency](../optimistic-concurrency.md).</span></span>  
  
2. <span data-ttu-id="156e0-120">Vytvoří proxy webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="156e0-120">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="156e0-121">Klienti webové služby XML vyžadují proxy protokolu SOAP, aby mohli využívat vystavené metody.</span><span class="sxs-lookup"><span data-stu-id="156e0-121">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="156e0-122">Aplikaci Visual Studio můžete vygenerovat tento proxy server za vás.</span><span class="sxs-lookup"><span data-stu-id="156e0-122">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="156e0-123">Když nastavíte webový odkaz na existující webovou službu z aplikace Visual Studio, veškeré chování popsané v tomto kroku bude transparentní.</span><span class="sxs-lookup"><span data-stu-id="156e0-123">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="156e0-124">Chcete-li vytvořit třídu proxy sami, pokračujte v této diskuzi.</span><span class="sxs-lookup"><span data-stu-id="156e0-124">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="156e0-125">Ve většině případů ale použití sady Visual Studio k vytvoření proxy třídy pro klientskou aplikaci postačuje.</span><span class="sxs-lookup"><span data-stu-id="156e0-125">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="156e0-126">Proxy server je možné vytvořit pomocí nástroje Web Services Description Language Tool.</span><span class="sxs-lookup"><span data-stu-id="156e0-126">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="156e0-127">Pokud je například webová služba XML vystavena na adrese URL `http://myserver/data/DataSetSample.asmx`, vydejte příkaz jako následující k vytvoření proxy serveru Visual Basic .NET s oborem názvů **WebData. DSSample** a uložte ho do souboru Sample. vb.</span><span class="sxs-lookup"><span data-stu-id="156e0-127">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="156e0-128">Pokud chcete vytvořit C# proxy v souboru Sample.cs, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="156e0-128">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="156e0-129">Proxy je pak možné zkompilovat jako knihovnu a importovat do klienta webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="156e0-129">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="156e0-130">Chcete-li zkompilovat kód proxy serveru Visual Basic .NET uložený v souboru Sample. vb jako Sample. dll, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="156e0-130">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="156e0-131">Chcete-li C# zkompilovat kód proxy uložený v Sample.cs jako Sample. dll, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="156e0-131">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. <span data-ttu-id="156e0-132">Vytvoří klienta webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="156e0-132">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="156e0-133">Pokud chcete, aby aplikace Visual Studio vygenerovala pro vás třídu proxy webové služby, stačí vytvořit klientský projekt a v okně Průzkumník řešení klikněte pravým tlačítkem myši na projekt, klikněte na **Přidat webový odkaz**a vyberte webovou službu ze seznamu dostupných webů. služby (to může vyžadovat poskytnutí adresy koncového bodu webové služby, pokud webová služba není dostupná v rámci aktuálního řešení nebo v aktuálním počítači.) Pokud vytvoříte proxy webové služby XML sami (jak je popsáno v předchozím kroku), můžete ho importovat do kódu klienta a využívat metody webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="156e0-133">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, click **Add Web Reference**, and select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint, if the Web service isn't available within the current solution, or on the current computer.) If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span> <span data-ttu-id="156e0-134">Následující vzorový kód importuje knihovnu proxy, volá **GetCustomers** , aby získal seznam zákazníků, přidal nového zákazníka a potom vrátí **datovou sadu** s aktualizacemi **UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="156e0-134">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="156e0-135">Všimněte si, že příklad předává **datovou sadu** vrácenou **sadou DataSet. GetChanges** to **UpdateCustomers** , protože do **UpdateCustomers**je nutné předat pouze upravené řádky.</span><span class="sxs-lookup"><span data-stu-id="156e0-135">Notice that the example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="156e0-136">**UpdateCustomers** vrátí přeloženou **datovou sadu**, kterou můžete **Sloučit** do existující **datové sady** , aby zahrnovala vyřešené změny a všechny informace o chybách řádků z aktualizace.</span><span class="sxs-lookup"><span data-stu-id="156e0-136">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="156e0-137">Následující kód předpokládá, že jste použili aplikaci Visual Studio k vytvoření webového odkazu a že jste přejmenovali webový odkaz na DsSample v dialogovém okně **Přidat webový odkaz** .</span><span class="sxs-lookup"><span data-stu-id="156e0-137">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
    ```vb  
    Imports System  
    Imports System.Data  
  
    Public Class Client  
  
      Public Shared Sub Main()  
        Dim proxySample As New DsSample.Sample ()  ' Proxy object.  
        Dim customersDataSet As DataSet = proxySample.GetCustomers()  
        Dim customersTable As DataTable = _  
          customersDataSet.Tables("Customers")  
  
        Dim rowAs DataRow = customersTable.NewRow()  
        row("CustomerID") = "ABCDE"  
        row("CompanyName") = "New Company Name"  
        customersTable.Rows.Add(row)  
  
        Dim updateDataSet As DataSet = _  
          proxySample.UpdateCustomers(customersDataSet.GetChanges())  
  
        customersDataSet.Merge(updateDataSet)  
        customersDataSet.AcceptChanges()  
      End Sub  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using System.Data;  
  
    public class Client  
    {  
      public static void Main()  
      {  
        Sample proxySample = new DsSample.Sample();  // Proxy object.  
        DataSet customersDataSet = proxySample.GetCustomers();  
        DataTable customersTable = customersDataSet.Tables["Customers"];  
  
        DataRow row = customersTable.NewRow();  
        row["CustomerID"] = "ABCDE";  
        row["CompanyName"] = "New Company Name";  
        customersTable.Rows.Add(row);  
  
        DataSet updateDataSet = new DataSet();  
  
        updateDataSet =   
          proxySample.UpdateCustomers(customersDataSet.GetChanges());  
  
        customersDataSet.Merge(updateDataSet);  
        customersDataSet.AcceptChanges();  
      }  
    }  
    ```  
  
     <span data-ttu-id="156e0-138">Pokud se rozhodnete vytvořit třídu proxy sami, musíte provést následující kroky navíc.</span><span class="sxs-lookup"><span data-stu-id="156e0-138">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="156e0-139">Chcete-li ukázku zkompilovat, poskytněte proxy knihovnu, která byla vytvořena (Sample. dll) a související knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="156e0-139">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="156e0-140">Chcete-li zkompilovat ukázkovou verzi rozhraní Visual Basic .NET, která je uložena v souboru Client. vb, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="156e0-140">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="156e0-141">Chcete-li C# zkompilovat verzi ukázky uloženou v souboru Client.cs, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="156e0-141">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="156e0-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="156e0-142">See also</span></span>

- [<span data-ttu-id="156e0-143">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="156e0-143">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="156e0-144">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="156e0-144">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="156e0-145">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="156e0-145">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="156e0-146">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="156e0-146">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="156e0-147">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="156e0-147">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="156e0-148">Parametry adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="156e0-148">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- <span data-ttu-id="156e0-149">[Nástroj Web Services Description Language (WSDL. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="156e0-149">[Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span></span>
- [<span data-ttu-id="156e0-150">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="156e0-150">ADO.NET Overview</span></span>](../ado-net-overview.md)
