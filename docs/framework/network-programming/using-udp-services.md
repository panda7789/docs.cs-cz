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
ms.openlocfilehash: 5ff40e8759b1732d4ad228b1414f96f9c37e5ac5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209770"
---
# <a name="use-udp-services"></a>Používání služeb UDP

<xref:System.Net.Sockets.UdpClient>Třída komunikuje se síťovými službami pomocí protokolu UDP. Vlastnosti a metody <xref:System.Net.Sockets.UdpClient> třídy mají přehled o vytvoření <xref:System.Net.Sockets.Socket> pro vyžádání a příjem dat pomocí protokolu UDP.

Protokol UDP (User Datagram Protocol) je jednoduchý protokol, který se snaží doručovat data na vzdáleného hostitele. Vzhledem k tomu, že protokol UDP je protokol bez připojení, datagramy UDP odeslané na vzdálený koncový bod nejsou zaručeny doručení, ani se nezaručuje, že dorazí ve stejném pořadí, ve kterém jsou odesílány. Aplikace, které používají protokol UDP, musí být připravené ke zpracování chybějících, duplicitních a nesekvenčních datagramů.

Chcete-li odeslat datagram pomocí protokolu UDP, je nutné znát síťovou adresu síťového zařízení, které je hostitelem služby, kterou potřebujete, a číslo portu UDP, které služba používá ke komunikaci. Autorita IANA (Internet Assigned Numbers Authority) definuje čísla portů pro běžné služby (viz část [název služby a Registry číslo portu přenosového protokolu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Služby, které nejsou v seznamu IANA, můžou mít čísla portů v rozsahu 1 024 až 65 535.

Speciální síťové adresy se používají k podpoře zpráv všesměrového vysílání UDP v sítích založených na protokolu IP. Následující diskuze používá jako příklad řadu adres IP verze 4, která se používá na internetu.

Adresy IP verze 4 používají ke specifikaci síťové adresy 32 bitů. U adres třídy C pomocí síťové masky 255.255.255.0 jsou tyto bity rozdělené na čtyři oktety. Při vyjádření v desítkové soustavě tvoří čtyři oktety známý Desítkový zápis, například 192.168.100.2. První dva oktety (v tomto příkladu 192,168) tvoří číslo sítě, třetí oktet (100) definuje podsíť a konečný oktet (2) je identifikátor hostitele.

Nastavením všech bitů IP adres na jeden nebo 255.255.255.255 se vytvoří omezená adresa všesměrového vysílání. Odeslání datagramu UDP na tuto adresu doručuje zprávu na libovolného hostitele v segmentu místní sítě. Protože směrovače nikdy nepředávají zprávy odeslané na tuto adresu, zprávy všesměrového vysílání obdrží pouze hostitelé v segmentu sítě.

Všesměrové vysílání lze směrovat na určité části sítě nastavením všech bitů identifikátoru hostitele. Pokud chcete například odeslat všesměrové vysílání všem hostitelům v síti identifikované pomocí IP adres počínaje 192.168.1, použijte adresu 192.168.1.255.

Následující příklad kódu používá <xref:System.Net.Sockets.UdpClient> k naslouchání datagramů UDP na portu 11 000. Klient obdrží řetězec zprávy a zapíše zprávu do konzoly.

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

Následující příklad kódu používá <xref:System.Net.Sockets.Socket> k odeslání datagramů UDP na adresu směrovaného všesměrového vysílání 192.168.1.255 pomocí portu 11 000. Klient odešle řetězec zprávy zadaný v příkazovém řádku.

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

## <a name="see-also"></a>Viz také

- <xref:System.Net.Sockets.UdpClient>
- <xref:System.Net.IPAddress>
