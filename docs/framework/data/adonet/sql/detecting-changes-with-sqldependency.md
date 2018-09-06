---
title: Detekce změn pomocí SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: 63d6a17e5aaf3e5d39ed0eda288e75c071be4d73
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871147"
---
# <a name="detecting-changes-with-sqldependency"></a>Detekce změn pomocí SqlDependency
A <xref:System.Data.SqlClient.SqlDependency> objektu lze přidružit <xref:System.Data.SqlClient.SqlCommand> aby bylo možné rozpoznat, kdy se výsledky dotazu se liší od těch, které původně načten. Můžete také přiřadit delegáta, kterého `OnChange` událost, která se aktivuje při změně výsledků pro přidružený příkaz. Je třeba přidružit <xref:System.Data.SqlClient.SqlDependency> pomocí příkazu před spuštěním příkazu. `HasChanges` Vlastnost <xref:System.Data.SqlClient.SqlDependency> lze také použít k určení, pokud výsledky dotazu se změnily od nejprve se data načetla.  
  
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Závislost infrastruktury spoléhá na <xref:System.Data.SqlClient.SqlConnection> , který se otevře při <xref:System.Data.SqlClient.SqlDependency.Start%2A> je volána, pokud chcete dostávat oznámení, která pro zadaný příkaz změnila podkladová data. Možnost pro klienta k zahájení volání `SqlDependency.Start` je řízen prostřednictvím <xref:System.Data.SqlClient.SqlClientPermission> a atributy zabezpečení přístupu kódu. Další informace najdete v tématu [povolení oznámení dotazů](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) a [zabezpečení přístupu kódu a ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).  
  
### <a name="example"></a>Příklad  
 Následující kroky ukazují, jak deklarovat závislost, provedení příkazu a když výsledné sady změn, dostanete oznámení:  
  
1.  Zahájit `SqlDependency` připojení k serveru.  
  
2.  Vytvoření <xref:System.Data.SqlClient.SqlConnection> a <xref:System.Data.SqlClient.SqlCommand> objekty pro připojení k serveru a definování příkazu jazyka Transact-SQL.  
  
3.  Vytvořte nový `SqlDependency` objektu, nebo použijte již existující a vytvořte mu vazbu k `SqlCommand` objektu. Interně, tím se vytvoří <xref:System.Data.Sql.SqlNotificationRequest> objektu a vazba k objektu command, podle potřeby. Žádost o toto oznámení obsahuje interní identifikátor, který jednoznačně identifikuje to `SqlDependency` objektu. Pokud už není aktivní naslouchací proces klienta, spustí se také.  
  
4.  Obslužná rutina události pro odběru `OnChange` událost `SqlDependency` objektu.  
  
5.  Spuštění příkazu pomocí kteréhokoli z `Execute` metody `SqlCommand` objektu. Vzhledem k tomu, že příkaz je vázán na objekt oznámení, server rozpoznal, že ho musíte vygenerovat oznámení a informace o frontě budou odkazovat na frontě závislosti.  
  
6.  Zastavit `SqlDependency` připojení k serveru.  
  
 Pokud se žádný uživatel následně změní podkladová data, Microsoft SQL Server rozpozná, že se čeká na oznámení pro tuto změnu a odešle oznámení, že je zpracován a předávaných do klienta prostřednictvím základní `SqlConnection` , který byl vytvořen voláním `SqlDependency.Start`. Naslouchací proces klienta obdrží zprávu zneplatnění. Naslouchací proces klienta poté vyhledá přidruženého `SqlDependency` objekt a aktivuje se `OnChange` událostí.  
  
 Následující fragment kódu ukazuje návrhový vzor, který můžete použít k vytvoření ukázkové aplikace.  
  
```vb  
Sub Initialization()  
    ' Create a dependency connection.  
    SqlDependency.Start(connectionString, queueName)  
End Sub  
  
Sub SomeMethod()   
    ' Assume connection is an open SqlConnection.  
    ' Create a new SqlCommand object.  
    Using command As New SqlCommand( _  
      "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", _  
      connection)  
  
        ' Create a dependency and associate it with the SqlCommand.  
        Dim dependency As New SqlDependency(command)  
        ' Maintain the refence in a class member.  
        ' Subscribe to the SqlDependency event.  
        AddHandler dependency.OnChange, AddressOf OnDependencyChange  
  
        ' Execute the command.  
        Using reader = command.ExecuteReader()  
            ' Process the DataReader.  
        End Using  
    End Using  
End Sub   
  
' Handler method  
Sub OnDependencyChange(ByVal sender As Object, _  
    ByVal e As SqlNotificationEventArgs)   
    ' Handle the event (for example, invalidate this cache entry).  
End Sub  
  
Sub Termination()  
    ' Release the dependency  
    SqlDependency.Stop(connectionString, queueName)  
End Sub  
```  
  
```csharp  
void Initialization()  
{  
    // Create a dependency connection.  
    SqlDependency.Start(connectionString, queueName);  
}  
  
void SomeMethod()  
{  
    // Assume connection is an open SqlConnection.  
  
    // Create a new SqlCommand object.  
    using (SqlCommand command=new SqlCommand(  
        "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers",   
        connection))  
    {  
  
        // Create a dependency and associate it with the SqlCommand.  
        SqlDependency dependency=new SqlDependency(command);  
        // Maintain the reference in a class member.  
  
        // Subscribe to the SqlDependency event.  
        dependency.OnChange+=new  
           OnChangeEventHandler(OnDependencyChange);  
  
        // Execute the command.  
        using (SqlDataReader reader = command.ExecuteReader())  
        {  
            // Process the DataReader.  
        }  
    }  
}  
  
// Handler method  
void OnDependencyChange(object sender,   
   SqlNotificationEventArgs e )  
{  
  // Handle the event (for example, invalidate this cache entry).  
}  
  
void Termination()  
{  
    // Release the dependency.  
    SqlDependency.Stop(connectionString, queueName);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Oznámení pro dotazy na SQL Serveru](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
