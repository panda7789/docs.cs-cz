---
title: "Pomocí služby UDP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- protocols, UDP
- network resources, UDP
- requesting data from Internet, UDP
- UDP
- receiving data, UDP
- Internet, UDP
- broadcasting messages to multiple addresses
- data requests, UDP
- UdpClient class, about UdpClient class
- sending data, UDP
- application protocols, UDP
ms.assetid: d5c3477a-e798-454c-a890-738ba14c5707
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 86f44c5aa4c744ab6966f0cb6b3834dd1f5f0f48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-udp-services"></a>Pomocí služby UDP
<xref:System.Net.Sockets.UdpClient> Třída komunikuje pomocí protokolu UDP síťové služby. Vlastnosti a metody <xref:System.Net.Sockets.UdpClient> abstraktní třída podrobnosti o vytváření <xref:System.Net.Sockets.Socket> pro podávání žádostí a příjmu dat pomocí protokolu UDP.  
  
 Protokol UDP (User Datagram) je jednoduchý protokol, který umožňuje usilovně k doručování dat do vzdáleného hostitele. Protože protokolu UDP je protokol pro přenos, ale datagramy UDP odeslané na vzdálený koncový bod není zaručené doručení, ani jsou jejich zaručené doručení ve stejném pořadí, v níž jsou odesílány. Aplikace, které používají UDP musí být připraveny pro zpracování datagramy chybí, duplicitní a mimo pořadí.  
  
 Chcete-li odeslat datagram, používat UDP, musíte znát síťová adresa hostující službu, kterou budete potřebovat a číslo portu UDP, který služba používá pro komunikaci síťového zařízení. Internet Assigned Numbers Authority (Iana) definuje čísla portů pro běžné služby (viz www.iana.org/assignments/port-numbers). Služby, které nejsou na seznamu Iana může mít čísla portů v rozsahu 1 024 jednotek do 65 535.  
  
 Speciální síťové adresy se používají pro podporu zprávy všesměrového vysílání UDP v sítích založených na protokolu IP. Následující diskusi používá rodina IP verze 4 adres používaných na Internetu jako příklad.  
  
 Zadejte rozsah adres protokolu IP verze 4 adresy pomocí 32bitová verze. Pomocí síťová maska 255.255.255.0 adres třídy C jsou tyto bity rozdělené do čtyř oktety. Když vyjádřené v desítkové soustavě, tvoří čtyři oktety obeznámeni s tečkami quad zápis, jako je například 192.168.100.2. Číslo sítě tvoří první dva oktety (192.168 v tomto příkladu), třetí oktet (100) definuje podsíť a poslední oktet (2) je identifikátor hostitele.  
  
 Nastavení služby bits IP adresy na jeden nebo 255.255.255.255, tvoří omezené adresy všesměrového vysílání. Odesílání datagramů UDP na tuto adresu doručení zprávy do libovolného hostitele v segmentu místní sítě. Protože směrovače nikdy předávat zprávy odeslané na tuto adresu, jenom hostitelé v segmentu sítě přijímat zprávy všesměrového vysílání.  
  
 Vysílání můžete přesměrováni na konkrétní části sítě nastavením všechny bity identifikátor hostitele. Například pokud chcete odeslat vysílání všichni hostitelé v síti, který začíná 192.168.1 IP adresy, použijte adresu 192.168.1.255.  
  
 Následující příklad kódu používá <xref:System.Net.Sockets.UdpClient> naslouchat odeslané na směrovanou adresu vysílání 192.168.1.255 na portu 11 000 datagramy UDP. Klient obdrží řetězec zprávy a zapíše zprávu do konzoly.  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class UDPListener  
   Private Const listenPort As Integer = 11000  
  
   Private Shared Sub StartListener()  
      Dim done As Boolean = False  
      Dim listener As New UdpClient(listenPort)  
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)  
      Try  
         While Not done  
            Console.WriteLine("Waiting for broadcast")  
            Dim bytes As Byte() = listener.Receive(groupEP)  
            Console.WriteLine("Received broadcast from {0} :", _  
                groupEP.ToString())   
            Console.WriteLine( _  
                Encoding.ASCII.GetString(bytes, 0, bytes.Length))  
            Console.WriteLine()  
         End While  
      Catch e As Exception  
         Console.WriteLine(e.ToString())  
      Finally  
         listener.Close()  
      End Try  
   End Sub 'StartListener  
  
   Public Shared Function Main() As Integer  
      StartListener()  
      Return 0  
   End Function 'Main  
End Class 'UDPListener  
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
public class UDPListener   
{  
    private const int listenPort = 11000;  
  
    private static void StartListener()   
    {  
        bool done = false;  
  
        UdpClient listener = new UdpClient(listenPort);  
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any,listenPort);  
  
        try   
        {  
            while (!done)   
            {  
                Console.WriteLine("Waiting for broadcast");  
                byte[] bytes = listener.Receive( ref groupEP);  
  
                Console.WriteLine("Received broadcast from {0} :\n {1}\n",  
                    groupEP.ToString(),  
                    Encoding.ASCII.GetString(bytes,0,bytes.Length));  
            }  
  
        }   
        catch (Exception e)   
        {  
            Console.WriteLine(e.ToString());  
        }  
        finally  
        {  
            listener.Close();  
        }  
    }  
  
    public static int Main()   
    {  
        StartListener();  
  
        return 0;  
    }  
}  
```  
  
 Následující příklad kódu používá <xref:System.Net.Sockets.UdpClient> odeslat datagramy UDP na směrovanou adresu vysílání 192.168.1.255, pomocí portu 11 000. Klient odešle zprávu řetězec zadaný v příkazovém řádku.  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class Program  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
          ProtocolType.Udp)  
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")  
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))  
      Dim ep As New IPEndPoint(broadcast, 11000)  
      s.SendTo(sendbuf, ep)  
      Console.WriteLine("Message sent to the broadcast address")  
   End Function 'Main  
End Class   
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
class Program   
{  
    static void Main(string[] args)   
    {  
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
            ProtocolType.Udp);  
  
        IPAddress broadcast = IPAddress.Parse("192.168.1.255");  
  
        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);  
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);  
  
        s.SendTo(sendbuf, ep);  
  
        Console.WriteLine("Message sent to the broadcast address");  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.Sockets.UdpClient>  
 <xref:System.Net.IPAddress>  
 
