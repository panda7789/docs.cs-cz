---
title: "Detekce změn s SqlDependency"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3fe5aca218da7c862be90645e6fa73bc628b2328
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="detecting-changes-with-sqldependency"></a><span data-ttu-id="f353a-102">Detekce změn s SqlDependency</span><span class="sxs-lookup"><span data-stu-id="f353a-102">Detecting Changes with SqlDependency</span></span>
<span data-ttu-id="f353a-103">A <xref:System.Data.SqlClient.SqlDependency> objekt může být přidružený <xref:System.Data.SqlClient.SqlCommand> aby bylo možné rozpoznat, kdy se výsledky dotazu lišit od těch původně načten.</span><span class="sxs-lookup"><span data-stu-id="f353a-103">A <xref:System.Data.SqlClient.SqlDependency> object can be associated with a <xref:System.Data.SqlClient.SqlCommand> in order to detect when query results differ from those originally retrieved.</span></span> <span data-ttu-id="f353a-104">Je také možné přiřadit delegáta, kterého `OnChange` událost, která bude platit při změně výsledků pro přidružený příkaz.</span><span class="sxs-lookup"><span data-stu-id="f353a-104">You can also assign a delegate to the `OnChange` event, which will fire when the results change for an associated command.</span></span> <span data-ttu-id="f353a-105">Je nutné přidružit <xref:System.Data.SqlClient.SqlDependency> pomocí příkazu před spuštěním příkazu.</span><span class="sxs-lookup"><span data-stu-id="f353a-105">You must associate the <xref:System.Data.SqlClient.SqlDependency> with the command before you execute the command.</span></span> <span data-ttu-id="f353a-106">`HasChanges` Vlastnost <xref:System.Data.SqlClient.SqlDependency> lze také použít k určení, pokud výsledky dotazu změnily od první načtena data.</span><span class="sxs-lookup"><span data-stu-id="f353a-106">The `HasChanges` property of the <xref:System.Data.SqlClient.SqlDependency> can also be used to determine if the query results have changed since the data was first retrieved.</span></span>  
  
