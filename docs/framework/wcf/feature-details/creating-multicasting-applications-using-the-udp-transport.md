---
title: Vytváření aplikací všesměrového vysílání pomocí přenosu UDP
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 40944129ce3b01d8422d5aba4cfbf913c56265ed
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144627"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="3aaca-102">Vytváření aplikací všesměrového vysílání pomocí přenosu UDP</span><span class="sxs-lookup"><span data-stu-id="3aaca-102">Creating Multicasting Applications using the UDP Transport</span></span>
<span data-ttu-id="3aaca-103">Aplikace vícesměrového vysílání odesílají malé zprávy velkému počtu příjemců současně, aniž by bylo nutné navázat připojení Point-to-Point.</span><span class="sxs-lookup"><span data-stu-id="3aaca-103">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="3aaca-104">Důrazem na takové aplikace je rychlost nad spolehlivostí.</span><span class="sxs-lookup"><span data-stu-id="3aaca-104">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="3aaca-105">Jinými slovy je důležitější odesílat včasná data, než aby bylo zajištěno, že konkrétní zpráva je skutečně přijata.</span><span class="sxs-lookup"><span data-stu-id="3aaca-105">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="3aaca-106">WCF teď podporuje psaní aplikací využívajících vícesměrové vysílání pomocí <xref:System.ServiceModel.UdpBinding> .</span><span class="sxs-lookup"><span data-stu-id="3aaca-106">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="3aaca-107">Tento přenos je užitečný ve scénářích, kdy služba potřebuje posílat malé zprávy na několik klientů současně.</span><span class="sxs-lookup"><span data-stu-id="3aaca-107">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="3aaca-108">Taková služba je příkladem takové služby.</span><span class="sxs-lookup"><span data-stu-id="3aaca-108">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="3aaca-109">Implementace aplikace vícesměrového vysílání</span><span class="sxs-lookup"><span data-stu-id="3aaca-109">Implementing a Multicast Application</span></span>  
 <span data-ttu-id="3aaca-110">K implementaci aplikace vícesměrového vysílání definujte kontrakt služby a pro každou součást softwaru, která potřebuje reagovat na zprávy vícesměrového vysílání, implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="3aaca-110">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="3aaca-111">Například burzovní aplikace pro vyměřování může definovat kontrakt služby:</span><span class="sxs-lookup"><span data-stu-id="3aaca-111">For example, a stock ticker application might define a service contract:</span></span>  
  
```csharp
// Shared contracts between the client and the service  
[ServiceContract]
interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void SendStockInfo(StockInfo[] stockInfo);
}

[DataContract]
class StockInfo
{
    [DataMember]
    public string Symbol;

    [DataMember]
    public float Price;

    public StockInfo(string symbol, float price)
    {
        this.Symbol = symbol;
        this.Price = price;
    }
}
```  
  
 <span data-ttu-id="3aaca-112">Každá aplikace, která chce přijímat zprávy vícesměrového vysílání, musí hostovat službu, která toto rozhraní zpřístupňuje.</span><span class="sxs-lookup"><span data-stu-id="3aaca-112">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="3aaca-113">Například zde je příklad kódu, který ukazuje, jak přijímat zprávy vícesměrového vysílání:</span><span class="sxs-lookup"><span data-stu-id="3aaca-113">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
```csharp
// Service Address
string serviceAddress = "soap.udp://224.0.0.1:40000";
// Binding
UdpBinding myBinding = new UdpBinding();
// Host
ServiceHost host = new ServiceHost(typeof(StockTickerService), new Uri(serviceAddress));
// Add service endpoint
host.AddServiceEndpoint(typeof(IStockTicker), myBinding, string.Empty);
// Openup the service host
host.Open();

Console.WriteLine("Start receiving stock information");
Console.ReadLine();
```  
  
 <span data-ttu-id="3aaca-114">Aplikace určuje adresu UDP, na které budou všechny služby naslouchat.</span><span class="sxs-lookup"><span data-stu-id="3aaca-114">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="3aaca-115">Vytvoří se nový, který bude <xref:System.ServiceModel.ServiceHost> vystavený koncový bod služby pomocí <xref:System.ServiceModel.UdpBinding> .</span><span class="sxs-lookup"><span data-stu-id="3aaca-115">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="3aaca-116"><xref:System.ServiceModel.ServiceHost>Pak se otevře a začne naslouchat příchozím zprávám.</span><span class="sxs-lookup"><span data-stu-id="3aaca-116">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="3aaca-117">V tomto typu scénáře se jedná o klienta, který ve skutečnosti odesílá zprávy vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="3aaca-117">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="3aaca-118">Každá služba, která naslouchá na správné adrese UDP, bude dostávat zprávy vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="3aaca-118">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="3aaca-119">Tady je příklad klienta, který odesílá zprávy vícesměrového vysílání:</span><span class="sxs-lookup"><span data-stu-id="3aaca-119">Here is an example of a client that sends out multicast messages:</span></span>  
  
