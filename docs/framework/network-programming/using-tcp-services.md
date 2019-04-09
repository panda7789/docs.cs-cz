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
ms.openlocfilehash: 6c792c8d819d17d1fc32fedeeacdacbbb1624d95
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125616"
---
# <a name="using-tcp-services"></a>Použití služeb TCP
<xref:System.Net.Sockets.TcpClient> Třídy vyžaduje data z internetových prostředků pomocí protokolu TCP. Metody a vlastnosti **TcpClient** abstraktní podrobnosti o vytváření <xref:System.Net.Sockets.Socket> pro podávání žádostí a příjmu dat pomocí protokolu TCP. Protože připojení ke vzdálenému zařízení je reprezentován jako datový proud, můžete data čtení a zápis s techniky zpracování datového proudu rozhraní .NET Framework.  
  
 Protokolu TCP naváže připojení se vzdálený koncový bod a potom použije toto připojení k odesílání a příjmu datových paketů. TCP zodpovídá za to, že datových paketů odesílaných ke koncovému bodu i týkajícím se této ve správném pořadí při doručení.  
  
 K navázání připojení TCP, musíte znát adresu síťového zařízení, který je hostitelem služby, které potřebujete a navíc musí znát port TCP, který službu používá ke komunikaci. Internet Assigned Numbers Authority (Iana) definuje čísla portů pro běžné služby (viz [název služby a registru číslo portu protokolu přenosu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Služby není na seznamu Iana může mít čísla portu v rozsahu 1 024 do 65 535.  
  
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
  
 <xref:System.Net.Sockets.TcpListener> slouží k monitorování portu TCP pro příchozí požadavky a vytvořte buď **soketu** nebo **TcpClient** , který spravuje připojení ke klientovi. <xref:System.Net.Sockets.TcpListener.Start%2A> Metoda umožňuje naslouchá a <xref:System.Net.Sockets.TcpListener.Stop%2A> metoda zakáže naslouchá na portu. <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> Metoda přijímá příchozí požadavky na připojení a vytváří **TcpClient** pro zpracování požadavku a <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> metoda přijímá příchozí požadavky na připojení a vytváří **soketu**žádost zpracovat.  
  
 Následující příklad ukazuje vytváření s použitím serveru sítě čas **TcpListener** monitorování portu TCP 13. Když je přijat příchozí požadavek na připojení, čas server jako odpověď vrátí aktuální datum a čas z hostitelského serveru.  
  
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
  
## <a name="see-also"></a>Viz také:
