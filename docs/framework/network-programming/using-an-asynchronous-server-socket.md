---
title: Použití asynchronního serverového soketu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- Socket class, asynchronous server sockets
- data requests, sockets
- sockets, asynchronous server sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- asynchronous server sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 813489a9-3efd-41b6-a33f-371d55397676
ms.openlocfilehash: 467804e685d800643c421ed1aad040a842b42886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180637"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="13963-102">Použití asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="13963-102">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="13963-103">Sokety asynchronních serverů používají ke zpracování požadavků na síťové služby asynchronní programovací model rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13963-103">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="13963-104">Třída <xref:System.Net.Sockets.Socket> se řídí standardním vzorem asynchronního pojmenování rozhraní .NET Framework. například synchronní <xref:System.Net.Sockets.Socket.Accept%2A> metoda odpovídá asynchronní <xref:System.Net.Sockets.Socket.BeginAccept%2A> a <xref:System.Net.Sockets.Socket.EndAccept%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="13963-104">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="13963-105">Soket asynchronního serveru vyžaduje metodu pro zahájení přijímání požadavků na připojení ze sítě, metodu zpětného volání pro zpracování požadavků na připojení a zahájení příjmu dat ze sítě a metodu zpětného volání pro ukončení příjmu dat.</span><span class="sxs-lookup"><span data-stu-id="13963-105">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="13963-106">Všechny tyto metody jsou podrobně popsány v této části.</span><span class="sxs-lookup"><span data-stu-id="13963-106">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="13963-107">V následujícím příkladu, chcete-li začít přijímat požadavky `StartListening` na připojení ze sítě, metoda inicializuje **Socket** a pak používá **BeginAccept** metoda začít přijímat nová připojení.</span><span class="sxs-lookup"><span data-stu-id="13963-107">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="13963-108">Metoda zpětného volání přijetí je volána při přijetí nového požadavku na připojení na soketu.</span><span class="sxs-lookup"><span data-stu-id="13963-108">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="13963-109">Je zodpovědný za získání **Socket** instance, která bude zpracovávat připojení a **předání,** které Socket off do vlákna, které bude zpracovávat požadavek.</span><span class="sxs-lookup"><span data-stu-id="13963-109">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="13963-110">Metoda přijetí zpětného volání <xref:System.AsyncCallback> implementuje delegáta; vrátí void a vezme jeden parametr <xref:System.IAsyncResult>typu .</span><span class="sxs-lookup"><span data-stu-id="13963-110">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="13963-111">Následující příklad je prostředí metody přijetí zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="13963-111">The following example is the shell of an accept callback method.</span></span>  
  
```vb  
Sub AcceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
void AcceptCallback(IAsyncResult ar)
{  
    // Add the callback code here.  
}  
```  
  
 <span data-ttu-id="13963-112">Metoda **BeginAccept** přebírá dva parametry, **delegáta AsyncCallback,** který odkazuje na metodu zpětného volání přijmout a objekt, který se používá k předání informací o stavu metodě zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="13963-112">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="13963-113">V následujícím příkladu **naslouchání Socket** je předán metodu zpětného volání prostřednictvím parametru *state.*</span><span class="sxs-lookup"><span data-stu-id="13963-113">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="13963-114">Tento příklad vytvoří **delegáta AsyncCallback** a začne přijímat připojení ze sítě.</span><span class="sxs-lookup"><span data-stu-id="13963-114">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 <span data-ttu-id="13963-115">Asynchronní sokety používají vlákna z fondu systémových vláken ke zpracování příchozích připojení.</span><span class="sxs-lookup"><span data-stu-id="13963-115">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="13963-116">Jedno vlákno je zodpovědné za přijímání připojení, jiné vlákno se používá ke zpracování každého příchozího připojení a jiné vlákno je zodpovědné za příjem dat z připojení.</span><span class="sxs-lookup"><span data-stu-id="13963-116">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="13963-117">Může se jedná o stejné vlákno v závislosti na tom, které vlákno je přiřazeno fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="13963-117">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="13963-118">V následujícím příkladu <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> třída pozastaví provádění hlavního vlákna a signály při provádění může pokračovat.</span><span class="sxs-lookup"><span data-stu-id="13963-118">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="13963-119">Následující příklad ukazuje asynchronní metodu, která vytvoří asynchronní soket TCP/IP v místním počítači a začne přijímat připojení.</span><span class="sxs-lookup"><span data-stu-id="13963-119">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="13963-120">Předpokládá, že je globální **ManualResetEvent** s názvem `allDone`, že metoda `SocketListener`je členem třídy s `AcceptCallback` názvem , a že je definována metoda zpětného volání s názvem.</span><span class="sxs-lookup"><span data-stu-id="13963-120">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `AcceptCallback` is defined.</span></span>  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}")  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.AcceptCallback), _  
                listener)  
  
            allDone.WaitOne()  
        End While  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
    Console.WriteLine("Closing the listener...")  