```csharp
// Multicast Address
string serviceAddress = "soap.udp://224.0.0.1:40000";

// Binding
UdpBinding myBinding = new UdpBinding();

// Channel factory
ChannelFactory<IStockTicker> factory
    = new ChannelFactory<IStockTicker>(myBinding,
                new EndpointAddress(serviceAddress));

// Call service
IStockTicker proxy = factory.CreateChannel();

while (true)
{
    // This will continue to mulicast stock information
    proxy.SendStockInfo(GetStockInfo());
    Console.WriteLine($"sent stock info at {DateTime.Now}");
    // Wait for one second before sending another update
    System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));
}
```  
  
 <span data-ttu-id="3aaca-120">Tento kód vygeneruje skladové informace a pak pomocí kontraktu služby IStockTicker odesílá zprávy vícesměrového vysílání pro volání služeb, které naslouchá na správné adrese UDP.</span><span class="sxs-lookup"><span data-stu-id="3aaca-120">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="3aaca-121">UDP a spolehlivé zasílání zpráv</span><span class="sxs-lookup"><span data-stu-id="3aaca-121">UDP and Reliable Messaging</span></span>  
  <span data-ttu-id="3aaca-122">Vazba UDP nepodporuje spolehlivé zasílání zpráv z důvodu odlehčené povahy protokolu UDP.</span><span class="sxs-lookup"><span data-stu-id="3aaca-122">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="3aaca-123">Pokud potřebujete potvrdit, že zprávy jsou přijímány vzdáleným koncovým bodem, použijte přenos, který podporuje spolehlivé zasílání zpráv jako HTTP nebo TCP.</span><span class="sxs-lookup"><span data-stu-id="3aaca-123">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="3aaca-124">Další informace o spolehlivém zasílání zpráv najdete v tématu <https://go.microsoft.com/fwlink/?LinkId=231830> .</span><span class="sxs-lookup"><span data-stu-id="3aaca-124">For more information about reliable messaging, see <https://go.microsoft.com/fwlink/?LinkId=231830>.</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="3aaca-125">Obousměrné zasílání zpráv vícesměrového vysílání</span><span class="sxs-lookup"><span data-stu-id="3aaca-125">Two-way Multicast Messaging</span></span>  
 <span data-ttu-id="3aaca-126">I když zprávy vícesměrového vysílání jsou všeobecně jednosměrné, UdpBinding podporuje výměnu zpráv žádostí a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="3aaca-126">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="3aaca-127">Zprávy odeslané pomocí přenosu UDP obsahují adresy od i do.</span><span class="sxs-lookup"><span data-stu-id="3aaca-127">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="3aaca-128">Při použití adresy z se musí dbát na to, že by se mohla vést ke škodlivým změnám v cestě en-route.</span><span class="sxs-lookup"><span data-stu-id="3aaca-128">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="3aaca-129">Adresu lze zkontrolovat pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="3aaca-129">The address can be checked using the following code:</span></span>  
  
```csharp
if (address.AddressFamily == AddressFamily.InterNetwork)
{
    // IPv4
    byte[] addressBytes = address.GetAddressBytes();
    return ((addressBytes[0] & 0xE0) == 0xE0);
}
else
{
    // IPv6
    return address.IsIPv6Multicast;
}
```  
  
 <span data-ttu-id="3aaca-130">Tento kód zkontroluje první bajt adresy z, aby bylo možné zjistit, zda obsahuje 0xE0, což znamená, že se jedná o adresu s vícenásobným přetypováním.</span><span class="sxs-lookup"><span data-stu-id="3aaca-130">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="3aaca-131">Aspekty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3aaca-131">Security Considerations</span></span>  
 <span data-ttu-id="3aaca-132">Při naslouchání zpráv vícesměrového vysílání se paketu protokolu ICMP pošle do směrovače s oznámením, že nasloucháte na adrese vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="3aaca-132">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="3aaca-133">Kdokoli v místní podsíti, který má oprávnění, by mohl naslouchat těmto typům paketů a určit, na které adrese vícesměrového vysílání a portu nasloucháte.</span><span class="sxs-lookup"><span data-stu-id="3aaca-133">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="3aaca-134">Pro jakékoli účely zabezpečení nepoužívejte IP adresu odesílatele.</span><span class="sxs-lookup"><span data-stu-id="3aaca-134">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="3aaca-135">Tyto informace můžou být falešné a můžou způsobit, že aplikace pošle odpovědi na nesprávný počítač.</span><span class="sxs-lookup"><span data-stu-id="3aaca-135">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="3aaca-136">Jedním ze způsobů, jak tuto hrozbu zmírnit, je povolit zabezpečení na úrovni zpráv.</span><span class="sxs-lookup"><span data-stu-id="3aaca-136">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="3aaca-137">Na úrovni sítě je možné použít také protokol IPSec (Internet Protocol Security) a/nebo NAP (Network Access Protection).</span><span class="sxs-lookup"><span data-stu-id="3aaca-137">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
