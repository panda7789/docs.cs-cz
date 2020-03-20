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
# <a name="using-udp-services"></a><span data-ttu-id="43272-102">Použití služeb UDP</span><span class="sxs-lookup"><span data-stu-id="43272-102">Using UDP Services</span></span>
<span data-ttu-id="43272-103">Třída <xref:System.Net.Sockets.UdpClient> komunikuje se síťovými službami pomocí UDP.</span><span class="sxs-lookup"><span data-stu-id="43272-103">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="43272-104">Vlastnosti a metody <xref:System.Net.Sockets.UdpClient> třídy abstraktní podrobnosti o vytvoření <xref:System.Net.Sockets.Socket> pro vyžádání a příjem dat pomocí UDP.</span><span class="sxs-lookup"><span data-stu-id="43272-104">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>

<span data-ttu-id="43272-105">User Datagram Protocol (UDP) je jednoduchý protokol, který vynakládá maximální úsilí na doručení dat vzdálenému hostiteli.</span><span class="sxs-lookup"><span data-stu-id="43272-105">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="43272-106">Protože je však protokol UDP protokol emitovaný bez připojení, není zaručeno, že datagramy UDP odeslané do vzdáleného koncového bodu dorazí, ani není zaručeno, že dorazí ve stejném pořadí, ve kterém jsou odesílány.</span><span class="sxs-lookup"><span data-stu-id="43272-106">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="43272-107">Aplikace, které používají UDP musí být připraveny ke zpracování chybějících, duplicitních a mimosekčních datových gramů.</span><span class="sxs-lookup"><span data-stu-id="43272-107">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>

<span data-ttu-id="43272-108">Chcete-li odeslat datagram pomocí udp, musíte znát síťovou adresu síťového zařízení hostujícího službu, kterou potřebujete, a číslo portu UDP, které služba používá ke komunikaci.</span><span class="sxs-lookup"><span data-stu-id="43272-108">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="43272-109">Úřad pro přiřazená čísla internetu (Iana) definuje čísla portů pro běžné služby (viz [Název služby a registr čísel portů transportního protokolu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="43272-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="43272-110">Služby, které nejsou uvedeny v seznamu Iana může mít čísla portů v rozsahu 1,024 do 65,535.</span><span class="sxs-lookup"><span data-stu-id="43272-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="43272-111">Speciální síťové adresy se používají k podpoře zpráv vysílání UDP v sítích založených na protokolu IP.</span><span class="sxs-lookup"><span data-stu-id="43272-111">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="43272-112">Následující diskuse používá jako příklad rodinu adres IP verze 4 používanou v Internetu.</span><span class="sxs-lookup"><span data-stu-id="43272-112">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>

<span data-ttu-id="43272-113">Adresy IP verze 4 používají k určení síťové adresy 32 bitů.</span><span class="sxs-lookup"><span data-stu-id="43272-113">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="43272-114">Pro adresy třídy C pomocí masky sítě 255.255.255.0 jsou tyto bity rozděleny do čtyř oktetů.</span><span class="sxs-lookup"><span data-stu-id="43272-114">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="43272-115">Jsou-li čtyři oktety vyjádřeny v desítkové mlze, tvoří známou tečkovanou čtyřkolku, například 192.168.100.2.</span><span class="sxs-lookup"><span data-stu-id="43272-115">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="43272-116">První dva oktety (192.168 v tomto příkladu) tvoří číslo sítě, třetí oktet (100) definuje podsíť a konečný oktet (2) je identifikátor hostitele.</span><span class="sxs-lookup"><span data-stu-id="43272-116">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>

<span data-ttu-id="43272-117">Nastavení všech bitů adresy IP na jednu nebo 255.255.255.255 tvoří omezenou adresu vysílání.</span><span class="sxs-lookup"><span data-stu-id="43272-117">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="43272-118">Odeslání datagramu UDP na tuto adresu doručí zprávu libovolnému hostiteli v segmentu místní sítě.</span><span class="sxs-lookup"><span data-stu-id="43272-118">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="43272-119">Vzhledem k tomu, že směrovače nikdy nepředávají zprávy odeslané na tuto adresu, obdrží zprávu všesměrového vysílání pouze hostitelé v segmentu sítě.</span><span class="sxs-lookup"><span data-stu-id="43272-119">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>

<span data-ttu-id="43272-120">Všesměrové vysílání lze směrovat na určité části sítě nastavením všech bitů identifikátoru hostitele.</span><span class="sxs-lookup"><span data-stu-id="43272-120">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="43272-121">Chcete-li například odeslat vysílání všem hostitelům v síti označených adresami IP začínajícími na 192.168.1, použijte adresu 192.168.1.255.</span><span class="sxs-lookup"><span data-stu-id="43272-121">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>

<span data-ttu-id="43272-122">Následující příklad kódu <xref:System.Net.Sockets.UdpClient> používá a naslouchat datagramům UDP na portu 11 000.</span><span class="sxs-lookup"><span data-stu-id="43272-122">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams on port 11,000.</span></span> <span data-ttu-id="43272-123">Klient obdrží řetězec zprávy a zapíše zprávu do konzoly.</span><span class="sxs-lookup"><span data-stu-id="43272-123">The client receives a message string and writes the message to the console.</span></span>

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

<span data-ttu-id="43272-124">Následující příklad kódu <xref:System.Net.Sockets.Socket> používá datagramy UDP na adresu řízeného vysílání 192.168.1.255 pomocí portu 11 000.</span><span class="sxs-lookup"><span data-stu-id="43272-124">The following code example uses a <xref:System.Net.Sockets.Socket> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="43272-125">Klient odešle řetězec zprávy zadaný na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="43272-125">The client sends the message string specified on the command line.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="43272-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="43272-126">See also</span></span>

- <xref:System.Net.Sockets.UdpClient>
- <xref:System.Net.IPAddress>
