---
title: Pomocí soketu asynchronní serveru
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ad52291f5f5f40a65d2f9ec1c07bfb3a3f39fc01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396604"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="47c7a-102">Pomocí soketu asynchronní serveru</span><span class="sxs-lookup"><span data-stu-id="47c7a-102">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="47c7a-103">Asynchronní serveru sockets používat asynchronní programovací model rozhraní .NET Framework ke zpracování žádosti o služby sítě.</span><span class="sxs-lookup"><span data-stu-id="47c7a-103">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="47c7a-104"><xref:System.Net.Sockets.Socket> Třída dodržovat standardní rozhraní .NET Framework asynchronního vzoru pro pojmenovávání; například synchronní <xref:System.Net.Sockets.Socket.Accept%2A> metoda odpovídá asynchronní <xref:System.Net.Sockets.Socket.BeginAccept%2A> a <xref:System.Net.Sockets.Socket.EndAccept%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="47c7a-104">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="47c7a-105">Soketu asynchronní server vyžaduje metodu Chcete-li začít přijímat žádosti o připojení ze sítě, metody zpětného volání zpracovat žádosti o připojení a začněte příjem dat ze sítě a metody zpětného volání pro ukončení přijímá data.</span><span class="sxs-lookup"><span data-stu-id="47c7a-105">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="47c7a-106">Všechny tyto metody jsou popsané dále v této části.</span><span class="sxs-lookup"><span data-stu-id="47c7a-106">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="47c7a-107">V následujícím příkladu, chcete-li začít přijímat žádosti o připojení ze sítě, metoda `StartListening` inicializuje **soketu** a použije je **BeginAccept** metoda zahájíte přijetí nové připojení.</span><span class="sxs-lookup"><span data-stu-id="47c7a-107">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="47c7a-108">Metoda zpětného volání přijmout je volána, když obdrží žádost o nové připojení soketu.</span><span class="sxs-lookup"><span data-stu-id="47c7a-108">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="47c7a-109">Zodpovídá za načítání **soketu** instanci, která bude zpracovávat připojení a zjistit, který blokováním **soketu** vypnout vláken, která zpracuje požadavek.</span><span class="sxs-lookup"><span data-stu-id="47c7a-109">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="47c7a-110">Implementuje metody zpětného volání přijmout <xref:System.AsyncCallback> delegovat; se vrátí void a přijímá jeden parametr typu <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="47c7a-110">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="47c7a-111">V následujícím příkladu je prostředí metody zpětného volání přijmout.</span><span class="sxs-lookup"><span data-stu-id="47c7a-111">The following example is the shell of an accept callback method.</span></span>  
  
```vb  
Sub acceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'acceptCallback  
```  
  
```csharp  
void acceptCallback( IAsyncResult ar) {  
    // Add the callback code here.  
}  
```  
  
 <span data-ttu-id="47c7a-112">**BeginAccept** metoda přebírá dva parametry **AsyncCallback** delegáta, který odkazuje na metodu zpětného volání přijmout a objekt, který slouží k předávání informací o stavu do metoda zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="47c7a-112">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="47c7a-113">V následujícím příkladu naslouchání **soketu** předaný metoda zpětného volání prostřednictvím *stavu* parametr.</span><span class="sxs-lookup"><span data-stu-id="47c7a-113">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="47c7a-114">Tento příklad vytvoří **AsyncCallback** delegáta a začne přijímat připojení ze sítě.</span><span class="sxs-lookup"><span data-stu-id="47c7a-114">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.acceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(  
    new AsyncCallback(SocketListener.acceptCallback),   
    listener);  
