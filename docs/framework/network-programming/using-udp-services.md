---
title: Použití služeb UDP
ms.date: 03/30/2017
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 8aabd71a841af2b01c644d52806f213ca9c92ec2
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47209356"
---
# <a name="using-udp-services"></a>Použití služeb UDP
<xref:System.Net.Sockets.UdpClient> Třídy komunikuje se síťovými službami pomocí protokolu UDP. Vlastnosti a metody <xref:System.Net.Sockets.UdpClient> třídy abstraktní podrobnosti o vytváření <xref:System.Net.Sockets.Socket> pro podávání žádostí a příjmu dat pomocí protokolu UDP.  
  
 Protokolu UDP (User Datagram) je jednoduchý protokol, který se pokusí k doručování dat vzdáleného hostitele. Ale protože protokolu UDP je protokol pro přenos, odeslané na vzdálený koncový bod datagramy UDP zaručené doručení ani jsou zaručeně dorazí ve stejném pořadí, ve které se odesílají. Aplikace, které používají UDP musí být připravena ke zpracování datagramy chybí, duplicitní a mimo pořadí.  
  
 K odeslání datagram pomocí protokolu UDP, musíte znát síťová adresa síťového zařízení, který je hostitelem služby, které potřebujete a číslo portu UDP, který službu používá ke komunikaci. Internet Assigned Numbers Authority (Iana) definuje čísla portů pro běžné služby (viz www.iana.org/assignments/port-numbers). Služby není na seznamu Iana může mít čísla portu v rozsahu 1 024 do 65 535.  
  
 Speciální síťové adresy se používají pro podporu všesměrového vysílání zpráv UDP v sítích založených na protokolu IP. Následující diskuse používá rodina IP verze 4 adres jako příklad je použita na Internetu.  
  
 Adresy IP verze 4 použijte k určení síťová adresa 32 bitů. Pomocí síťová maska 255.255.255.0 adres třídy C tyto bity jsou rozdělené do čtyř oktetech. Když vyjádřené v desítkové soustavě, tvoří čtyři oktety známými notacemi čtyřmi tečkami, jako je například 192.168.100.2. Číslo sítě tvoří první dva oktety (192.168 v tomto příkladu), třetí octet (100) definuje podsíť a poslední oktet (2) je identifikátor hostitele.  
  
 Nastavení všechny bity IP adresy na jeden nebo 255.255.255.255 tvoří omezené adresa všesměrového vysílání. Odesílání UDP datagram na tuto adresu doručí do libovolného hostitele v místní síti segmentu. Protože směrovače nikdy předávat zprávy na tuto adresu, zobrazí se pouze hostitelé v segmentu sítě všesměrového vysílání zpráva.  
  
 Vysílání mohou přesměrováni na konkrétní části sítě tak, že nastavíte všechny bity identifikátor hostitele. Například k odesílání vysílání pro všechny hostitele v síti identifikovaných podle IP adresy, počínaje 192.168.1 použijte adresu 192.168.1.255.  
  
 Následující příklad kódu používá <xref:System.Net.Sockets.UdpClient> pro naslouchání odeslané na směrovanou adresu vysílání 192.168.1.255 na portu 11 000 datagramy UDP. Klient obdrží řetězec zprávy a zapisuje zprávy do konzoly.  
  
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
  
 Následující příklad kódu používá <xref:System.Net.Sockets.UdpClient> odesílat datagramů UDP na směrovanou adresu vysílání 192.168.1.255, pomocí portů 11 000. Klient odešle zprávu řetězci zadanému na příkazovém řádku.  
  
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
 
