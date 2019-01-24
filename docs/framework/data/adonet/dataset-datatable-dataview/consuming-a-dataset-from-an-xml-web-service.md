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
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>Spotřebování datové sady z webové služby XML
<xref:System.Data.DataSet> Byl navržen v odpojeném návrhu v části pro usnadnění pohodlný přenos dat přes Internet. **Datovou sadu** je "serializovatelný", můžete nastavit jako vstup nebo výstup z webové služby XML bez jakékoli další kódování požadované Streamovat obsah **datovou sadu** z webové služby XML do klienta a zpět. **Datovou sadu** je implicitně převeden na datový proud XML ve formátu formát DiffGram, posílaných prostřednictvím sítě a pak znovu vytvořena z datový proud XML jako **datovou sadu** na přijímající straně. To poskytuje velmi jednoduché a flexibilní metodu pro předávání a vracení relačních dat pomocí webové služby XML. Další informace o formátu formát DiffGram najdete v tématu [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).  
  
 Následující příklad ukazuje, jak vytvořit webové služby XML a klienta, který používat **datovou sadu** přenosu relačních dat (včetně upravených dat) a vyřešte všechny aktualizace zpět do původního zdroje dat.  
  
> [!NOTE]
>  Doporučujeme vám vždy zvážit důsledky zabezpečení při vytváření webové služby XML. Informace o zabezpečení webové služby XML, naleznete v tématu [zabezpečení XML webové služby vytvořené pomocí ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>Vytvoření webové služby XML, který vrací a používá datovou sadu  
  
1.  Vytvoření webové služby XML.  
  
     V tomto příkladu se vytvoří webové služby XML, který vrátí seznam zákazníků z dat, v tomto případě **Northwind** databáze a přijímá **datovou sadu** se aktualizace dat, které webové služby XML Přeloží zpět na původní zdroj dat.  
  
     Webové služby XML poskytuje dvě metody: **GetCustomers**, který vrátí seznam zákazníků, a **UpdateCustomers**, chcete-li vyřešit aktualizací zpět do zdroje dat. Webové služby XML je uložen v souboru na webovém serveru, který volá DataSetSample.asmx. Následující kód popisuje, jak obsah DataSetSample.asmx.  
  
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
  
     V rámci typického scénáře **UpdateCustomers** metody by byla zapsána na skutečné porušení optimistického řízení souběžnosti. Pro zjednodušení příkladu nezahrnuje to. Další informace o optimistického řízení souběžnosti, naleznete v tématu [optimistického řízení souběžnosti](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).  
  
2.  Vytvořte proxy XML webové služby.  
  
     Aby bylo možné využívat metody vystavené, vyžadují klienti XML webové služby serveru proxy protokolu SOAP. Můžete použít Visual Studio vygenerovat tento proxy server za vás. Nastavením webový odkaz na existující webové služby z Visual Studia vyvolá transparentně všechny chování, které jsou popsané v tomto kroku. Pokud chcete vytvořit třídu proxy, sami, pokračujte v této diskuse. Ve většině případů ale pomocí sady Visual Studio k vytvoření třídy proxy pro klientské aplikace je dostačující.  
  
     Proxy server můžete vytvořit pomocí jazyka nástroj pro popis webových služeb. Například, pokud webové služby XML je přístupný na adrese URL `http://myserver/data/DataSetSample.asmx`, například následující příkaz vytvořit proxy Visual Basic .NET s oborem názvů z **WebData.DSSample** a uloží je v souboru sample.vb.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     V souboru sample.cs vytvořit proxy server C#, vydejte následující příkaz.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     Proxy server pak může být sestaven jako knihovna a importovat do klient XML webové služby. Pro kompilaci kódu jazyka Visual Basic .NET proxy uložené v sample.vb jako sample.dll, vydejte následující příkaz.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     Chcete-li zkompilovat proxy kód jazyka C# uložené v sample.cs jako sample.dll, vydejte následující příkaz.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3.  Vytvoření klienta XML webové služby.  
  
     Pokud chcete vygenerovat třídu proxy webové služby za vás sada Visual Studio, jednoduše vytvořte klientský projekt a v okně Průzkumníka řešení, klikněte pravým tlačítkem na projekt, klikněte na tlačítko **přidat webový odkaz**a vyberte webové služby z seznam dostupných webových služeb (to může vyžadovat zadání adresy koncového bodu webové služby, pokud webová služba není k dispozici v aktuálním řešení, nebo v aktuálním počítači.) Pokud budete moct vytvořit proxy XML webové služby sami (jak je popsáno v předchozím kroku), můžete importovat do kódu klienta a využívají metody XML webové služby. Následující ukázkový kód importuje knihovna proxy serveru, volání **GetCustomers** zobrazíte seznam zákazníků, přidá nového zákazníka a poté vrátí **datovou sadu** s aktualizacemi **UpdateCustomers** .  
  
     Všimněte si, že příklad předá **datovou sadu** vrácený **DataSet.GetChanges** k **UpdateCustomers** vzhledem k tomu potřebovat pouze změněné řádky se mají předat  **UpdateCustomers**. **UpdateCustomers** vrátí vyřešený **datovou sadu**, které pak můžete **sloučit** do existujících **datovou sadu** začlenit vyřešené změny a všechny informace o chybě řádek z aktualizace. Následující kód předpokládá, že používáte Visual Studio vytvořit webový odkaz a přejmenovali webový odkaz na DsSample v **přidat webový odkaz** dialogové okno.  
  
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
  
     Pokud se rozhodnete vytvořit třídu proxy, sami, je nutné provést následující dodatečné kroky. Pro kompilaci vzorku, zadejte proxy server knihovny, který byl vytvořen (sample.dll) a související knihoven .NET. Kompilace jazyka Visual Basic .NET verze ukázky, které jsou uložené v souboru client.vb, vydejte následující příkaz.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Chcete-li zkompilovat verzi C#, ukázky, které jsou uložené v souboru client.cs, vydejte následující příkaz.  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>Viz také:
- [ADO.NET](../../../../../docs/framework/data/adonet/index.md)
- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [Naplnění datové sady z adaptéru dat](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [Aktualizace zdrojů dat pomocí adaptérů dat](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [Parametry adaptéru dat](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)
- [Web Services Description Language Tool (Wsdl.exe)](https://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
