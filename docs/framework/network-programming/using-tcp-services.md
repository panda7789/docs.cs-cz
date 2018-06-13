---
title: Pomocí služby TCP
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, TCP
- receiving data, TCP
- TcpClient class, about TcpClient class
- data requests, TCP
- application protocols, TCP
- network resources, TCP
- sending data, TCP
- TCP
- protocols, TCP
- Internet, TCP
ms.assetid: d2811830-3bcb-495c-b82d-cda9cf919aad
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d11566182cc9d0b4f2634350868ec94a0685d996
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397166"
---
# <a name="using-tcp-services"></a><span data-ttu-id="192c3-102">Pomocí služby TCP</span><span class="sxs-lookup"><span data-stu-id="192c3-102">Using TCP Services</span></span>
<span data-ttu-id="192c3-103"><xref:System.Net.Sockets.TcpClient> Třída vyžaduje data z internetových prostředků pomocí protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="192c3-103">The <xref:System.Net.Sockets.TcpClient> class requests data from an Internet resource using TCP.</span></span> <span data-ttu-id="192c3-104">Metody a vlastnosti **TcpClient** abstraktní podrobnosti o vytváření <xref:System.Net.Sockets.Socket> pro podávání žádostí a příjmu dat pomocí protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="192c3-104">The methods and properties of **TcpClient** abstract the details for creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using TCP.</span></span> <span data-ttu-id="192c3-105">Protože připojení k vzdálené zařízení je reprezentována jako datový proud, data můžete číst a zapisovat s techniky zpracování datového proudu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="192c3-105">Because the connection to the remote device is represented as a stream, data can be read and written with .NET Framework stream-handling techniques.</span></span>  
  
 <span data-ttu-id="192c3-106">Protokol TCP naváže připojení se vzdálený koncový bod a pak toto připojení používá k odesílání a příjmu datových paketů.</span><span class="sxs-lookup"><span data-stu-id="192c3-106">The TCP protocol establishes a connection with a remote endpoint and then uses that connection to send and receive data packets.</span></span> <span data-ttu-id="192c3-107">TCP je odpovědný za dodržování, datových paketů odesílaných ke koncovému bodu i po jejich příchodu sestaví ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="192c3-107">TCP is responsible for ensuring that data packets are sent to the endpoint and assembled in the correct order when they arrive.</span></span>  
  
 <span data-ttu-id="192c3-108">K navázání připojení TCP, musíte znát adresu síťového zařízení, který je hostitelem služby, které potřebujete, a musí znát port TCP, který službu používá ke komunikaci.</span><span class="sxs-lookup"><span data-stu-id="192c3-108">To establish a TCP connection, you must know the address of the network device hosting the service you need and you must know the TCP port that the service uses to communicate.</span></span> <span data-ttu-id="192c3-109">Internet Assigned Numbers Authority (Iana) definuje čísla portů pro běžné služby (viz www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="192c3-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="192c3-110">Služby, které nejsou na seznamu Iana může mít čísla portů v rozsahu 1 024 jednotek do 65 535.</span><span class="sxs-lookup"><span data-stu-id="192c3-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="192c3-111">Následující příklad ukazuje nastavení nahoru **TcpClient** pro připojení k serveru čas na portu TCP 13.</span><span class="sxs-lookup"><span data-stu-id="192c3-111">The following example demonstrates setting up a **TcpClient** to connect to a time server on TCP port 13.</span></span>  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeClient  
    Private const portNum As Integer = 13  
    Private const hostName As String = "host.contoso.com"  
  
    ' Entry point  that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Try  
            Dim client As New TcpClient(hostName, portNum)  
  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim bytes(1024) As Byte  
            Dim bytesRead As Integer = ns.Read(bytes, 0, bytes.Length)  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytesRead))  
  
        Catch e As Exception  
            Console.WriteLine(e.ToString())  
        End Try  
  
        client.Close()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeClient  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeClient {  
    private const int portNum = 13;  
    private const string hostName = "host.contoso.com";  
  
    public static int Main(String[] args) {  
        try {  
            TcpClient client = new TcpClient(hostName, portNum);  
  
            NetworkStream ns = client.GetStream();  
  
            byte[] bytes = new byte[1024];  
            int bytesRead = ns.Read(bytes, 0, bytes.Length);  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));  
  
            client.Close();  
  
        } catch (Exception e) {  
            Console.WriteLine(e.ToString());  
        }  
  
        return 0;  
    }  
}  
```  
  
 <span data-ttu-id="192c3-112"><xref:System.Net.Sockets.TcpListener> slouží k monitorování portu TCP pro příchozí požadavky a poté vytvořit buď **soketu** nebo **TcpClient** který spravuje připojení ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="192c3-112"><xref:System.Net.Sockets.TcpListener> is used to monitor a TCP port for incoming requests and then create either a **Socket** or a **TcpClient** that manages the connection to the client.</span></span> <span data-ttu-id="192c3-113"><xref:System.Net.Sockets.TcpListener.Start%2A> Metoda umožňuje naslouchá a <xref:System.Net.Sockets.TcpListener.Stop%2A> metoda zakáže naslouchá na portu.</span><span class="sxs-lookup"><span data-stu-id="192c3-113">The <xref:System.Net.Sockets.TcpListener.Start%2A> method enables listening, and the <xref:System.Net.Sockets.TcpListener.Stop%2A> method disables listening on the port.</span></span> <span data-ttu-id="192c3-114"><xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> Metoda přijímá příchozí požadavky na připojení a vytváří **TcpClient** pro zpracování požadavku a <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> metoda přijímá příchozí požadavky na připojení a vytváří **soketu**pro zpracování požadavku.</span><span class="sxs-lookup"><span data-stu-id="192c3-114">The <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> method accepts incoming connection requests and creates a **TcpClient** to handle the request, and the <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> method accepts incoming connection requests and creates a **Socket** to handle the request.</span></span>  
  
 <span data-ttu-id="192c3-115">Následující příklad ukazuje, vytváření s použitím serveru sítě čas **TcpListener** monitorování portu TCP 13.</span><span class="sxs-lookup"><span data-stu-id="192c3-115">The following example demonstrates creating a network time server using a **TcpListener** to monitor TCP port 13.</span></span> <span data-ttu-id="192c3-116">Když je přijatá příchozí požadavek na připojení, čas server odpoví aktuální datum a čas z hostitelského serveru.</span><span class="sxs-lookup"><span data-stu-id="192c3-116">When an incoming connection request is accepted, the time server responds with the current date and time from the host server.</span></span>  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeServer  
  
    Private const portNum As Integer = 13  
  
    ' Entry point that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Dim done As Boolean = False  
  
        Dim listener As New TcpListener(portNum)  
  
        listener.Start()  
  
        While Not done  
            Console.Write("Waiting for connection...")  
            Dim client As TcpClient = listener.AcceptTcpClient()  
  
            Console.WriteLine("Connection accepted.")  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim byteTime As Byte() = _  
                Encoding.ASCII.GetBytes(DateTime.Now.ToString())  
  
            Try  
                ns.Write(byteTime, 0, byteTime.Length)  
                ns.Close()  
                client.Close()  
            Catch e As Exception  
                Console.WriteLine(e.ToString())  
            End Try  
        End While  
  
        listener.Stop()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeServer  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeServer {  
  
    private const int portNum = 13;  
  
    public static int Main(String[] args) {  
        bool done = false;  
  
        TcpListener listener = new TcpListener(portNum);  
  
        listener.Start();  
  
        while (!done) {  
            Console.Write("Waiting for connection...");  
            TcpClient client = listener.AcceptTcpClient();  
  
            Console.WriteLine("Connection accepted.");  
            NetworkStream ns = client.GetStream();  
  
            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());  
  
            try {  
                ns.Write(byteTime, 0, byteTime.Length);  
                ns.Close();  
                client.Close();  
            } catch (Exception e) {  
                Console.WriteLine(e.ToString());  
            }  
        }  
  
        listener.Stop();  
  
        return 0;  
    }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="192c3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="192c3-117">See Also</span></span>  
 
