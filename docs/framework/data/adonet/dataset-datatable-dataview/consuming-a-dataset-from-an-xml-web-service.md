---
title: Využití datové sady z webové služby XML
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: 2c8924ee3374489dded7e819ecde8e4d9da750bb
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374383"
---
# <a name="consume-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="ec7f5-102">Využití datové sady z webové služby XML</span><span class="sxs-lookup"><span data-stu-id="ec7f5-102">Consume a DataSet from an XML web service</span></span>

<span data-ttu-id="ec7f5-103"><xref:System.Data.DataSet>Bylo navrženo s odpojeným návrhem, v rámci kterého se usnadnil pohodlný přenos dat přes Internet.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="ec7f5-104">**Datová sada** je "serializovatelný" v tom, že ji lze zadat jako vstup nebo výstup z webových služeb XML bez jakéhokoli dalšího kódování požadovaného pro streamování obsahu **datové sady** z webové služby XML do klienta a zpět.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="ec7f5-105">**Datová sada** je implicitně převedena na datový proud XML pomocí formátu DiffGram, který je odeslán přes síť a následně znovu sestaven z datového proudu XML jako **datová sada** na přijímacím konci.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="ec7f5-106">Získáte tak jednoduchou a flexibilní metodu pro přenášení a vracení relačních dat pomocí webových služeb XML.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-106">This gives you a simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="ec7f5-107">Další informace o formátu formátu DiffGram naleznete v tématu [DiffGram](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="ec7f5-107">For more information about the DiffGram format, see [DiffGrams](diffgrams.md).</span></span>  
  
 <span data-ttu-id="ec7f5-108">Následující příklad ukazuje, jak vytvořit webovou službu XML a klienta, které používají **datovou sadu** pro přenos relačních dat (včetně upravených dat) a řešení všech aktualizací zpátky do původního zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec7f5-109">Přenosy `DataSet` nebo `DataTable` instance v rámci volání webové služby XML nejsou bezpečné, pokud vstup není důvěryhodný.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-109">Transmitting `DataSet` or `DataTable` instances as part of XML Web service calls is not safe if the input is not trusted.</span></span> <span data-ttu-id="ec7f5-110">Další informace najdete v tématu [doprovodné materiály k zabezpečení datových sad a DataTable](/dotnet/framework/data/adonet/dataset-datatable-dataview/security-guidance).</span><span class="sxs-lookup"><span data-stu-id="ec7f5-110">For more information, see [DataSet and DataTable security guidance](/dotnet/framework/data/adonet/dataset-datatable-dataview/security-guidance).</span></span>
> <span data-ttu-id="ec7f5-111">Doporučujeme vám také při vytváření webové služby XML vždy vzít v úvahu důsledky zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-111">We also recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="ec7f5-112">Informace o zabezpečení webové služby XML najdete v tématu [zabezpečení webových služeb XML vytvořených pomocí ASP.NET](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ec7f5-112">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span></span>  
  
## <a name="create-an-xml-web-service"></a><span data-ttu-id="ec7f5-113">Vytvoření webové služby XML</span><span class="sxs-lookup"><span data-stu-id="ec7f5-113">Create an XML web service</span></span>
  
