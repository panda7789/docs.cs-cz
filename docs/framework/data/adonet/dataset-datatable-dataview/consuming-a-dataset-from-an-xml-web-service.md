---
title: Spotřebování datové sady z webové služby XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: 69eb1490c61cc7187d11c776fe95c659271750b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608479"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="bf4ce-102">Spotřebování datové sady z webové služby XML</span><span class="sxs-lookup"><span data-stu-id="bf4ce-102">Consuming a DataSet from an XML Web Service</span></span>
<span data-ttu-id="bf4ce-103"><xref:System.Data.DataSet> Byl navržen v odpojeném návrhu v části pro usnadnění pohodlný přenos dat přes Internet.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="bf4ce-104">**Datovou sadu** je "serializovatelný", můžete nastavit jako vstup nebo výstup z webové služby XML bez jakékoli další kódování požadované Streamovat obsah **datovou sadu** z webové služby XML do klienta a zpět.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="bf4ce-105">**Datovou sadu** je implicitně převeden na datový proud XML ve formátu formát DiffGram, posílaných prostřednictvím sítě a pak znovu vytvořena z datový proud XML jako **datovou sadu** na přijímající straně.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="bf4ce-106">To poskytuje velmi jednoduché a flexibilní metodu pro předávání a vracení relačních dat pomocí webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-106">This gives you a very simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="bf4ce-107">Další informace o formátu formát DiffGram najdete v tématu [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="bf4ce-107">For more information about the DiffGram format, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>  
  
 <span data-ttu-id="bf4ce-108">Následující příklad ukazuje, jak vytvořit webové služby XML a klienta, který používat **datovou sadu** přenosu relačních dat (včetně upravených dat) a vyřešte všechny aktualizace zpět do původního zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf4ce-109">Doporučujeme vám vždy zvážit důsledky zabezpečení při vytváření webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-109">We recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="bf4ce-110">Informace o zabezpečení webové služby XML, naleznete v tématu [zabezpečení XML webové služby vytvořené pomocí ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).</span><span class="sxs-lookup"><span data-stu-id="bf4ce-110">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).</span></span>  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a><span data-ttu-id="bf4ce-111">Vytvoření webové služby XML, který vrací a používá datovou sadu</span><span class="sxs-lookup"><span data-stu-id="bf4ce-111">To create an XML Web service that returns and consumes a DataSet</span></span>  
  
