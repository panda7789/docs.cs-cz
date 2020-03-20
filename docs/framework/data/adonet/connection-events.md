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
# <a name="connection-events"></a>Události připojení
Všichni zprostředkovatelé dat rozhraní .NET Framework mají objekty **connection** se dvěma událostmi, které můžete použít k načtení informačních zpráv ze zdroje dat nebo k určení, zda se změnil stav **připojení.** Následující tabulka popisuje události objektu **Connection.**  
  
|Událost|Popis|  
|-----------|-----------------|  
|**Informační zpráva**|Vyvolá se při vrácení informační zprávy ze zdroje dat. Informační zprávy jsou zprávy ze zdroje dat, které nevedou k vyvolání výjimky.|  
|**Změna stavu**|Vyvolá se při změně stavu **připojení.**|  
  
## <a name="working-with-the-infomessage-event"></a>Práce s událostí InfoMessage  
 Upozornění a informační zprávy můžete načíst ze zdroje <xref:System.Data.SqlClient.SqlConnection.InfoMessage> dat <xref:System.Data.SqlClient.SqlConnection> serveru SQL Server pomocí události objektu. Chyby vrácené ze zdroje dat s úrovní závažnosti 11 až 16 způsobit výjimku vyvolat. <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Událost však lze získat zprávy ze zdroje dat, které nejsou spojeny s chybou. V případě serveru Microsoft SQL Server je jakákoli chyba se závažností 10 nebo menší považována za informační <xref:System.Data.SqlClient.SqlConnection.InfoMessage> zprávu a může být zachycena pomocí události. Další informace naleznete v článku [Rozdělení chyb databázového stroje.](/sql/relational-databases/errors-events/database-engine-error-severities)
  
 Událost <xref:System.Data.SqlClient.SqlConnection.InfoMessage> obdrží <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> objekt obsahující, v jeho **Errors** vlastnost, kolekce zpráv ze zdroje dat. Můžete dotaz **Error** objekty v této kolekci pro číslo chyby a text zprávy, jakož i zdroj chyby. Zprostředkovatel dat rozhraní .NET Framework pro SQL Server také obsahuje podrobnosti o databázi, uložené proceduře a čísle řádku, ze kterého zpráva pochází.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak přidat <xref:System.Data.SqlClient.SqlConnection.InfoMessage> obslužnou rutinu události pro událost.  
  
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
  
## <a name="handling-errors-as-infomessages"></a>Zpracování chyb jako informačních zpráv  
 Událost <xref:System.Data.SqlClient.SqlConnection.InfoMessage> se obvykle vypaluje pouze pro informační a varovné zprávy odeslané ze serveru. Však když dojde k skutečné chybě, provádění **ExecuteNonQuery** nebo **ExecuteReader** metoda, která iniciovala operaci serveru je zastavena a je vyvolána výjimka.  
  
 Pokud chcete pokračovat ve zpracování zbývajících příkazů v příkazu bez ohledu na <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> chyby <xref:System.Data.SqlClient.SqlConnection> vytvořené `true`serverem, nastavte vlastnost do . To způsobí, že připojení <xref:System.Data.SqlClient.SqlConnection.InfoMessage> k požáru události pro chyby namísto vyvolání výjimky a přerušení zpracování. Klientská aplikace pak může tuto událost zpracovat a reagovat na chybové stavy.  
  
> [!NOTE]
> Jako výjimku musí být zpracována chyba s úrovní závažnosti 17 nebo vyšší, která způsobí, že server zastaví zpracování příkazu. V tomto případě je vyvolána výjimka bez ohledu na <xref:System.Data.SqlClient.SqlConnection.InfoMessage> to, jak je chyba zpracována v události.  
  
## <a name="working-with-the-statechange-event"></a>Práce s událostí StateChange  
 **StateChange** Událost nastane při změně stavu **připojení.** **StateChange** <xref:System.Data.StateChangeEventArgs> událost obdrží, které umožňují určit změnu stavu **připojení** pomocí **OriginalState** a **CurrentState** vlastnosti. Vlastnost **OriginalState** je <xref:System.Data.ConnectionState> výčet, který označuje stav **connection** před změnou. **CurrentState** je <xref:System.Data.ConnectionState> výčet, který označuje stav **připojení** po změně.  
  
 Následující příklad kódu používá událost **StateChange** k zápisu zprávy do konzoly při změně stavu **připojení.**  
  
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
  
## <a name="see-also"></a>Viz také

- [Připojení ke zdroji dat](connecting-to-a-data-source.md)
- [Přehled ADO.NET](ado-net-overview.md)
