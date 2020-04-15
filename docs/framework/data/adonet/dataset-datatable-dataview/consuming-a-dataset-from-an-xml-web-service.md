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
# <a name="consume-a-dataset-from-an-xml-web-service"></a>Využití datové sady z webové služby XML

Byl <xref:System.Data.DataSet> navržen s odpojeným designem, částečně pro usnadnění pohodlného přenosu dat přes internet. **DataSet** je "serializovatelný" v tom, že může být zadán jako vstup nebo výstup z webových služeb XML bez dalšího kódování potřebného k vysílání datového souboru **z** webové služby XML do klienta a zpět. **DataSet** je implicitně převedena na datový proud XML pomocí formátu DiffGram, odeslána po síti a pak rekonstruována z datového proudu XML jako **dataset** na přijímacím konci. To vám dává velmi jednoduchou a flexibilní metodu pro přenos a vrácení relačních dat pomocí webových služeb XML. Další informace o formátu DiffGram naleznete v [tématu DiffGrams](diffgrams.md).  
  
 Následující příklad ukazuje, jak vytvořit webovou službu XML a klienta, kteří používají **DataSet** k přenosu relačních dat (včetně změněných dat) a vyřešit všechny aktualizace zpět do původního zdroje dat.  
  
> [!NOTE]
> Při vytváření webové služby XML doporučujeme vždy zvážit důsledky zabezpečení. Informace o zabezpečení webové služby XML naleznete v [tématu Zabezpečení webových služeb XML vytvořených pomocí ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).  
  
## <a name="create-an-xml-web-service"></a>Vytvoření webové služby XML
  
1. Vytvořte webovou službu XML.  
  
     V příkladu je vytvořena webová služba XML, která vrací data, v tomto případě seznam zákazníků z databáze **Northwind,** a přijímá **datovou sadu** s aktualizacemi dat, které webová služba XML překládá zpět na původní zdroj dat.  
  
     Webová služba XML zpřístupňuje dvě metody: **GetCustomers**, vrátit seznam zákazníků a **UpdateCustomers**, chcete-li přeložit aktualizace zpět do zdroje dat. Webová služba XML je uložena v souboru na webovém serveru s názvem DataSetSample.asmx. Následující kód popisuje obsah DataSetSample.asmx.  
  
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
  
     V typickém scénáři **UpdateCustomers** metoda by být zapsána zachytit optimistické porušení souběžnosti. Pro jednoduchost příklad neobsahuje toto. Další informace o optimistické souběžnosti naleznete [v tématu Optimistic Koncurrency](../optimistic-concurrency.md).  
  
2. Vytvořte proxy server webové služby XML.  
  
     Klienti webové služby XML vyžadují proxy server SOAP, aby mohli využívat exponované metody. Můžete mít Visual Studio generovat tento proxy pro vás. Nastavením webového odkazu na existující webovou službu z aplikace Visual Studio dojde k transparentnímu chování popsanému v tomto kroku. Pokud chcete vytvořit proxy třídy sami, pokračujte v této diskusi. Ve většině případů však použití sady Visual Studio k vytvoření třídy proxy pro klientskou aplikaci je dostačující.  
  
     Proxy server lze vytvořit pomocí nástroje Pro jazyk popisu webových služeb. Pokud je například webová služba XML `http://myserver/data/DataSetSample.asmx`vystavena na adrese URL , vyjezte příkaz, například následující, abyste vytvořili proxy serveru .NET jazyka Visual Basic s oborem názvů **webData.DSSample** a uložili jej do souboru sample.vb.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     Chcete-li v souboru vytvořit proxy server C#, sample.cs, vyjezte následující příkaz.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     Proxy server pak může být kompilován jako knihovna a importován do klienta webové služby XML. Chcete-li zkompilovat proxy kód jazyka Visual Basic .NET uložený v souboru sample.vb jako soubor sample.dll, vyjezte následující příkaz.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     Chcete-li zkompilovat proxy kód jazyka C# uložený v sample.cs jako sample.dll, vyjemte následující příkaz.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. Vytvořte klienta webové služby XML.  
  
     Pokud chcete, aby visual studio generovat proxy webové služby třídy pro vás, jednoduše vytvořit projekt klienta a v okně Průzkumník řešení, klepněte pravým tlačítkem myši na projekt a potom vyberte **přidat** > **odkaz na službu**. V dialogovém okně **Přidat odkaz na službu** vyberte **Upřesnit**a pak vyberte **Přidat webový odkaz**. Vyberte webovou službu ze seznamu dostupných webových služeb (to může vyžadovat zadání adresy koncového bodu webové služby, pokud webová služba není k dispozici v aktuálním řešení nebo v aktuálním počítači). Pokud vytvoříte proxy služby XML sami (jak je popsáno v předchozím kroku), můžete jej importovat do klientského kódu a využívat metody webové služby XML.

     Následující ukázkový kód importuje knihovnu proxy, volá **GetCustomers** získat seznam zákazníků, přidá nového zákazníka a vrátí **DataSet** s aktualizacemi **UpdateCustomers**.  
  
     Příklad předá **DataSet** vrácené **DataSet.GetChanges** **updateCustomers** protože pouze upravené řádky musí být **předány UpdateCustomers**. **UpdateCustomers** vrátí vyřešenou **datovou sadu**, kterou pak můžete **sloučit** do existující **sady DataSet** a začlenit vyřešené změny a všechny informace o chybě řádku z aktualizace. Následující kód předpokládá, že jste použili Visual Studio k vytvoření webového odkazu a že jste přejmenovali webový odkaz na DsSample v dialogovém okně **Přidat webový odkaz.**  
  
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
  
     Pokud se rozhodnete vytvořit třídu proxy sami, musíte provést následující další kroky. Chcete-li zkompilovat ukázku, zařazujte knihovnu proxy, která byla vytvořena (sample.dll) a související knihovny .NET. Chcete-li zkompilovat verzi ukázky .NET jazyka Visual Basic uloženou v souboru client.vb, vyjekujte následujícím příkazem.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Chcete-li zkompilovat verzi ukázky jazyka C#, která je uložena v souboru client.cs, vystavte následující příkaz.  
  
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
- [Nástroj pro jazyk popisu webových služeb (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [Přehled ADO.NET](../ado-net-overview.md)
