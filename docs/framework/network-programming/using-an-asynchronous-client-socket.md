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
ms.locfileid: "33393680"
---
# <a name="using-an-asynchronous-client-socket"></a><span data-ttu-id="73f4c-102">Pomocí soketu asynchronní klienta</span><span class="sxs-lookup"><span data-stu-id="73f4c-102">Using an Asynchronous Client Socket</span></span>
<span data-ttu-id="73f4c-103">Soketu asynchronní klienta nepozastaví aplikace při čekání na dokončení operací sítě.</span><span class="sxs-lookup"><span data-stu-id="73f4c-103">An asynchronous client socket does not suspend the application while waiting for network operations to complete.</span></span> <span data-ttu-id="73f4c-104">Místo toho používá standardní asynchronní programovací model rozhraní .NET Framework ke zpracování připojení k síti na jedno vlákno, zatímco aplikace stále běží na původní vlákno.</span><span class="sxs-lookup"><span data-stu-id="73f4c-104">Instead, it uses the standard .NET Framework asynchronous programming model to process the network connection on one thread while the application continues to run on the original thread.</span></span> <span data-ttu-id="73f4c-105">Asynchronní sockets jsou vhodné pro aplikace, která hodně využívají sítě nebo nelze počkejte na dokončení před pokračováním síťových operací.</span><span class="sxs-lookup"><span data-stu-id="73f4c-105">Asynchronous sockets are appropriate for applications that make heavy use of the network or that cannot wait for network operations to complete before continuing.</span></span>  
  
 <span data-ttu-id="73f4c-106"><xref:System.Net.Sockets.Socket> Třída způsobem názvy rozhraní .NET Framework vzor pro asynchronní metody; například synchronní <xref:System.Net.Sockets.Socket.Receive%2A> metoda odpovídá asynchronní <xref:System.Net.Sockets.Socket.BeginReceive%2A> a <xref:System.Net.Sockets.Socket.EndReceive%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="73f4c-106">The <xref:System.Net.Sockets.Socket> class follows the .NET Framework naming pattern for asynchronous methods; for example, the synchronous <xref:System.Net.Sockets.Socket.Receive%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginReceive%2A> and <xref:System.Net.Sockets.Socket.EndReceive%2A> methods.</span></span>  
  
 <span data-ttu-id="73f4c-107">Asynchronní operace vyžadují metody zpětného volání k vrácení výsledku operace.</span><span class="sxs-lookup"><span data-stu-id="73f4c-107">Asynchronous operations require a callback method to return the result of the operation.</span></span> <span data-ttu-id="73f4c-108">Pokud vaše aplikace není nutné znát výsledek, žádná metoda zpětného volání není potřeba.</span><span class="sxs-lookup"><span data-stu-id="73f4c-108">If your application does not need to know the result, then no callback method is required.</span></span> <span data-ttu-id="73f4c-109">Ukázkový kód v této části ukazuje, jak pomocí metody zahájíte připojení k síťovým zařízením a metody zpětného volání a dokončete připojení, metoda zahájit odesílání dat a metody zpětného volání k dokončení odesílání a způsob, jak začít přijímat data a Metoda zpětného volání pro příjem dat ukončení.</span><span class="sxs-lookup"><span data-stu-id="73f4c-109">The example code in this section demonstrates using a method to start connecting to a network device and a callback method to complete the connection, a method to start sending data and a callback method to complete the send, and a method to start receiving data and a callback method to end receiving data.</span></span>  
  
 <span data-ttu-id="73f4c-110">Asynchronní sockets pomocí více vláken z fondu podprocesů systému proces síťová připojení.</span><span class="sxs-lookup"><span data-stu-id="73f4c-110">Asynchronous sockets use multiple threads from the system thread pool to process network connections.</span></span> <span data-ttu-id="73f4c-111">Jedno vlákno zodpovídá za inicializaci odesílání nebo přijímání dat; jiná vlákna dokončení připojení k síťové zařízení a odesílat nebo přijímat data.</span><span class="sxs-lookup"><span data-stu-id="73f4c-111">One thread is responsible for initiating the sending or receiving of data; other threads complete the connection to the network device and send or receive the data.</span></span> <span data-ttu-id="73f4c-112">V následujících příkladech instance <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> třída slouží k pozastavení provádění hlavního vlákna a signál při spuštění může pokračovat.</span><span class="sxs-lookup"><span data-stu-id="73f4c-112">In the following examples, instances of the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class are used to suspend execution of the main thread and signal when execution can continue.</span></span>  
  
 <span data-ttu-id="73f4c-113">V následujícím příkladu se pro připojení k síťovým zařízením, asynchronní soketu `Connect` metoda inicializuje **soketu** a potom zavolá <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> metodu předáním vzdálený koncový bod, který představuje síťové zařízení , připojit metoda zpětného volání a stavu objektu (klient **soketu**), který slouží k předání informací o stavu mezi asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="73f4c-113">In the following example, to connect an asynchronous socket to a network device, the `Connect` method initializes a **Socket** and then calls the <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> method, passing a remote endpoint that represents the network device, the connect callback method, and a state object (the client **Socket**), which is used to pass state information between asynchronous calls.</span></span> <span data-ttu-id="73f4c-114">V příkladu implementuje `Connect` metoda připojení zadaný **soketu** zadaný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="73f4c-114">The example implements the `Connect` method to connect the specified **Socket** to the specified endpoint.</span></span> <span data-ttu-id="73f4c-115">Předpokládá globální konfiguraci **ManualResetEvent** s názvem `connectDone`.</span><span class="sxs-lookup"><span data-stu-id="73f4c-115">It assumes a global **ManualResetEvent** named `connectDone`.</span></span>  
  
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
  
 <span data-ttu-id="73f4c-116">Metoda zpětného volání připojit `ConnectCallback` implementuje <xref:System.AsyncCallback> delegovat.</span><span class="sxs-lookup"><span data-stu-id="73f4c-116">The connect callback method `ConnectCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="73f4c-117">Připojení k vzdálené zařízení při vzdálené zařízení je k dispozici a pak signály vlákno aplikace, je připojení dokončena nastavením **ManualResetEvent** `connectDone`.</span><span class="sxs-lookup"><span data-stu-id="73f4c-117">It connects to the remote device when the remote device is available and then signals the application thread that the connection is complete by setting the **ManualResetEvent** `connectDone`.</span></span> <span data-ttu-id="73f4c-118">Následující kód implementuje `ConnectCallback` metoda.</span><span class="sxs-lookup"><span data-stu-id="73f4c-118">The following code implements the `ConnectCallback` method.</span></span>  
  
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
  
 <span data-ttu-id="73f4c-119">Příklad metoda `Send` kóduje data zadaný řetězec ve formátu ASCII a odešle ji asynchronně síťovému zařízení reprezentována zadaný časový limit soketu.</span><span class="sxs-lookup"><span data-stu-id="73f4c-119">The example method `Send` encodes the specified string data in ASCII format and sends it asynchronously to the network device represented by the specified socket.</span></span> <span data-ttu-id="73f4c-120">Následující příklad implementuje `Send` metoda.</span><span class="sxs-lookup"><span data-stu-id="73f4c-120">The following example implements the `Send` method.</span></span>  
  
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
  
 <span data-ttu-id="73f4c-121">Metoda zpětného volání odesílání `SendCallback` implementuje <xref:System.AsyncCallback> delegovat.</span><span class="sxs-lookup"><span data-stu-id="73f4c-121">The send callback method `SendCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="73f4c-122">Síťové zařízení je připraven přijmout odešle data.</span><span class="sxs-lookup"><span data-stu-id="73f4c-122">It sends the data when the network device is ready to receive.</span></span> <span data-ttu-id="73f4c-123">Následující příklad ukazuje implementaci `SendCallback` metoda.</span><span class="sxs-lookup"><span data-stu-id="73f4c-123">The following example shows the implementation of the `SendCallback` method.</span></span> <span data-ttu-id="73f4c-124">Předpokládá globální konfiguraci **ManualResetEvent** s názvem `sendDone`.</span><span class="sxs-lookup"><span data-stu-id="73f4c-124">It assumes a global **ManualResetEvent** named `sendDone`.</span></span>  
  
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
  
 <span data-ttu-id="73f4c-125">Čtení dat ze soketu klienta vyžaduje objekt stavu, který předává hodnoty mezi asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="73f4c-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="73f4c-126">Následující třídy je objekt příklad stavu pro příjem dat ze soketu klienta.</span><span class="sxs-lookup"><span data-stu-id="73f4c-126">The following class is an example state object for receiving data from a client socket.</span></span> <span data-ttu-id="73f4c-127">Obsahuje pole pro Soket klienta, vyrovnávací paměť pro přijatá data a <xref:System.Text.StringBuilder> pro uložení příchozí řetězec.</span><span class="sxs-lookup"><span data-stu-id="73f4c-127">It contains a field for the client socket, a buffer for the received data, and a <xref:System.Text.StringBuilder> to hold the incoming data string.</span></span> <span data-ttu-id="73f4c-128">Uvedení těchto polí objekt stavu umožňuje jejich hodnoty nutné zachovat napříč více volání čtení dat ze soketu klienta.</span><span class="sxs-lookup"><span data-stu-id="73f4c-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="73f4c-129">V příkladu `Receive` metoda nastaví stav objektu a pak zavolá **BeginReceive** metoda mají asynchronně číst data z klienta soketu.</span><span class="sxs-lookup"><span data-stu-id="73f4c-129">The example `Receive` method sets up the state object and then calls the **BeginReceive** method to read the data from the client socket asynchronously.</span></span> <span data-ttu-id="73f4c-130">Následující příklad implementuje `Receive` metoda.</span><span class="sxs-lookup"><span data-stu-id="73f4c-130">The following example implements the `Receive` method.</span></span>  
  
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
  
 <span data-ttu-id="73f4c-131">Metoda zpětného volání receive `ReceiveCallback` implementuje **AsyncCallback** delegovat.</span><span class="sxs-lookup"><span data-stu-id="73f4c-131">The receive callback method `ReceiveCallback` implements the **AsyncCallback** delegate.</span></span> <span data-ttu-id="73f4c-132">Přijetí dat ze síťového zařízení a vytvoří řetězec zprávy.</span><span class="sxs-lookup"><span data-stu-id="73f4c-132">It receives the data from the network device and builds a message string.</span></span> <span data-ttu-id="73f4c-133">Při čtení jeden nebo více bajtů dat do vyrovnávací paměti dat ze sítě a pak zavolá **BeginReceive** metoda znovu, dokud data odeslaná klientem je dokončena.</span><span class="sxs-lookup"><span data-stu-id="73f4c-133">It reads one or more bytes of data from the network into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="73f4c-134">Jakmile je načíst všechna data z klienta, `ReceiveCallback` signály vlákno aplikace, data je dokončena nastavením **ManualResetEvent** `sendDone`.</span><span class="sxs-lookup"><span data-stu-id="73f4c-134">Once all the data is read from the client, `ReceiveCallback` signals the application thread that the data is complete by setting the **ManualResetEvent** `sendDone`.</span></span>  
  
 <span data-ttu-id="73f4c-135">Následující příklad kódu implementuje `ReceiveCallback` metoda.</span><span class="sxs-lookup"><span data-stu-id="73f4c-135">The following example code implements the `ReceiveCallback` method.</span></span> <span data-ttu-id="73f4c-136">Předpokládá globální řetězec s názvem `response` , obsahuje přijaté řetězec a globální konfiguraci **ManualResetEvent** s názvem `receiveDone`.</span><span class="sxs-lookup"><span data-stu-id="73f4c-136">It assumes a global string named `response` that holds the received string and a global **ManualResetEvent** named `receiveDone`.</span></span> <span data-ttu-id="73f4c-137">Server musí vypnout Soket klienta řádně k ukončení relace sítě.</span><span class="sxs-lookup"><span data-stu-id="73f4c-137">The server must shut down the client socket gracefully to end the network session.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73f4c-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="73f4c-138">See Also</span></span>  
 [<span data-ttu-id="73f4c-139">Použití synchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="73f4c-139">Using a Synchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [<span data-ttu-id="73f4c-140">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="73f4c-140">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)  
 [<span data-ttu-id="73f4c-141">Příklad asynchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="73f4c-141">Asynchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)
