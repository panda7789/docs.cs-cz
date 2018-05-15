---
title: Využívání datové sady z webové služby XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: da3eca875df9b80f66241a2ecb72c5ba5c1df309
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="61d4f-102">Využívání datové sady z webové služby XML</span><span class="sxs-lookup"><span data-stu-id="61d4f-102">Consuming a DataSet from an XML Web Service</span></span>
<span data-ttu-id="61d4f-103"><xref:System.Data.DataSet> Byl navržen odpojené návrh, v části pro usnadnění pohodlný přenos dat přes Internet.</span><span class="sxs-lookup"><span data-stu-id="61d4f-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="61d4f-104">**Datovou sadu** je "serializovatelný", můžete zadat jako vstup nebo výstup webové služby XML bez další kódování požadované Streamovat obsah **datovou sadu** z webové služby XML na klienta a naopak.</span><span class="sxs-lookup"><span data-stu-id="61d4f-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="61d4f-105">**Datovou sadu** se implicitně převést na datový proud XML formátu formát DiffGram, odesílají přes síť a potom znovu vytvořena z datového proudu XML jako **datovou sadu** na koncové straně příjmu.</span><span class="sxs-lookup"><span data-stu-id="61d4f-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="61d4f-106">To vám dává velmi jednoduchá a flexibilní metodu pro přenášení a vrácení relačních dat pomocí webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="61d4f-106">This gives you a very simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="61d4f-107">Další informace o formátu, formátu DiffGram najdete v tématu [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="61d4f-107">For more information about the DiffGram format, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>  
  
 <span data-ttu-id="61d4f-108">Následující příklad ukazuje postup vytvoření webové služby XML a klienta, který používat **datovou sadu** přenosu relační data (včetně upravených dat) a vyřešte všechny aktualizace zpět do původního zdroje data.</span><span class="sxs-lookup"><span data-stu-id="61d4f-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61d4f-109">Doporučujeme, abyste při vytváření webové služby XML vždy zvažte vliv na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="61d4f-109">We recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="61d4f-110">Informace o zabezpečení webové služby XML, najdete v části [zabezpečení XML webové služby vytvořené pomocí ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).</span><span class="sxs-lookup"><span data-stu-id="61d4f-110">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).</span></span>  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a><span data-ttu-id="61d4f-111">Chcete-li vytvořit XML webové služby, který vrátí a odebírá datové sady</span><span class="sxs-lookup"><span data-stu-id="61d4f-111">To create an XML Web service that returns and consumes a DataSet</span></span>  
  
