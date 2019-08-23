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
# <a name="connection-events"></a>Události připojení
Všichni poskytovatelé dat .NET Framework mají objekty **připojení** se dvěma událostmi, které můžete použít k načtení informativních zpráv ze zdroje dat nebo k určení, jestli se změnil stav **připojení** . Následující tabulka popisuje události objektu **připojení** .  
  
|Událost|Popis|  
|-----------|-----------------|  
|**InfoMessage**|Nastane, pokud se ze zdroje dat vrátí informační zpráva. Informační zprávy jsou zprávy ze zdroje dat, které nevedou k vyvolání výjimky.|  
|**StateChange**|Vyvolá se v případě, že dojde ke změně stavu **připojení** .|  
  
## <a name="working-with-the-infomessage-event"></a>Práce s událostí InfoMessage  
 Můžete načíst upozornění a informativní zprávy ze zdroje dat SQL Server s využitím <xref:System.Data.SqlClient.SqlConnection.InfoMessage> události <xref:System.Data.SqlClient.SqlConnection> objektu. Chyby vrácené ze zdroje dat se úrovní závažnosti 11 až 16 způsobují výjimku, která má být vyvolána. <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Událost však lze použít k získání zpráv ze zdroje dat, které nejsou přidruženy k chybě. V případě Microsoft SQL Server se jako informační zpráva považuje jakákoli chyba se závažností 10 nebo méně, která může být zachycena pomocí <xref:System.Data.SqlClient.SqlConnection.InfoMessage> události. Další informace najdete v článku o [závažnosti chyb databázového stroje](/sql/relational-databases/errors-events/database-engine-error-severities) .
  
 Událost obdrží objekt obsahující ve vlastnosti Errors kolekci zpráv ze zdroje dat. <xref:System.Data.SqlClient.SqlConnection.InfoMessage> <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> Můžete zadat dotaz na objekty **chyby** v této kolekci pro číslo chyby a text zprávy a také zdroj chyby. Zprostředkovatel dat .NET Framework pro SQL Server obsahuje také podrobnosti o databázi, uložené proceduře a čísle řádku, ze kterého zpráva pochází.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak přidat obslužnou rutinu události pro <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událost.  
  
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
  
## <a name="handling-errors-as-infomessages"></a>Zpracování chyb jako InfoMessages  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Událost se normálně aktivuje jenom pro informativní a varovné zprávy, které se odesílají ze serveru. Pokud však dojde ke skutečné chybě, spuštění metody **ExecuteNonQuery** nebo **ExecuteReader** , která iniciovala operaci serveru, je zastaveno a je vyvolána výjimka.  
  
 Pokud chcete pokračovat v zpracovávání zbývajících příkazů v příkazu bez ohledu na chyby vyprodukované serverem, nastavte <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> vlastnost <xref:System.Data.SqlClient.SqlConnection> `true`na. To způsobí, že připojení <xref:System.Data.SqlClient.SqlConnection.InfoMessage> vyvolá událost pro chyby namísto vyvolání výjimky a přerušení zpracování. Klientská aplikace pak může tuto událost zpracovat a reagovat na chybové podmínky.  
  
> [!NOTE]
> Chyba s úrovní závažnosti 17 nebo vyšší, která způsobí, že server přestane zpracovávat příkazy, musí být zpracován jako výjimka. V tomto případě je vyvolána výjimka bez ohledu na to, jak je chyba zpracována v <xref:System.Data.SqlClient.SqlConnection.InfoMessage> události.  
  
## <a name="working-with-the-statechange-event"></a>Práce s událostí StateChange  
 K události **StateChange** dojde, když se změní stav **připojení** . Událost **StateChange** přijímá <xref:System.Data.StateChangeEventArgs> , která umožňuje určit změnu stavu **připojení** pomocí vlastností **OriginalState** a **CurrentState** . Vlastnost **OriginalState** je <xref:System.Data.ConnectionState> výčet, který označuje stav **připojení** před jeho změnou. **CurrentState** je <xref:System.Data.ConnectionState> výčet, který označuje stav **připojení** po jeho změně.  
  
 Následující příklad kódu používá událost **StateChange** k zápisu zprávy do konzoly, když se změní stav **připojení** .  
  
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
  
## <a name="see-also"></a>Viz také:

- [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
