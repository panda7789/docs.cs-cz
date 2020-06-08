---
title: Použití asynchronního serverového soketu
description: Tento příklad ukazuje soket asynchronního serveru. Třída Socket používá .NET Framework asynchronní programování ke zpracování požadavků síťových služeb.
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
ms.openlocfilehash: 8b85afb3ffdf69973eff37ccbb067b470ed44e3a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502025"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="e605c-104">Použití asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="e605c-104">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="e605c-105">Asynchronní serverové sokety používají .NET Framework asynchronní programovací model ke zpracování požadavků síťových služeb.</span><span class="sxs-lookup"><span data-stu-id="e605c-105">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="e605c-106"><xref:System.Net.Sockets.Socket>Třída následuje za standardním .NET Framework vzor asynchronního pojmenovávání; například synchronní <xref:System.Net.Sockets.Socket.Accept%2A> Metoda odpovídá asynchronním <xref:System.Net.Sockets.Socket.BeginAccept%2A> a <xref:System.Net.Sockets.Socket.EndAccept%2A> metodám.</span><span class="sxs-lookup"><span data-stu-id="e605c-106">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="e605c-107">Asynchronní serverový soket vyžaduje metodu pro zahájení přijímání požadavků na připojení ze sítě, metody zpětného volání pro zpracování žádostí o připojení a zahájení přijímání dat ze sítě a metody zpětného volání pro ukončení přijímání dat.</span><span class="sxs-lookup"><span data-stu-id="e605c-107">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="e605c-108">Všechny tyto metody jsou popsány dále v této části.</span><span class="sxs-lookup"><span data-stu-id="e605c-108">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="e605c-109">V následujícím příkladu, aby bylo možné začít přijímat žádosti o připojení ze sítě, `StartListening` inicializuje metoda **soket** a poté pomocí metody **BeginAccept** spustí přijímání nových připojení.</span><span class="sxs-lookup"><span data-stu-id="e605c-109">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="e605c-110">Metoda přijetí zpětného volání se volá, když se na soketu přijme nový požadavek na připojení.</span><span class="sxs-lookup"><span data-stu-id="e605c-110">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="e605c-111">Zodpovídá za získání instance **soketu** , která bude zpracovávat připojení a vydává tento **soket** do vlákna, které požadavek zpracuje.</span><span class="sxs-lookup"><span data-stu-id="e605c-111">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="e605c-112">Metoda Accept zpětného volání implementuje <xref:System.AsyncCallback> delegáta, vrátí void a přijímá jeden parametr typu <xref:System.IAsyncResult> .</span><span class="sxs-lookup"><span data-stu-id="e605c-112">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="e605c-113">V následujícím příkladu je prostředí metody přijetí zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="e605c-113">The following example is the shell of an accept callback method.</span></span>  
  
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
  
 <span data-ttu-id="e605c-114">Metoda **BeginAccept** přijímá dva parametry, delegáta **AsyncCallback** , který odkazuje na metodu přijetí zpětného volání, a objekt, který slouží k předávání informací o stavu metodě zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="e605c-114">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="e605c-115">V následujícím příkladu je naslouchající **soket** předán metodě zpětného volání prostřednictvím parametru *State* .</span><span class="sxs-lookup"><span data-stu-id="e605c-115">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="e605c-116">Tento příklad vytvoří delegáta **AsyncCallback** a začne přijímat připojení ze sítě.</span><span class="sxs-lookup"><span data-stu-id="e605c-116">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 <span data-ttu-id="e605c-117">Asynchronní sokety používají vlákna z fondu vláken systému ke zpracování příchozích připojení.</span><span class="sxs-lookup"><span data-stu-id="e605c-117">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="e605c-118">Jedno vlákno zodpovídá za příjem připojení, používá se jiné vlákno pro zpracování každého příchozího připojení a další vlákno zodpovídá za příjem dat z připojení.</span><span class="sxs-lookup"><span data-stu-id="e605c-118">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="e605c-119">Může se jednat o stejné vlákno v závislosti na tom, které vlákno je přiřazeno fondem vláken.</span><span class="sxs-lookup"><span data-stu-id="e605c-119">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="e605c-120">V následujícím příkladu <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Třída pozastaví provádění hlavního vlákna a signalizuje, když provádění může pokračovat.</span><span class="sxs-lookup"><span data-stu-id="e605c-120">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="e605c-121">Následující příklad ukazuje asynchronní metodu, která vytváří asynchronní soket TCP/IP v místním počítači a zahajuje přijímání připojení.</span><span class="sxs-lookup"><span data-stu-id="e605c-121">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="e605c-122">Předpokládá, že existuje globální **ManualResetEvent** s názvem `allDone` , že metoda je členem třídy s názvem `SocketListener` a že je definována metoda zpětného volání s názvem `AcceptCallback` .</span><span class="sxs-lookup"><span data-stu-id="e605c-122">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `AcceptCallback` is defined.</span></span>  
  
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
  
 <span data-ttu-id="e605c-123">Metoda přijetí zpětného volání ( `AcceptCallback` v předchozím příkladu) zodpovídá za signalizaci, že podproces hlavní aplikace pokračuje ve zpracování, navázání připojení k klientovi a spuštění asynchronního čtení dat z klienta.</span><span class="sxs-lookup"><span data-stu-id="e605c-123">The accept callback method (`AcceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="e605c-124">Následující příklad je první část implementace `AcceptCallback` metody.</span><span class="sxs-lookup"><span data-stu-id="e605c-124">The following example is the first part of an implementation of the `AcceptCallback` method.</span></span> <span data-ttu-id="e605c-125">Tato část metody signalizuje, že hlavní vlákno aplikace pokračuje ve zpracování a naváže připojení ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="e605c-125">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="e605c-126">Předpokládá globální **ManualResetEvent** s názvem `allDone` .</span><span class="sxs-lookup"><span data-stu-id="e605c-126">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
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
  
 <span data-ttu-id="e605c-127">Čtení dat z klientského soketu vyžaduje objekt stavu, který předává hodnoty mezi asynchronními voláními.</span><span class="sxs-lookup"><span data-stu-id="e605c-127">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="e605c-128">Následující příklad implementuje objekt state pro příjem řetězce ze vzdáleného klienta.</span><span class="sxs-lookup"><span data-stu-id="e605c-128">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="e605c-129">Obsahuje pole pro soket klienta, vyrovnávací paměť dat pro příjem dat a <xref:System.Text.StringBuilder> pro vytvoření datového řetězce odesílaného klientem.</span><span class="sxs-lookup"><span data-stu-id="e605c-129">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="e605c-130">Umístění těchto polí do objektu State umožňuje zachovat jejich hodnoty napříč více voláními pro čtení dat z soketu klienta.</span><span class="sxs-lookup"><span data-stu-id="e605c-130">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="e605c-131">Část `AcceptCallback` metody, která zahajuje příjem dat z soketu klienta, nejprve Inicializuje instanci `StateObject` třídy a pak zavolá <xref:System.Net.Sockets.Socket.BeginReceive%2A> metodu pro zahájení načítání dat z soketu klienta asynchronně.</span><span class="sxs-lookup"><span data-stu-id="e605c-131">The section of the `AcceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="e605c-132">Následující příklad ukazuje `AcceptCallback` metodu Complete.</span><span class="sxs-lookup"><span data-stu-id="e605c-132">The following example shows the complete `AcceptCallback` method.</span></span> <span data-ttu-id="e605c-133">Předpokládá, že existuje globální **ManualResetEvent** s názvem `allDone,` , že `StateObject` Třída je definována a že `ReadCallback` Metoda je definována ve třídě s názvem `SocketListener` .</span><span class="sxs-lookup"><span data-stu-id="e605c-133">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `ReadCallback` method is defined in a class named `SocketListener`.</span></span>  
  
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
  
 <span data-ttu-id="e605c-134">Poslední metodou, která se musí implementovat pro server asynchronního soketu, je metoda zpětného volání pro čtení, která vrací data odesílaná klientem.</span><span class="sxs-lookup"><span data-stu-id="e605c-134">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="e605c-135">Podobně jako metoda Accept zpětného volání je metoda zpětného volání pro čtení delegátem **AsyncCallback** .</span><span class="sxs-lookup"><span data-stu-id="e605c-135">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="e605c-136">Tato metoda přečte jeden nebo více bajtů z soketu klienta do vyrovnávací paměti dat a pak znovu zavolá metodu **BeginReceive** , dokud nebudou data odesílaná klientem dokončena.</span><span class="sxs-lookup"><span data-stu-id="e605c-136">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="e605c-137">Po načtení celé zprávy z klienta se řetězec zobrazí v konzole nástroje a soket serveru, který zpracovává připojení ke klientovi, je uzavřený.</span><span class="sxs-lookup"><span data-stu-id="e605c-137">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="e605c-138">Následující ukázka implementuje `ReadCallback` metodu.</span><span class="sxs-lookup"><span data-stu-id="e605c-138">The following sample implements the `ReadCallback` method.</span></span> <span data-ttu-id="e605c-139">Předpokládá, že `StateObject` je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="e605c-139">It assumes that the `StateObject` class is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e605c-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e605c-140">See also</span></span>

- [<span data-ttu-id="e605c-141">Použití synchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="e605c-141">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="e605c-142">Příklad asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="e605c-142">Asynchronous Server Socket Example</span></span>](asynchronous-server-socket-example.md)
- [<span data-ttu-id="e605c-143">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="e605c-143">Threading</span></span>](../../standard/threading/index.md)
- [<span data-ttu-id="e605c-144">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="e605c-144">Listening with Sockets</span></span>](listening-with-sockets.md)
