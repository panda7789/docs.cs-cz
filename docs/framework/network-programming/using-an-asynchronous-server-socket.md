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
ms.openlocfilehash: 32a2a99d5f71cb500dca467433f138a893d01e5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796816"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="fd216-102">Použití asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="fd216-102">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="fd216-103">Asynchronního serverového sokety používají asynchronní programovací model rozhraní .NET Framework pro zpracování žádostí o služby sítě.</span><span class="sxs-lookup"><span data-stu-id="fd216-103">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="fd216-104"><xref:System.Net.Sockets.Socket> Třídy vyplývá ze standardních rozhraní .NET Framework asynchronní vzor pro pojmenování; například synchronní <xref:System.Net.Sockets.Socket.Accept%2A> metoda odpovídá asynchronní <xref:System.Net.Sockets.Socket.BeginAccept%2A> a <xref:System.Net.Sockets.Socket.EndAccept%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fd216-104">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="fd216-105">Asynchronního serverového soketu vyžaduje metodu začít přijímat žádosti o připojení ze sítě, metody zpětného volání pro zpracování žádosti o připojení a začít přijímat data ze sítě a metody zpětného volání k ukončení přijímá data.</span><span class="sxs-lookup"><span data-stu-id="fd216-105">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="fd216-106">Všechny tyto metody jsou popsány dále v této části.</span><span class="sxs-lookup"><span data-stu-id="fd216-106">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="fd216-107">V následujícím příkladu, chcete-li začít přijímat žádosti o připojení ze sítě, metoda `StartListening` inicializuje **soketu** a použije je **BeginAccept** metoda začněte přijímat nové připojení.</span><span class="sxs-lookup"><span data-stu-id="fd216-107">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="fd216-108">Přijmout metoda zpětného volání je volána, když obdrží nový požadavek na připojení soketu.</span><span class="sxs-lookup"><span data-stu-id="fd216-108">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="fd216-109">Je zodpovědná za získání **soketu** instanci, která bude zpracovávat připojení a zpracování, která **soketu** vypnout na vlákno, které bude zpracovávat žádosti.</span><span class="sxs-lookup"><span data-stu-id="fd216-109">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="fd216-110">Implementuje metody zpětného volání přijmout <xref:System.AsyncCallback> delegovat; vrátí hodnotu typu void a přijímá jeden parametr typu <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="fd216-110">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="fd216-111">V následujícím příkladu je prostředí přijmout metody zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="fd216-111">The following example is the shell of an accept callback method.</span></span>  
  
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
  
 <span data-ttu-id="fd216-112">**BeginAccept** metoda přebírá dva parametry **AsyncCallback** delegáta, který odkazuje na metodu zpětného volání přijmout a objekt, který slouží k předávání informací o stavu metodě zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="fd216-112">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="fd216-113">V následujícím příkladu naslouchání **soketu** se předá metodě zpětného volání prostřednictvím *stavu* parametru.</span><span class="sxs-lookup"><span data-stu-id="fd216-113">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="fd216-114">Tento příklad vytvoří **AsyncCallback** delegáta a začne přijímat připojení ze sítě.</span><span class="sxs-lookup"><span data-stu-id="fd216-114">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 <span data-ttu-id="fd216-115">Asynchronní sokety používají podprocesy z fondu podprocesů systém ke zpracování příchozích připojení.</span><span class="sxs-lookup"><span data-stu-id="fd216-115">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="fd216-116">Jedno vlákno je zodpovědný za přijímat připojení, jiné vlákno se používá ke zpracování jednotlivých příchozí připojení a jiné vlákno zodpovídá za příjem dat z připojení.</span><span class="sxs-lookup"><span data-stu-id="fd216-116">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="fd216-117">To může být stejném vlákně, v závislosti na tom, které vlákno je přiřazeno ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="fd216-117">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="fd216-118">V následujícím příkladu <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> třídy pozastaví provádění z hlavního vlákna a signalizuje, že provádění může pokračovat.</span><span class="sxs-lookup"><span data-stu-id="fd216-118">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="fd216-119">Následující příklad ukazuje asynchronní metodu, která vytvoří asynchronní soket TCP/IP v místním počítači a začne přijímat připojení.</span><span class="sxs-lookup"><span data-stu-id="fd216-119">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="fd216-120">Předpokládá, že je globální **ManualResetEvent** s názvem `allDone`, že metoda je členem třídy s názvem `SocketListener`, a že s názvem metody zpětného volání `AcceptCallback` je definována.</span><span class="sxs-lookup"><span data-stu-id="fd216-120">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `AcceptCallback` is defined.</span></span>  
  
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
  
 <span data-ttu-id="fd216-121">Metoda zpětného volání přijmout (`AcceptCallback` v předchozím příkladu) zodpovídá za signalizace hlavního vlákna aplikace pokračovat zpracování, navazování připojení s klientem a spouští se asynchronní čtení dat z klienta.</span><span class="sxs-lookup"><span data-stu-id="fd216-121">The accept callback method (`AcceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="fd216-122">Následující příklad je první část implementace `AcceptCallback` metody.</span><span class="sxs-lookup"><span data-stu-id="fd216-122">The following example is the first part of an implementation of the `AcceptCallback` method.</span></span> <span data-ttu-id="fd216-123">Tato část metody signály hlavního vlákna aplikace chcete pokračovat ve zpracování a naváže připojení ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="fd216-123">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="fd216-124">Předpokládá globální **ManualResetEvent** s názvem `allDone`.</span><span class="sxs-lookup"><span data-stu-id="fd216-124">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
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
  
 <span data-ttu-id="fd216-125">Čtení dat z klientského soketu vyžaduje stav objektu, který předává hodnoty mezi byla zahájena asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="fd216-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="fd216-126">Následující příklad implementuje objekt stavu pro příjem řetězec ze vzdáleného klienta.</span><span class="sxs-lookup"><span data-stu-id="fd216-126">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="fd216-127">Obsahuje pole pro klientského soketu dat vyrovnávací paměti pro příjem dat a <xref:System.Text.StringBuilder> pro vytvoření řetězce data odesílaném klientem.</span><span class="sxs-lookup"><span data-stu-id="fd216-127">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="fd216-128">Umístění těchto polí v objektu stavu umožňuje jejich hodnot zachovaná napříč více volání na čtení dat z klientského soketu.</span><span class="sxs-lookup"><span data-stu-id="fd216-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="fd216-129">Část `AcceptCallback` metodu, která začne dostávat data z klientského soketu nejprve inicializuje novou instanci `StateObject` třídy a poté zavolá <xref:System.Net.Sockets.Socket.BeginReceive%2A> metoda začne asynchronně číst data z klientského soketu.</span><span class="sxs-lookup"><span data-stu-id="fd216-129">The section of the `AcceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="fd216-130">Následující příklad ukazuje kompletní `AcceptCallback` metody.</span><span class="sxs-lookup"><span data-stu-id="fd216-130">The following example shows the complete `AcceptCallback` method.</span></span> <span data-ttu-id="fd216-131">Předpokládá, že je globální **ManualResetEvent** s názvem `allDone,` , který `StateObject` třída je definována a že `ReadCallback` je definována metoda v třídě s názvem `SocketListener`.</span><span class="sxs-lookup"><span data-stu-id="fd216-131">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `ReadCallback` method is defined in a class named `SocketListener`.</span></span>  
  
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
  
 <span data-ttu-id="fd216-132">Poslední metodu, kterou je potřeba implementovat pro server websocket asynchronní je metoda čtení zpětného volání, která vrací data odeslaná klientem.</span><span class="sxs-lookup"><span data-stu-id="fd216-132">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="fd216-133">Podobně jako metody zpětného volání přijmout, je metoda zpětného volání pro čtení **AsyncCallback** delegovat.</span><span class="sxs-lookup"><span data-stu-id="fd216-133">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="fd216-134">Tato metoda načte jeden nebo více bajtů z klientského soketu do vyrovnávací paměti dat a pak zavolá **BeginReceive** metoda znovu, dokud data odeslaná klientem je dokončena.</span><span class="sxs-lookup"><span data-stu-id="fd216-134">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="fd216-135">Po celá zpráva byla přečtena z klienta, řetězec se zobrazí v konzole a zavření serverového soketu zpracování připojení ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="fd216-135">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="fd216-136">Následující ukázkový implementuje `ReadCallback` metody.</span><span class="sxs-lookup"><span data-stu-id="fd216-136">The following sample implements the `ReadCallback` method.</span></span> <span data-ttu-id="fd216-137">Předpokládá, `StateObject` třída je definována.</span><span class="sxs-lookup"><span data-stu-id="fd216-137">It assumes that the `StateObject` class is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd216-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd216-138">See also</span></span>

- [<span data-ttu-id="fd216-139">Použití synchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="fd216-139">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)
- [<span data-ttu-id="fd216-140">Příklad asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="fd216-140">Asynchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)
- [<span data-ttu-id="fd216-141">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="fd216-141">Threading</span></span>](../../../docs/standard/threading/index.md)
- [<span data-ttu-id="fd216-142">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="fd216-142">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
