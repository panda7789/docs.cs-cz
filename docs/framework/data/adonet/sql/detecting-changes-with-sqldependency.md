---
title: Detekce změn pomocí SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: 3719188064388b00c756dd037d4a475ca6debd13
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782418"
---
# <a name="detecting-changes-with-sqldependency"></a><span data-ttu-id="18dbe-102">Detekce změn pomocí SqlDependency</span><span class="sxs-lookup"><span data-stu-id="18dbe-102">Detecting Changes with SqlDependency</span></span>

<span data-ttu-id="18dbe-103">Objekt může být přidružen <xref:System.Data.SqlClient.SqlCommand> k objektu, aby zjistil, že se výsledky dotazu liší od původně načtených. <xref:System.Data.SqlClient.SqlDependency></span><span class="sxs-lookup"><span data-stu-id="18dbe-103">A <xref:System.Data.SqlClient.SqlDependency> object can be associated with a <xref:System.Data.SqlClient.SqlCommand> in order to detect when query results differ from those originally retrieved.</span></span> <span data-ttu-id="18dbe-104">Můžete také přiřadit delegáta `OnChange` události, která se aktivuje při změně výsledků pro přidružený příkaz.</span><span class="sxs-lookup"><span data-stu-id="18dbe-104">You can also assign a delegate to the `OnChange` event, which will fire when the results change for an associated command.</span></span> <span data-ttu-id="18dbe-105">Před provedením příkazu <xref:System.Data.SqlClient.SqlDependency> je nutné připojit k příkazu příkaz.</span><span class="sxs-lookup"><span data-stu-id="18dbe-105">You must associate the <xref:System.Data.SqlClient.SqlDependency> with the command before you execute the command.</span></span> <span data-ttu-id="18dbe-106">`HasChanges` Vlastnost<xref:System.Data.SqlClient.SqlDependency> lze také použít k určení, zda se od prvního načtení dat změnily výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="18dbe-106">The `HasChanges` property of the <xref:System.Data.SqlClient.SqlDependency> can also be used to determine if the query results have changed since the data was first retrieved.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="18dbe-107">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="18dbe-107">Security Considerations</span></span>

