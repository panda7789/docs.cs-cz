---
title: Události připojení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: c1ef9ff9cc4d77e4951e99ed74c96cf78eb71506
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44139837"
---
# <a name="connection-events"></a><span data-ttu-id="e9c39-102">Události připojení</span><span class="sxs-lookup"><span data-stu-id="e9c39-102">Connection Events</span></span>
<span data-ttu-id="e9c39-103">Všechny zprostředkovatele dat .NET Framework mají **připojení** objekty se dvě události, které můžete použít k načtení informační zprávy ze zdroje dat nebo k určení, zda stav **připojení** má změnit.</span><span class="sxs-lookup"><span data-stu-id="e9c39-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="e9c39-104">Následující tabulka popisuje událostí **připojení** objektu.</span><span class="sxs-lookup"><span data-stu-id="e9c39-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="e9c39-105">Událost</span><span class="sxs-lookup"><span data-stu-id="e9c39-105">Event</span></span>|<span data-ttu-id="e9c39-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e9c39-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9c39-107">**InfoMessage**</span><span class="sxs-lookup"><span data-stu-id="e9c39-107">**InfoMessage**</span></span>|<span data-ttu-id="e9c39-108">Nastane, když je informační zpráva vrácená ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="e9c39-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="e9c39-109">Informační zprávy jsou zprávy ze zdroje dat, které nevedou k vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="e9c39-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="e9c39-110">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="e9c39-110">**StateChange**</span></span>|<span data-ttu-id="e9c39-111">Nastane, pokud stav **připojení** změny.</span><span class="sxs-lookup"><span data-stu-id="e9c39-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="e9c39-112">Práce s InfoMessage událostí</span><span class="sxs-lookup"><span data-stu-id="e9c39-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="e9c39-113">Můžete získat upozornění a informativní zprávy ze zdroje dat serveru SQL Server pomocí <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událost <xref:System.Data.SqlClient.SqlConnection> objektu.</span><span class="sxs-lookup"><span data-stu-id="e9c39-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="e9c39-114">Chyby vrácené ze zdroje dat s úrovní závažnosti 11 až 16 způsobí vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="e9c39-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="e9c39-115">Ale <xref:System.Data.SqlClient.SqlConnection.InfoMessage> události je možné získat zprávy ze zdroje dat, které nejsou přidruženy k chybě.</span><span class="sxs-lookup"><span data-stu-id="e9c39-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="e9c39-116">V případě Microsoft SQL Server, se považuje za informační zpráva všechny chyby se závažností 10 nebo méně a mohou být zachyceny pomocí <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událostí.</span><span class="sxs-lookup"><span data-stu-id="e9c39-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="e9c39-117">Další informace najdete v tématu [závažnosti chyby modulu databáze](/sql/relational-databases/errors-events/database-engine-error-severities) článku.</span><span class="sxs-lookup"><span data-stu-id="e9c39-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="e9c39-118"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Přijímá události <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> objekt obsahující v jeho **chyby** vlastnost, zprávy ze zdroje dat kolekce.</span><span class="sxs-lookup"><span data-stu-id="e9c39-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="e9c39-119">Můžete zadat dotaz **chyba** objekty v této kolekci pro text chyby číslo a zpráva, stejně jako zdroje chyby.</span><span class="sxs-lookup"><span data-stu-id="e9c39-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="e9c39-120">Zprostředkovatel dat .NET Framework pro SQL Server obsahuje také podrobnosti o databázi, uložené procedury a číslo řádku, který zpráva pochází z.</span><span class="sxs-lookup"><span data-stu-id="e9c39-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e9c39-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9c39-121">Example</span></span>  
 <span data-ttu-id="e9c39-122">Následující příklad kódu ukazuje, jak přidat obslužnou rutinu události pro <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událostí.</span><span class="sxs-lookup"><span data-stu-id="e9c39-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
```vb  
' Assumes that connection represents a SqlConnection object.  
  AddHandler connection.InfoMessage, _  
    New SqlInfoMessageEventHandler(AddressOf OnInfoMessage)  
  
Private Shared Sub OnInfoMessage(sender As Object, _  
  args As SqlInfoMessageEventArgs)  
  Dim err As SqlError  
  For Each err In args.Errors  
    Console.WriteLine("The {0} has received a severity {1}, _  
       state {2} error number {3}\n" & _  
      "on line {4} of procedure {5} on server {6}:\n{7}", _  
      err.Source, err.Class, err.State, err.Number, err.LineNumber, _  
    err.Procedure, err.Server, err.Message)  
  Next  
End Sub  
```  
  
