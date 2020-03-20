---
title: Události připojení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: a7ad0d4d950da71db0aebca872949fa82669c5c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151696"
---
# <a name="connection-events"></a><span data-ttu-id="c2a34-102">Události připojení</span><span class="sxs-lookup"><span data-stu-id="c2a34-102">Connection Events</span></span>
<span data-ttu-id="c2a34-103">Všichni zprostředkovatelé dat rozhraní .NET Framework mají objekty **connection** se dvěma událostmi, které můžete použít k načtení informačních zpráv ze zdroje dat nebo k určení, zda se změnil stav **připojení.**</span><span class="sxs-lookup"><span data-stu-id="c2a34-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="c2a34-104">Následující tabulka popisuje události objektu **Connection.**</span><span class="sxs-lookup"><span data-stu-id="c2a34-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="c2a34-105">Událost</span><span class="sxs-lookup"><span data-stu-id="c2a34-105">Event</span></span>|<span data-ttu-id="c2a34-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c2a34-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c2a34-107">**Informační zpráva**</span><span class="sxs-lookup"><span data-stu-id="c2a34-107">**InfoMessage**</span></span>|<span data-ttu-id="c2a34-108">Vyvolá se při vrácení informační zprávy ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="c2a34-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="c2a34-109">Informační zprávy jsou zprávy ze zdroje dat, které nevedou k vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="c2a34-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="c2a34-110">**Změna stavu**</span><span class="sxs-lookup"><span data-stu-id="c2a34-110">**StateChange**</span></span>|<span data-ttu-id="c2a34-111">Vyvolá se při změně stavu **připojení.**</span><span class="sxs-lookup"><span data-stu-id="c2a34-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="c2a34-112">Práce s událostí InfoMessage</span><span class="sxs-lookup"><span data-stu-id="c2a34-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="c2a34-113">Upozornění a informační zprávy můžete načíst ze zdroje <xref:System.Data.SqlClient.SqlConnection.InfoMessage> dat <xref:System.Data.SqlClient.SqlConnection> serveru SQL Server pomocí události objektu.</span><span class="sxs-lookup"><span data-stu-id="c2a34-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="c2a34-114">Chyby vrácené ze zdroje dat s úrovní závažnosti 11 až 16 způsobit výjimku vyvolat.</span><span class="sxs-lookup"><span data-stu-id="c2a34-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="c2a34-115"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> Událost však lze získat zprávy ze zdroje dat, které nejsou spojeny s chybou.</span><span class="sxs-lookup"><span data-stu-id="c2a34-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="c2a34-116">V případě serveru Microsoft SQL Server je jakákoli chyba se závažností 10 nebo menší považována za informační <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zprávu a může být zachycena pomocí události.</span><span class="sxs-lookup"><span data-stu-id="c2a34-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="c2a34-117">Další informace naleznete v článku [Rozdělení chyb databázového stroje.](/sql/relational-databases/errors-events/database-engine-error-severities)</span><span class="sxs-lookup"><span data-stu-id="c2a34-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="c2a34-118">Událost <xref:System.Data.SqlClient.SqlConnection.InfoMessage> obdrží <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> objekt obsahující, v jeho **Errors** vlastnost, kolekce zpráv ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="c2a34-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="c2a34-119">Můžete dotaz **Error** objekty v této kolekci pro číslo chyby a text zprávy, jakož i zdroj chyby.</span><span class="sxs-lookup"><span data-stu-id="c2a34-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="c2a34-120">Zprostředkovatel dat rozhraní .NET Framework pro SQL Server také obsahuje podrobnosti o databázi, uložené proceduře a čísle řádku, ze kterého zpráva pochází.</span><span class="sxs-lookup"><span data-stu-id="c2a34-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="c2a34-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2a34-121">Example</span></span>  
 <span data-ttu-id="c2a34-122">Následující příklad kódu ukazuje, jak přidat <xref:System.Data.SqlClient.SqlConnection.InfoMessage> obslužnou rutinu události pro událost.</span><span class="sxs-lookup"><span data-stu-id="c2a34-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
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
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="c2a34-123">Zpracování chyb jako informačních zpráv</span><span class="sxs-lookup"><span data-stu-id="c2a34-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="c2a34-124">Událost <xref:System.Data.SqlClient.SqlConnection.InfoMessage> se obvykle vypaluje pouze pro informační a varovné zprávy odeslané ze serveru.</span><span class="sxs-lookup"><span data-stu-id="c2a34-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="c2a34-125">Však když dojde k skutečné chybě, provádění **ExecuteNonQuery** nebo **ExecuteReader** metoda, která iniciovala operaci serveru je zastavena a je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="c2a34-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="c2a34-126">Pokud chcete pokračovat ve zpracování zbývajících příkazů v příkazu bez ohledu na <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> chyby <xref:System.Data.SqlClient.SqlConnection> vytvořené `true`serverem, nastavte vlastnost do .</span><span class="sxs-lookup"><span data-stu-id="c2a34-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="c2a34-127">To způsobí, že připojení <xref:System.Data.SqlClient.SqlConnection.InfoMessage> k požáru události pro chyby namísto vyvolání výjimky a přerušení zpracování.</span><span class="sxs-lookup"><span data-stu-id="c2a34-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="c2a34-128">Klientská aplikace pak může tuto událost zpracovat a reagovat na chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="c2a34-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2a34-129">Jako výjimku musí být zpracována chyba s úrovní závažnosti 17 nebo vyšší, která způsobí, že server zastaví zpracování příkazu.</span><span class="sxs-lookup"><span data-stu-id="c2a34-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="c2a34-130">V tomto případě je vyvolána výjimka bez ohledu na <xref:System.Data.SqlClient.SqlConnection.InfoMessage> to, jak je chyba zpracována v události.</span><span class="sxs-lookup"><span data-stu-id="c2a34-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="c2a34-131">Práce s událostí StateChange</span><span class="sxs-lookup"><span data-stu-id="c2a34-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="c2a34-132">**StateChange** Událost nastane při změně stavu **připojení.**</span><span class="sxs-lookup"><span data-stu-id="c2a34-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="c2a34-133">**StateChange** <xref:System.Data.StateChangeEventArgs> událost obdrží, které umožňují určit změnu stavu **připojení** pomocí **OriginalState** a **CurrentState** vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c2a34-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="c2a34-134">Vlastnost **OriginalState** je <xref:System.Data.ConnectionState> výčet, který označuje stav **connection** před změnou.</span><span class="sxs-lookup"><span data-stu-id="c2a34-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="c2a34-135">**CurrentState** je <xref:System.Data.ConnectionState> výčet, který označuje stav **připojení** po změně.</span><span class="sxs-lookup"><span data-stu-id="c2a34-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="c2a34-136">Následující příklad kódu používá událost **StateChange** k zápisu zprávy do konzoly při změně stavu **připojení.**</span><span class="sxs-lookup"><span data-stu-id="c2a34-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c2a34-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2a34-137">See also</span></span>

- [<span data-ttu-id="c2a34-138">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="c2a34-138">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="c2a34-139">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c2a34-139">ADO.NET Overview</span></span>](ado-net-overview.md)
