---
title: Provádění SqlCommand pomocí SqlNotificationRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 3115bfb80d4e5e61ed49da11e36eaa37bc24334f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791530"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Provádění SqlCommand pomocí SqlNotificationRequest

<xref:System.Data.SqlClient.SqlCommand> Dá se nakonfigurovat tak, aby vygeneroval oznámení, když se změní data po načtení ze serveru, a sada výsledků by byla odlišná, pokud se dotaz znovu spustil. To je užitečné ve scénářích, kdy chcete používat vlastní fronty oznámení na serveru nebo když nechcete zachovat živé objekty.

## <a name="creating-the-notification-request"></a>Vytváření žádosti o oznámení

Pomocí <xref:System.Data.Sql.SqlNotificationRequest> objektu můžete vytvořit žádost o oznámení tak, že ji vytvoříte vazbou `SqlCommand` na objekt. Po vytvoření žádosti už `SqlNotificationRequest` objekt nebudete potřebovat. Můžete zadat dotaz na frontu pro všechna oznámení a odpovídajícím způsobem reagovat. K oznámením může dojít i v případě, že se aplikace vypíná a následně restartuje.

Když se spustí příkaz s přidruženým oznámením, všechny změny v původní aktivační události sady výsledků odesílají zprávu do fronty SQL Server, která byla nakonfigurovaná v žádosti o oznámení.

Způsob dotazování fronty SQL Server a interpretace zprávy jsou specifické pro vaši aplikaci. Aplikace zodpovídá za cyklické dotazování fronty a na základě obsahu zprávy.

> [!NOTE]
> Pokud používáte požadavky na oznamování <xref:System.Data.SqlClient.SqlDependency>SQL Server s, vytvořte vlastní název fronty namísto použití výchozího názvu služby.

Neexistují žádné nové prvky zabezpečení na straně klienta pro <xref:System.Data.Sql.SqlNotificationRequest>. Tato funkce je primárně součástí serveru a Server vytvořil zvláštní oprávnění, která musí uživatelé vyžadovat pro vyžádání oznámení.

### <a name="example"></a>Příklad

Následující fragment kódu ukazuje, jak vytvořit <xref:System.Data.Sql.SqlNotificationRequest> a přidružit ho <xref:System.Data.SqlClient.SqlCommand>k.

```vb
' Assume connection is an open SqlConnection.
' Create a new SqlCommand object.
Dim command As New SqlCommand( _
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)

' Create a SqlNotificationRequest object.
Dim notifcationRequest As New SqlNotificationRequest()
notificationRequest.id = "NotificationID"
notificationRequest.Service = "mySSBQueue"

' Associate the notification request with the command.
command.Notification = notificationRequest
' Execute the command.
command.ExecuteReader()
' Process the DataReader.
' You can use Transact-SQL syntax to periodically poll the
' SQL Server queue to see if you have a new message.
```

```csharp
// Assume connection is an open SqlConnection.
// Create a new SqlCommand object.
SqlCommand command=new SqlCommand(
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);

// Create a SqlNotificationRequest object.
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="see-also"></a>Viz také:

- [Oznámení pro dotazy na SQL Serveru](query-notifications-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
