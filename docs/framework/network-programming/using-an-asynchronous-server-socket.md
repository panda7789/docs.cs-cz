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
# <a name="using-an-asynchronous-server-socket"></a>Použití asynchronního serverového soketu
Sokety asynchronních serverů používají ke zpracování požadavků na síťové služby asynchronní programovací model rozhraní .NET Framework. Třída <xref:System.Net.Sockets.Socket> se řídí standardním vzorem asynchronního pojmenování rozhraní .NET Framework. například synchronní <xref:System.Net.Sockets.Socket.Accept%2A> metoda odpovídá asynchronní <xref:System.Net.Sockets.Socket.BeginAccept%2A> a <xref:System.Net.Sockets.Socket.EndAccept%2A> metody.  
  
 Soket asynchronního serveru vyžaduje metodu pro zahájení přijímání požadavků na připojení ze sítě, metodu zpětného volání pro zpracování požadavků na připojení a zahájení příjmu dat ze sítě a metodu zpětného volání pro ukončení příjmu dat. Všechny tyto metody jsou podrobně popsány v této části.  
  
 V následujícím příkladu, chcete-li začít přijímat požadavky `StartListening` na připojení ze sítě, metoda inicializuje **Socket** a pak používá **BeginAccept** metoda začít přijímat nová připojení. Metoda zpětného volání přijetí je volána při přijetí nového požadavku na připojení na soketu. Je zodpovědný za získání **Socket** instance, která bude zpracovávat připojení a **předání,** které Socket off do vlákna, které bude zpracovávat požadavek. Metoda přijetí zpětného volání <xref:System.AsyncCallback> implementuje delegáta; vrátí void a vezme jeden parametr <xref:System.IAsyncResult>typu . Následující příklad je prostředí metody přijetí zpětného volání.  
  
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
  
 Metoda **BeginAccept** přebírá dva parametry, **delegáta AsyncCallback,** který odkazuje na metodu zpětného volání přijmout a objekt, který se používá k předání informací o stavu metodě zpětného volání. V následujícím příkladu **naslouchání Socket** je předán metodu zpětného volání prostřednictvím parametru *state.* Tento příklad vytvoří **delegáta AsyncCallback** a začne přijímat připojení ze sítě.  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 Asynchronní sokety používají vlákna z fondu systémových vláken ke zpracování příchozích připojení. Jedno vlákno je zodpovědné za přijímání připojení, jiné vlákno se používá ke zpracování každého příchozího připojení a jiné vlákno je zodpovědné za příjem dat z připojení. Může se jedná o stejné vlákno v závislosti na tom, které vlákno je přiřazeno fondu vláken. V následujícím příkladu <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> třída pozastaví provádění hlavního vlákna a signály při provádění může pokračovat.  
  
 Následující příklad ukazuje asynchronní metodu, která vytvoří asynchronní soket TCP/IP v místním počítači a začne přijímat připojení. Předpokládá, že je globální **ManualResetEvent** s názvem `allDone`, že metoda `SocketListener`je členem třídy s `AcceptCallback` názvem , a že je definována metoda zpětného volání s názvem.  
  
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
  
 Metoda zpětného volání`AcceptCallback` přijmout ( v předchozím příkladu) je zodpovědná za signalizaci hlavního vlákna aplikace pro pokračování ve zpracování, navázání připojení s klientem a spuštění asynchronního čtení dat z klienta. Následující příklad je první část implementace `AcceptCallback` metody. Tato část metody signalizuje hlavní vlákno aplikace pokračovat ve zpracování a naváže připojení ke klientovi. Předpokládá globální **ManualResetEvent** s `allDone`názvem .  
  
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
  
 Čtení dat ze soketu klienta vyžaduje objekt stavu, který předává hodnoty mezi asynchronními voláními. Následující příklad implementuje objekt stavu pro příjem řetězce ze vzdáleného klienta. Obsahuje pole pro klientský soket, vyrovnávací paměť <xref:System.Text.StringBuilder> dat pro příjem dat a pro vytvoření datového řetězce odeslaného klientem. Umístění těchto polí do objektu stavu umožňuje jejich hodnoty zachovat přes více volání číst data ze soketu klienta.  
  
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
  
 Část `AcceptCallback` metody, která spustí příjem dat ze soketu klienta nejprve inicializuje instanci `StateObject` třídy a pak volá metodu <xref:System.Net.Sockets.Socket.BeginReceive%2A> začít číst data ze soketu klienta asynchronně.  
  
 Následující příklad ukazuje `AcceptCallback` úplnou metodu. Předpokládá, že je globální **ManualResetEvent** s `StateObject` názvem, `allDone,` že třída `ReadCallback` je definována a `SocketListener`že metoda je definována ve třídě s názvem .  
  
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
  
 Konečná metoda, která musí být implementována pro asynchronní soketový server je metoda zpětného volání pro čtení, která vrací data odeslaná klientem. Stejně jako metoda přijetí zpětného volání je metoda zpětného volání pro čtení delegátem **AsyncCallback.** Tato metoda přečte jeden nebo více bajtů ze soketu klienta do vyrovnávací paměti dat a pak znovu zavolá metodu **BeginReceive,** dokud nebudou data odeslaná klientem dokončena. Po přečtení celé zprávy z klienta se řetězec zobrazí v konzole a soket serveru, který zpracovává připojení ke klientovi, je uzavřen.  
  
 Následující ukázka implementuje metodu. `ReadCallback` Předpokládá, že `StateObject` třída je definována.  
  
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
  
## <a name="see-also"></a>Viz také

- [Použití synchronního serverového soketu](using-a-synchronous-server-socket.md)
- [Příklad asynchronního serverového soketu](asynchronous-server-socket-example.md)
- [Threading](../../standard/threading/index.md)
- [Naslouchání pomocí soketů](listening-with-sockets.md)
