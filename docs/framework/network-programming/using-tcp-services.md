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
# <a name="using-tcp-services"></a>Pomocí služby TCP
<xref:System.Net.Sockets.TcpClient> Třída vyžaduje data z internetových prostředků pomocí protokolu TCP. Metody a vlastnosti **TcpClient** abstraktní podrobnosti o vytváření <xref:System.Net.Sockets.Socket> pro podávání žádostí a příjmu dat pomocí protokolu TCP. Protože připojení k vzdálené zařízení je reprezentována jako datový proud, data můžete číst a zapisovat s techniky zpracování datového proudu rozhraní .NET Framework.  
  
 Protokol TCP naváže připojení se vzdálený koncový bod a pak toto připojení používá k odesílání a příjmu datových paketů. TCP je odpovědný za dodržování, datových paketů odesílaných ke koncovému bodu i po jejich příchodu sestaví ve správném pořadí.  
  
 K navázání připojení TCP, musíte znát adresu síťového zařízení, který je hostitelem služby, které potřebujete, a musí znát port TCP, který službu používá ke komunikaci. Internet Assigned Numbers Authority (Iana) definuje čísla portů pro běžné služby (viz www.iana.org/assignments/port-numbers). Služby, které nejsou na seznamu Iana může mít čísla portů v rozsahu 1 024 jednotek do 65 535.  
  
 Následující příklad ukazuje nastavení nahoru **TcpClient** pro připojení k serveru čas na portu TCP 13.  
  
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
  
 <xref:System.Net.Sockets.TcpListener> slouží k monitorování portu TCP pro příchozí požadavky a poté vytvořit buď **soketu** nebo **TcpClient** který spravuje připojení ke klientovi. <xref:System.Net.Sockets.TcpListener.Start%2A> Metoda umožňuje naslouchá a <xref:System.Net.Sockets.TcpListener.Stop%2A> metoda zakáže naslouchá na portu. <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> Metoda přijímá příchozí požadavky na připojení a vytváří **TcpClient** pro zpracování požadavku a <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> metoda přijímá příchozí požadavky na připojení a vytváří **soketu**pro zpracování požadavku.  
  
 Následující příklad ukazuje, vytváření s použitím serveru sítě čas **TcpListener** monitorování portu TCP 13. Když je přijatá příchozí požadavek na připojení, čas server odpoví aktuální datum a čas z hostitelského serveru.  
  
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
  
## <a name="see-also"></a>Viz také  
 
