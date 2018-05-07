---
title: Detekce změn s SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: a25afbe0124f7870df886a1e26e0df2a0716b205
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="detecting-changes-with-sqldependency"></a>Detekce změn s SqlDependency
A <xref:System.Data.SqlClient.SqlDependency> objekt může být přidružený <xref:System.Data.SqlClient.SqlCommand> aby bylo možné rozpoznat, kdy se výsledky dotazu lišit od těch původně načten. Je také možné přiřadit delegáta, kterého `OnChange` událost, která bude platit při změně výsledků pro přidružený příkaz. Je nutné přidružit <xref:System.Data.SqlClient.SqlDependency> pomocí příkazu před spuštěním příkazu. `HasChanges` Vlastnost <xref:System.Data.SqlClient.SqlDependency> lze také použít k určení, pokud výsledky dotazu změnily od první načtena data.  
  
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Využívá infrastrukturu závislostí <xref:System.Data.SqlClient.SqlConnection> , když je otevřen <xref:System.Data.SqlClient.SqlDependency.Start%2A> nazývá příjem oznámení, která zdrojová data změnila pro daný příkaz vyžaduje, aby. Možnost pro klienta zahájíte volání `SqlDependency.Start` se řídí prostřednictvím <xref:System.Data.SqlClient.SqlClientPermission> a atributy zabezpečení přístupu kódu. Další informace najdete v tématu [povolení oznámení dotazů](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) a [zabezpečení přístupu kódu a ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).  
  
### <a name="example"></a>Příklad  
 Následující kroky ukazují, jak závislost deklarovat, spusťte příkaz a přijímat oznámení v případě výsledek nastavit změny:  
  
1.  Zahájení `SqlDependency` připojení k serveru.  
  
2.  Vytvoření <xref:System.Data.SqlClient.SqlConnection> a <xref:System.Data.SqlClient.SqlCommand> objekty, které chcete připojit k serveru a zadejte příkaz jazyka Transact-SQL.  
  
3.  Vytvořte novou `SqlDependency` objektu, nebo použijte existující a navázat jej na `SqlCommand` objektu. Interně, tím se vytvoří <xref:System.Data.Sql.SqlNotificationRequest> objektu a váže k objektu command podle potřeby. Tato žádost o oznámení obsahuje interní identifikátor, který jednoznačně identifikuje tento `SqlDependency` objektu. Také spustí naslouchací proces klienta, pokud již není aktivní.  
  
4.  Obslužné rutiny události pro přihlášení k odběru `OnChange` události `SqlDependency` objektu.  
  
5.  Provedení příkazu pomocí kteréhokoli `Execute` metody `SqlCommand` objektu. Vzhledem k tomu, že příkaz je vázaná na objekt oznámení, server rozpozná, že ji musíte vygenerovat oznámení, a informace o frontě bude odkazovat na frontu závislosti.  
  
6.  Zastavit `SqlDependency` připojení k serveru.  
  
 Pokud se každý uživatel, následně změní v základních datech, Microsoft SQL Server zjistí, že je oznámení čekající na vyřízení pro tuto změnu a odešle oznámení, že je zpracován a předávaných do klienta prostřednictvím základní `SqlConnection` který byl vytvořen Při volání `SqlDependency.Start`. Naslouchací proces klienta obdrží zprávu zneplatnění. Naslouchací proces klienta poté vyhledá přidruženého `SqlDependency` objekt a aktivuje se `OnChange` událostí.  
  
 Následující fragment kódu ukazuje vzor návrhu, které byste použili k vytvoření ukázkové aplikace.  
  
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
        // Maintain the refence in a class member.  
  
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
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
