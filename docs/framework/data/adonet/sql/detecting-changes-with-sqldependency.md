---
title: Detekce změn pomocí SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: 63d6a17e5aaf3e5d39ed0eda288e75c071be4d73
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724773"
---
# <a name="detecting-changes-with-sqldependency"></a><span data-ttu-id="a2080-102">Detekce změn pomocí SqlDependency</span><span class="sxs-lookup"><span data-stu-id="a2080-102">Detecting Changes with SqlDependency</span></span>
<span data-ttu-id="a2080-103">A <xref:System.Data.SqlClient.SqlDependency> objektu lze přidružit <xref:System.Data.SqlClient.SqlCommand> aby bylo možné rozpoznat, kdy se výsledky dotazu se liší od těch, které původně načten.</span><span class="sxs-lookup"><span data-stu-id="a2080-103">A <xref:System.Data.SqlClient.SqlDependency> object can be associated with a <xref:System.Data.SqlClient.SqlCommand> in order to detect when query results differ from those originally retrieved.</span></span> <span data-ttu-id="a2080-104">Můžete také přiřadit delegáta, kterého `OnChange` událost, která se aktivuje při změně výsledků pro přidružený příkaz.</span><span class="sxs-lookup"><span data-stu-id="a2080-104">You can also assign a delegate to the `OnChange` event, which will fire when the results change for an associated command.</span></span> <span data-ttu-id="a2080-105">Je třeba přidružit <xref:System.Data.SqlClient.SqlDependency> pomocí příkazu před spuštěním příkazu.</span><span class="sxs-lookup"><span data-stu-id="a2080-105">You must associate the <xref:System.Data.SqlClient.SqlDependency> with the command before you execute the command.</span></span> <span data-ttu-id="a2080-106">`HasChanges` Vlastnost <xref:System.Data.SqlClient.SqlDependency> lze také použít k určení, pokud výsledky dotazu se změnily od nejprve se data načetla.</span><span class="sxs-lookup"><span data-stu-id="a2080-106">The `HasChanges` property of the <xref:System.Data.SqlClient.SqlDependency> can also be used to determine if the query results have changed since the data was first retrieved.</span></span>  
  
