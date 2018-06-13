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
# <a name="using-an-asynchronous-server-socket"></a>Pomocí soketu asynchronní serveru
Asynchronní serveru sockets používat asynchronní programovací model rozhraní .NET Framework ke zpracování žádosti o služby sítě. <xref:System.Net.Sockets.Socket> Třída dodržovat standardní rozhraní .NET Framework asynchronního vzoru pro pojmenovávání; například synchronní <xref:System.Net.Sockets.Socket.Accept%2A> metoda odpovídá asynchronní <xref:System.Net.Sockets.Socket.BeginAccept%2A> a <xref:System.Net.Sockets.Socket.EndAccept%2A> metody.  
  
 Soketu asynchronní server vyžaduje metodu Chcete-li začít přijímat žádosti o připojení ze sítě, metody zpětného volání zpracovat žádosti o připojení a začněte příjem dat ze sítě a metody zpětného volání pro ukončení přijímá data. Všechny tyto metody jsou popsané dále v této části.  
  
 V následujícím příkladu, chcete-li začít přijímat žádosti o připojení ze sítě, metoda `StartListening` inicializuje **soketu** a použije je **BeginAccept** metoda zahájíte přijetí nové připojení. Metoda zpětného volání přijmout je volána, když obdrží žádost o nové připojení soketu. Zodpovídá za načítání **soketu** instanci, která bude zpracovávat připojení a zjistit, který blokováním **soketu** vypnout vláken, která zpracuje požadavek. Implementuje metody zpětného volání přijmout <xref:System.AsyncCallback> delegovat; se vrátí void a přijímá jeden parametr typu <xref:System.IAsyncResult>. V následujícím příkladu je prostředí metody zpětného volání přijmout.  
  
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
  
 **BeginAccept** metoda přebírá dva parametry **AsyncCallback** delegáta, který odkazuje na metodu zpětného volání přijmout a objekt, který slouží k předávání informací o stavu do metoda zpětného volání. V následujícím příkladu naslouchání **soketu** předaný metoda zpětného volání prostřednictvím *stavu* parametr. Tento příklad vytvoří **AsyncCallback** delegáta a začne přijímat připojení ze sítě.  
  
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
  
 Asynchronní sockets používat vláken z fondu podprocesů systému ke zpracování příchozích připojení. Jedno vlákno je zodpovědná za přijímat připojení, další vlákno použitý pro zpracování každé příchozí připojení a jiné vlákno je zodpovědná za přijetí dat z připojení. Může jít o stejném vlákně, v závislosti na tom, který je přiřazen přístup z více vláken ve fondu vláken. V následujícím příkladu <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> třídy pozastaví spuštění hlavního vlákna a signalizuje, že můžete pokračovat v provádění.  
  
 Následující příklad ukazuje asynchronní metodu, která vytvoří asynchronní soketu TCP/IP v místním počítači a začne přijímat připojení. Předpokládá, že je globální konfiguraci **ManualResetEvent** s názvem `allDone`, že metoda je členem třídy s názvem `SocketListener`, a že s názvem metody zpětného volání `acceptCallback` je definována.  
  
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
  
 Metoda zpětného volání přijmout (`acceptCallback` v předchozím příkladu) zodpovídá za hlavní vlákno aplikace pokračovat zpracování navazování připojení ke klientovi a spouští asynchronní signalizace pro čtení dat z klienta. V následujícím příkladu je první část implementace `acceptCallback` metoda. Tato část metody signály hlavní vlákno aplikace pokračovat zpracování a vytvoří připojení ke klientovi. Předpokládá globální konfiguraci **ManualResetEvent** s názvem `allDone`.  
  
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
  
 Čtení dat ze soketu klienta vyžaduje objekt stavu, který předává hodnoty mezi asynchronní volání. Následující příklad implementuje objekt stavu pro příjem řetězec ze vzdáleného klienta. Obsahuje pole pro Soket klienta, vyrovnávací paměť dat pro příjem dat a <xref:System.Text.StringBuilder> pro vytváření dat řetězec odesílaný klientem. Uvedení těchto polí objekt stavu umožňuje jejich hodnoty nutné zachovat napříč více volání čtení dat ze soketu klienta.  
  
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
  
 Části `acceptCallback` metoda, která spustí příjem dat ze soketu klienta nejprve inicializuje instanci `StateObject` třídy a pak volání <xref:System.Net.Sockets.Socket.BeginReceive%2A> metoda zahájíte asynchronnímu čtení dat ze soketu klienta.  
  
 Následující příklad ukazuje kompletní `acceptCallback` metoda. Předpokládá, že je globální konfiguraci **ManualResetEvent** s názvem `allDone,` , `StateObject` třída definována a že `readCallback` metoda je definována v třídy s názvem `SocketListener`.  
  
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
  
 Poslední metodu, kterou je nutné implementovat pro server asynchronní soketu je metoda zpětného volání pro čtení, která vrací data odeslaná klientem. Jako metody zpětného volání přijmout, je metoda zpětného volání pro čtení **AsyncCallback** delegovat. Tato metoda čte bajtů jeden nebo více z klienta soketů do vyrovnávací paměti dat a pak zavolá **BeginReceive** metoda znovu, dokud data odeslaná klientem je dokončena. Po celé zprávy byl načten z klienta, řetězec se zobrazí v konzole a server soketu zpracování připojení ke klientovi je uzavřený.  
  
 Následující ukázkové implementuje `readCallback` metoda. Předpokládá, že `StateObject` třída definovaná.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Použití synchronního serverového soketu](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [Příklad asynchronního serverového soketu](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)  
 [Dělení na vlákna](../../../docs/standard/threading/index.md)  
 [Naslouchání pomocí soketů](../../../docs/framework/network-programming/listening-with-sockets.md)
