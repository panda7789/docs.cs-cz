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
ms.openlocfilehash: 11ed53a4e51ba6993fd4e240116b0e1de910a01e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047051"
---
# <a name="using-an-asynchronous-server-socket"></a>Použití asynchronního serverového soketu
Asynchronní serverové sokety používají .NET Framework asynchronní programovací model ke zpracování požadavků síťových služeb. Třída následuje za standardním .NET Framework vzor asynchronního pojmenovávání; například synchronní <xref:System.Net.Sockets.Socket.Accept%2A> Metoda odpovídá asynchronním <xref:System.Net.Sockets.Socket.BeginAccept%2A> a <xref:System.Net.Sockets.Socket.EndAccept%2A> metodám. <xref:System.Net.Sockets.Socket>  
  
 Asynchronní serverový soket vyžaduje metodu pro zahájení přijímání požadavků na připojení ze sítě, metody zpětného volání pro zpracování žádostí o připojení a zahájení přijímání dat ze sítě a metody zpětného volání pro ukončení přijímání dat. Všechny tyto metody jsou popsány dále v této části.  
  
 V následujícím příkladu, aby bylo možné začít přijímat žádosti o připojení ze sítě, inicializuje `StartListening` metoda **soket** a poté pomocí metody **BeginAccept** spustí přijímání nových připojení. Metoda přijetí zpětného volání se volá, když se na soketu přijme nový požadavek na připojení. Zodpovídá za získání instance **soketu** , která bude zpracovávat připojení a vydává tento **soket** do vlákna, které požadavek zpracuje. Metoda Accept zpětného volání implementuje <xref:System.AsyncCallback> delegáta, vrátí void a přijímá jeden parametr typu <xref:System.IAsyncResult>. V následujícím příkladu je prostředí metody přijetí zpětného volání.  
  
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
  
 Metoda **BeginAccept** přijímá dva parametry, delegáta **AsyncCallback** , který odkazuje na metodu přijetí zpětného volání, a objekt, který slouží k předávání informací o stavu metodě zpětného volání. V následujícím příkladu je naslouchající **soket** předán metodě zpětného volání prostřednictvím parametru *State* . Tento příklad vytvoří delegáta **AsyncCallback** a začne přijímat připojení ze sítě.  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 Asynchronní sokety používají vlákna z fondu vláken systému ke zpracování příchozích připojení. Jedno vlákno zodpovídá za příjem připojení, používá se jiné vlákno pro zpracování každého příchozího připojení a další vlákno zodpovídá za příjem dat z připojení. Může se jednat o stejné vlákno v závislosti na tom, které vlákno je přiřazeno fondem vláken. V následujícím příkladu <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> třída pozastaví provádění hlavního vlákna a signalizuje, když provádění může pokračovat.  
  
 Následující příklad ukazuje asynchronní metodu, která vytváří asynchronní soket TCP/IP v místním počítači a zahajuje přijímání připojení. Předpokládá, že existuje globální **ManualResetEvent** s názvem `allDone`, že metoda je členem třídy s názvem `SocketListener`a že je definována metoda zpětného volání s názvem `AcceptCallback` .  
  
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
  
 Metoda přijetí zpětného volání`AcceptCallback` (v předchozím příkladu) zodpovídá za signalizaci, že podproces hlavní aplikace pokračuje ve zpracování, navázání připojení k klientovi a spuštění asynchronního čtení dat z klienta. Následující příklad je první část implementace `AcceptCallback` metody. Tato část metody signalizuje, že hlavní vlákno aplikace pokračuje ve zpracování a naváže připojení ke klientovi. Předpokládá globální **ManualResetEvent** s názvem `allDone`.  
  
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
  
 Čtení dat z klientského soketu vyžaduje objekt stavu, který předává hodnoty mezi asynchronními voláními. Následující příklad implementuje objekt state pro příjem řetězce ze vzdáleného klienta. Obsahuje pole pro soket klienta, vyrovnávací paměť dat pro příjem dat a <xref:System.Text.StringBuilder> pro vytvoření datového řetězce odesílaného klientem. Umístění těchto polí do objektu State umožňuje zachovat jejich hodnoty napříč více voláními pro čtení dat z soketu klienta.  
  
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
  
 Část `AcceptCallback` metody, která zahajuje příjem dat z soketu klienta, nejprve Inicializuje instanci `StateObject` <xref:System.Net.Sockets.Socket.BeginReceive%2A> třídy a pak zavolá metodu pro zahájení načítání dat z soketu klienta asynchronně.  
  
 Následující příklad ukazuje metodu Complete `AcceptCallback` . Předpokládá, že existuje globální **ManualResetEvent** s `allDone,` názvem, že `StateObject` `ReadCallback` třída je definována a že metoda je definována ve třídě s názvem `SocketListener`.  
  
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
  
 Poslední metodou, která se musí implementovat pro server asynchronního soketu, je metoda zpětného volání pro čtení, která vrací data odesílaná klientem. Podobně jako metoda Accept zpětného volání je metoda zpětného volání pro čtení delegátem **AsyncCallback** . Tato metoda přečte jeden nebo více bajtů z soketu klienta do vyrovnávací paměti dat a pak znovu zavolá metodu **BeginReceive** , dokud nebudou data odesílaná klientem dokončena. Po načtení celé zprávy z klienta se řetězec zobrazí v konzole nástroje a soket serveru, který zpracovává připojení ke klientovi, je uzavřený.  
  
 Následující ukázka implementuje `ReadCallback` metodu. Předpokládá, že `StateObject` je třída definovaná.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Použití synchronního serverového soketu](using-a-synchronous-server-socket.md)
- [Příklad asynchronního serverového soketu](asynchronous-server-socket-example.md)
- [Dělení na vlákna](../../standard/threading/index.md)
- [Naslouchání pomocí soketů](listening-with-sockets.md)
