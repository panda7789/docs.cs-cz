---
title: Události připojení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: 2d11a2e3a3ca7218aecd5d38dd9dd036f99d7687
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687814"
---
# <a name="connection-events"></a>Události připojení
Všechny zprostředkovatele dat .NET Framework mají **připojení** objekty se dvě události, které můžete použít k načtení informační zprávy ze zdroje dat nebo k určení, zda stav **připojení** má změnit. Následující tabulka popisuje událostí **připojení** objektu.  
  
|Událost|Popis|  
|-----------|-----------------|  
|**InfoMessage**|Nastane, když je informační zpráva vrácená ze zdroje dat. Informační zprávy jsou zprávy ze zdroje dat, které nevedou k vyvolání výjimky.|  
|**StateChange**|Nastane, pokud stav **připojení** změny.|  
  
## <a name="working-with-the-infomessage-event"></a>Práce s InfoMessage událostí  
 Můžete získat upozornění a informativní zprávy ze zdroje dat serveru SQL Server pomocí <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událost <xref:System.Data.SqlClient.SqlConnection> objektu. Chyby vrácené ze zdroje dat s úrovní závažnosti 11 až 16 způsobí vyvolání výjimky. Ale <xref:System.Data.SqlClient.SqlConnection.InfoMessage> události je možné získat zprávy ze zdroje dat, které nejsou přidruženy k chybě. V případě Microsoft SQL Server, se považuje za informační zpráva všechny chyby se závažností 10 nebo méně a mohou být zachyceny pomocí <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událostí. Další informace najdete v tématu [závažnosti chyby modulu databáze](/sql/relational-databases/errors-events/database-engine-error-severities) článku.
  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Přijímá události <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> objekt obsahující v jeho **chyby** vlastnost, zprávy ze zdroje dat kolekce. Můžete zadat dotaz **chyba** objekty v této kolekci pro text chyby číslo a zpráva, stejně jako zdroje chyby. Zprostředkovatel dat .NET Framework pro SQL Server obsahuje také podrobnosti o databázi, uložené procedury a číslo řádku, který zpráva pochází z.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak přidat obslužnou rutinu události pro <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událostí.  
  
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
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Události obvykle bude platit jenom pro informativní a varovné zprávy odeslané ze serveru. Ale když skutečné došlo k chybě, provádění **metodu ExecuteNonQuery** nebo **ExecuteReader** zastavení metodou, která zahájila činnost serveru a je vyvolána výjimka.  
  
 Pokud chcete pokračovat zpracování zbytek příkazů v příkazu bez ohledu na všechny chyby vytvořený server, nastavte <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> vlastnost <xref:System.Data.SqlClient.SqlConnection> k `true`. To způsobí, že připojení, která se aktivuje <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událost chyby namísto vyvolání výjimky a přerušení zpracování. Klientská aplikace může potom zpracování této události a reagovat na chybové stavy.  
  
> [!NOTE]
>  K chybě 17 nebo vyšší úroveň závažnosti, která způsobí, že server zastaví zpracování příkazu musí být zpracován jako výjimku. V takovém případě je vyvolána výjimka bez ohledu na to, jak je chyba zpracována v <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událostí.  
  
## <a name="working-with-the-statechange-event"></a>Práce s StateChange událostí  
 **StateChange** dojde k události při stavu **připojení** změny. **StateChange** přijímá události <xref:System.Data.StateChangeEventArgs> , díky kterým můžete určit změnu stavu **připojení** pomocí **OriginalState** a **CurrentState** vlastnosti. **OriginalState** je vlastnost <xref:System.Data.ConnectionState> výčet, který označuje stav **připojení** před ho změnit. **CurrentState** je <xref:System.Data.ConnectionState> výčet, který označuje stav **připojení** po ho změnit.  
  
 Následující příklad kódu používá **StateChange** událostí k zápisu zprávy do konzoly při stavu **připojení** změny.  
  
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
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