1. <span data-ttu-id="ec7f5-114">Vytvořte webovou službu XML.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-114">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="ec7f5-115">V tomto příkladu je vytvořena webová služba XML, která vrací data, v tomto případě seznam zákazníků z databáze **Northwind** a obdrží **datovou sadu** s aktualizacemi dat, které webová služba XML překládá zpět na původní zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-115">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="ec7f5-116">Webová služba XML zpřístupňuje dvě metody: **GetCustomers**, vrátí seznam zákazníků a **UpdateCustomers**, aby vyřešila aktualizace zpět do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-116">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="ec7f5-117">Webová služba XML je uložena v souboru na webovém serveru s názvem DataSetSample. asmx.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-117">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="ec7f5-118">Následující kód popisuje obsah DataSetSample. asmx.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-118">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
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
  
     <span data-ttu-id="ec7f5-119">V typickém scénáři by byla metoda **UpdateCustomers** zapsána k zachycení optimistického narušení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-119">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="ec7f5-120">Pro zjednodušení tento příklad nezahrnuje.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-120">For simplicity, the example does not include this.</span></span> <span data-ttu-id="ec7f5-121">Další informace o optimistické souběžnosti naleznete v tématu [Optimistická souběžnost](../optimistic-concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="ec7f5-121">For more information about optimistic concurrency, see [Optimistic Concurrency](../optimistic-concurrency.md).</span></span>  
  
2. <span data-ttu-id="ec7f5-122">Vytvoří proxy webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-122">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="ec7f5-123">Klienti webové služby XML vyžadují proxy protokolu SOAP, aby mohli využívat vystavené metody.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-123">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="ec7f5-124">Aplikaci Visual Studio můžete vygenerovat tento proxy server za vás.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-124">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="ec7f5-125">Když nastavíte webový odkaz na existující webovou službu z aplikace Visual Studio, veškeré chování popsané v tomto kroku bude transparentní.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-125">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="ec7f5-126">Chcete-li vytvořit třídu proxy sami, pokračujte v této diskuzi.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-126">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="ec7f5-127">Ve většině případů ale použití sady Visual Studio k vytvoření proxy třídy pro klientskou aplikaci postačuje.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-127">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="ec7f5-128">Proxy server je možné vytvořit pomocí nástroje Web Services Description Language Tool.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-128">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="ec7f5-129">Pokud je například webová služba XML vystavena na adrese URL `http://myserver/data/DataSetSample.asmx` , vydejte příkaz jako následující k vytvoření proxy serveru Visual Basic .NET s oborem názvů **WebData. DSSample** a uložte ho do souboru Sample. vb.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-129">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="ec7f5-130">Pokud chcete v souboru sample.cs vytvořit proxy C#, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-130">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="ec7f5-131">Proxy je pak možné zkompilovat jako knihovnu a importovat do klienta webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-131">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="ec7f5-132">Chcete-li zkompilovat kód proxy serveru Visual Basic .NET uložený v souboru Sample. vb jako sample.dll, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-132">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="ec7f5-133">Chcete-li zkompilovat kód proxy jazyka C# uložený v sample.cs jako sample.dll, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-133">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. <span data-ttu-id="ec7f5-134">Vytvoří klienta webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-134">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="ec7f5-135">Pokud chcete, aby aplikace Visual Studio vygenerovala pro vás třídu proxy webové služby, stačí vytvořit klientský projekt a v okně Průzkumník řešení klikněte pravým tlačítkem myši na projekt a pak vyberte **Přidat**  >  **odkaz na službu**.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-135">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, and then select **Add** > **Service Reference**.</span></span> <span data-ttu-id="ec7f5-136">V dialogovém okně **Přidat odkaz na službu** vyberte **Upřesnit**a pak vyberte **Přidat webový odkaz**.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-136">In the **Add Service Reference** dialog box, select **Advanced**, and then select **Add Web Reference**.</span></span> <span data-ttu-id="ec7f5-137">Vyberte webovou službu ze seznamu dostupných webových služeb (to může vyžadovat, aby se zadala adresa koncového bodu webové služby, pokud webová služba není v aktuálním řešení nebo v aktuálním počítači k dispozici).</span><span class="sxs-lookup"><span data-stu-id="ec7f5-137">Select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint if the Web service isn't available within the current solution or on the current computer).</span></span> <span data-ttu-id="ec7f5-138">Pokud vytvoříte proxy webové služby XML sami (jak je popsáno v předchozím kroku), můžete ho importovat do kódu klienta a využívat metody webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-138">If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span>

     <span data-ttu-id="ec7f5-139">Následující vzorový kód importuje knihovnu proxy, volá **GetCustomers** , aby získal seznam zákazníků, přidal nového zákazníka a potom vrátí **datovou sadu** s aktualizacemi **UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-139">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="ec7f5-140">Tento příklad předá **datovou sadu** vrácenou sadou **DataSet. GetChanges** to **UpdateCustomers** , protože do **UpdateCustomers**je nutné předat pouze upravené řádky.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-140">The example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="ec7f5-141">**UpdateCustomers** vrátí přeloženou **datovou sadu**, kterou můžete **Sloučit** do existující **datové sady** , aby zahrnovala vyřešené změny a všechny informace o chybách řádků z aktualizace.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-141">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="ec7f5-142">Následující kód předpokládá, že jste použili aplikaci Visual Studio k vytvoření webového odkazu a že jste přejmenovali webový odkaz na DsSample v dialogovém okně **Přidat webový odkaz** .</span><span class="sxs-lookup"><span data-stu-id="ec7f5-142">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
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
  
     <span data-ttu-id="ec7f5-143">Pokud se rozhodnete vytvořit třídu proxy sami, musíte provést následující kroky navíc.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-143">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="ec7f5-144">Pokud chcete ukázku zkompilovat, poskytněte proxy knihovnu, která byla vytvořena (sample.dll) a související knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-144">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="ec7f5-145">Chcete-li zkompilovat ukázkovou verzi rozhraní Visual Basic .NET, která je uložena v souboru Client. vb, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-145">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="ec7f5-146">Pro zkompilování ukázky verze C#, která je uložena v souboru client.cs, vydejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="ec7f5-146">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ec7f5-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec7f5-147">See also</span></span>

- [<span data-ttu-id="ec7f5-148">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ec7f5-148">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="ec7f5-149">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="ec7f5-149">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="ec7f5-150">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="ec7f5-150">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="ec7f5-151">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="ec7f5-151">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="ec7f5-152">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="ec7f5-152">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="ec7f5-153">Parametry adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="ec7f5-153">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- <span data-ttu-id="ec7f5-154">[Nástroj Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ec7f5-154">[Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span></span>
- [<span data-ttu-id="ec7f5-155">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ec7f5-155">ADO.NET Overview</span></span>](../ado-net-overview.md)