## <a name="security-considerations"></a><span data-ttu-id="a2080-107">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a2080-107">Security Considerations</span></span>  
 <span data-ttu-id="a2080-108">Závislost infrastruktury spoléhá na <xref:System.Data.SqlClient.SqlConnection> , který se otevře při <xref:System.Data.SqlClient.SqlDependency.Start%2A> je volána, pokud chcete dostávat oznámení, která pro zadaný příkaz změnila podkladová data.</span><span class="sxs-lookup"><span data-stu-id="a2080-108">The dependency infrastructure relies on a <xref:System.Data.SqlClient.SqlConnection> that is opened when <xref:System.Data.SqlClient.SqlDependency.Start%2A> is called in order to receive notifications that the underlying data has changed for a given command.</span></span> <span data-ttu-id="a2080-109">Možnost pro klienta k zahájení volání `SqlDependency.Start` je řízen prostřednictvím <xref:System.Data.SqlClient.SqlClientPermission> a atributy zabezpečení přístupu kódu.</span><span class="sxs-lookup"><span data-stu-id="a2080-109">The ability for a client to initiate the call to `SqlDependency.Start` is controlled through the use of <xref:System.Data.SqlClient.SqlClientPermission> and code access security attributes.</span></span> <span data-ttu-id="a2080-110">Další informace najdete v tématu [povolení oznámení dotazů](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) a [zabezpečení přístupu kódu a ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="a2080-110">For more information, see [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) and [Code Access Security and ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="a2080-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="a2080-111">Example</span></span>  
 <span data-ttu-id="a2080-112">Následující kroky ukazují, jak deklarovat závislost, provedení příkazu a když výsledné sady změn, dostanete oznámení:</span><span class="sxs-lookup"><span data-stu-id="a2080-112">The following steps illustrate how to declare a dependency, execute a command, and receive a notification when the result set changes:</span></span>  
  
1.  <span data-ttu-id="a2080-113">Zahájit `SqlDependency` připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="a2080-113">Initiate a `SqlDependency` connection to the server.</span></span>  
  
2.  <span data-ttu-id="a2080-114">Vytvoření <xref:System.Data.SqlClient.SqlConnection> a <xref:System.Data.SqlClient.SqlCommand> objekty pro připojení k serveru a definování příkazu jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="a2080-114">Create <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to connect to the server and define a Transact-SQL statement.</span></span>  
  
3.  <span data-ttu-id="a2080-115">Vytvořte nový `SqlDependency` objektu, nebo použijte již existující a vytvořte mu vazbu k `SqlCommand` objektu.</span><span class="sxs-lookup"><span data-stu-id="a2080-115">Create a new `SqlDependency` object, or use an existing one, and bind it to the `SqlCommand` object.</span></span> <span data-ttu-id="a2080-116">Interně, tím se vytvoří <xref:System.Data.Sql.SqlNotificationRequest> objektu a vazba k objektu command, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="a2080-116">Internally, this creates a <xref:System.Data.Sql.SqlNotificationRequest> object and binds it to the command object as needed.</span></span> <span data-ttu-id="a2080-117">Žádost o toto oznámení obsahuje interní identifikátor, který jednoznačně identifikuje to `SqlDependency` objektu.</span><span class="sxs-lookup"><span data-stu-id="a2080-117">This notification request contains an internal identifier that uniquely identifies this `SqlDependency` object.</span></span> <span data-ttu-id="a2080-118">Pokud už není aktivní naslouchací proces klienta, spustí se také.</span><span class="sxs-lookup"><span data-stu-id="a2080-118">It also starts the client listener if it is not already active.</span></span>  
  
4.  <span data-ttu-id="a2080-119">Obslužná rutina události pro odběru `OnChange` událost `SqlDependency` objektu.</span><span class="sxs-lookup"><span data-stu-id="a2080-119">Subscribe an event handler to the `OnChange` event of the `SqlDependency` object.</span></span>  
  
5.  <span data-ttu-id="a2080-120">Spuštění příkazu pomocí kteréhokoli z `Execute` metody `SqlCommand` objektu.</span><span class="sxs-lookup"><span data-stu-id="a2080-120">Execute the command using any of the `Execute` methods of the `SqlCommand` object.</span></span> <span data-ttu-id="a2080-121">Vzhledem k tomu, že příkaz je vázán na objekt oznámení, server rozpoznal, že ho musíte vygenerovat oznámení a informace o frontě budou odkazovat na frontě závislosti.</span><span class="sxs-lookup"><span data-stu-id="a2080-121">Because the command is bound to the notification object, the server recognizes that it must generate a notification, and the queue information will point to the dependencies queue.</span></span>  
  
6.  <span data-ttu-id="a2080-122">Zastavit `SqlDependency` připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="a2080-122">Stop the `SqlDependency` connection to the server.</span></span>  
  
 <span data-ttu-id="a2080-123">Pokud se žádný uživatel následně změní podkladová data, Microsoft SQL Server rozpozná, že se čeká na oznámení pro tuto změnu a odešle oznámení, že je zpracován a předávaných do klienta prostřednictvím základní `SqlConnection` , který byl vytvořen voláním `SqlDependency.Start`.</span><span class="sxs-lookup"><span data-stu-id="a2080-123">If any user subsequently changes the underlying data, Microsoft SQL Server detects that there is a notification pending for such a change, and posts a notification that is processed and forwarded to the client through the underlying `SqlConnection` that was created by calling `SqlDependency.Start`.</span></span> <span data-ttu-id="a2080-124">Naslouchací proces klienta obdrží zprávu zneplatnění.</span><span class="sxs-lookup"><span data-stu-id="a2080-124">The client listener receives the invalidation message.</span></span> <span data-ttu-id="a2080-125">Naslouchací proces klienta poté vyhledá přidruženého `SqlDependency` objekt a aktivuje se `OnChange` událostí.</span><span class="sxs-lookup"><span data-stu-id="a2080-125">The client listener then locates the associated `SqlDependency` object and fires the `OnChange` event.</span></span>  
  
 <span data-ttu-id="a2080-126">Následující fragment kódu ukazuje návrhový vzor, který můžete použít k vytvoření ukázkové aplikace.</span><span class="sxs-lookup"><span data-stu-id="a2080-126">The following code fragment shows the design pattern you would use to create a sample application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2080-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2080-127">See Also</span></span>  
 [<span data-ttu-id="a2080-128">Oznámení pro dotazy na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="a2080-128">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="a2080-129">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="a2080-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
