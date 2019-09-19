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
ms.openlocfilehash: 22e7c670f93293bd37edcb181c8130cdbe9ceb26
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047052"
---
# <a name="using-an-asynchronous-client-socket"></a>Použití asynchronního klientského soketu
Asynchronní klientský soket nezastaví aplikaci při čekání na dokončení síťových operací. Místo toho používá standardní .NET Framework asynchronní programovací model pro zpracování síťového připojení v jednom vláknu, zatímco aplikace pokračuje v běhu v původním vlákně. Asynchronní sokety jsou vhodné pro aplikace, které využívají těžké sítě nebo které nemůžou před pokračováním čekat na dokončení síťových operací.  
  
 Třída se řídí vzorem pojmenování .NET Framework pro asynchronní metody, například synchronní <xref:System.Net.Sockets.Socket.Receive%2A> Metoda odpovídá asynchronním <xref:System.Net.Sockets.Socket.BeginReceive%2A> a <xref:System.Net.Sockets.Socket.EndReceive%2A> metodám. <xref:System.Net.Sockets.Socket>  
  
 Asynchronní operace vyžadují metodu zpětného volání, která vrátí výsledek operace. Pokud vaše aplikace nemusí znát výsledek, není nutná žádná metoda zpětného volání. Vzorový kód v této části ukazuje použití metody pro spuštění připojení k síťovému zařízení a metodu zpětného volání pro dokončení připojení, metodu pro zahájení odesílání dat a metodu zpětného volání pro dokončení odesílání a metodu pro zahájení přijímání dat a Metoda zpětného volání pro ukončení přijímání dat  
  
 Asynchronní sokety používají pro zpracování síťových připojení více vláken z fondu vláken systému. Jedno vlákno zodpovídá za zahájení odesílání nebo přijímání dat; další vlákna dokončí připojení k síťovému zařízení a odesílají nebo přijímají data. V následujících příkladech se instance <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> třídy používají k pozastavení provádění hlavního vlákna a signálu, když může provádění pokračovat.  
  
 V následujícím příkladu pro připojení asynchronního soketu k síťovému zařízení `Connect` metoda inicializuje **soket** <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> a pak zavolá metodu, která předává vzdálený koncový bod, který představuje síťové zařízení, zpětné volání připojení. Metoda a stavový objekt ( **soket**klienta), který slouží k předávání informací o stavu mezi asynchronními voláními. V příkladu je implementována `Connect` metoda pro připojení zadaného **soketu** k určenému koncovému bodu. Předpokládá globální **ManualResetEvent** s názvem `connectDone`.  
  
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
  
 Metoda `ConnectCallback` připojení zpětného volání <xref:System.AsyncCallback> implementuje delegáta. Připojí se ke vzdálenému zařízení, když je dostupné vzdálené zařízení, a poté signalizuje vlákno aplikace, které bylo připojení dokončeno, nastavením **ManualResetEvent** `connectDone`. Následující kód implementuje `ConnectCallback` metodu.  
  
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
  
 Ukázková metoda `Send` Zakóduje zadaná řetězcová data ve formátu ASCII a asynchronně ji pošle na síťové zařízení reprezentované zadaným soketem. Následující příklad implementuje `Send` metodu.  
  
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
  
 Metoda `SendCallback` odeslání zpětného volání <xref:System.AsyncCallback> implementuje delegáta. Odesílá data, až bude síťové zařízení připravené přijímat. Následující příklad ukazuje implementaci `SendCallback` metody. Předpokládá globální **ManualResetEvent** s názvem `sendDone`.  
  
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
  
 Čtení dat z klientského soketu vyžaduje objekt stavu, který předává hodnoty mezi asynchronními voláními. Následující třída je příkladem stavu objektu pro příjem dat z klientského soketu. Obsahuje pole pro soket klienta, vyrovnávací paměť pro přijatá data a <xref:System.Text.StringBuilder> a pro uložení příchozího datového řetězce. Umístění těchto polí do objektu State umožňuje zachovat jejich hodnoty napříč více voláními pro čtení dat z soketu klienta.  
  
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
  
 Ukázková `Receive` metoda nastaví stavový objekt a pak zavolá metodu **BeginReceive** pro asynchronní čtení dat z soketu klienta. Následující příklad implementuje `Receive` metodu.  
  
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
  
 Metoda `ReceiveCallback` Receive zpětného volání implementuje delegáta **AsyncCallback** . Obdrží data ze síťového zařízení a vytvoří řetězec zprávy. Přečte jednu nebo více bajtů dat ze sítě do vyrovnávací paměti dat a pak znovu zavolá metodu **BeginReceive** , dokud nebudou data odesílaná klientem dokončena. Po načtení všech dat z klienta signalizuje vlákno aplikace `ReceiveCallback` , že data jsou dokončena, nastavením **ManualResetEvent** `sendDone`.  
  
 Následující příklad kódu implementuje `ReceiveCallback` metodu. Předpokládá globální řetězec s názvem `response` , který obsahuje přijatý řetězec a globální **ManualResetEvent** s názvem. `receiveDone` Aby bylo možné ukončit síťovou relaci, server musí řádně vypnout soket klienta.  
  
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

- [Použití synchronního klientského soketu](using-a-synchronous-client-socket.md)
- [Naslouchání pomocí soketů](listening-with-sockets.md)
- [Příklad asynchronního klientského soketu](asynchronous-client-socket-example.md)
