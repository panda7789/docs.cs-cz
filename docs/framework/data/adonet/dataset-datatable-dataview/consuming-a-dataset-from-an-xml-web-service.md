---
title: Využívání datové sady z webové služby XML
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 9bfcd4d8dca38c9438c072c143cf7ba0eafd6ecf
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>Využívání datové sady z webové služby XML
<xref:System.Data.DataSet> Byl navržen odpojené návrh, v části pro usnadnění pohodlný přenos dat přes Internet. **Datovou sadu** je "serializovatelný", můžete zadat jako vstup nebo výstup webové služby XML bez další kódování požadované Streamovat obsah **datovou sadu** z webové služby XML na klienta a naopak. **Datovou sadu** se implicitně převést na datový proud XML formátu formát DiffGram, odesílají přes síť a potom znovu vytvořena z datového proudu XML jako **datovou sadu** na koncové straně příjmu. To vám dává velmi jednoduchá a flexibilní metodu pro přenášení a vrácení relačních dat pomocí webové služby XML. Další informace o formátu, formátu DiffGram najdete v tématu [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).  
  
 Následující příklad ukazuje postup vytvoření webové služby XML a klienta, který používat **datovou sadu** přenosu relační data (včetně upravených dat) a vyřešte všechny aktualizace zpět do původního zdroje data.  
  
> [!NOTE]
>  Doporučujeme, abyste při vytváření webové služby XML vždy zvažte vliv na zabezpečení. Informace o zabezpečení webové služby XML, najdete v části [zabezpečení XML webové služby vytvořené pomocí ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>Chcete-li vytvořit XML webové služby, který vrátí a odebírá datové sady  
  
1.  Vytvoření webové služby XML.  
  
     V příkladu se vytvoří webové služby XML vracející data, v tomto případě seznam zákazníků z **Northwind** databáze a přijímá **datovou sadu** s aktualizace dat, které webové služby XML Přeloží zpět do původního zdroje data.  
  
     Webové služby XML zpřístupní dvě metody: **GetCustomers**vrátit se do seznamu zákazníků, a **UpdateCustomers**, chcete-li vyřešit aktualizací zpět do zdroje dat. Webové služby XML je uložený v souboru na webový server s názvem DataSetSample.asmx. Následující kód popisuje obsah DataSetSample.asmx.  
  
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
  
     V typických možností **UpdateCustomers** metoda by byla zapsána k zachycení optimistickou metodu souběžného porušení. Pro jednoduchost příklad nezahrnuje to. Další informace o optimistickou metodu souběžného zpracování najdete v tématu [optimistickou metodu souběžného](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).  
  
2.  Vytvořte proxy XML webové služby.  
  
     Klienti XML webové služby vyžadují proxy server protokolu SOAP, aby bylo možné využívat zveřejněné metody. Můžete mít Visual Studio generovat tento proxy server za vás. Nastavením odkaz na existující webovou službu z Visual Studia dojde transparentně všechny chování popsané v tomto kroku. Pokud chcete vytvořit třídu proxy sami, pokračujte toto pojednání. Ve většině situací ale pomocí sady Visual Studio vytvořit třídu proxy pro klientskou aplikaci je dostatečná.  
  
     Proxy server můžete vytvořit pomocí Web Services Description Language Tool. Například pokud webové služby XML je vystavený v http://myserver/data/DataSetSample.asmx adresu URL, příkaz ke například následující vytvořit proxy Visual Basic .NET k oboru názvů z **WebData.DSSample** a ukládá je v souboru Sample.vb.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     V souboru sample.cs vytvořit proxy C#, vydejte následující příkaz.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     Proxy server můžete pak zkompilovat jako knihovnu a importovat klient XML webové služby. Zkompilovat kód jazyka Visual Basic .NET proxy uložené v sample.vb jako sample.dll, vydejte následující příkaz.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     Pro kompilaci proxy kódu C# uložené v sample.cs jako sample.dll, vydejte následující příkaz.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3.  Vytvoření klienta XML webové služby.  
  
     Pokud chcete mít k vygenerovat třídu proxy webové služby sady Visual Studio, jednoduše vytvořit projekt klienta a, v okně Průzkumníku řešení klikněte pravým tlačítkem na projekt, klikněte na **přidat odkaz na Web**a vyberte webovou službu z seznam dostupných webových služeb (může to vyžadovat poskytnutí adresu koncový bod webové služby, pokud webová služba není k dispozici v aktuálním řešení, nebo v počítači.) Pokud služby proxy webových XML sami (jak je popsáno v předchozím kroku) vytvoříte, můžete ho importovat do kódu klienta a využívat metody XML webové služby. Následující vzorový kód importuje knihovnu proxy serveru, volání **GetCustomers** k získání seznamu zákazníků, přidá nového zákazníka a poté vrátí **datovou sadu** s aktualizace **UpdateCustomers** .  
  
     Všimněte si, že v příkladu předá **datovou sadu** vrácený **DataSet.GetChanges** k **UpdateCustomers** protože pouze změněné řádky potřebovat mají být předány  **UpdateCustomers**. **UpdateCustomers** vrátí vyřešený **datovou sadu**, která pak můžete **sloučení** do existujících **datovou sadu** začlenit přeložit změny a všechny informace o chybě řádek z aktualizace. Následující kód předpokládá, zda používáte Visual Studio vytvořit odkaz na Web a že přejmenovali webového odkazu na DsSample v **přidat odkaz na Web** dialogové okno.  
  
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
  
     Pokud se rozhodnete vytvořit třídu proxy sami, musíte provést následující další kroky. Zkompilovat ukázkový, zadejte knihovnu proxy serveru, který byl vytvořen (sample.dll) a související knihovny .NET. Kompilace jazyka Visual Basic .NET verzi příkladu, uložené v souboru client.vb, vydejte následující příkaz.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Kompilace verze jazyka C# ukázce uložené v souboru client.cs, vydejte následující příkaz.  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [Naplnění datové sady z adaptéru dat](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [Aktualizace zdrojů dat pomocí adaptérů dat](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Parametry adaptéru dat](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [Web Services Description Language Tool (Wsdl.exe)](https://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
