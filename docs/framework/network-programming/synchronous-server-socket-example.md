---
title: Příklad synchronního serverového soketu
description: V tomto příkladu .NET Framework program vytvoří server, který přijímá připojení od klientů pomocí synchronního soketu. Přijímá a vrací řetězec.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronous server sockets
- sockets, code examples
- sockets, synchronous server sockets
ms.assetid: 5916c764-879f-4716-99fb-1d21c6237f1c
ms.openlocfilehash: 0e2fb91dc493b2da4c68a98ac8a62494e78a9fd1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502103"
---
# <a name="synchronous-server-socket-example"></a><span data-ttu-id="c7036-104">Příklad synchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="c7036-104">Synchronous Server Socket Example</span></span>
<span data-ttu-id="c7036-105">Následující ukázkový program vytvoří server, který přijímá žádosti o připojení od klientů.</span><span class="sxs-lookup"><span data-stu-id="c7036-105">The following example program creates a server that receives connection requests from clients.</span></span> <span data-ttu-id="c7036-106">Server je sestaven se synchronním soketem, takže spuštění serverové aplikace je při čekání na připojení z klienta pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="c7036-106">The server is built with a synchronous socket, so execution of the server application is suspended while it waits for a connection from a client.</span></span> <span data-ttu-id="c7036-107">Aplikace přijme řetězec z klienta, zobrazí řetězec v konzole nástroje a potom vrátí řetězec zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="c7036-107">The application receives a string from the client, displays the string on the console, and then echoes the string back to the client.</span></span> <span data-ttu-id="c7036-108">Řetězec z klienta musí obsahovat řetězec " \<EOF> " k signalizaci konce zprávy.</span><span class="sxs-lookup"><span data-stu-id="c7036-108">The string from the client must contain the string "\<EOF>" to signal the end of the message.</span></span>  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
Imports Microsoft.VisualBasic  
  
Public Class SynchronousSocketListener  
  
    ' Incoming data from the client.  
    Public Shared data As String = Nothing  
  
    Public Shared Sub Main()  
        ' Data buffer for incoming data.  
        Dim bytes() As Byte = New [Byte](1024) {}  
  
        ' Establish the local endpoint for the socket.  
        ' Dns.GetHostName returns the name of the
        ' host running the application.  
        Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
        Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
        Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
  
        ' Create a TCP/IP socket.  
        Dim listener As New Socket(ipAddress.AddressFamily, _  
            SocketType.Stream, ProtocolType.Tcp)  
  
        ' Bind the socket to the local endpoint and
        ' listen for incoming connections.  
  
        listener.Bind(localEndPoint)  
        listener.Listen(10)  
  
        ' Start listening for connections.  
        While True  
            Console.WriteLine("Waiting for a connection...")  
            ' Program is suspended while waiting for an incoming connection.  
            Dim handler As Socket = listener.Accept()  
            data = Nothing  
  
            ' An incoming connection needs to be processed.  
            While True  
                Dim bytesRec As Integer = handler.Receive(bytes)  
                data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
                If data.IndexOf("<EOF>") > -1 Then  
                    Exit While  
                End If  
            End While  
            ' Show the data on the console.  
            Console.WriteLine("Text received : {0}", data)  
            ' Echo the data back to the client.  
            Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
            handler.Send(msg)  
            handler.Shutdown(SocketShutdown.Both)  
            handler.Close()  
        End While  
    End Sub  
  
End Class 'SynchronousSocketListener  
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
public class SynchronousSocketListener {  
  
    // Incoming data from the client.  
    public static string data = null;  
  
    public static void StartListening() {  
        // Data buffer for incoming data.  
        byte[] bytes = new Byte[1024];  
  
        // Establish the local endpoint for the socket.  
        // Dns.GetHostName returns the name of the
        // host running the application.  
        IPHostEntry ipHostInfo = Dns.GetHostEntry(Dns.GetHostName());  
        IPAddress ipAddress = ipHostInfo.AddressList[0];  
        IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
  
        // Create a TCP/IP socket.  
        Socket listener = new Socket(ipAddress.AddressFamily,  
            SocketType.Stream, ProtocolType.Tcp );  
  
        // Bind the socket to the local endpoint and
        // listen for incoming connections.  
        try {  
            listener.Bind(localEndPoint);  
            listener.Listen(10);  
  
            // Start listening for connections.  
            while (true) {  
                Console.WriteLine("Waiting for a connection...");  
                // Program is suspended while waiting for an incoming connection.  
                Socket handler = listener.Accept();  
                data = null;  
  
                // An incoming connection needs to be processed.  
                while (true) {  
                    int bytesRec = handler.Receive(bytes);  
                    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
                    if (data.IndexOf("<EOF>") > -1) {  
                        break;  
                    }  
                }  
  
                // Show the data on the console.  
                Console.WriteLine( "Text received : {0}", data);  
  
                // Echo the data back to the client.  
                byte[] msg = Encoding.ASCII.GetBytes(data);  
  
                handler.Send(msg);  
                handler.Shutdown(SocketShutdown.Both);  
                handler.Close();  
            }  
  
        } catch (Exception e) {  
            Console.WriteLine(e.ToString());  
        }  
  
        Console.WriteLine("\nPress ENTER to continue...");  
        Console.Read();  
  
    }  
  
    public static int Main(String[] args) {  
        StartListening();  
        return 0;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7036-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7036-109">See also</span></span>

- [<span data-ttu-id="c7036-110">Příklad synchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="c7036-110">Synchronous Client Socket Example</span></span>](synchronous-client-socket-example.md)
- [<span data-ttu-id="c7036-111">Použití synchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="c7036-111">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="c7036-112">Příklady kódu soketu</span><span class="sxs-lookup"><span data-stu-id="c7036-112">Socket Code Examples</span></span>](socket-code-examples.md)
