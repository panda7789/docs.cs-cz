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
ms.openlocfilehash: 477095ada6e44f66cbc60cd80375da9a87f38e39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180609"
---
# <a name="using-udp-services"></a>Použití služeb UDP
Třída <xref:System.Net.Sockets.UdpClient> komunikuje se síťovými službami pomocí UDP. Vlastnosti a metody <xref:System.Net.Sockets.UdpClient> třídy abstraktní podrobnosti o vytvoření <xref:System.Net.Sockets.Socket> pro vyžádání a příjem dat pomocí UDP.

User Datagram Protocol (UDP) je jednoduchý protokol, který vynakládá maximální úsilí na doručení dat vzdálenému hostiteli. Protože je však protokol UDP protokol emitovaný bez připojení, není zaručeno, že datagramy UDP odeslané do vzdáleného koncového bodu dorazí, ani není zaručeno, že dorazí ve stejném pořadí, ve kterém jsou odesílány. Aplikace, které používají UDP musí být připraveny ke zpracování chybějících, duplicitních a mimosekčních datových gramů.

Chcete-li odeslat datagram pomocí udp, musíte znát síťovou adresu síťového zařízení hostujícího službu, kterou potřebujete, a číslo portu UDP, které služba používá ke komunikaci. Úřad pro přiřazená čísla internetu (Iana) definuje čísla portů pro běžné služby (viz [Název služby a registr čísel portů transportního protokolu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Služby, které nejsou uvedeny v seznamu Iana může mít čísla portů v rozsahu 1,024 do 65,535.

Speciální síťové adresy se používají k podpoře zpráv vysílání UDP v sítích založených na protokolu IP. Následující diskuse používá jako příklad rodinu adres IP verze 4 používanou v Internetu.

Adresy IP verze 4 používají k určení síťové adresy 32 bitů. Pro adresy třídy C pomocí masky sítě 255.255.255.0 jsou tyto bity rozděleny do čtyř oktetů. Jsou-li čtyři oktety vyjádřeny v desítkové mlze, tvoří známou tečkovanou čtyřkolku, například 192.168.100.2. První dva oktety (192.168 v tomto příkladu) tvoří číslo sítě, třetí oktet (100) definuje podsíť a konečný oktet (2) je identifikátor hostitele.

Nastavení všech bitů adresy IP na jednu nebo 255.255.255.255 tvoří omezenou adresu vysílání. Odeslání datagramu UDP na tuto adresu doručí zprávu libovolnému hostiteli v segmentu místní sítě. Vzhledem k tomu, že směrovače nikdy nepředávají zprávy odeslané na tuto adresu, obdrží zprávu všesměrového vysílání pouze hostitelé v segmentu sítě.

Všesměrové vysílání lze směrovat na určité části sítě nastavením všech bitů identifikátoru hostitele. Chcete-li například odeslat vysílání všem hostitelům v síti označených adresami IP začínajícími na 192.168.1, použijte adresu 192.168.1.255.

Následující příklad kódu <xref:System.Net.Sockets.UdpClient> používá a naslouchat datagramům UDP na portu 11 000. Klient obdrží řetězec zprávy a zapíše zprávu do konzoly.

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

Následující příklad kódu <xref:System.Net.Sockets.Socket> používá datagramy UDP na adresu řízeného vysílání 192.168.1.255 pomocí portu 11 000. Klient odešle řetězec zprávy zadaný na příkazovém řádku.

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