## <a name="security-considerations"></a><span data-ttu-id="f353a-107">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f353a-107">Security Considerations</span></span>  
 <span data-ttu-id="f353a-108">Využívá infrastrukturu závislostí <xref:System.Data.SqlClient.SqlConnection> , když je otevřen <xref:System.Data.SqlClient.SqlDependency.Start%2A> nazývá příjem oznámení, která zdrojová data změnila pro daný příkaz vyžaduje, aby.</span><span class="sxs-lookup"><span data-stu-id="f353a-108">The dependency infrastructure relies on a <xref:System.Data.SqlClient.SqlConnection> that is opened when <xref:System.Data.SqlClient.SqlDependency.Start%2A> is called in order to receive notifications that the underlying data has changed for a given command.</span></span> <span data-ttu-id="f353a-109">Možnost pro klienta zahájíte volání `SqlDependency.Start` se řídí prostřednictvím <xref:System.Data.SqlClient.SqlClientPermission> a atributy zabezpečení přístupu kódu.</span><span class="sxs-lookup"><span data-stu-id="f353a-109">The ability for a client to initiate the call to `SqlDependency.Start` is controlled through the use of <xref:System.Data.SqlClient.SqlClientPermission> and code access security attributes.</span></span> <span data-ttu-id="f353a-110">Další informace najdete v tématu [povolení oznámení dotazů](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) a [zabezpečení přístupu kódu a ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="f353a-110">For more information, see [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) and [Code Access Security and ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="f353a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="f353a-111">Example</span></span>  
 <span data-ttu-id="f353a-112">Následující kroky ukazují, jak závislost deklarovat, spusťte příkaz a přijímat oznámení v případě výsledek nastavit změny:</span><span class="sxs-lookup"><span data-stu-id="f353a-112">The following steps illustrate how to declare a dependency, execute a command, and receive a notification when the result set changes:</span></span>  
  
1.  <span data-ttu-id="f353a-113">Zahájení `SqlDependency` připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="f353a-113">Initiate a `SqlDependency` connection to the server.</span></span>  
  
2.  <span data-ttu-id="f353a-114">Vytvoření <xref:System.Data.SqlClient.SqlConnection> a <xref:System.Data.SqlClient.SqlCommand> objekty, které chcete připojit k serveru a zadejte příkaz jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="f353a-114">Create <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to connect to the server and define a Transact-SQL statement.</span></span>  
  
3.  <span data-ttu-id="f353a-115">Vytvořte novou `SqlDependency` objektu, nebo použijte existující a navázat jej na `SqlCommand` objektu.</span><span class="sxs-lookup"><span data-stu-id="f353a-115">Create a new `SqlDependency` object, or use an existing one, and bind it to the `SqlCommand` object.</span></span> <span data-ttu-id="f353a-116">Interně, tím se vytvoří <xref:System.Data.Sql.SqlNotificationRequest> objektu a váže k objektu command podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="f353a-116">Internally, this creates a <xref:System.Data.Sql.SqlNotificationRequest> object and binds it to the command object as needed.</span></span> <span data-ttu-id="f353a-117">Tato žádost o oznámení obsahuje interní identifikátor, který jednoznačně identifikuje tento `SqlDependency` objektu.</span><span class="sxs-lookup"><span data-stu-id="f353a-117">This notification request contains an internal identifier that uniquely identifies this `SqlDependency` object.</span></span> <span data-ttu-id="f353a-118">Také spustí naslouchací proces klienta, pokud již není aktivní.</span><span class="sxs-lookup"><span data-stu-id="f353a-118">It also starts the client listener if it is not already active.</span></span>  
  
4.  <span data-ttu-id="f353a-119">Obslužné rutiny události pro přihlášení k odběru `OnChange` události `SqlDependency` objektu.</span><span class="sxs-lookup"><span data-stu-id="f353a-119">Subscribe an event handler to the `OnChange` event of the `SqlDependency` object.</span></span>  
  
5.  <span data-ttu-id="f353a-120">Provedení příkazu pomocí kteréhokoli `Execute` metody `SqlCommand` objektu.</span><span class="sxs-lookup"><span data-stu-id="f353a-120">Execute the command using any of the `Execute` methods of the `SqlCommand` object.</span></span> <span data-ttu-id="f353a-121">Vzhledem k tomu, že příkaz je vázaná na objekt oznámení, server rozpozná, že ji musíte vygenerovat oznámení, a informace o frontě bude odkazovat na frontu závislosti.</span><span class="sxs-lookup"><span data-stu-id="f353a-121">Because the command is bound to the notification object, the server recognizes that it must generate a notification, and the queue information will point to the dependencies queue.</span></span>  
  
6.  <span data-ttu-id="f353a-122">Zastavit `SqlDependency` připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="f353a-122">Stop the `SqlDependency` connection to the server.</span></span>  
  
 <span data-ttu-id="f353a-123">Pokud se každý uživatel, následně změní v základních datech, Microsoft SQL Server zjistí, že je oznámení čekající na vyřízení pro tuto změnu a odešle oznámení, že je zpracován a předávaných do klienta prostřednictvím základní `SqlConnection` který byl vytvořen Při volání `SqlDependency.Start`.</span><span class="sxs-lookup"><span data-stu-id="f353a-123">If any user subsequently changes the underlying data, Microsoft SQL Server detects that there is a notification pending for such a change, and posts a notification that is processed and forwarded to the client through the underlying `SqlConnection` that was created by calling `SqlDependency.Start`.</span></span> <span data-ttu-id="f353a-124">Naslouchací proces klienta obdrží zprávu zneplatnění.</span><span class="sxs-lookup"><span data-stu-id="f353a-124">The client listener receives the invalidation message.</span></span> <span data-ttu-id="f353a-125">Naslouchací proces klienta poté vyhledá přidruženého `SqlDependency` objekt a aktivuje se `OnChange` událostí.</span><span class="sxs-lookup"><span data-stu-id="f353a-125">The client listener then locates the associated `SqlDependency` object and fires the `OnChange` event.</span></span>  
  
 <span data-ttu-id="f353a-126">Následující fragment kódu ukazuje vzor návrhu, které byste použili k vytvoření ukázkové aplikace.</span><span class="sxs-lookup"><span data-stu-id="f353a-126">The following code fragment shows the design pattern you would use to create a sample application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f353a-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="f353a-127">See Also</span></span>  
 [<span data-ttu-id="f353a-128">Oznámení dotazu v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="f353a-128">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="f353a-129">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="f353a-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
