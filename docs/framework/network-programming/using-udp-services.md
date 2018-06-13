---
title: Pomocí služby UDP
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
manager: markl
ms.openlocfilehash: bc325a551afd0190ea71b46cc53a275de635bda3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397631"
---
# <a name="using-udp-services"></a><span data-ttu-id="413b7-102">Pomocí služby UDP</span><span class="sxs-lookup"><span data-stu-id="413b7-102">Using UDP Services</span></span>
<span data-ttu-id="413b7-103"><xref:System.Net.Sockets.UdpClient> Třída komunikuje pomocí protokolu UDP síťové služby.</span><span class="sxs-lookup"><span data-stu-id="413b7-103">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="413b7-104">Vlastnosti a metody <xref:System.Net.Sockets.UdpClient> abstraktní třída podrobnosti o vytváření <xref:System.Net.Sockets.Socket> pro podávání žádostí a příjmu dat pomocí protokolu UDP.</span><span class="sxs-lookup"><span data-stu-id="413b7-104">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>  
  
 <span data-ttu-id="413b7-105">Protokol UDP (User Datagram) je jednoduchý protokol, který umožňuje usilovně k doručování dat do vzdáleného hostitele.</span><span class="sxs-lookup"><span data-stu-id="413b7-105">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="413b7-106">Protože protokolu UDP je protokol pro přenos, ale datagramy UDP odeslané na vzdálený koncový bod není zaručené doručení, ani jsou jejich zaručené doručení ve stejném pořadí, v níž jsou odesílány.</span><span class="sxs-lookup"><span data-stu-id="413b7-106">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="413b7-107">Aplikace, které používají UDP musí být připraveny pro zpracování datagramy chybí, duplicitní a mimo pořadí.</span><span class="sxs-lookup"><span data-stu-id="413b7-107">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>  
  
 <span data-ttu-id="413b7-108">Chcete-li odeslat datagram, používat UDP, musíte znát síťová adresa hostující službu, kterou budete potřebovat a číslo portu UDP, který služba používá pro komunikaci síťového zařízení.</span><span class="sxs-lookup"><span data-stu-id="413b7-108">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="413b7-109">Internet Assigned Numbers Authority (Iana) definuje čísla portů pro běžné služby (viz www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="413b7-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="413b7-110">Služby, které nejsou na seznamu Iana může mít čísla portů v rozsahu 1 024 jednotek do 65 535.</span><span class="sxs-lookup"><span data-stu-id="413b7-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="413b7-111">Speciální síťové adresy se používají pro podporu zprávy všesměrového vysílání UDP v sítích založených na protokolu IP.</span><span class="sxs-lookup"><span data-stu-id="413b7-111">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="413b7-112">Následující diskusi používá rodina IP verze 4 adres používaných na Internetu jako příklad.</span><span class="sxs-lookup"><span data-stu-id="413b7-112">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>  
  
 <span data-ttu-id="413b7-113">Zadejte rozsah adres protokolu IP verze 4 adresy pomocí 32bitová verze.</span><span class="sxs-lookup"><span data-stu-id="413b7-113">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="413b7-114">Pomocí síťová maska 255.255.255.0 adres třídy C jsou tyto bity rozdělené do čtyř oktety.</span><span class="sxs-lookup"><span data-stu-id="413b7-114">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="413b7-115">Když vyjádřené v desítkové soustavě, tvoří čtyři oktety obeznámeni s tečkami quad zápis, jako je například 192.168.100.2.</span><span class="sxs-lookup"><span data-stu-id="413b7-115">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="413b7-116">Číslo sítě tvoří první dva oktety (192.168 v tomto příkladu), třetí oktet (100) definuje podsíť a poslední oktet (2) je identifikátor hostitele.</span><span class="sxs-lookup"><span data-stu-id="413b7-116">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>  
  
 <span data-ttu-id="413b7-117">Nastavení služby bits IP adresy na jeden nebo 255.255.255.255, tvoří omezené adresy všesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="413b7-117">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="413b7-118">Odesílání datagramů UDP na tuto adresu doručení zprávy do libovolného hostitele v segmentu místní sítě.</span><span class="sxs-lookup"><span data-stu-id="413b7-118">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="413b7-119">Protože směrovače nikdy předávat zprávy odeslané na tuto adresu, jenom hostitelé v segmentu sítě přijímat zprávy všesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="413b7-119">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>  
  
 <span data-ttu-id="413b7-120">Vysílání můžete přesměrováni na konkrétní části sítě nastavením všechny bity identifikátor hostitele.</span><span class="sxs-lookup"><span data-stu-id="413b7-120">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="413b7-121">Například pokud chcete odeslat vysílání všichni hostitelé v síti, který začíná 192.168.1 IP adresy, použijte adresu 192.168.1.255.</span><span class="sxs-lookup"><span data-stu-id="413b7-121">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>  
  
 <span data-ttu-id="413b7-122">Následující příklad kódu používá <xref:System.Net.Sockets.UdpClient> naslouchat odeslané na směrovanou adresu vysílání 192.168.1.255 na portu 11 000 datagramy UDP.</span><span class="sxs-lookup"><span data-stu-id="413b7-122">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams sent to the directed broadcast address 192.168.1.255 on port 11,000.</span></span> <span data-ttu-id="413b7-123">Klient obdrží řetězec zprávy a zapíše zprávu do konzoly.</span><span class="sxs-lookup"><span data-stu-id="413b7-123">The client receives a message string and writes the message to the console.</span></span>  
  
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
  
 <span data-ttu-id="413b7-124">Následující příklad kódu používá <xref:System.Net.Sockets.UdpClient> odeslat datagramy UDP na směrovanou adresu vysílání 192.168.1.255, pomocí portu 11 000.</span><span class="sxs-lookup"><span data-stu-id="413b7-124">The following code example uses a <xref:System.Net.Sockets.UdpClient> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="413b7-125">Klient odešle zprávu řetězec zadaný v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="413b7-125">The client sends the message string specified on the command line.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="413b7-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="413b7-126">See Also</span></span>  
 <xref:System.Net.Sockets.UdpClient>  
 <xref:System.Net.IPAddress>  
 
