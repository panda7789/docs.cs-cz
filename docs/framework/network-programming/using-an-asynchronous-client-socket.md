---
title: Použití asynchronního klientského soketu
description: Tento příklad ukazuje asynchronní klientský soket. .NET Framework asynchronní programování umožňuje, aby při zpracování připojení běžela aplikace i nadále.
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
ms.openlocfilehash: 9cf46e9519bcecf4d7a20ff99b86fa5f66af2087
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502038"
---
# <a name="using-an-asynchronous-client-socket"></a><span data-ttu-id="e6e50-104">Použití asynchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="e6e50-104">Using an Asynchronous Client Socket</span></span>
<span data-ttu-id="e6e50-105">Asynchronní klientský soket nezastaví aplikaci při čekání na dokončení síťových operací.</span><span class="sxs-lookup"><span data-stu-id="e6e50-105">An asynchronous client socket does not suspend the application while waiting for network operations to complete.</span></span> <span data-ttu-id="e6e50-106">Místo toho používá standardní .NET Framework asynchronní programovací model pro zpracování síťového připojení v jednom vláknu, zatímco aplikace pokračuje v běhu v původním vlákně.</span><span class="sxs-lookup"><span data-stu-id="e6e50-106">Instead, it uses the standard .NET Framework asynchronous programming model to process the network connection on one thread while the application continues to run on the original thread.</span></span> <span data-ttu-id="e6e50-107">Asynchronní sokety jsou vhodné pro aplikace, které využívají těžké sítě nebo které nemůžou před pokračováním čekat na dokončení síťových operací.</span><span class="sxs-lookup"><span data-stu-id="e6e50-107">Asynchronous sockets are appropriate for applications that make heavy use of the network or that cannot wait for network operations to complete before continuing.</span></span>  
  
 <span data-ttu-id="e6e50-108"><xref:System.Net.Sockets.Socket>Třída se řídí vzorem pojmenování .NET Framework pro asynchronní metody, například synchronní <xref:System.Net.Sockets.Socket.Receive%2A> Metoda odpovídá asynchronním <xref:System.Net.Sockets.Socket.BeginReceive%2A> a <xref:System.Net.Sockets.Socket.EndReceive%2A> metodám.</span><span class="sxs-lookup"><span data-stu-id="e6e50-108">The <xref:System.Net.Sockets.Socket> class follows the .NET Framework naming pattern for asynchronous methods; for example, the synchronous <xref:System.Net.Sockets.Socket.Receive%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginReceive%2A> and <xref:System.Net.Sockets.Socket.EndReceive%2A> methods.</span></span>  
  
 <span data-ttu-id="e6e50-109">Asynchronní operace vyžadují metodu zpětného volání, která vrátí výsledek operace.</span><span class="sxs-lookup"><span data-stu-id="e6e50-109">Asynchronous operations require a callback method to return the result of the operation.</span></span> <span data-ttu-id="e6e50-110">Pokud vaše aplikace nemusí znát výsledek, není nutná žádná metoda zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="e6e50-110">If your application does not need to know the result, then no callback method is required.</span></span> <span data-ttu-id="e6e50-111">Vzorový kód v této části ukazuje použití metody pro spuštění připojení k síťovému zařízení a metodu zpětného volání pro dokončení připojení, metodu pro zahájení odesílání dat a metodu zpětného volání pro dokončení odesílání a metodu pro zahájení přijímání dat a metodu zpětného volání pro ukončení přijímajících dat.</span><span class="sxs-lookup"><span data-stu-id="e6e50-111">The example code in this section demonstrates using a method to start connecting to a network device and a callback method to complete the connection, a method to start sending data and a callback method to complete the send, and a method to start receiving data and a callback method to end receiving data.</span></span>  
  
 <span data-ttu-id="e6e50-112">Asynchronní sokety používají pro zpracování síťových připojení více vláken z fondu vláken systému.</span><span class="sxs-lookup"><span data-stu-id="e6e50-112">Asynchronous sockets use multiple threads from the system thread pool to process network connections.</span></span> <span data-ttu-id="e6e50-113">Jedno vlákno zodpovídá za zahájení odesílání nebo přijímání dat; další vlákna dokončí připojení k síťovému zařízení a odesílají nebo přijímají data.</span><span class="sxs-lookup"><span data-stu-id="e6e50-113">One thread is responsible for initiating the sending or receiving of data; other threads complete the connection to the network device and send or receive the data.</span></span> <span data-ttu-id="e6e50-114">V následujících příkladech se instance <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> třídy používají k pozastavení provádění hlavního vlákna a signálu, když může provádění pokračovat.</span><span class="sxs-lookup"><span data-stu-id="e6e50-114">In the following examples, instances of the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class are used to suspend execution of the main thread and signal when execution can continue.</span></span>  
  
 <span data-ttu-id="e6e50-115">V následujícím příkladu, pro připojení asynchronního soketu k síťovému zařízení, `Connect` metoda inicializuje **soket** a pak zavolá <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> metodu, která předává vzdálený koncový bod, který představuje síťové zařízení, metodu zpětného volání připojení a objekt stavu ( **soket**klienta), který slouží k předávání informací o stavu mezi asynchronními voláními.</span><span class="sxs-lookup"><span data-stu-id="e6e50-115">In the following example, to connect an asynchronous socket to a network device, the `Connect` method initializes a **Socket** and then calls the <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> method, passing a remote endpoint that represents the network device, the connect callback method, and a state object (the client **Socket**), which is used to pass state information between asynchronous calls.</span></span> <span data-ttu-id="e6e50-116">V příkladu je implementována `Connect` metoda pro připojení zadaného **soketu** k určenému koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="e6e50-116">The example implements the `Connect` method to connect the specified **Socket** to the specified endpoint.</span></span> <span data-ttu-id="e6e50-117">Předpokládá globální **ManualResetEvent** s názvem `connectDone` .</span><span class="sxs-lookup"><span data-stu-id="e6e50-117">It assumes a global **ManualResetEvent** named `connectDone`.</span></span>  
  
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
  
 <span data-ttu-id="e6e50-118">Metoda připojení zpětného volání `ConnectCallback` implementuje <xref:System.AsyncCallback> delegáta.</span><span class="sxs-lookup"><span data-stu-id="e6e50-118">The connect callback method `ConnectCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="e6e50-119">Připojí se ke vzdálenému zařízení, když je dostupné vzdálené zařízení, a poté signalizuje vlákno aplikace, které bylo připojení dokončeno, nastavením **ManualResetEvent** `connectDone` .</span><span class="sxs-lookup"><span data-stu-id="e6e50-119">It connects to the remote device when the remote device is available and then signals the application thread that the connection is complete by setting the **ManualResetEvent** `connectDone`.</span></span> <span data-ttu-id="e6e50-120">Následující kód implementuje `ConnectCallback` metodu.</span><span class="sxs-lookup"><span data-stu-id="e6e50-120">The following code implements the `ConnectCallback` method.</span></span>  
  
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
  
 <span data-ttu-id="e6e50-121">Ukázková metoda `Send` Zakóduje zadaná řetězcová data ve formátu ASCII a asynchronně ji pošle na síťové zařízení reprezentované zadaným soketem.</span><span class="sxs-lookup"><span data-stu-id="e6e50-121">The example method `Send` encodes the specified string data in ASCII format and sends it asynchronously to the network device represented by the specified socket.</span></span> <span data-ttu-id="e6e50-122">Následující příklad implementuje `Send` metodu.</span><span class="sxs-lookup"><span data-stu-id="e6e50-122">The following example implements the `Send` method.</span></span>  
  
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
  
 <span data-ttu-id="e6e50-123">Metoda odeslání zpětného volání `SendCallback` implementuje <xref:System.AsyncCallback> delegáta.</span><span class="sxs-lookup"><span data-stu-id="e6e50-123">The send callback method `SendCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="e6e50-124">Odesílá data, až bude síťové zařízení připravené přijímat.</span><span class="sxs-lookup"><span data-stu-id="e6e50-124">It sends the data when the network device is ready to receive.</span></span> <span data-ttu-id="e6e50-125">Následující příklad ukazuje implementaci `SendCallback` metody.</span><span class="sxs-lookup"><span data-stu-id="e6e50-125">The following example shows the implementation of the `SendCallback` method.</span></span> <span data-ttu-id="e6e50-126">Předpokládá globální **ManualResetEvent** s názvem `sendDone` .</span><span class="sxs-lookup"><span data-stu-id="e6e50-126">It assumes a global **ManualResetEvent** named `sendDone`.</span></span>  
  
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
  
 <span data-ttu-id="e6e50-127">Čtení dat z klientského soketu vyžaduje objekt stavu, který předává hodnoty mezi asynchronními voláními.</span><span class="sxs-lookup"><span data-stu-id="e6e50-127">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="e6e50-128">Následující třída je příkladem stavu objektu pro příjem dat z klientského soketu.</span><span class="sxs-lookup"><span data-stu-id="e6e50-128">The following class is an example state object for receiving data from a client socket.</span></span> <span data-ttu-id="e6e50-129">Obsahuje pole pro soket klienta, vyrovnávací paměť pro přijatá data a a <xref:System.Text.StringBuilder> pro uložení příchozího datového řetězce.</span><span class="sxs-lookup"><span data-stu-id="e6e50-129">It contains a field for the client socket, a buffer for the received data, and a <xref:System.Text.StringBuilder> to hold the incoming data string.</span></span> <span data-ttu-id="e6e50-130">Umístění těchto polí do objektu State umožňuje zachovat jejich hodnoty napříč více voláními pro čtení dat z soketu klienta.</span><span class="sxs-lookup"><span data-stu-id="e6e50-130">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="e6e50-131">Ukázková `Receive` Metoda nastaví stavový objekt a pak zavolá metodu **BeginReceive** pro asynchronní čtení dat z soketu klienta.</span><span class="sxs-lookup"><span data-stu-id="e6e50-131">The example `Receive` method sets up the state object and then calls the **BeginReceive** method to read the data from the client socket asynchronously.</span></span> <span data-ttu-id="e6e50-132">Následující příklad implementuje `Receive` metodu.</span><span class="sxs-lookup"><span data-stu-id="e6e50-132">The following example implements the `Receive` method.</span></span>  
  
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
  
 <span data-ttu-id="e6e50-133">Metoda Receive zpětného volání `ReceiveCallback` implementuje delegáta **AsyncCallback** .</span><span class="sxs-lookup"><span data-stu-id="e6e50-133">The receive callback method `ReceiveCallback` implements the **AsyncCallback** delegate.</span></span> <span data-ttu-id="e6e50-134">Obdrží data ze síťového zařízení a vytvoří řetězec zprávy.</span><span class="sxs-lookup"><span data-stu-id="e6e50-134">It receives the data from the network device and builds a message string.</span></span> <span data-ttu-id="e6e50-135">Přečte jednu nebo více bajtů dat ze sítě do vyrovnávací paměti dat a pak znovu zavolá metodu **BeginReceive** , dokud nebudou data odesílaná klientem dokončena.</span><span class="sxs-lookup"><span data-stu-id="e6e50-135">It reads one or more bytes of data from the network into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="e6e50-136">Po načtení všech dat z klienta `ReceiveCallback` signalizuje vlákno aplikace, že data jsou dokončena, nastavením **ManualResetEvent** `sendDone` .</span><span class="sxs-lookup"><span data-stu-id="e6e50-136">Once all the data is read from the client, `ReceiveCallback` signals the application thread that the data is complete by setting the **ManualResetEvent** `sendDone`.</span></span>  
  
 <span data-ttu-id="e6e50-137">Následující příklad kódu implementuje `ReceiveCallback` metodu.</span><span class="sxs-lookup"><span data-stu-id="e6e50-137">The following example code implements the `ReceiveCallback` method.</span></span> <span data-ttu-id="e6e50-138">Předpokládá globální řetězec s názvem `response` , který obsahuje přijatý řetězec a globální **ManualResetEvent** s názvem `receiveDone` .</span><span class="sxs-lookup"><span data-stu-id="e6e50-138">It assumes a global string named `response` that holds the received string and a global **ManualResetEvent** named `receiveDone`.</span></span> <span data-ttu-id="e6e50-139">Aby bylo možné ukončit síťovou relaci, server musí řádně vypnout soket klienta.</span><span class="sxs-lookup"><span data-stu-id="e6e50-139">The server must shut down the client socket gracefully to end the network session.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6e50-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6e50-140">See also</span></span>

- [<span data-ttu-id="e6e50-141">Použití synchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="e6e50-141">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="e6e50-142">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="e6e50-142">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="e6e50-143">Příklad asynchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="e6e50-143">Asynchronous Client Socket Example</span></span>](asynchronous-client-socket-example.md)
