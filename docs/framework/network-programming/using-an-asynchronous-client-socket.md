---
title: Použití asynchronního klientského soketu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- asynchronous client sockets
- Socket class, asynchronous client sockets
- requesting data from Internet, sockets
- sockets, asynchronous client sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: fd85bc88-e06c-467d-a30d-9fd7cffcfca1
ms.openlocfilehash: 748745ca6799005dccdbfcbcc37a8c2a38f2a88e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180651"
---
# <a name="using-an-asynchronous-client-socket"></a>Použití asynchronního klientského soketu
Asynchronní klientský soket nepozastaví aplikaci při čekání na dokončení síťových operací. Místo toho používá standardní asynchronní programovací model rozhraní .NET Framework ke zpracování síťového připojení v jednom vlákně, zatímco aplikace pokračuje v běhu v původním vlákně. Asynchronní sokety jsou vhodné pro aplikace, které využívají síť nebo které nemohou čekat na dokončení síťových operací před pokračováním.  
  
 Třída <xref:System.Net.Sockets.Socket> následuje vzor pojmenování rozhraní .NET Framework pro asynchronní metody; například synchronní <xref:System.Net.Sockets.Socket.Receive%2A> metoda odpovídá asynchronní <xref:System.Net.Sockets.Socket.BeginReceive%2A> a <xref:System.Net.Sockets.Socket.EndReceive%2A> metody.  
  
 Asynchronní operace vyžadují metodu zpětného volání k vrácení výsledku operace. Pokud vaše aplikace nepotřebuje znát výsledek, není vyžadována žádná metoda zpětného volání. Ukázkový kód v této části ukazuje použití metody pro zahájení připojení k síťovému zařízení a metodu zpětného volání k dokončení připojení, metodu pro zahájení odesílání dat a metodu zpětného volání k dokončení odesílání a metodu pro zahájení příjmu dat a callback pro ukončení příjmu dat.  
  
 Asynchronní sokety ke zpracování síťových připojení používají více vláken ze systémového fondu vláken. Jedno vlákno je zodpovědné za zahájení odesílání nebo přijímání dat; ostatní vlákna dokončí připojení k síťovému zařízení a odesílají nebo přijímají data. V následujících příkladech instance <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> třídy se používají k pozastavení provádění hlavního vlákna a signálu, když může pokračovat provádění.  
  
 V následujícím příkladu pro připojení asynchronního soketu `Connect` k síťovému zařízení metoda inicializuje **Socket** a pak volá metodu, <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> předávání vzdáleného koncového bodu, který představuje síťové zařízení, metodu zpětného volání connect a objekt stavu (klientSocket ), který se používá k předávání informací o stavu mezi asynchronními voláními. **Socket** Příklad implementuje `Connect` metodu pro připojení zadaného **Socket** u zadaného koncového bodu. Předpokládá globální **ManualResetEvent** s `connectDone`názvem .  
  
```vb  
Public Shared Sub Connect(remoteEP As EndPoint, client As Socket)  
    client.BeginConnect(remoteEP, _  
       AddressOf ConnectCallback, client)  
  
    connectDone.WaitOne()  
End Sub 'Connect  
```  
  
```csharp  
public static void Connect(EndPoint remoteEP, Socket client) {  
    client.BeginConnect(remoteEP,
        new AsyncCallback(ConnectCallback), client );  
  
   connectDone.WaitOne();  
}  
```  
  
 Metoda `ConnectCallback` zpětného volání connect <xref:System.AsyncCallback> implementuje delegáta. Připojí se ke vzdálenému zařízení, když je vzdálené zařízení k dispozici, a poté signalizuje podprocesu aplikace, že připojení je dokončeno nastavením **aplikace ManualResetEvent** `connectDone`. Následující kód implementuje metodu. `ConnectCallback`  
  
```vb  
Private Shared Sub ConnectCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete the connection.  
        client.EndConnect(ar)  
  
        Console.WriteLine("Socket connected to {0}", _  
            client.RemoteEndPoint.ToString())  
  
        ' Signal that the connection has been made.  
        connectDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ConnectCallback  
```  
  
```csharp  
private static void ConnectCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete the connection.  
        client.EndConnect(ar);  
  
        Console.WriteLine("Socket connected to {0}",  
            client.RemoteEndPoint.ToString());  
  
        // Signal that the connection has been made.  
        connectDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 Metoda example `Send` kóduje zadaná řetězcová data ve formátu ASCII a odešle je asynchronně do síťového zařízení reprezentovaného zadaným soketem. Následující příklad implementuje metodu. `Send`  
  
```vb  
Private Shared Sub Send(client As Socket, data As [String])  
    ' Convert the string data to byte data using ASCII encoding.  
    Dim byteData As Byte() = Encoding.ASCII.GetBytes(data)  
  
    ' Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None, _  
        AddressOf SendCallback, client)  
