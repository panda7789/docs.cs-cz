---
title: Události připojení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: 8ed62d0193639b434d66c446e3b9d0c184577a80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949564"
---
# <a name="connection-events"></a><span data-ttu-id="e4845-102">Události připojení</span><span class="sxs-lookup"><span data-stu-id="e4845-102">Connection Events</span></span>
<span data-ttu-id="e4845-103">Všichni poskytovatelé dat .NET Framework mají objekty **připojení** se dvěma událostmi, které můžete použít k načtení informativních zpráv ze zdroje dat nebo k určení, jestli se změnil stav **připojení** .</span><span class="sxs-lookup"><span data-stu-id="e4845-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="e4845-104">Následující tabulka popisuje události objektu **připojení** .</span><span class="sxs-lookup"><span data-stu-id="e4845-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="e4845-105">Událost</span><span class="sxs-lookup"><span data-stu-id="e4845-105">Event</span></span>|<span data-ttu-id="e4845-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e4845-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e4845-107">**InfoMessage**</span><span class="sxs-lookup"><span data-stu-id="e4845-107">**InfoMessage**</span></span>|<span data-ttu-id="e4845-108">Nastane, pokud se ze zdroje dat vrátí informační zpráva.</span><span class="sxs-lookup"><span data-stu-id="e4845-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="e4845-109">Informační zprávy jsou zprávy ze zdroje dat, které nevedou k vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="e4845-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="e4845-110">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="e4845-110">**StateChange**</span></span>|<span data-ttu-id="e4845-111">Vyvolá se v případě, že dojde ke změně stavu **připojení** .</span><span class="sxs-lookup"><span data-stu-id="e4845-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="e4845-112">Práce s událostí InfoMessage</span><span class="sxs-lookup"><span data-stu-id="e4845-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="e4845-113">Můžete načíst upozornění a informativní zprávy ze zdroje dat SQL Server s využitím <xref:System.Data.SqlClient.SqlConnection.InfoMessage> události <xref:System.Data.SqlClient.SqlConnection> objektu.</span><span class="sxs-lookup"><span data-stu-id="e4845-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="e4845-114">Chyby vrácené ze zdroje dat se úrovní závažnosti 11 až 16 způsobují výjimku, která má být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="e4845-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="e4845-115"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Událost však lze použít k získání zpráv ze zdroje dat, které nejsou přidruženy k chybě.</span><span class="sxs-lookup"><span data-stu-id="e4845-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="e4845-116">V případě Microsoft SQL Server se jako informační zpráva považuje jakákoli chyba se závažností 10 nebo méně, která může být zachycena pomocí <xref:System.Data.SqlClient.SqlConnection.InfoMessage> události.</span><span class="sxs-lookup"><span data-stu-id="e4845-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="e4845-117">Další informace najdete v článku o [závažnosti chyb databázového stroje](/sql/relational-databases/errors-events/database-engine-error-severities) .</span><span class="sxs-lookup"><span data-stu-id="e4845-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="e4845-118">Událost obdrží objekt obsahující ve vlastnosti Errors kolekci zpráv ze zdroje dat. <xref:System.Data.SqlClient.SqlConnection.InfoMessage> <xref:System.Data.SqlClient.SqlInfoMessageEventArgs></span><span class="sxs-lookup"><span data-stu-id="e4845-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="e4845-119">Můžete zadat dotaz na objekty **chyby** v této kolekci pro číslo chyby a text zprávy a také zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="e4845-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="e4845-120">Zprostředkovatel dat .NET Framework pro SQL Server obsahuje také podrobnosti o databázi, uložené proceduře a čísle řádku, ze kterého zpráva pochází.</span><span class="sxs-lookup"><span data-stu-id="e4845-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e4845-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4845-121">Example</span></span>  
 <span data-ttu-id="e4845-122">Následující příklad kódu ukazuje, jak přidat obslužnou rutinu události pro <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událost.</span><span class="sxs-lookup"><span data-stu-id="e4845-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
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
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="e4845-123">Zpracování chyb jako InfoMessages</span><span class="sxs-lookup"><span data-stu-id="e4845-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="e4845-124"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Událost se normálně aktivuje jenom pro informativní a varovné zprávy, které se odesílají ze serveru.</span><span class="sxs-lookup"><span data-stu-id="e4845-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="e4845-125">Pokud však dojde ke skutečné chybě, spuštění metody **ExecuteNonQuery** nebo **ExecuteReader** , která iniciovala operaci serveru, je zastaveno a je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e4845-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="e4845-126">Pokud chcete pokračovat v zpracovávání zbývajících příkazů v příkazu bez ohledu na chyby vyprodukované serverem, nastavte <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> vlastnost <xref:System.Data.SqlClient.SqlConnection> `true`na.</span><span class="sxs-lookup"><span data-stu-id="e4845-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="e4845-127">To způsobí, že připojení <xref:System.Data.SqlClient.SqlConnection.InfoMessage> vyvolá událost pro chyby namísto vyvolání výjimky a přerušení zpracování.</span><span class="sxs-lookup"><span data-stu-id="e4845-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="e4845-128">Klientská aplikace pak může tuto událost zpracovat a reagovat na chybové podmínky.</span><span class="sxs-lookup"><span data-stu-id="e4845-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4845-129">Chyba s úrovní závažnosti 17 nebo vyšší, která způsobí, že server přestane zpracovávat příkazy, musí být zpracován jako výjimka.</span><span class="sxs-lookup"><span data-stu-id="e4845-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="e4845-130">V tomto případě je vyvolána výjimka bez ohledu na to, jak je chyba zpracována v <xref:System.Data.SqlClient.SqlConnection.InfoMessage> události.</span><span class="sxs-lookup"><span data-stu-id="e4845-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="e4845-131">Práce s událostí StateChange</span><span class="sxs-lookup"><span data-stu-id="e4845-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="e4845-132">K události **StateChange** dojde, když se změní stav **připojení** .</span><span class="sxs-lookup"><span data-stu-id="e4845-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="e4845-133">Událost **StateChange** přijímá <xref:System.Data.StateChangeEventArgs> , která umožňuje určit změnu stavu **připojení** pomocí vlastností **OriginalState** a **CurrentState** .</span><span class="sxs-lookup"><span data-stu-id="e4845-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="e4845-134">Vlastnost **OriginalState** je <xref:System.Data.ConnectionState> výčet, který označuje stav **připojení** před jeho změnou.</span><span class="sxs-lookup"><span data-stu-id="e4845-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="e4845-135">**CurrentState** je <xref:System.Data.ConnectionState> výčet, který označuje stav **připojení** po jeho změně.</span><span class="sxs-lookup"><span data-stu-id="e4845-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="e4845-136">Následující příklad kódu používá událost **StateChange** k zápisu zprávy do konzoly, když se změní stav **připojení** .</span><span class="sxs-lookup"><span data-stu-id="e4845-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e4845-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4845-137">See also</span></span>

- [<span data-ttu-id="e4845-138">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="e4845-138">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="e4845-139">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="e4845-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