1.  <span data-ttu-id="61d4f-112">Vytvoření webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="61d4f-112">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="61d4f-113">V příkladu se vytvoří webové služby XML vracející data, v tomto případě seznam zákazníků z **Northwind** databáze a přijímá **datovou sadu** s aktualizace dat, které webové služby XML Přeloží zpět do původního zdroje data.</span><span class="sxs-lookup"><span data-stu-id="61d4f-113">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="61d4f-114">Webové služby XML zpřístupní dvě metody: **GetCustomers**vrátit se do seznamu zákazníků, a **UpdateCustomers**, chcete-li vyřešit aktualizací zpět do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="61d4f-114">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="61d4f-115">Webové služby XML je uložený v souboru na webový server s názvem DataSetSample.asmx.</span><span class="sxs-lookup"><span data-stu-id="61d4f-115">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="61d4f-116">Následující kód popisuje obsah DataSetSample.asmx.</span><span class="sxs-lookup"><span data-stu-id="61d4f-116">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
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
  
     <span data-ttu-id="61d4f-117">V typických možností **UpdateCustomers** metoda by byla zapsána k zachycení optimistickou metodu souběžného porušení.</span><span class="sxs-lookup"><span data-stu-id="61d4f-117">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="61d4f-118">Pro jednoduchost příklad nezahrnuje to.</span><span class="sxs-lookup"><span data-stu-id="61d4f-118">For simplicity, the example does not include this.</span></span> <span data-ttu-id="61d4f-119">Další informace o optimistickou metodu souběžného zpracování najdete v tématu [optimistickou metodu souběžného](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="61d4f-119">For more information about optimistic concurrency, see [Optimistic Concurrency](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).</span></span>  
  
2.  <span data-ttu-id="61d4f-120">Vytvořte proxy XML webové služby.</span><span class="sxs-lookup"><span data-stu-id="61d4f-120">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="61d4f-121">Klienti XML webové služby vyžadují proxy server protokolu SOAP, aby bylo možné využívat zveřejněné metody.</span><span class="sxs-lookup"><span data-stu-id="61d4f-121">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="61d4f-122">Můžete mít Visual Studio generovat tento proxy server za vás.</span><span class="sxs-lookup"><span data-stu-id="61d4f-122">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="61d4f-123">Nastavením odkaz na existující webovou službu z Visual Studia dojde transparentně všechny chování popsané v tomto kroku.</span><span class="sxs-lookup"><span data-stu-id="61d4f-123">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="61d4f-124">Pokud chcete vytvořit třídu proxy sami, pokračujte toto pojednání.</span><span class="sxs-lookup"><span data-stu-id="61d4f-124">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="61d4f-125">Ve většině situací ale pomocí sady Visual Studio vytvořit třídu proxy pro klientskou aplikaci je dostatečná.</span><span class="sxs-lookup"><span data-stu-id="61d4f-125">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="61d4f-126">Proxy server můžete vytvořit pomocí Web Services Description Language Tool.</span><span class="sxs-lookup"><span data-stu-id="61d4f-126">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="61d4f-127">Například, pokud webové služby XML je vystaven na adrese URL http://myserver/data/DataSetSample.asmx, vydejte příkaz například následující vytvořit proxy Visual Basic .NET k oboru názvů z **WebData.DSSample** a uložte ho sample.vb souboru.</span><span class="sxs-lookup"><span data-stu-id="61d4f-127">For example, if the XML Web service is exposed at the URL http://myserver/data/DataSetSample.asmx, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="61d4f-128">V souboru sample.cs vytvořit proxy C#, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="61d4f-128">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="61d4f-129">Proxy server můžete pak zkompilovat jako knihovnu a importovat klient XML webové služby.</span><span class="sxs-lookup"><span data-stu-id="61d4f-129">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="61d4f-130">Zkompilovat kód jazyka Visual Basic .NET proxy uložené v sample.vb jako sample.dll, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="61d4f-130">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="61d4f-131">Pro kompilaci proxy kódu C# uložené v sample.cs jako sample.dll, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="61d4f-131">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3.  <span data-ttu-id="61d4f-132">Vytvoření klienta XML webové služby.</span><span class="sxs-lookup"><span data-stu-id="61d4f-132">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="61d4f-133">Pokud chcete mít k vygenerovat třídu proxy webové služby sady Visual Studio, jednoduše vytvořit projekt klienta a, v okně Průzkumníku řešení klikněte pravým tlačítkem na projekt, klikněte na **přidat odkaz na Web**a vyberte webovou službu z seznam dostupných webových služeb (může to vyžadovat poskytnutí adresu koncový bod webové služby, pokud webová služba není k dispozici v aktuálním řešení, nebo v počítači.) Pokud služby proxy webových XML sami (jak je popsáno v předchozím kroku) vytvoříte, můžete ho importovat do kódu klienta a využívat metody XML webové služby.</span><span class="sxs-lookup"><span data-stu-id="61d4f-133">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, click **Add Web Reference**, and select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint, if the Web service isn't available within the current solution, or on the current computer.) If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span> <span data-ttu-id="61d4f-134">Následující vzorový kód importuje knihovnu proxy serveru, volání **GetCustomers** k získání seznamu zákazníků, přidá nového zákazníka a poté vrátí **datovou sadu** s aktualizace **UpdateCustomers** .</span><span class="sxs-lookup"><span data-stu-id="61d4f-134">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="61d4f-135">Všimněte si, že v příkladu předá **datovou sadu** vrácený **DataSet.GetChanges** k **UpdateCustomers** protože pouze změněné řádky potřebovat mají být předány  **UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="61d4f-135">Notice that the example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="61d4f-136">**UpdateCustomers** vrátí vyřešený **datovou sadu**, která pak můžete **sloučení** do existujících **datovou sadu** začlenit přeložit změny a všechny informace o chybě řádek z aktualizace.</span><span class="sxs-lookup"><span data-stu-id="61d4f-136">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="61d4f-137">Následující kód předpokládá, zda používáte Visual Studio vytvořit odkaz na Web a že přejmenovali webového odkazu na DsSample v **přidat odkaz na Web** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="61d4f-137">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
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
  
     <span data-ttu-id="61d4f-138">Pokud se rozhodnete vytvořit třídu proxy sami, musíte provést následující další kroky.</span><span class="sxs-lookup"><span data-stu-id="61d4f-138">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="61d4f-139">Zkompilovat ukázkový, zadejte knihovnu proxy serveru, který byl vytvořen (sample.dll) a související knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="61d4f-139">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="61d4f-140">Kompilace jazyka Visual Basic .NET verzi příkladu, uložené v souboru client.vb, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="61d4f-140">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="61d4f-141">Kompilace verze jazyka C# ukázce uložené v souboru client.cs, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="61d4f-141">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="61d4f-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="61d4f-142">See Also</span></span>  
 [<span data-ttu-id="61d4f-143">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="61d4f-143">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="61d4f-144">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="61d4f-144">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="61d4f-145">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="61d4f-145">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="61d4f-146">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="61d4f-146">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="61d4f-147">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="61d4f-147">Updating Data Sources with DataAdapters</span></span>](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="61d4f-148">Parametry adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="61d4f-148">DataAdapter Parameters</span></span>](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [<span data-ttu-id="61d4f-149">Web Services Description Language Tool (Wsdl.exe)</span><span class="sxs-lookup"><span data-stu-id="61d4f-149">Web Services Description Language Tool (Wsdl.exe)</span></span>](https://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88)  
 [<span data-ttu-id="61d4f-150">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="61d4f-150">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
