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
# <a name="consume-a-dataset-from-an-xml-web-service"></a>Využití datové sady z webové služby XML

<xref:System.Data.DataSet>Bylo navrženo s odpojeným návrhem, v rámci kterého se usnadnil pohodlný přenos dat přes Internet. **Datová sada** je "serializovatelný" v tom, že ji lze zadat jako vstup nebo výstup z webových služeb XML bez jakéhokoli dalšího kódování požadovaného pro streamování obsahu **datové sady** z webové služby XML do klienta a zpět. **Datová sada** je implicitně převedena na datový proud XML pomocí formátu DiffGram, který je odeslán přes síť a následně znovu sestaven z datového proudu XML jako **datová sada** na přijímacím konci. Získáte tak jednoduchou a flexibilní metodu pro přenášení a vracení relačních dat pomocí webových služeb XML. Další informace o formátu formátu DiffGram naleznete v tématu [DiffGram](diffgrams.md).  
  
 Následující příklad ukazuje, jak vytvořit webovou službu XML a klienta, které používají **datovou sadu** pro přenos relačních dat (včetně upravených dat) a řešení všech aktualizací zpátky do původního zdroje dat.  
  
> [!NOTE]
> Přenosy `DataSet` nebo `DataTable` instance v rámci volání webové služby XML nejsou bezpečné, pokud vstup není důvěryhodný. Další informace najdete v tématu [doprovodné materiály k zabezpečení datových sad a DataTable](/dotnet/framework/data/adonet/dataset-datatable-dataview/security-guidance).
> Doporučujeme vám také při vytváření webové služby XML vždy vzít v úvahu důsledky zabezpečení. Informace o zabezpečení webové služby XML najdete v tématu [zabezpečení webových služeb XML vytvořených pomocí ASP.NET](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).  
  
## <a name="create-an-xml-web-service"></a>Vytvoření webové služby XML
  
1. Vytvořte webovou službu XML.  
  
     V tomto příkladu je vytvořena webová služba XML, která vrací data, v tomto případě seznam zákazníků z databáze **Northwind** a obdrží **datovou sadu** s aktualizacemi dat, které webová služba XML překládá zpět na původní zdroj dat.  
  
     Webová služba XML zpřístupňuje dvě metody: **GetCustomers**, vrátí seznam zákazníků a **UpdateCustomers**, aby vyřešila aktualizace zpět do zdroje dat. Webová služba XML je uložena v souboru na webovém serveru s názvem DataSetSample. asmx. Následující kód popisuje obsah DataSetSample. asmx.  
  
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
  
     V typickém scénáři by byla metoda **UpdateCustomers** zapsána k zachycení optimistického narušení souběžnosti. Pro zjednodušení tento příklad nezahrnuje. Další informace o optimistické souběžnosti naleznete v tématu [Optimistická souběžnost](../optimistic-concurrency.md).  
  
2. Vytvoří proxy webové služby XML.  
  
     Klienti webové služby XML vyžadují proxy protokolu SOAP, aby mohli využívat vystavené metody. Aplikaci Visual Studio můžete vygenerovat tento proxy server za vás. Když nastavíte webový odkaz na existující webovou službu z aplikace Visual Studio, veškeré chování popsané v tomto kroku bude transparentní. Chcete-li vytvořit třídu proxy sami, pokračujte v této diskuzi. Ve většině případů ale použití sady Visual Studio k vytvoření proxy třídy pro klientskou aplikaci postačuje.  
  
     Proxy server je možné vytvořit pomocí nástroje Web Services Description Language Tool. Pokud je například webová služba XML vystavena na adrese URL `http://myserver/data/DataSetSample.asmx` , vydejte příkaz jako následující k vytvoření proxy serveru Visual Basic .NET s oborem názvů **WebData. DSSample** a uložte ho do souboru Sample. vb.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     Pokud chcete v souboru sample.cs vytvořit proxy C#, vydejte následující příkaz.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     Proxy je pak možné zkompilovat jako knihovnu a importovat do klienta webové služby XML. Chcete-li zkompilovat kód proxy serveru Visual Basic .NET uložený v souboru Sample. vb jako sample.dll, vydejte následující příkaz.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     Chcete-li zkompilovat kód proxy jazyka C# uložený v sample.cs jako sample.dll, vydejte následující příkaz.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. Vytvoří klienta webové služby XML.  
  
     Pokud chcete, aby aplikace Visual Studio vygenerovala pro vás třídu proxy webové služby, stačí vytvořit klientský projekt a v okně Průzkumník řešení klikněte pravým tlačítkem myši na projekt a pak vyberte **Přidat**  >  **odkaz na službu**. V dialogovém okně **Přidat odkaz na službu** vyberte **Upřesnit**a pak vyberte **Přidat webový odkaz**. Vyberte webovou službu ze seznamu dostupných webových služeb (to může vyžadovat, aby se zadala adresa koncového bodu webové služby, pokud webová služba není v aktuálním řešení nebo v aktuálním počítači k dispozici). Pokud vytvoříte proxy webové služby XML sami (jak je popsáno v předchozím kroku), můžete ho importovat do kódu klienta a využívat metody webové služby XML.

     Následující vzorový kód importuje knihovnu proxy, volá **GetCustomers** , aby získal seznam zákazníků, přidal nového zákazníka a potom vrátí **datovou sadu** s aktualizacemi **UpdateCustomers**.  
  
     Tento příklad předá **datovou sadu** vrácenou sadou **DataSet. GetChanges** to **UpdateCustomers** , protože do **UpdateCustomers**je nutné předat pouze upravené řádky. **UpdateCustomers** vrátí přeloženou **datovou sadu**, kterou můžete **Sloučit** do existující **datové sady** , aby zahrnovala vyřešené změny a všechny informace o chybách řádků z aktualizace. Následující kód předpokládá, že jste použili aplikaci Visual Studio k vytvoření webového odkazu a že jste přejmenovali webový odkaz na DsSample v dialogovém okně **Přidat webový odkaz** .  
  
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
  
     Pokud se rozhodnete vytvořit třídu proxy sami, musíte provést následující kroky navíc. Pokud chcete ukázku zkompilovat, poskytněte proxy knihovnu, která byla vytvořena (sample.dll) a související knihovny .NET. Chcete-li zkompilovat ukázkovou verzi rozhraní Visual Basic .NET, která je uložena v souboru Client. vb, vydejte následující příkaz.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Pro zkompilování ukázky verze C#, která je uložena v souboru client.cs, vydejte následující příkaz.  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>Viz také

- [ADO.NET](../index.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Datové tabulky](datatables.md)
- [Naplnění datové sady z adaptéru dat](../populating-a-dataset-from-a-dataadapter.md)
- [Aktualizace zdrojů dat pomocí adaptérů dat](../updating-data-sources-with-dataadapters.md)
- [Parametry adaptéru dat](../dataadapter-parameters.md)
- [Nástroj Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [Přehled ADO.NET](../ado-net-overview.md)