1.  <span data-ttu-id="bf4ce-112">Vytvoření webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-112">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="bf4ce-113">V tomto příkladu se vytvoří webové služby XML, který vrátí seznam zákazníků z dat, v tomto případě **Northwind** databáze a přijímá **datovou sadu** se aktualizace dat, které webové služby XML Přeloží zpět na původní zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-113">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="bf4ce-114">Webové služby XML poskytuje dvě metody: **GetCustomers**, který vrátí seznam zákazníků, a **UpdateCustomers**, chcete-li vyřešit aktualizací zpět do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-114">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="bf4ce-115">Webové služby XML je uložen v souboru na webovém serveru, který volá DataSetSample.asmx.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-115">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="bf4ce-116">Následující kód popisuje, jak obsah DataSetSample.asmx.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-116">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
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
  
     <span data-ttu-id="bf4ce-117">V rámci typického scénáře **UpdateCustomers** metody by byla zapsána na skutečné porušení optimistického řízení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-117">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="bf4ce-118">Pro zjednodušení příkladu nezahrnuje to.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-118">For simplicity, the example does not include this.</span></span> <span data-ttu-id="bf4ce-119">Další informace o optimistického řízení souběžnosti, naleznete v tématu [optimistického řízení souběžnosti](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="bf4ce-119">For more information about optimistic concurrency, see [Optimistic Concurrency](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).</span></span>  
  
2.  <span data-ttu-id="bf4ce-120">Vytvořte proxy XML webové služby.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-120">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="bf4ce-121">Aby bylo možné využívat metody vystavené, vyžadují klienti XML webové služby serveru proxy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-121">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="bf4ce-122">Můžete použít Visual Studio vygenerovat tento proxy server za vás.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-122">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="bf4ce-123">Nastavením webový odkaz na existující webové služby z Visual Studia vyvolá transparentně všechny chování, které jsou popsané v tomto kroku.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-123">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="bf4ce-124">Pokud chcete vytvořit třídu proxy, sami, pokračujte v této diskuse.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-124">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="bf4ce-125">Ve většině případů ale pomocí sady Visual Studio k vytvoření třídy proxy pro klientské aplikace je dostačující.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-125">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="bf4ce-126">Proxy server můžete vytvořit pomocí jazyka nástroj pro popis webových služeb.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-126">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="bf4ce-127">Například, pokud webové služby XML je přístupný na adrese URL `http://myserver/data/DataSetSample.asmx`, například následující příkaz vytvořit proxy Visual Basic .NET s oborem názvů z **WebData.DSSample** a uloží je v souboru sample.vb.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-127">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="bf4ce-128">V souboru sample.cs vytvořit proxy server C#, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-128">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="bf4ce-129">Proxy server pak může být sestaven jako knihovna a importovat do klient XML webové služby.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-129">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="bf4ce-130">Pro kompilaci kódu jazyka Visual Basic .NET proxy uložené v sample.vb jako sample.dll, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-130">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="bf4ce-131">Chcete-li zkompilovat proxy kód jazyka C# uložené v sample.cs jako sample.dll, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-131">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3.  <span data-ttu-id="bf4ce-132">Vytvoření klienta XML webové služby.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-132">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="bf4ce-133">Pokud chcete vygenerovat třídu proxy webové služby za vás sada Visual Studio, jednoduše vytvořte klientský projekt a v okně Průzkumníka řešení, klikněte pravým tlačítkem na projekt, klikněte na tlačítko **přidat webový odkaz**a vyberte webové služby z seznam dostupných webových služeb (to může vyžadovat zadání adresy koncového bodu webové služby, pokud webová služba není k dispozici v aktuálním řešení, nebo v aktuálním počítači.) Pokud budete moct vytvořit proxy XML webové služby sami (jak je popsáno v předchozím kroku), můžete importovat do kódu klienta a využívají metody XML webové služby.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-133">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, click **Add Web Reference**, and select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint, if the Web service isn't available within the current solution, or on the current computer.) If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span> <span data-ttu-id="bf4ce-134">Následující ukázkový kód importuje knihovna proxy serveru, volání **GetCustomers** zobrazíte seznam zákazníků, přidá nového zákazníka a poté vrátí **datovou sadu** s aktualizacemi **UpdateCustomers** .</span><span class="sxs-lookup"><span data-stu-id="bf4ce-134">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="bf4ce-135">Všimněte si, že příklad předá **datovou sadu** vrácený **DataSet.GetChanges** k **UpdateCustomers** vzhledem k tomu potřebovat pouze změněné řádky se mají předat  **UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-135">Notice that the example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="bf4ce-136">**UpdateCustomers** vrátí vyřešený **datovou sadu**, které pak můžete **sloučit** do existujících **datovou sadu** začlenit vyřešené změny a všechny informace o chybě řádek z aktualizace.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-136">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="bf4ce-137">Následující kód předpokládá, že používáte Visual Studio vytvořit webový odkaz a přejmenovali webový odkaz na DsSample v **přidat webový odkaz** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-137">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
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
  
     <span data-ttu-id="bf4ce-138">Pokud se rozhodnete vytvořit třídu proxy, sami, je nutné provést následující dodatečné kroky.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-138">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="bf4ce-139">Pro kompilaci vzorku, zadejte proxy server knihovny, který byl vytvořen (sample.dll) a související knihoven .NET.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-139">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="bf4ce-140">Kompilace jazyka Visual Basic .NET verze ukázky, které jsou uložené v souboru client.vb, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-140">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="bf4ce-141">Chcete-li zkompilovat verzi C#, ukázky, které jsou uložené v souboru client.cs, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="bf4ce-141">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bf4ce-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf4ce-142">See also</span></span>
- [<span data-ttu-id="bf4ce-143">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bf4ce-143">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="bf4ce-144">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="bf4ce-144">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="bf4ce-145">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="bf4ce-145">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="bf4ce-146">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="bf4ce-146">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="bf4ce-147">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="bf4ce-147">Updating Data Sources with DataAdapters</span></span>](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="bf4ce-148">Parametry adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="bf4ce-148">DataAdapter Parameters</span></span>](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)
- [<span data-ttu-id="bf4ce-149">Web Services Description Language Tool (Wsdl.exe)</span><span class="sxs-lookup"><span data-stu-id="bf4ce-149">Web Services Description Language Tool (Wsdl.exe)</span></span>](https://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88)
- [<span data-ttu-id="bf4ce-150">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="bf4ce-150">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
