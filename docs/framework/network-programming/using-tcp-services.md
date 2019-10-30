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
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039490"
---
# <a name="using-tcp-services"></a>Použití služeb TCP

Třída <xref:System.Net.Sockets.TcpClient> žádá o data z internetového prostředku pomocí protokolu TCP. Metody a vlastnosti **TcpClient** abstraktní informace o vytváření <xref:System.Net.Sockets.Socket> pro vyžádání a příjem dat pomocí protokolu TCP. Vzhledem k tomu, že připojení ke vzdálenému zařízení je reprezentované jako datový proud, můžete data číst a zapisovat pomocí .NET Framework techniků zpracování streamování.

Protokol TCP naváže připojení se vzdáleným koncovým bodem a pak pomocí tohoto připojení odesílá a přijímá datové pakety. Protokol TCP zodpovídá za to, aby bylo zajištěno, že se do koncového bodu odesílají datové pakety a při jejich doručení sestaví ve správném pořadí.

Aby bylo možné navázat připojení TCP, je nutné znát adresu síťového zařízení, které je hostitelem služby, kterou potřebujete, a musíte znát port TCP, který služba používá ke komunikaci. Autorita IANA (Internet Assigned Numbers Authority) definuje čísla portů pro běžné služby (viz část [název služby a Registry číslo portu přenosového protokolu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Služby, které nejsou v seznamu IANA, můžou mít čísla portů v rozsahu 1 024 až 65 535.

Následující příklad ukazuje nastavení **TcpClient** pro připojení k časovému serveru na portu TCP 13:

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

<xref:System.Net.Sockets.TcpListener> slouží k monitorování portu TCP pro příchozí požadavky a pak vytvoření **soketu** nebo **TcpClient** , které spravuje připojení ke klientovi. Metoda <xref:System.Net.Sockets.TcpListener.Start%2A> umožňuje naslouchání a metoda <xref:System.Net.Sockets.TcpListener.Stop%2A> zakáže naslouchání na portu. Metoda <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> akceptuje příchozí požadavky na připojení a vytvoří **TcpClient** pro zpracování požadavku a metoda <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> akceptuje příchozí požadavky na připojení a vytvoří **soket** pro zpracování žádosti.

Následující příklad ukazuje vytvoření serveru síťového času pomocí **Třída TcpListener nesmí** k monitorování portu TCP 13. Po přijetí požadavku na příchozí připojení odpoví časový server aktuálním datem a časem z hostitelského serveru.

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
