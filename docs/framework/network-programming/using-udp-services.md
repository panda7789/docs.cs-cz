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
ms.openlocfilehash: 397c51501ac333d6df699064b3fe82920bc38152
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086101"
---
# <a name="using-udp-services"></a>Použití služeb UDP
<xref:System.Net.Sockets.UdpClient> Třídy komunikuje se síťovými službami pomocí protokolu UDP. Vlastnosti a metody <xref:System.Net.Sockets.UdpClient> třídy abstraktní podrobnosti o vytváření <xref:System.Net.Sockets.Socket> pro podávání žádostí a příjmu dat pomocí protokolu UDP.

Protokolu UDP (User Datagram) je jednoduchý protokol, který se pokusí k doručování dat vzdáleného hostitele. Ale protože protokolu UDP je protokol pro přenos, odeslané na vzdálený koncový bod datagramy UDP zaručené doručení ani jsou zaručeně dorazí ve stejném pořadí, ve které se odesílají. Aplikace, které používají UDP musí být připravena ke zpracování datagramy chybí, duplicitní a mimo pořadí.

K odeslání datagram pomocí protokolu UDP, musíte znát síťová adresa síťového zařízení, který je hostitelem služby, které potřebujete a číslo portu UDP, který službu používá ke komunikaci. Internet Assigned Numbers Authority (Iana) definuje čísla portů pro běžné služby (viz [název služby a registru číslo portu protokolu přenosu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Služby není na seznamu Iana může mít čísla portu v rozsahu 1 024 do 65 535.

Speciální síťové adresy se používají pro podporu všesměrového vysílání zpráv UDP v sítích založených na protokolu IP. Následující diskuse používá rodina IP verze 4 adres jako příklad je použita na Internetu.

Adresy IP verze 4 použijte k určení síťová adresa 32 bitů. Pomocí síťová maska 255.255.255.0 adres třídy C tyto bity jsou rozdělené do čtyř oktetech. Když vyjádřené v desítkové soustavě, tvoří čtyři oktety známými notacemi čtyřmi tečkami, jako je například 192.168.100.2. Číslo sítě tvoří první dva oktety (192.168 v tomto příkladu), třetí octet (100) definuje podsíť a poslední oktet (2) je identifikátor hostitele.

Nastavení všechny bity IP adresy na jeden nebo 255.255.255.255 tvoří omezené adresa všesměrového vysílání. Odesílání UDP datagram na tuto adresu doručí do libovolného hostitele v místní síti segmentu. Protože směrovače nikdy předávat zprávy na tuto adresu, zobrazí se pouze hostitelé v segmentu sítě všesměrového vysílání zpráva.

Vysílání mohou přesměrováni na konkrétní části sítě tak, že nastavíte všechny bity identifikátor hostitele. Například k odesílání vysílání pro všechny hostitele v síti identifikovaných podle IP adresy, počínaje 192.168.1 použijte adresu 192.168.1.255.

Následující příklad kódu používá <xref:System.Net.Sockets.UdpClient> pro naslouchání datagramů UDP port 11 000. Klient obdrží řetězec zprávy a zapisuje zprávy do konzoly.

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class UDPListener
   Private Const listenPort As Integer = 11000
   
   Private Shared Sub StartListener()
      Dim listener As New UdpClient(listenPort)
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)
      Try
         While True
            Console.WriteLine("Waiting for broadcast")
            Dim bytes As Byte() = listener.Receive(groupEP)
            Console.WriteLine("Received broadcast from {0} :", groupEP)
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytes.Length))
         End While
      Catch e As SocketException
         Console.WriteLine(e)
      Finally
         listener.Close()
      End Try
   End Sub 'StartListener
   
   Public Shared Sub Main()
      StartListener()
   End Sub 'Main
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
        UdpClient listener = new UdpClient(listenPort);
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any, listenPort);
        
        try
        {
            while (true)
            {
                Console.WriteLine("Waiting for broadcast");
                byte[] bytes = listener.Receive(ref groupEP);
                
                Console.WriteLine($"Received broadcast from {groupEP} :");
                Console.WriteLine($" {Encoding.ASCII.GetString(bytes, 0, bytes.Length)}");
            }
        }
        catch (SocketException e)
        {
            Console.WriteLine(e);
        }
        finally
        {
            listener.Close();
        }
    }
    
    public static void Main()
    {
        StartListener();
    }
}
```

Následující příklad kódu používá <xref:System.Net.Sockets.Socket> odesílat datagramů UDP na směrovanou adresu vysílání 192.168.1.255, pomocí portů 11 000. Klient odešle zprávu řetězci zadanému na příkazovém řádku.

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class Program
    Public Shared Sub Main(args() As [String])
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp)
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))
      Dim ep As New IPEndPoint(broadcast, 11000)
      s.SendTo(sendbuf, ep)
      Console.WriteLine("Message sent to the broadcast address")
   End Sub 'Main
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
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp);
        
        IPAddress broadcast = IPAddress.Parse("192.168.1.255");
        
        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);
        
        s.SendTo(sendbuf, ep);
        
        Console.WriteLine("Message sent to the broadcast address");
    }
}
```

## <a name="see-also"></a>Viz také:

- <xref:System.Net.Sockets.UdpClient>
- <xref:System.Net.IPAddress>
