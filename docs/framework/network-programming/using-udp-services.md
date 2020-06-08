---
title: Použití služeb UDP
description: Třída UdpClient vyabstrakce podrobnosti pro vytvoření soketu pro vyžádání a příjem dat pomocí protokolu UDP v .NET Framework.
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
ms.openlocfilehash: 4c2e88492f737800151d30097719d7d011054a5e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501947"
---
# <a name="use-udp-services"></a><span data-ttu-id="920da-103">Používání služeb UDP</span><span class="sxs-lookup"><span data-stu-id="920da-103">Use UDP services</span></span>

<span data-ttu-id="920da-104"><xref:System.Net.Sockets.UdpClient>Třída komunikuje se síťovými službami pomocí protokolu UDP.</span><span class="sxs-lookup"><span data-stu-id="920da-104">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="920da-105">Vlastnosti a metody <xref:System.Net.Sockets.UdpClient> třídy mají přehled o vytvoření <xref:System.Net.Sockets.Socket> pro vyžádání a příjem dat pomocí protokolu UDP.</span><span class="sxs-lookup"><span data-stu-id="920da-105">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>

<span data-ttu-id="920da-106">Protokol UDP (User Datagram Protocol) je jednoduchý protokol, který se snaží doručovat data na vzdáleného hostitele.</span><span class="sxs-lookup"><span data-stu-id="920da-106">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="920da-107">Vzhledem k tomu, že protokol UDP je protokol bez připojení, datagramy UDP odeslané na vzdálený koncový bod nejsou zaručeny doručení, ani se nezaručuje, že dorazí ve stejném pořadí, ve kterém jsou odesílány.</span><span class="sxs-lookup"><span data-stu-id="920da-107">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="920da-108">Aplikace, které používají protokol UDP, musí být připravené ke zpracování chybějících, duplicitních a nesekvenčních datagramů.</span><span class="sxs-lookup"><span data-stu-id="920da-108">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>

<span data-ttu-id="920da-109">Chcete-li odeslat datagram pomocí protokolu UDP, je nutné znát síťovou adresu síťového zařízení, které je hostitelem služby, kterou potřebujete, a číslo portu UDP, které služba používá ke komunikaci.</span><span class="sxs-lookup"><span data-stu-id="920da-109">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="920da-110">Autorita IANA (Internet Assigned Numbers Authority) definuje čísla portů pro běžné služby (viz část [název služby a Registry číslo portu přenosového protokolu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="920da-110">The Internet Assigned Numbers Authority (IANA) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="920da-111">Služby, které nejsou v seznamu IANA, můžou mít čísla portů v rozsahu 1 024 až 65 535.</span><span class="sxs-lookup"><span data-stu-id="920da-111">Services not on the IANA list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="920da-112">Speciální síťové adresy se používají k podpoře zpráv všesměrového vysílání UDP v sítích založených na protokolu IP.</span><span class="sxs-lookup"><span data-stu-id="920da-112">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="920da-113">Následující diskuze používá jako příklad řadu adres IP verze 4, která se používá na internetu.</span><span class="sxs-lookup"><span data-stu-id="920da-113">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>

<span data-ttu-id="920da-114">Adresy IP verze 4 používají ke specifikaci síťové adresy 32 bitů.</span><span class="sxs-lookup"><span data-stu-id="920da-114">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="920da-115">U adres třídy C pomocí síťové masky 255.255.255.0 jsou tyto bity rozdělené na čtyři oktety.</span><span class="sxs-lookup"><span data-stu-id="920da-115">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="920da-116">Při vyjádření v desítkové soustavě tvoří čtyři oktety známý Desítkový zápis, například 192.168.100.2.</span><span class="sxs-lookup"><span data-stu-id="920da-116">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="920da-117">První dva oktety (v tomto příkladu 192,168) tvoří číslo sítě, třetí oktet (100) definuje podsíť a konečný oktet (2) je identifikátor hostitele.</span><span class="sxs-lookup"><span data-stu-id="920da-117">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>

<span data-ttu-id="920da-118">Nastavením všech bitů IP adres na jeden nebo 255.255.255.255 se vytvoří omezená adresa všesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="920da-118">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="920da-119">Odeslání datagramu UDP na tuto adresu doručuje zprávu na libovolného hostitele v segmentu místní sítě.</span><span class="sxs-lookup"><span data-stu-id="920da-119">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="920da-120">Protože směrovače nikdy nepředávají zprávy odeslané na tuto adresu, zprávy všesměrového vysílání obdrží pouze hostitelé v segmentu sítě.</span><span class="sxs-lookup"><span data-stu-id="920da-120">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>

<span data-ttu-id="920da-121">Všesměrové vysílání lze směrovat na určité části sítě nastavením všech bitů identifikátoru hostitele.</span><span class="sxs-lookup"><span data-stu-id="920da-121">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="920da-122">Pokud chcete například odeslat všesměrové vysílání všem hostitelům v síti identifikované pomocí IP adres počínaje 192.168.1, použijte adresu 192.168.1.255.</span><span class="sxs-lookup"><span data-stu-id="920da-122">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>

<span data-ttu-id="920da-123">Následující příklad kódu používá <xref:System.Net.Sockets.UdpClient> k naslouchání datagramů UDP na portu 11 000.</span><span class="sxs-lookup"><span data-stu-id="920da-123">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams on port 11,000.</span></span> <span data-ttu-id="920da-124">Klient obdrží řetězec zprávy a zapíše zprávu do konzoly.</span><span class="sxs-lookup"><span data-stu-id="920da-124">The client receives a message string and writes the message to the console.</span></span>

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

<span data-ttu-id="920da-125">Následující příklad kódu používá <xref:System.Net.Sockets.Socket> k odeslání datagramů UDP na adresu směrovaného všesměrového vysílání 192.168.1.255 pomocí portu 11 000.</span><span class="sxs-lookup"><span data-stu-id="920da-125">The following code example uses a <xref:System.Net.Sockets.Socket> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="920da-126">Klient odešle řetězec zprávy zadaný v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="920da-126">The client sends the message string specified on the command line.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="920da-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="920da-127">See also</span></span>

- <xref:System.Net.Sockets.UdpClient>
- <xref:System.Net.IPAddress>