End Sub 'StartListening  
```  
  
```csharp  
public void StartListening()
{  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0], 11000);  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}");  
  
    Socket listener = new Socket(localEP.Address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);  
  
    try
    {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true)
        {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
  
            allDone.WaitOne();  
        }  
    }
    catch (Exception e)
    {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine("Closing the listener...");  
}  
```  
  
 <span data-ttu-id="13963-121">Metoda zpětného volání`AcceptCallback` přijmout ( v předchozím příkladu) je zodpovědná za signalizaci hlavního vlákna aplikace pro pokračování ve zpracování, navázání připojení s klientem a spuštění asynchronního čtení dat z klienta.</span><span class="sxs-lookup"><span data-stu-id="13963-121">The accept callback method (`AcceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="13963-122">Následující příklad je první část implementace `AcceptCallback` metody.</span><span class="sxs-lookup"><span data-stu-id="13963-122">The following example is the first part of an implementation of the `AcceptCallback` method.</span></span> <span data-ttu-id="13963-123">Tato část metody signalizuje hlavní vlákno aplikace pokračovat ve zpracování a naváže připojení ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="13963-123">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="13963-124">Předpokládá globální **ManualResetEvent** s `allDone`názvem .</span><span class="sxs-lookup"><span data-stu-id="13963-124">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
```vb  
Public Sub AcceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
public void AcceptCallback(IAsyncResult ar)
{  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.
}  
```  
  
 <span data-ttu-id="13963-125">Čtení dat ze soketu klienta vyžaduje objekt stavu, který předává hodnoty mezi asynchronními voláními.</span><span class="sxs-lookup"><span data-stu-id="13963-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="13963-126">Následující příklad implementuje objekt stavu pro příjem řetězce ze vzdáleného klienta.</span><span class="sxs-lookup"><span data-stu-id="13963-126">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="13963-127">Obsahuje pole pro klientský soket, vyrovnávací paměť <xref:System.Text.StringBuilder> dat pro příjem dat a pro vytvoření datového řetězce odeslaného klientem.</span><span class="sxs-lookup"><span data-stu-id="13963-127">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="13963-128">Umístění těchto polí do objektu stavu umožňuje jejich hodnoty zachovat přes více volání číst data ze soketu klienta.</span><span class="sxs-lookup"><span data-stu-id="13963-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject
{  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 <span data-ttu-id="13963-129">Část `AcceptCallback` metody, která spustí příjem dat ze soketu klienta nejprve inicializuje instanci `StateObject` třídy a pak volá metodu <xref:System.Net.Sockets.Socket.BeginReceive%2A> začít číst data ze soketu klienta asynchronně.</span><span class="sxs-lookup"><span data-stu-id="13963-129">The section of the `AcceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="13963-130">Následující příklad ukazuje `AcceptCallback` úplnou metodu.</span><span class="sxs-lookup"><span data-stu-id="13963-130">The following example shows the complete `AcceptCallback` method.</span></span> <span data-ttu-id="13963-131">Předpokládá, že je globální **ManualResetEvent** s `StateObject` názvem, `allDone,` že třída `ReadCallback` je definována a `SocketListener`že metoda je definována ve třídě s názvem .</span><span class="sxs-lookup"><span data-stu-id="13963-131">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `ReadCallback` method is defined in a class named `SocketListener`.</span></span>  
  
```vb  
Public Shared Sub AcceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.ReadCallback, state)  
End Sub 'AcceptCallback  
```  
  
```csharp  
public static void AcceptCallback(IAsyncResult ar)
{  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.ReadCallback), state);  
}  
```  
  
 <span data-ttu-id="13963-132">Konečná metoda, která musí být implementována pro asynchronní soketový server je metoda zpětného volání pro čtení, která vrací data odeslaná klientem.</span><span class="sxs-lookup"><span data-stu-id="13963-132">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="13963-133">Stejně jako metoda přijetí zpětného volání je metoda zpětného volání pro čtení delegátem **AsyncCallback.**</span><span class="sxs-lookup"><span data-stu-id="13963-133">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="13963-134">Tato metoda přečte jeden nebo více bajtů ze soketu klienta do vyrovnávací paměti dat a pak znovu zavolá metodu **BeginReceive,** dokud nebudou data odeslaná klientem dokončena.</span><span class="sxs-lookup"><span data-stu-id="13963-134">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="13963-135">Po přečtení celé zprávy z klienta se řetězec zobrazí v konzole a soket serveru, který zpracovává připojení ke klientovi, je uzavřen.</span><span class="sxs-lookup"><span data-stu-id="13963-135">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="13963-136">Následující ukázka implementuje metodu. `ReadCallback`</span><span class="sxs-lookup"><span data-stu-id="13963-136">The following sample implements the `ReadCallback` method.</span></span> <span data-ttu-id="13963-137">Předpokládá, že `StateObject` třída je definována.</span><span class="sxs-lookup"><span data-stu-id="13963-137">It assumes that the `StateObject` class is defined.</span></span>  
  
```vb  
Public Shared Sub ReadCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReadCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine($"Read {content.Length} bytes from socket. {ControlChars.Cr} Data : {content}")  
        End If  
    End If  
End Sub 'ReadCallback  
```  
  
```csharp  
public static void ReadCallback(IAsyncResult ar)
{  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0)
    {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReadCallback), state);  
    }
    else
    {  
        if (state.sb.Length > 1)
        {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine($"Read {content.Length} bytes from socket.\n Data : {content}");
        }  
        handler.Close();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="13963-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="13963-138">See also</span></span>

- [<span data-ttu-id="13963-139">Použití synchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="13963-139">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="13963-140">Příklad asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="13963-140">Asynchronous Server Socket Example</span></span>](asynchronous-server-socket-example.md)
- [<span data-ttu-id="13963-141">Threading</span><span class="sxs-lookup"><span data-stu-id="13963-141">Threading</span></span>](../../standard/threading/index.md)
- [<span data-ttu-id="13963-142">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="13963-142">Listening with Sockets</span></span>](listening-with-sockets.md)
