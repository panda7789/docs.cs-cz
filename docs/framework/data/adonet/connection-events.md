---
title: Připojení událostí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: 719e529c7813679f1e927b66e7db0e110714e438
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="connection-events"></a>Připojení událostí
Všechny zprostředkovatele dat .NET Framework mají **připojení** objekty s dvě události, které můžete použít k načtení informační zprávy ze zdroje dat nebo k určení, zda stav **připojení** má změnit. Následující tabulka popisuje události z **připojení** objektu.  
  
|Událost|Popis|  
|-----------|-----------------|  
|**InfoMessage**|Nastane, když je pouze informativní zpráva vrácená ze zdroje dat. Informační zprávy jsou zprávy ze zdroje dat, které za následek výjimku hlášeny.|  
|**StateChange**|Nastane při stav **připojení** změny.|  
  
## <a name="working-with-the-infomessage-event"></a>Práce s InfoMessage událostí  
 Upozornění a informativní zprávy můžete načíst z zdroje dat systému SQL Server pomocí <xref:System.Data.SqlClient.SqlConnection.InfoMessage> události <xref:System.Data.SqlClient.SqlConnection> objektu. Chyby vrácené ze zdroje dat s úroveň závažnosti: 11 až 16 způsobit vyvolání výjimky. Ale <xref:System.Data.SqlClient.SqlConnection.InfoMessage> události lze použít k získání zprávy ze zdroje dat, které nejsou přidružené k chybě. V případě Microsoft SQL Server, se považuje za informační zpráva chyby se závažností 10 nebo méně a mohou být zachyceny pomocí <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událostí. Další informace najdete v tématu "Úrovně závažnosti chyby zpráva" v SQL Server Books Online.  
  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Přijímá události <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> objekt obsahující v jeho **chyby** vlastnost, zprávy ze zdroje dat kolekce. Můžete zadat dotaz **chyba** objekty v této kolekci pro text chyby číslo a zprávy, jakož i zdroji této chyby. Zprostředkovatel dat .NET Framework pro SQL Server obsahuje také podrobnosti o databáze, uložené procedury a číslo řádku, který pochází zprávy.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak přidat obslužné rutiny události pro <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událostí.  
  
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
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Událostí bude obvykle platit pouze pro informační a výstražných zpráv odesílaných ze serveru. Ale když skutečné dojde k chybě, provádění **ExecuteNonQuery** nebo **ExecuteReader** je metoda, která iniciovala operaci serveru zastavilo a je vyvolána výjimka.  
  
 Pokud chcete pokračovat zpracování zbytek příkazy v příkazu bez ohledu na případné chyby vyprodukované serveru, nastavte <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> vlastnost <xref:System.Data.SqlClient.SqlConnection> k `true`. To způsobí, že připojení k fire <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událost chyby místo vyvolání výjimky a přerušení zpracování. Klientská aplikace můžete zpracování této události a reagovat na chybové stavy.  
  
> [!NOTE]
>  K chybě s úrovní závažnosti 17 nebo vyšší, která způsobí, že server zastavit zpracování příkazu musí být zpracován jako výjimku. V takovém případě je vyvolána výjimka, bez ohledu na to, jak se chyba zpracovává v <xref:System.Data.SqlClient.SqlConnection.InfoMessage> událostí.  
  
## <a name="working-with-the-statechange-event"></a>Práce s událost StateChange  
 **StateChange** dojde k události při stav **připojení** změny. **StateChange** přijímá události <xref:System.Data.StateChangeEventArgs> které umožňují zjistit změny ve stavu systému **připojení** pomocí **OriginalState** a **CurrentState** vlastnosti. **OriginalState** vlastnost je <xref:System.Data.ConnectionState> výčet, který označuje stav **připojení** před ho změnit. **CurrentState** je <xref:System.Data.ConnectionState> výčet, který označuje stav **připojení** po ho změnit.  
  
 Následující příklad kódu používá **StateChange** událostí zapsat zprávu do konzole při stav **připojení** změny.  
  
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
 [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
