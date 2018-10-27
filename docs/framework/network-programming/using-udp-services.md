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
ms.openlocfilehash: 8f0c34b2226863bc04800ac4558c07e969f02154
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50191126"
---
# <a name="using-udp-services"></a><span data-ttu-id="4f8a1-102">Použití služeb UDP</span><span class="sxs-lookup"><span data-stu-id="4f8a1-102">Using UDP Services</span></span>
<span data-ttu-id="4f8a1-103"><xref:System.Net.Sockets.UdpClient> Třídy komunikuje se síťovými službami pomocí protokolu UDP.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-103">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="4f8a1-104">Vlastnosti a metody <xref:System.Net.Sockets.UdpClient> třídy abstraktní podrobnosti o vytváření <xref:System.Net.Sockets.Socket> pro podávání žádostí a příjmu dat pomocí protokolu UDP.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-104">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>  
  
 <span data-ttu-id="4f8a1-105">Protokolu UDP (User Datagram) je jednoduchý protokol, který se pokusí k doručování dat vzdáleného hostitele.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-105">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="4f8a1-106">Ale protože protokolu UDP je protokol pro přenos, odeslané na vzdálený koncový bod datagramy UDP zaručené doručení ani jsou zaručeně dorazí ve stejném pořadí, ve které se odesílají.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-106">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="4f8a1-107">Aplikace, které používají UDP musí být připravena ke zpracování datagramy chybí, duplicitní a mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-107">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>  
  
 <span data-ttu-id="4f8a1-108">K odeslání datagram pomocí protokolu UDP, musíte znát síťová adresa síťového zařízení, který je hostitelem služby, které potřebujete a číslo portu UDP, který službu používá ke komunikaci.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-108">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="4f8a1-109">Internet Assigned Numbers Authority (Iana) definuje čísla portů pro běžné služby (viz [název služby a registru číslo portu protokolu přenosu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="4f8a1-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="4f8a1-110">Služby není na seznamu Iana může mít čísla portu v rozsahu 1 024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="4f8a1-111">Speciální síťové adresy se používají pro podporu všesměrového vysílání zpráv UDP v sítích založených na protokolu IP.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-111">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="4f8a1-112">Následující diskuse používá rodina IP verze 4 adres jako příklad je použita na Internetu.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-112">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>  
  
 <span data-ttu-id="4f8a1-113">Adresy IP verze 4 použijte k určení síťová adresa 32 bitů.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-113">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="4f8a1-114">Pomocí síťová maska 255.255.255.0 adres třídy C tyto bity jsou rozdělené do čtyř oktetech.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-114">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="4f8a1-115">Když vyjádřené v desítkové soustavě, tvoří čtyři oktety známými notacemi čtyřmi tečkami, jako je například 192.168.100.2.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-115">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="4f8a1-116">Číslo sítě tvoří první dva oktety (192.168 v tomto příkladu), třetí octet (100) definuje podsíť a poslední oktet (2) je identifikátor hostitele.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-116">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>  
  
 <span data-ttu-id="4f8a1-117">Nastavení všechny bity IP adresy na jeden nebo 255.255.255.255 tvoří omezené adresa všesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-117">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="4f8a1-118">Odesílání UDP datagram na tuto adresu doručí do libovolného hostitele v místní síti segmentu.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-118">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="4f8a1-119">Protože směrovače nikdy předávat zprávy na tuto adresu, zobrazí se pouze hostitelé v segmentu sítě všesměrového vysílání zpráva.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-119">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>  
  
 <span data-ttu-id="4f8a1-120">Vysílání mohou přesměrováni na konkrétní části sítě tak, že nastavíte všechny bity identifikátor hostitele.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-120">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="4f8a1-121">Například k odesílání vysílání pro všechny hostitele v síti identifikovaných podle IP adresy, počínaje 192.168.1 použijte adresu 192.168.1.255.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-121">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>  
  
 <span data-ttu-id="4f8a1-122">Následující příklad kódu používá <xref:System.Net.Sockets.UdpClient> pro naslouchání odeslané na směrovanou adresu vysílání 192.168.1.255 na portu 11 000 datagramy UDP.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-122">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams sent to the directed broadcast address 192.168.1.255 on port 11,000.</span></span> <span data-ttu-id="4f8a1-123">Klient obdrží řetězec zprávy a zapisuje zprávy do konzoly.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-123">The client receives a message string and writes the message to the console.</span></span>  
  
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
  
 <span data-ttu-id="4f8a1-124">Následující příklad kódu používá <xref:System.Net.Sockets.UdpClient> odesílat datagramů UDP na směrovanou adresu vysílání 192.168.1.255, pomocí portů 11 000.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-124">The following code example uses a <xref:System.Net.Sockets.UdpClient> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="4f8a1-125">Klient odešle zprávu řetězci zadanému na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="4f8a1-125">The client sends the message string specified on the command line.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f8a1-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f8a1-126">See Also</span></span>  
 <xref:System.Net.Sockets.UdpClient>  
 <xref:System.Net.IPAddress>  
 
