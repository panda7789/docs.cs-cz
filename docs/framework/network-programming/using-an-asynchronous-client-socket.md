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
ms.openlocfilehash: 4d7020b6bc5049101ec08329d53d966771e38035
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168893"
---
# <a name="using-an-asynchronous-client-socket"></a>Použití asynchronního klientského soketu
Asynchronního klientského soketu nepozastaví aplikace při čekání na dokončení operací sítě. Místo toho využívá standardní asynchronní programovací model rozhraní .NET Framework ke zpracování síťového připojení na jedno vlákno, zatímco aplikace stále běží v původním vláknu. Asynchronní sockets jsou vhodné pro aplikace, které usnadňují použití sítě nebo nemůže čekat na dokončení před pokračováním síťových operací.  
  
 <xref:System.Net.Sockets.Socket> Třídy způsobem názvy rozhraní .NET Framework vzorku pro asynchronní metody; například synchronní <xref:System.Net.Sockets.Socket.Receive%2A> metoda odpovídá asynchronní <xref:System.Net.Sockets.Socket.BeginReceive%2A> a <xref:System.Net.Sockets.Socket.EndReceive%2A> metody.  
  
 Asynchronní operace vyžadují metoda zpětného volání k vrácení výsledku operace. Pokud aplikace nepotřebuje vědět, výsledek, vyžaduje se žádná metoda zpětného volání. Ukázkový kód v této části ukazuje, jak pomocí metody spustíte připojení k síťovým zařízením a metody zpětného volání a dokončete připojení, metoda zahájit odesílání dat a metody zpětného volání k dokončení odesílání a metoda spuštění příjem dat a Metoda zpětného volání k ukončení přijímání dat  
  
 Asynchronní sokety používají více vláken z fondu podprocesů systému pro proces připojení k síti. Jedno vlákno zodpovídá za inicializaci odesílání nebo přijímání dat; ostatní vlákna dokončete připojení ke službě síťového zařízení a odesílat nebo přijímat data. V následujících příkladech instance <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> třídy se používají k pozastavení provádění z hlavního vlákna a signál, pokud provádění může pokračovat.  
  
 V následujícím příkladu, pro připojení k síťovým zařízením, asynchronní soketu `Connect` metoda inicializuje **soketu** a pak zavolá <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> předejte vzdálený koncový bod, který představuje síťové zařízení , připojit metoda zpětného volání a stavu objektu (klient **soketu**), který se používá k předávání informací o stavu mezi byla zahájena asynchronní volání. V příkladu implementuje `Connect` metodu připojení zadanou **soketu** na zadaný koncový bod. Předpokládá globální **ManualResetEvent** s názvem `connectDone`.  
  
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
  
 Metoda zpětného volání připojit `ConnectCallback` implementuje <xref:System.AsyncCallback> delegovat. Připojení ke vzdálenému zařízení při vzdálené zařízení je k dispozici a potom signály vlákna aplikace, že se připojení tak, že nastavíte **ManualResetEvent** `connectDone`. Následující kód implementuje `ConnectCallback` metody.  
  
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
  
 Ukázková metoda `Send` kóduje zadaného řetězce data ve formátu ASCII a asynchronně odešle síťovému zařízení reprezentované zadaným soketu. Následující příklad implementuje `Send` metody.  
  
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
  
 Metoda zpětného volání odesílání `SendCallback` implementuje <xref:System.AsyncCallback> delegovat. Když je připravena přijímat síťové zařízení odešle data. Následující příklad ukazuje implementaci `SendCallback` metody. Předpokládá globální **ManualResetEvent** s názvem `sendDone`.  
  
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
  
 Čtení dat z klientského soketu vyžaduje stav objektu, který předává hodnoty mezi byla zahájena asynchronní volání. Třída následující je příklad objekt stavu pro příjem dat z klientského soketu. Obsahuje pole pro klientského soketu vyrovnávací paměti pro přijatá data a <xref:System.Text.StringBuilder> k uložení vstupní řetězec data. Umístění těchto polí v objektu stavu umožňuje jejich hodnot zachovaná napříč více volání na čtení dat z klientského soketu.  
  
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
  
 V příkladu `Receive` metoda nastaví stav objektu a pak zavolá **BeginReceive** metody, které se mají asynchronně číst data z klientského soketu. Následující příklad implementuje `Receive` metody.  
  
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
  
 Zpětné volání metody receive `ReceiveCallback` implementuje **AsyncCallback** delegovat. Přijme data ze síťového zařízení a vytvoří řetězec zprávy. Načte jeden nebo více bajtů dat ze sítě do vyrovnávací paměti dat a pak zavolá **BeginReceive** metoda znovu, dokud data odeslaná klientem je dokončena. Jakmile data načítají z klienta, `ReceiveCallback` signály vlákna aplikace, že data jsou kompletní tak, že nastavíte **ManualResetEvent** `sendDone`.  
  
 Následující příklad kódu implementuje `ReceiveCallback` metody. Globální řetězec s názvem předpokládá `response` , který obsahuje řetězec přijatých a globální **ManualResetEvent** s názvem `receiveDone`. Na serveru musí vypnout klientského soketu řádně k ukončení relace sítě.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Použití synchronního klientského soketu](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)
- [Naslouchání pomocí soketů](../../../docs/framework/network-programming/listening-with-sockets.md)
- [Příklad asynchronního klientského soketu](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)