<span data-ttu-id="18dbe-108">Infrastruktura závislostí závisí na typu <xref:System.Data.SqlClient.SqlConnection> , který je otevřen <xref:System.Data.SqlClient.SqlDependency.Start%2A> , když je volána, aby přijímal oznámení, že se pro daný příkaz změnila podkladová data.</span><span class="sxs-lookup"><span data-stu-id="18dbe-108">The dependency infrastructure relies on a <xref:System.Data.SqlClient.SqlConnection> that is opened when <xref:System.Data.SqlClient.SqlDependency.Start%2A> is called in order to receive notifications that the underlying data has changed for a given command.</span></span> <span data-ttu-id="18dbe-109">Schopnost klienta iniciovat volání `SqlDependency.Start` je řízena <xref:System.Data.SqlClient.SqlClientPermission> pomocí atributů zabezpečení přístupu kódu.</span><span class="sxs-lookup"><span data-stu-id="18dbe-109">The ability for a client to initiate the call to `SqlDependency.Start` is controlled through the use of <xref:System.Data.SqlClient.SqlClientPermission> and code access security attributes.</span></span> <span data-ttu-id="18dbe-110">Další informace najdete v tématu [Povolení oznámení dotazů](enabling-query-notifications.md) a [zabezpečení přístupu kódu a ADO.NET](../code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="18dbe-110">For more information, see [Enabling Query Notifications](enabling-query-notifications.md) and [Code Access Security and ADO.NET](../code-access-security.md).</span></span>

### <a name="example"></a><span data-ttu-id="18dbe-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="18dbe-111">Example</span></span>

<span data-ttu-id="18dbe-112">Následující postup ukazuje, jak deklarovat závislost, spustit příkaz a obdržet oznámení při změně sady výsledků dotazu:</span><span class="sxs-lookup"><span data-stu-id="18dbe-112">The following steps illustrate how to declare a dependency, execute a command, and receive a notification when the result set changes:</span></span>

1. <span data-ttu-id="18dbe-113">Navázat `SqlDependency` připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="18dbe-113">Initiate a `SqlDependency` connection to the server.</span></span>

2. <span data-ttu-id="18dbe-114">Vytvořte <xref:System.Data.SqlClient.SqlConnection>objektypropřipojení kserveruadefinujtepříkazTransact-SQL.<xref:System.Data.SqlClient.SqlCommand></span><span class="sxs-lookup"><span data-stu-id="18dbe-114">Create <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to connect to the server and define a Transact-SQL statement.</span></span>

3. <span data-ttu-id="18dbe-115">Vytvořte nový `SqlDependency` objekt nebo použijte existující objekt a navažte jej `SqlCommand` na objekt.</span><span class="sxs-lookup"><span data-stu-id="18dbe-115">Create a new `SqlDependency` object, or use an existing one, and bind it to the `SqlCommand` object.</span></span> <span data-ttu-id="18dbe-116">Interně to vytvoří <xref:System.Data.Sql.SqlNotificationRequest> objekt a váže ho k objektu Command podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="18dbe-116">Internally, this creates a <xref:System.Data.Sql.SqlNotificationRequest> object and binds it to the command object as needed.</span></span> <span data-ttu-id="18dbe-117">Tato žádost o oznámení obsahuje interní identifikátor, který tento `SqlDependency` objekt jednoznačně identifikuje.</span><span class="sxs-lookup"><span data-stu-id="18dbe-117">This notification request contains an internal identifier that uniquely identifies this `SqlDependency` object.</span></span> <span data-ttu-id="18dbe-118">Také spustí naslouchací proces klienta, pokud ještě není aktivní.</span><span class="sxs-lookup"><span data-stu-id="18dbe-118">It also starts the client listener if it is not already active.</span></span>

4. <span data-ttu-id="18dbe-119">Přihlaste se k odběru `OnChange` obslužné rutiny `SqlDependency` události pro událost objektu.</span><span class="sxs-lookup"><span data-stu-id="18dbe-119">Subscribe an event handler to the `OnChange` event of the `SqlDependency` object.</span></span>

5. <span data-ttu-id="18dbe-120">Spusťte příkaz pomocí kterékoli z `Execute` metod `SqlCommand` objektu.</span><span class="sxs-lookup"><span data-stu-id="18dbe-120">Execute the command using any of the `Execute` methods of the `SqlCommand` object.</span></span> <span data-ttu-id="18dbe-121">Vzhledem k tomu, že příkaz je svázán s objektem oznámení, server rozpozná, že musí vygenerovat oznámení, a informace o frontě budou ukazovat na frontu závislostí.</span><span class="sxs-lookup"><span data-stu-id="18dbe-121">Because the command is bound to the notification object, the server recognizes that it must generate a notification, and the queue information will point to the dependencies queue.</span></span>

6. <span data-ttu-id="18dbe-122">Zastavte `SqlDependency` připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="18dbe-122">Stop the `SqlDependency` connection to the server.</span></span>

<span data-ttu-id="18dbe-123">Pokud některý uživatel následně změní podkladová data, Microsoft SQL Server zjistí, že pro takovou změnu čeká na oznámení, a odešle oznámení, které se zpracuje a přepošle klientovi prostřednictvím vytvořeného podkladu `SqlConnection` . voláním `SqlDependency.Start`.</span><span class="sxs-lookup"><span data-stu-id="18dbe-123">If any user subsequently changes the underlying data, Microsoft SQL Server detects that there is a notification pending for such a change, and posts a notification that is processed and forwarded to the client through the underlying `SqlConnection` that was created by calling `SqlDependency.Start`.</span></span> <span data-ttu-id="18dbe-124">Naslouchací proces klienta obdrží zprávu o neplatnosti.</span><span class="sxs-lookup"><span data-stu-id="18dbe-124">The client listener receives the invalidation message.</span></span> <span data-ttu-id="18dbe-125">Naslouchací proces klienta potom vyhledá přidružený `SqlDependency` objekt a `OnChange` aktivuje událost.</span><span class="sxs-lookup"><span data-stu-id="18dbe-125">The client listener then locates the associated `SqlDependency` object and fires the `OnChange` event.</span></span>

<span data-ttu-id="18dbe-126">Následující fragment kódu ukazuje vzor návrhu, který byste použili k vytvoření ukázkové aplikace.</span><span class="sxs-lookup"><span data-stu-id="18dbe-126">The following code fragment shows the design pattern you would use to create a sample application.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="18dbe-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18dbe-127">See also</span></span>

- [<span data-ttu-id="18dbe-128">Oznámení pro dotazy na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="18dbe-128">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="18dbe-129">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="18dbe-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
