---
title: Použití služeb TCP
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
ms.openlocfilehash: 3678586647dcf9c47b4494197fbf56cab865b3d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73039490"
---
# <a name="using-tcp-services"></a>Použití služeb TCP

Třída <xref:System.Net.Sockets.TcpClient> požaduje data z internetového prostředku pomocí protokolu TCP. Metody a vlastnosti **TcpClient** abstraktní podrobnosti pro vytvoření <xref:System.Net.Sockets.Socket> pro vyžádání a příjem dat pomocí TCP. Vzhledem k tomu, že připojení ke vzdálenému zařízení je reprezentováno jako datový proud, lze data číst a zapisovat pomocí technik zpracování datového proudu rozhraní .NET Framework.

Protokol TCP naváže připojení se vzdáleným koncovým bodem a potom toto připojení použije k odesílání a přijímání datových paketů. Protokol TCP je zodpovědný za zajištění, že datové pakety jsou odesílány do koncového bodu a sestaveny ve správném pořadí při jejich doručení.

Chcete-li navázat připojení TCP, musíte znát adresu síťového zařízení hostujícího službu, kterou potřebujete, a musíte znát port TCP, který služba používá ke komunikaci. Úřad pro přiřazená čísla internetu (Iana) definuje čísla portů pro běžné služby (viz [Název služby a registr čísel portů transportního protokolu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Služby, které nejsou uvedeny v seznamu Iana může mít čísla portů v rozsahu 1,024 do 65,535.

Následující příklad ukazuje nastavení **tcpclient** pro připojení k časovému serveru na portu TCP 13:

```vb
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

    Overloads Public Shared Function Main(args As String()) As Integer
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
    End Function
End Class
```

```csharp
using System;
using System.Net.Sockets;
using System.Text;

public class TcpTimeClient
{
    private const int portNum = 13;
    private const string hostName = "host.contoso.com";

    public static int Main(String[] args)
    {
        try
        {
            var client = new TcpClient(hostName, portNum);

            NetworkStream ns = client.GetStream();

            byte[] bytes = new byte[1024];
            int bytesRead = ns.Read(bytes, 0, bytes.Length);

            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));

            client.Close();

        }
        catch (Exception e)
        {
            Console.WriteLine(e.ToString());
        }

        return 0;
    }
}
```

<xref:System.Net.Sockets.TcpListener>Slouží ke sledování portu TCP pro příchozí požadavky a potom k vytvoření **socketu** nebo **klienta TcpClient,** který spravuje připojení ke klientovi. Metoda <xref:System.Net.Sockets.TcpListener.Start%2A> umožňuje naslouchání <xref:System.Net.Sockets.TcpListener.Stop%2A> a metoda zakáže naslouchání na portu. Metoda <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> přijímá příchozí požadavky na připojení a vytvoří **TcpClient** pro <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> zpracování požadavku a metoda přijímá příchozí požadavky na připojení a vytvoří **Socket** pro zpracování požadavku.

Následující příklad ukazuje vytvoření síťového časového serveru pomocí **tcplisteneru** ke sledování portu TCP 13. Při přijetí příchozího požadavku na připojení odpoví časový server aktuálním datem a časem z hostitelského serveru.

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class TcpTimeServer

    Private const portNum As Integer = 13

    ' Entry point that delegates to C-style main Private Function.
    Public Overloads Shared Sub Main()
        System.Environment.ExitCode = _
            Main(System.Environment.GetCommandLineArgs())
    End Sub

    Overloads Public Shared Function Main(args As String()) As Integer
        Dim done As Boolean = False

        Dim listener As New TcpListener(IPAddress.Any, portNum)

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
    End Function
End Class
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

public class TcpTimeServer
{

    private const int portNum = 13;

    public static int Main(String[] args)
    {
        bool done = false;

        var listener = new TcpListener(IPAddress.Any, portNum);

        listener.Start();

        while (!done)
        {
            Console.Write("Waiting for connection...");
            TcpClient client = listener.AcceptTcpClient();

            Console.WriteLine("Connection accepted.");
            NetworkStream ns = client.GetStream();

            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());

            try
            {
                ns.Write(byteTime, 0, byteTime.Length);
                ns.Close();
                client.Close();
            }
            catch (Exception e)
            {
                Console.WriteLine(e.ToString());
            }
        }

        listener.Stop();

        return 0;
    }

}
```