```  
  
 <span data-ttu-id="47c7a-115">Asynchronní sockets používat vláken z fondu podprocesů systému ke zpracování příchozích připojení.</span><span class="sxs-lookup"><span data-stu-id="47c7a-115">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="47c7a-116">Jedno vlákno je zodpovědná za přijímat připojení, další vlákno použitý pro zpracování každé příchozí připojení a jiné vlákno je zodpovědná za přijetí dat z připojení.</span><span class="sxs-lookup"><span data-stu-id="47c7a-116">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="47c7a-117">Může jít o stejném vlákně, v závislosti na tom, který je přiřazen přístup z více vláken ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="47c7a-117">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="47c7a-118">V následujícím příkladu <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> třídy pozastaví spuštění hlavního vlákna a signalizuje, že můžete pokračovat v provádění.</span><span class="sxs-lookup"><span data-stu-id="47c7a-118">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="47c7a-119">Následující příklad ukazuje asynchronní metodu, která vytvoří asynchronní soketu TCP/IP v místním počítači a začne přijímat připojení.</span><span class="sxs-lookup"><span data-stu-id="47c7a-119">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="47c7a-120">Předpokládá, že je globální konfiguraci **ManualResetEvent** s názvem `allDone`, že metoda je členem třídy s názvem `SocketListener`, a že s názvem metody zpětného volání `acceptCallback` je definována.</span><span class="sxs-lookup"><span data-stu-id="47c7a-120">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `acceptCallback` is defined.</span></span>  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine("Local address and port : {0}", localEP.ToString())  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.acceptCallback), _  
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
public void StartListening() {  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0],11000);  
  
    Console.WriteLine("Local address and port : {0}",localEP.ToString());  
  
    Socket listener = new Socket( localEP.Address.AddressFamily,  
        SocketType.Stream, ProtocolType.Tcp );  
  
    try {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true) {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(  
                new AsyncCallback(SocketListener.acceptCallback),   
                listener );  
  
            allDone.WaitOne();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine( "Closing the listener...");  
}  
```  
  
 <span data-ttu-id="47c7a-121">Metoda zpětného volání přijmout (`acceptCallback` v předchozím příkladu) zodpovídá za hlavní vlákno aplikace pokračovat zpracování navazování připojení ke klientovi a spouští asynchronní signalizace pro čtení dat z klienta.</span><span class="sxs-lookup"><span data-stu-id="47c7a-121">The accept callback method (`acceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="47c7a-122">V následujícím příkladu je první část implementace `acceptCallback` metoda.</span><span class="sxs-lookup"><span data-stu-id="47c7a-122">The following example is the first part of an implementation of the `acceptCallback` method.</span></span> <span data-ttu-id="47c7a-123">Tato část metody signály hlavní vlákno aplikace pokračovat zpracování a vytvoří připojení ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="47c7a-123">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="47c7a-124">Předpokládá globální konfiguraci **ManualResetEvent** s názvem `allDone`.</span><span class="sxs-lookup"><span data-stu-id="47c7a-124">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
```vb  
Public Sub acceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'acceptCallback  
```  
  
```csharp  
public void acceptCallback(IAsyncResult ar) {  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.    
}  
```  
  
 <span data-ttu-id="47c7a-125">Čtení dat ze soketu klienta vyžaduje objekt stavu, který předává hodnoty mezi asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="47c7a-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="47c7a-126">Následující příklad implementuje objekt stavu pro příjem řetězec ze vzdáleného klienta.</span><span class="sxs-lookup"><span data-stu-id="47c7a-126">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="47c7a-127">Obsahuje pole pro Soket klienta, vyrovnávací paměť dat pro příjem dat a <xref:System.Text.StringBuilder> pro vytváření dat řetězec odesílaný klientem.</span><span class="sxs-lookup"><span data-stu-id="47c7a-127">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="47c7a-128">Uvedení těchto polí objekt stavu umožňuje jejich hodnoty nutné zachovat napříč více volání čtení dat ze soketu klienta.</span><span class="sxs-lookup"><span data-stu-id="47c7a-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 <span data-ttu-id="47c7a-129">Části `acceptCallback` metoda, která spustí příjem dat ze soketu klienta nejprve inicializuje instanci `StateObject` třídy a pak volání <xref:System.Net.Sockets.Socket.BeginReceive%2A> metoda zahájíte asynchronnímu čtení dat ze soketu klienta.</span><span class="sxs-lookup"><span data-stu-id="47c7a-129">The section of the `acceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="47c7a-130">Následující příklad ukazuje kompletní `acceptCallback` metoda.</span><span class="sxs-lookup"><span data-stu-id="47c7a-130">The following example shows the complete `acceptCallback` method.</span></span> <span data-ttu-id="47c7a-131">Předpokládá, že je globální konfiguraci **ManualResetEvent** s názvem `allDone,` , `StateObject` třída definována a že `readCallback` metoda je definována v třídy s názvem `SocketListener`.</span><span class="sxs-lookup"><span data-stu-id="47c7a-131">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `readCallback` method is defined in a class named `SocketListener`.</span></span>  
  
```vb  
Public Shared Sub acceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.readCallback, state)  
End Sub 'acceptCallback  
```  
  
```csharp  
public static void acceptCallback(IAsyncResult ar) {  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.readCallback), state);  
}  
```  
  
 <span data-ttu-id="47c7a-132">Poslední metodu, kterou je nutné implementovat pro server asynchronní soketu je metoda zpětného volání pro čtení, která vrací data odeslaná klientem.</span><span class="sxs-lookup"><span data-stu-id="47c7a-132">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="47c7a-133">Jako metody zpětného volání přijmout, je metoda zpětného volání pro čtení **AsyncCallback** delegovat.</span><span class="sxs-lookup"><span data-stu-id="47c7a-133">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="47c7a-134">Tato metoda čte bajtů jeden nebo více z klienta soketů do vyrovnávací paměti dat a pak zavolá **BeginReceive** metoda znovu, dokud data odeslaná klientem je dokončena.</span><span class="sxs-lookup"><span data-stu-id="47c7a-134">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="47c7a-135">Po celé zprávy byl načten z klienta, řetězec se zobrazí v konzole a server soketu zpracování připojení ke klientovi je uzavřený.</span><span class="sxs-lookup"><span data-stu-id="47c7a-135">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="47c7a-136">Následující ukázkové implementuje `readCallback` metoda.</span><span class="sxs-lookup"><span data-stu-id="47c7a-136">The following sample implements the `readCallback` method.</span></span> <span data-ttu-id="47c7a-137">Předpokládá, že `StateObject` třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="47c7a-137">It assumes that the `StateObject` class is defined.</span></span>  
  
```vb  
Public Shared Sub readCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.   
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf readCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine("Read {0} bytes from socket." + _  
                ControlChars.Cr + " Data : {1}", content.Length, content)  
        End If  
    End If  
End Sub 'readCallback  
```  
  
```csharp  
public static void readCallback(IAsyncResult ar) {  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0) {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer,0,StateObject.BufferSize, 0,  
            new AsyncCallback(readCallback), state);  
    } else {  
        if (state.sb.Length > 1) {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine("Read {0} bytes from socket.\n Data : {1}",  
               content.Length, content);  
        }  
        handler.Close();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="47c7a-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="47c7a-138">See Also</span></span>  
 [<span data-ttu-id="47c7a-139">Použití synchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="47c7a-139">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [<span data-ttu-id="47c7a-140">Příklad asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="47c7a-140">Asynchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)  
 [<span data-ttu-id="47c7a-141">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="47c7a-141">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="47c7a-142">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="47c7a-142">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
