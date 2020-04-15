---
title: Spotřebování datové sady z webové služby XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: d7328949e3eb4822b1a645bb5f0c1866f01ecb0a
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389748"
---
# <a name="consume-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="2ad5f-102">Využití datové sady z webové služby XML</span><span class="sxs-lookup"><span data-stu-id="2ad5f-102">Consume a DataSet from an XML web service</span></span>

<span data-ttu-id="2ad5f-103">Byl <xref:System.Data.DataSet> navržen s odpojeným designem, částečně pro usnadnění pohodlného přenosu dat přes internet.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="2ad5f-104">**DataSet** je "serializovatelný" v tom, že může být zadán jako vstup nebo výstup z webových služeb XML bez dalšího kódování potřebného k vysílání datového souboru **z** webové služby XML do klienta a zpět.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="2ad5f-105">**DataSet** je implicitně převedena na datový proud XML pomocí formátu DiffGram, odeslána po síti a pak rekonstruována z datového proudu XML jako **dataset** na přijímacím konci.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="2ad5f-106">To vám dává velmi jednoduchou a flexibilní metodu pro přenos a vrácení relačních dat pomocí webových služeb XML.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-106">This gives you a very simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="2ad5f-107">Další informace o formátu DiffGram naleznete v [tématu DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="2ad5f-107">For more information about the DiffGram format, see [DiffGrams](diffgrams.md).</span></span>  
  
 <span data-ttu-id="2ad5f-108">Následující příklad ukazuje, jak vytvořit webovou službu XML a klienta, kteří používají **DataSet** k přenosu relačních dat (včetně změněných dat) a vyřešit všechny aktualizace zpět do původního zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ad5f-109">Při vytváření webové služby XML doporučujeme vždy zvážit důsledky zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-109">We recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="2ad5f-110">Informace o zabezpečení webové služby XML naleznete v [tématu Zabezpečení webových služeb XML vytvořených pomocí ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2ad5f-110">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span></span>  
  
## <a name="create-an-xml-web-service"></a><span data-ttu-id="2ad5f-111">Vytvoření webové služby XML</span><span class="sxs-lookup"><span data-stu-id="2ad5f-111">Create an XML web service</span></span>
  
1. <span data-ttu-id="2ad5f-112">Vytvořte webovou službu XML.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-112">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="2ad5f-113">V příkladu je vytvořena webová služba XML, která vrací data, v tomto případě seznam zákazníků z databáze **Northwind,** a přijímá **datovou sadu** s aktualizacemi dat, které webová služba XML překládá zpět na původní zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-113">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="2ad5f-114">Webová služba XML zpřístupňuje dvě metody: **GetCustomers**, vrátit seznam zákazníků a **UpdateCustomers**, chcete-li přeložit aktualizace zpět do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-114">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="2ad5f-115">Webová služba XML je uložena v souboru na webovém serveru s názvem DataSetSample.asmx.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-115">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="2ad5f-116">Následující kód popisuje obsah DataSetSample.asmx.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-116">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
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
  
     <span data-ttu-id="2ad5f-117">V typickém scénáři **UpdateCustomers** metoda by být zapsána zachytit optimistické porušení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-117">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="2ad5f-118">Pro jednoduchost příklad neobsahuje toto.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-118">For simplicity, the example does not include this.</span></span> <span data-ttu-id="2ad5f-119">Další informace o optimistické souběžnosti naleznete [v tématu Optimistic Koncurrency](../optimistic-concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="2ad5f-119">For more information about optimistic concurrency, see [Optimistic Concurrency](../optimistic-concurrency.md).</span></span>  
  
2. <span data-ttu-id="2ad5f-120">Vytvořte proxy server webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-120">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="2ad5f-121">Klienti webové služby XML vyžadují proxy server SOAP, aby mohli využívat exponované metody.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-121">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="2ad5f-122">Můžete mít Visual Studio generovat tento proxy pro vás.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-122">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="2ad5f-123">Nastavením webového odkazu na existující webovou službu z aplikace Visual Studio dojde k transparentnímu chování popsanému v tomto kroku.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-123">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="2ad5f-124">Pokud chcete vytvořit proxy třídy sami, pokračujte v této diskusi.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-124">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="2ad5f-125">Ve většině případů však použití sady Visual Studio k vytvoření třídy proxy pro klientskou aplikaci je dostačující.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-125">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="2ad5f-126">Proxy server lze vytvořit pomocí nástroje Pro jazyk popisu webových služeb.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-126">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="2ad5f-127">Pokud je například webová služba XML `http://myserver/data/DataSetSample.asmx`vystavena na adrese URL , vyjezte příkaz, například následující, abyste vytvořili proxy serveru .NET jazyka Visual Basic s oborem názvů **webData.DSSample** a uložili jej do souboru sample.vb.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-127">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="2ad5f-128">Chcete-li v souboru vytvořit proxy server C#, sample.cs, vyjezte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-128">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="2ad5f-129">Proxy server pak může být kompilován jako knihovna a importován do klienta webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-129">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="2ad5f-130">Chcete-li zkompilovat proxy kód jazyka Visual Basic .NET uložený v souboru sample.vb jako soubor sample.dll, vyjezte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-130">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="2ad5f-131">Chcete-li zkompilovat proxy kód jazyka C# uložený v sample.cs jako sample.dll, vyjemte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-131">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. <span data-ttu-id="2ad5f-132">Vytvořte klienta webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-132">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="2ad5f-133">Pokud chcete, aby visual studio generovat proxy webové služby třídy pro vás, jednoduše vytvořit projekt klienta a v okně Průzkumník řešení, klepněte pravým tlačítkem myši na projekt a potom vyberte **přidat** > **odkaz na službu**.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-133">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, and then select **Add** > **Service Reference**.</span></span> <span data-ttu-id="2ad5f-134">V dialogovém okně **Přidat odkaz na službu** vyberte **Upřesnit**a pak vyberte **Přidat webový odkaz**.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-134">In the **Add Service Reference** dialog box, select **Advanced**, and then select **Add Web Reference**.</span></span> <span data-ttu-id="2ad5f-135">Vyberte webovou službu ze seznamu dostupných webových služeb (to může vyžadovat zadání adresy koncového bodu webové služby, pokud webová služba není k dispozici v aktuálním řešení nebo v aktuálním počítači).</span><span class="sxs-lookup"><span data-stu-id="2ad5f-135">Select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint if the Web service isn't available within the current solution or on the current computer).</span></span> <span data-ttu-id="2ad5f-136">Pokud vytvoříte proxy služby XML sami (jak je popsáno v předchozím kroku), můžete jej importovat do klientského kódu a využívat metody webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-136">If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span>

     <span data-ttu-id="2ad5f-137">Následující ukázkový kód importuje knihovnu proxy, volá **GetCustomers** získat seznam zákazníků, přidá nového zákazníka a vrátí **DataSet** s aktualizacemi **UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-137">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="2ad5f-138">Příklad předá **DataSet** vrácené **DataSet.GetChanges** **updateCustomers** protože pouze upravené řádky musí být **předány UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-138">The example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="2ad5f-139">**UpdateCustomers** vrátí vyřešenou **datovou sadu**, kterou pak můžete **sloučit** do existující **sady DataSet** a začlenit vyřešené změny a všechny informace o chybě řádku z aktualizace.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-139">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="2ad5f-140">Následující kód předpokládá, že jste použili Visual Studio k vytvoření webového odkazu a že jste přejmenovali webový odkaz na DsSample v dialogovém okně **Přidat webový odkaz.**</span><span class="sxs-lookup"><span data-stu-id="2ad5f-140">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
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
  
     <span data-ttu-id="2ad5f-141">Pokud se rozhodnete vytvořit třídu proxy sami, musíte provést následující další kroky.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-141">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="2ad5f-142">Chcete-li zkompilovat ukázku, zařazujte knihovnu proxy, která byla vytvořena (sample.dll) a související knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-142">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="2ad5f-143">Chcete-li zkompilovat verzi ukázky .NET jazyka Visual Basic uloženou v souboru client.vb, vyjekujte následujícím příkazem.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-143">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="2ad5f-144">Chcete-li zkompilovat verzi ukázky jazyka C#, která je uložena v souboru client.cs, vystavte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="2ad5f-144">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2ad5f-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ad5f-145">See also</span></span>

- [<span data-ttu-id="2ad5f-146">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2ad5f-146">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="2ad5f-147">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="2ad5f-147">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="2ad5f-148">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="2ad5f-148">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="2ad5f-149">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="2ad5f-149">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="2ad5f-150">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="2ad5f-150">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="2ad5f-151">Parametry adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="2ad5f-151">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- <span data-ttu-id="2ad5f-152">[Nástroj pro jazyk popisu webových služeb (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2ad5f-152">[Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span></span>
- [<span data-ttu-id="2ad5f-153">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2ad5f-153">ADO.NET Overview</span></span>](../ado-net-overview.md)