```csharp  
// Assumes that connection represents a SqlConnection object.  
  connection.InfoMessage +=   
    new SqlInfoMessageEventHandler(OnInfoMessage);  
  
protected static void OnInfoMessage(  
  object sender, SqlInfoMessageEventArgs args)  
{  
  foreach (SqlError err in args.Errors)  
  {  
    Console.WriteLine(  
  "The {0} has received a severity {1}, state {2} error number {3}\n" +  
  "on line {4} of procedure {5} on server {6}:\n{7}",  
   err.Source, err.Class, err.State, err.Number, err.LineNumber,   
   err.Procedure, err.Server, err.Message);  
  }  
}  
```  
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="e9c39-123">Zpracování chyb jako InfoMessages</span><span class="sxs-lookup"><span data-stu-id="e9c39-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="e9c39-124"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Události obvykle bude platit jenom pro informativní a varovné zprávy odeslané ze serveru.</span><span class="sxs-lookup"><span data-stu-id="e9c39-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="e9c39-125">Ale když skutečné došlo k chybě, provádění **metodu ExecuteNonQuery** nebo **ExecuteReader** zastavení metodou, která zahájila činnost serveru a je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e9c39-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="e9c39-126">Pokud chcete pokračovat zpracování zbytek příkazů v příkazu bez ohledu na všechny chyby vytvořený server, nastavte <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> vlastnost <xref:System.Data.SqlClient.SqlConnection> k `true`.</span><span class="sxs-lookup"><span data-stu-id="e9c39-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="e9c39-127">To způsobí, že připojení, která se aktivuje <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událost chyby namísto vyvolání výjimky a přerušení zpracování.</span><span class="sxs-lookup"><span data-stu-id="e9c39-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="e9c39-128">Klientská aplikace může potom zpracování této události a reagovat na chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="e9c39-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9c39-129">K chybě 17 nebo vyšší úroveň závažnosti, která způsobí, že server zastaví zpracování příkazu musí být zpracován jako výjimku.</span><span class="sxs-lookup"><span data-stu-id="e9c39-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="e9c39-130">V takovém případě je vyvolána výjimka bez ohledu na to, jak je chyba zpracována v <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událostí.</span><span class="sxs-lookup"><span data-stu-id="e9c39-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="e9c39-131">Práce s StateChange událostí</span><span class="sxs-lookup"><span data-stu-id="e9c39-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="e9c39-132">**StateChange** dojde k události při stavu **připojení** změny.</span><span class="sxs-lookup"><span data-stu-id="e9c39-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="e9c39-133">**StateChange** přijímá události <xref:System.Data.StateChangeEventArgs> , díky kterým můžete určit změnu stavu **připojení** pomocí **OriginalState** a **CurrentState** vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e9c39-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="e9c39-134">**OriginalState** je vlastnost <xref:System.Data.ConnectionState> výčet, který označuje stav **připojení** před ho změnit.</span><span class="sxs-lookup"><span data-stu-id="e9c39-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="e9c39-135">**CurrentState** je <xref:System.Data.ConnectionState> výčet, který označuje stav **připojení** po ho změnit.</span><span class="sxs-lookup"><span data-stu-id="e9c39-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="e9c39-136">Následující příklad kódu používá **StateChange** událostí k zápisu zprávy do konzoly při stavu **připojení** změny.</span><span class="sxs-lookup"><span data-stu-id="e9c39-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
```vb  
' Assumes connection represents a SqlConnection object.  
  AddHandler connection.StateChange, _  
    New StateChangeEventHandler(AddressOf OnStateChange)  
  
Protected Shared Sub OnStateChange( _  
  sender As Object, args As StateChangeEventArgs)  
  
  Console.WriteLine( _  
  "The current Connection state has changed from {0} to {1}.", _  
  args.OriginalState, args.CurrentState)  
End Sub  
```  
  
```csharp  
// Assumes connection represents a SqlConnection object.  
  connection.StateChange  += new StateChangeEventHandler(OnStateChange);  
  
protected static void OnStateChange(object sender,   
  StateChangeEventArgs args)  
{  
  Console.WriteLine(  
    "The current Connection state has changed from {0} to {1}.",  
      args.OriginalState, args.CurrentState);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9c39-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9c39-137">See Also</span></span>  
 [<span data-ttu-id="e9c39-138">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="e9c39-138">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="e9c39-139">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="e9c39-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
