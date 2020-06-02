---
title: Detekce změn pomocí SqlDependency
description: K detekci, kdy se výsledky dotazu liší od těch, které byly původně načteny v ADO.NET, přidružte objekt SqlDependency k objektu SqlCommand.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: b196d42477e1778c45df64b1390502645fdd649d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286465"
---
# <a name="detecting-changes-with-sqldependency"></a>Detekce změn pomocí SqlDependency

<xref:System.Data.SqlClient.SqlDependency>Objekt může být přidružen k objektu, <xref:System.Data.SqlClient.SqlCommand> aby zjistil, že se výsledky dotazu liší od původně načtených. Můžete také přiřadit delegáta `OnChange` události, která se aktivuje při změně výsledků pro přidružený příkaz. <xref:System.Data.SqlClient.SqlDependency>Před provedením příkazu je nutné připojit k příkazu příkaz. `HasChanges`Vlastnost <xref:System.Data.SqlClient.SqlDependency> lze také použít k určení, zda se od prvního načtení dat změnily výsledky dotazu.

## <a name="security-considerations"></a>Aspekty zabezpečení

Infrastruktura závislostí závisí na typu <xref:System.Data.SqlClient.SqlConnection> , který je otevřen, když <xref:System.Data.SqlClient.SqlDependency.Start%2A> je volána, aby přijímal oznámení, že se pro daný příkaz změnila podkladová data. Schopnost klienta iniciovat volání `SqlDependency.Start` je řízena pomocí <xref:System.Data.SqlClient.SqlClientPermission> atributů zabezpečení přístupu kódu. Další informace najdete v tématu [Povolení oznámení dotazů](enabling-query-notifications.md) a [zabezpečení přístupu kódu a ADO.NET](../code-access-security.md).

### <a name="example"></a>Příklad

Následující postup ukazuje, jak deklarovat závislost, spustit příkaz a obdržet oznámení při změně sady výsledků dotazu:

1. Navázat `SqlDependency` připojení k serveru.

2. Vytvořte <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.SqlClient.SqlCommand> objekty pro připojení k serveru a definujte příkaz Transact-SQL.

3. Vytvořte nový `SqlDependency` objekt nebo použijte existující objekt a navažte jej na `SqlCommand` objekt. Interně to vytvoří <xref:System.Data.Sql.SqlNotificationRequest> objekt a váže ho k objektu Command podle potřeby. Tato žádost o oznámení obsahuje interní identifikátor, který tento objekt jednoznačně identifikuje `SqlDependency` . Také spustí naslouchací proces klienta, pokud ještě není aktivní.

4. Přihlaste se k odběru obslužné rutiny události pro `OnChange` událost `SqlDependency` objektu.

5. Spusťte příkaz pomocí kterékoli z `Execute` metod `SqlCommand` objektu. Vzhledem k tomu, že příkaz je svázán s objektem oznámení, server rozpozná, že musí vygenerovat oznámení, a informace o frontě budou ukazovat na frontu závislostí.

6. Zastavte `SqlDependency` připojení k serveru.

Pokud některý uživatel následně změní podkladová data, Microsoft SQL Server zjistí, že pro takovou změnu čeká na oznámení, a odešle oznámení, které se zpracovává a přesměruje klientovi prostřednictvím podkladu `SqlConnection` vytvořeného voláním `SqlDependency.Start` . Naslouchací proces klienta obdrží zprávu o neplatnosti. Naslouchací proces klienta potom vyhledá přidružený `SqlDependency` objekt a aktivuje `OnChange` událost.

Následující fragment kódu ukazuje vzor návrhu, který byste použili k vytvoření ukázkové aplikace.

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
        ' Maintain the refernce in a class member.
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

- [Oznámení pro dotazy na SQL Serveru](query-notifications-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
