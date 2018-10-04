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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f89bf9e3ea9f2b3c385d267cfc77a05ee8eb82d6
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266413"
---
# <a name="using-an-asynchronous-server-socket"></a>Použití asynchronního serverového soketu
Asynchronního serverového sokety používají asynchronní programovací model rozhraní .NET Framework pro zpracování žádostí o služby sítě. <xref:System.Net.Sockets.Socket> Třídy vyplývá ze standardních rozhraní .NET Framework asynchronní vzor pro pojmenování; například synchronní <xref:System.Net.Sockets.Socket.Accept%2A> metoda odpovídá asynchronní <xref:System.Net.Sockets.Socket.BeginAccept%2A> a <xref:System.Net.Sockets.Socket.EndAccept%2A> metody.  
  
 Asynchronního serverového soketu vyžaduje metodu začít přijímat žádosti o připojení ze sítě, metody zpětného volání pro zpracování žádosti o připojení a začít přijímat data ze sítě a metody zpětného volání k ukončení přijímá data. Všechny tyto metody jsou popsány dále v této části.  
  
 V následujícím příkladu, chcete-li začít přijímat žádosti o připojení ze sítě, metoda `StartListening` inicializuje **soketu** a použije je **BeginAccept** metoda začněte přijímat nové připojení. Přijmout metoda zpětného volání je volána, když obdrží nový požadavek na připojení soketu. Je zodpovědná za získání **soketu** instanci, která bude zpracovávat připojení a zpracování, která **soketu** vypnout na vlákno, které bude zpracovávat žádosti. Implementuje metody zpětného volání přijmout <xref:System.AsyncCallback> delegovat; vrátí hodnotu typu void a přijímá jeden parametr typu <xref:System.IAsyncResult>. V následujícím příkladu je prostředí přijmout metody zpětného volání.  
  
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
  
 **BeginAccept** metoda přebírá dva parametry **AsyncCallback** delegáta, který odkazuje na metodu zpětného volání přijmout a objekt, který slouží k předávání informací o stavu metodě zpětného volání. V následujícím příkladu naslouchání **soketu** se předá metodě zpětného volání prostřednictvím *stavu* parametru. Tento příklad vytvoří **AsyncCallback** delegáta a začne přijímat připojení ze sítě.  
  
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
  
 Asynchronní sokety používají podprocesy z fondu podprocesů systém ke zpracování příchozích připojení. Jedno vlákno je zodpovědný za přijímat připojení, jiné vlákno se používá ke zpracování jednotlivých příchozí připojení a jiné vlákno zodpovídá za příjem dat z připojení. To může být stejném vlákně, v závislosti na tom, které vlákno je přiřazeno ve fondu vláken. V následujícím příkladu <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> třídy pozastaví provádění z hlavního vlákna a signalizuje, že provádění může pokračovat.  
  
 Následující příklad ukazuje asynchronní metodu, která vytvoří asynchronní soket TCP/IP v místním počítači a začne přijímat připojení. Předpokládá, že je globální **ManualResetEvent** s názvem `allDone`, že metoda je členem třídy s názvem `SocketListener`, a že s názvem metody zpětného volání `acceptCallback` je definována.  
  
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
  
 Metoda zpětného volání přijmout (`acceptCallback` v předchozím příkladu) zodpovídá za signalizace hlavního vlákna aplikace pokračovat zpracování, navazování připojení s klientem a spouští se asynchronní čtení dat z klienta. Následující příklad je první část implementace `acceptCallback` metody. Tato část metody signály hlavního vlákna aplikace chcete pokračovat ve zpracování a naváže připojení ke klientovi. Předpokládá globální **ManualResetEvent** s názvem `allDone`.  
  
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
  
 Čtení dat z klientského soketu vyžaduje stav objektu, který předává hodnoty mezi byla zahájena asynchronní volání. Následující příklad implementuje objekt stavu pro příjem řetězec ze vzdáleného klienta. Obsahuje pole pro klientského soketu dat vyrovnávací paměti pro příjem dat a <xref:System.Text.StringBuilder> pro vytvoření řetězce data odesílaném klientem. Umístění těchto polí v objektu stavu umožňuje jejich hodnot zachovaná napříč více volání na čtení dat z klientského soketu.  
  
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
  
 Část `acceptCallback` metodu, která začne dostávat data z klientského soketu nejprve inicializuje novou instanci `StateObject` třídy a poté zavolá <xref:System.Net.Sockets.Socket.BeginReceive%2A> metoda začne asynchronně číst data z klientského soketu.  
  
 Následující příklad ukazuje kompletní `acceptCallback` metody. Předpokládá, že je globální **ManualResetEvent** s názvem `allDone,` , který `StateObject` třída je definována a že `readCallback` je definována metoda v třídě s názvem `SocketListener`.  
  
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
  
 Poslední metodu, kterou je potřeba implementovat pro server websocket asynchronní je metoda čtení zpětného volání, která vrací data odeslaná klientem. Podobně jako metody zpětného volání přijmout, je metoda zpětného volání pro čtení **AsyncCallback** delegovat. Tato metoda načte jeden nebo více bajtů z klientského soketu do vyrovnávací paměti dat a pak zavolá **BeginReceive** metoda znovu, dokud data odeslaná klientem je dokončena. Po celá zpráva byla přečtena z klienta, řetězec se zobrazí v konzole a zavření serverového soketu zpracování připojení ke klientovi.  
  
 Následující ukázkový implementuje `readCallback` metody. Předpokládá, `StateObject` třída je definována.  
  
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
