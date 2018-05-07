---
title: Pomocí soketu asynchronní klienta
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 59d7e30bfa9bbaf2308e78f47de03bb7be69c44d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-an-asynchronous-client-socket"></a>Pomocí soketu asynchronní klienta
Soketu asynchronní klienta nepozastaví aplikace při čekání na dokončení operací sítě. Místo toho používá standardní asynchronní programovací model rozhraní .NET Framework ke zpracování připojení k síti na jedno vlákno, zatímco aplikace stále běží na původní vlákno. Asynchronní sockets jsou vhodné pro aplikace, která hodně využívají sítě nebo nelze počkejte na dokončení před pokračováním síťových operací.  
  
 <xref:System.Net.Sockets.Socket> Třída způsobem názvy rozhraní .NET Framework vzor pro asynchronní metody; například synchronní <xref:System.Net.Sockets.Socket.Receive%2A> metoda odpovídá asynchronní <xref:System.Net.Sockets.Socket.BeginReceive%2A> a <xref:System.Net.Sockets.Socket.EndReceive%2A> metody.  
  
 Asynchronní operace vyžadují metody zpětného volání k vrácení výsledku operace. Pokud vaše aplikace není nutné znát výsledek, žádná metoda zpětného volání není potřeba. Ukázkový kód v této části ukazuje, jak pomocí metody zahájíte připojení k síťovým zařízením a metody zpětného volání a dokončete připojení, metoda zahájit odesílání dat a metody zpětného volání k dokončení odesílání a způsob, jak začít přijímat data a Metoda zpětného volání pro příjem dat ukončení.  
  
 Asynchronní sockets pomocí více vláken z fondu podprocesů systému proces síťová připojení. Jedno vlákno zodpovídá za inicializaci odesílání nebo přijímání dat; jiná vlákna dokončení připojení k síťové zařízení a odesílat nebo přijímat data. V následujících příkladech instance <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> třída slouží k pozastavení provádění hlavního vlákna a signál při spuštění může pokračovat.  
  
 V následujícím příkladu se pro připojení k síťovým zařízením, asynchronní soketu `Connect` metoda inicializuje **soketu** a potom zavolá <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> metodu předáním vzdálený koncový bod, který představuje síťové zařízení , připojit metoda zpětného volání a stavu objektu (klient **soketu**), který slouží k předání informací o stavu mezi asynchronní volání. V příkladu implementuje `Connect` metoda připojení zadaný **soketu** zadaný koncový bod. Předpokládá globální konfiguraci **ManualResetEvent** s názvem `connectDone`.  
  
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
  
 Metoda zpětného volání připojit `ConnectCallback` implementuje <xref:System.AsyncCallback> delegovat. Připojení k vzdálené zařízení při vzdálené zařízení je k dispozici a pak signály vlákno aplikace, je připojení dokončena nastavením **ManualResetEvent** `connectDone`. Následující kód implementuje `ConnectCallback` metoda.  
  
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
  
 Příklad metoda `Send` kóduje data zadaný řetězec ve formátu ASCII a odešle ji asynchronně síťovému zařízení reprezentována zadaný časový limit soketu. Následující příklad implementuje `Send` metoda.  
  
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
  
 Metoda zpětného volání odesílání `SendCallback` implementuje <xref:System.AsyncCallback> delegovat. Síťové zařízení je připraven přijmout odešle data. Následující příklad ukazuje implementaci `SendCallback` metoda. Předpokládá globální konfiguraci **ManualResetEvent** s názvem `sendDone`.  
  
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
  
 Čtení dat ze soketu klienta vyžaduje objekt stavu, který předává hodnoty mezi asynchronní volání. Následující třídy je objekt příklad stavu pro příjem dat ze soketu klienta. Obsahuje pole pro Soket klienta, vyrovnávací paměť pro přijatá data a <xref:System.Text.StringBuilder> pro uložení příchozí řetězec. Uvedení těchto polí objekt stavu umožňuje jejich hodnoty nutné zachovat napříč více volání čtení dat ze soketu klienta.  
  
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
  
 V příkladu `Receive` metoda nastaví stav objektu a pak zavolá **BeginReceive** metoda mají asynchronně číst data z klienta soketu. Následující příklad implementuje `Receive` metoda.  
  
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
  
 Metoda zpětného volání receive `ReceiveCallback` implementuje **AsyncCallback** delegovat. Přijetí dat ze síťového zařízení a vytvoří řetězec zprávy. Při čtení jeden nebo více bajtů dat do vyrovnávací paměti dat ze sítě a pak zavolá **BeginReceive** metoda znovu, dokud data odeslaná klientem je dokončena. Jakmile je načíst všechna data z klienta, `ReceiveCallback` signály vlákno aplikace, data je dokončena nastavením **ManualResetEvent** `sendDone`.  
  
 Následující příklad kódu implementuje `ReceiveCallback` metoda. Předpokládá globální řetězec s názvem `response` , obsahuje přijaté řetězec a globální konfiguraci **ManualResetEvent** s názvem `receiveDone`. Server musí vypnout Soket klienta řádně k ukončení relace sítě.  
  
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
 [Použití synchronního klientského soketu](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [Naslouchání pomocí soketů](../../../docs/framework/network-programming/listening-with-sockets.md)  
 [Příklad asynchronního klientského soketu](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)