End Sub 'Send  
```  
  
```csharp  
private static void Send(Socket client, String data) {  
    // Convert the string data to byte data using ASCII encoding.  
    byte[] byteData = Encoding.ASCII.GetBytes(data);  
  
    // Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None,  
        new AsyncCallback(SendCallback), client);  
}  
```  
  
 Metoda `SendCallback` zpětného volání odeslání <xref:System.AsyncCallback> implementuje delegáta. Odešle data, když je síťové zařízení připraveno k příjmu. Následující příklad ukazuje implementaci `SendCallback` metody. Předpokládá globální **ManualResetEvent** s `sendDone`názvem .  
  
```vb  
Private Shared Sub SendCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete sending the data to the remote device.  
        Dim bytesSent As Integer = client.EndSend(ar)  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent)  
  
        ' Signal that all bytes have been sent.  
        sendDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'SendCallback  
```  
  
```csharp  
private static void SendCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete sending the data to the remote device.  
        int bytesSent = client.EndSend(ar);  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent);  
  
        // Signal that all bytes have been sent.  
        sendDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 Čtení dat ze soketu klienta vyžaduje objekt stavu, který předává hodnoty mezi asynchronními voláními. Následující třída je ukázkovým objektem stavu pro příjem dat ze soketu klienta. Obsahuje pole pro soket klienta, vyrovnávací paměť <xref:System.Text.StringBuilder> pro přijatá data a pro uložení příchozího datového řetězce. Umístění těchto polí do objektu stavu umožňuje jejich hodnoty zachovat přes více volání číst data ze soketu klienta.  
  
```vb  
Public Class StateObject  
    ' Client socket.  
    Public workSocket As Socket = Nothing
    ' Size of receive buffer.  
    Public BufferSize As Integer = 256  
    ' Receive buffer.  
    Public buffer(256) As Byte
    ' Received data string.  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    // Client socket.  
    public Socket workSocket = null;  
    // Size of receive buffer.  
    public const int BufferSize = 256;  
    // Receive buffer.  
    public byte[] buffer = new byte[BufferSize];  
    // Received data string.  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 Metoda `Receive` example nastaví objekt stavu a pak volá **metodu BeginReceive** ke čtení dat ze soketu klienta asynchronně. Následující příklad implementuje metodu. `Receive`  
  
```vb  
Private Shared Sub Receive(client As Socket)  
    Try  
        ' Create the state object.  
        Dim state As New StateObject()  
        state.workSocket = client  
  
        ' Begin receiving the data from the remote device.  
        client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReceiveCallback, state)  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'Receive  
```  
  
```csharp  
private static void Receive(Socket client) {  
    try {  
        // Create the state object.  
        StateObject state = new StateObject();  
        state.workSocket = client;  
  
        // Begin receiving the data from the remote device.  
        client.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReceiveCallback), state);  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 Metoda `ReceiveCallback` zpětného volání pro příjem implementuje delegáta **AsyncCallback.** Přijímá data ze síťového zařízení a vytvoří řetězec zprávy. Přečte jeden nebo více bajtů dat ze sítě do vyrovnávací paměti dat a pak znovu zavolá metodu **BeginReceive,** dokud nebudou data odeslaná klientem dokončena. Jakmile jsou všechna data přečtena `ReceiveCallback` z klienta, signalizuje podproces aplikace, že data jsou dokončena nastavením **ManualResetEvent** `sendDone`.  
  
 Následující příklad kódu implementuje metodu. `ReceiveCallback` Předpokládá globální řetězec s `response` názvem, který obsahuje přijatý řetězec `receiveDone`a globální **ManualResetEvent** s názvem . Server musí řádně vypnout klientský soket, aby ukončil síťovou relaci.  
  
```vb  
Private Shared Sub ReceiveCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the state object and the client socket
        ' from the asynchronous state object.  
        Dim state As StateObject = CType(ar.AsyncState, StateObject)  
        Dim client As Socket = state.workSocket  
  
        ' Read data from the remote device.  
        Dim bytesRead As Integer = client.EndReceive(ar)  
  
        If bytesRead > 0 Then  
            ' There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, _  
                bytesRead))  
  
            '  Get the rest of the data.  
            client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
                AddressOf ReceiveCallback, state)  
        Else  
            ' All the data has arrived; put it in response.  
            If state.sb.Length > 1 Then  
                response = state.sb.ToString()  
            End If  
            ' Signal that all bytes have been received.  
            receiveDone.Set()  
        End If  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ReceiveCallback  
```  
  
```csharp  
private static void ReceiveCallback( IAsyncResult ar ) {  
    try {  
        // Retrieve the state object and the client socket
        // from the asynchronous state object.  
        StateObject state = (StateObject) ar.AsyncState;  
        Socket client = state.workSocket;  
        // Read data from the remote device.  
        int bytesRead = client.EndReceive(ar);  
        if (bytesRead > 0) {  
            // There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,bytesRead));  
                //  Get the rest of the data.  
            client.BeginReceive(state.buffer,0,StateObject.BufferSize,0,  
                new AsyncCallback(ReceiveCallback), state);  
        } else {  
            // All the data has arrived; put it in response.  
            if (state.sb.Length > 1) {  
                response = state.sb.ToString();  
            }  
            // Signal that all bytes have been received.  
            receiveDone.Set();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Použití synchronního klientského soketu](using-a-synchronous-client-socket.md)
- [Naslouchání pomocí soketů](listening-with-sockets.md)
- [Příklad asynchronního klientského soketu](asynchronous-client-socket-example.md)
