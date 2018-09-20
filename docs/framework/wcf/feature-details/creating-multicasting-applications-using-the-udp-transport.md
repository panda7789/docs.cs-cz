---
title: Vytváření aplikací všesměrového vysílání pomocí přenosu UDP
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 89ac99ffec614eeebd076f9868568dcf2c7b04fd
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46324750"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="4f584-102">Vytváření aplikací všesměrového vysílání pomocí přenosu UDP</span><span class="sxs-lookup"><span data-stu-id="4f584-102">Creating Multicasting Applications using the UDP Transport</span></span>
<span data-ttu-id="4f584-103">Vícesměrové vysílání aplikace odesílat zprávy malé velký počet příjemců ve stejnou dobu bez nutnosti vytvářet bod pro bod připojení.</span><span class="sxs-lookup"><span data-stu-id="4f584-103">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="4f584-104">Zvýraznění takové aplikace je rychlost spolehlivost.</span><span class="sxs-lookup"><span data-stu-id="4f584-104">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="4f584-105">Jinými slovy je důležitější zaslat včas dat, než se ujistěte se, že ve skutečnosti přijetí žádné konkrétní zprávu.</span><span class="sxs-lookup"><span data-stu-id="4f584-105">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="4f584-106">WCF teď podporuje vytváření aplikací s použitím vícesměrového vysílání <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="4f584-106">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="4f584-107">Tento přenos je užitečné v situacích, kdy služba potřebuje odeslat malých zpráv na počet klientů najednou.</span><span class="sxs-lookup"><span data-stu-id="4f584-107">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="4f584-108">Aplikace akciích je příkladem takové služby.</span><span class="sxs-lookup"><span data-stu-id="4f584-108">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="4f584-109">Implementace aplikace pro vícesměrové vysílání</span><span class="sxs-lookup"><span data-stu-id="4f584-109">Implementing a Multicast Application</span></span>  
 <span data-ttu-id="4f584-110">K implementaci aplikace vícesměrového vysílání, definování kontraktu služby a pro každý softwarová součást, kterou je potřeba reagovat na zprávy vícesměrového vysílání, implementace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="4f584-110">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="4f584-111">Například může aplikace akciích definování kontraktu služby:</span><span class="sxs-lookup"><span data-stu-id="4f584-111">For example, a stock ticker application might define a service contract:</span></span>  
  
```  
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
  
 <span data-ttu-id="4f584-112">Každá aplikace, který chce dostávat zprávy vícesměrového vysílání musí hostovat službu, která poskytuje toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4f584-112">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="4f584-113">Například tady je ukázka kódu, který ukazuje, jak přijmout zprávy vícesměrového vysílání:</span><span class="sxs-lookup"><span data-stu-id="4f584-113">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
```  
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
  
 <span data-ttu-id="4f584-114">Aplikace určuje adresu UDP, který bude naslouchat všechny služby.</span><span class="sxs-lookup"><span data-stu-id="4f584-114">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="4f584-115">Nový <xref:System.ServiceModel.ServiceHost> se vytvoří a koncový bod služby je přístupné přes <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="4f584-115">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="4f584-116"><xref:System.ServiceModel.ServiceHost> Potom se otevře a spustí se naslouchání pro příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="4f584-116">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="4f584-117">V takové situaci je klienta, který ve skutečnosti odesílá zprávy vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="4f584-117">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="4f584-118">Každá služba, která naslouchá na správné adrese UDP bude přijímat zprávy vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="4f584-118">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="4f584-119">Tady je příklad z klienta, který odesílá zprávy vícesměrového vysílání:</span><span class="sxs-lookup"><span data-stu-id="4f584-119">Here is an example of a client that sends out multicast messages:</span></span>  
  
```  
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
    Console.WriteLine(String.Format("sent stock info at {0}", DateTime.Now));
    // Wait for one second before sending another update
    System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));
}
```  
  
 <span data-ttu-id="4f584-120">Tento kód vygeneruje základní informace a potom pomocí kontraktu služby IStockTicker odesílat zprávy vícesměrového vysílání volat služby naslouchá na správnou adresu UDP.</span><span class="sxs-lookup"><span data-stu-id="4f584-120">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="4f584-121">Spolehlivé zasílání zpráv a UDP</span><span class="sxs-lookup"><span data-stu-id="4f584-121">UDP and Reliable Messaging</span></span>  
 <span data-ttu-id="4f584-122">Vazba protokolu UDP nepodporuje spolehlivé zasílání zpráv vzhledem k povaze zjednodušené protokolu UDP.</span><span class="sxs-lookup"><span data-stu-id="4f584-122">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="4f584-123">Pokud je potřeba potvrdit, že zprávy jsou přijímány vzdálený koncový bod, používejte přenos, který podporuje spolehlivé zasílání zpráv protokolu HTTP nebo TCP.</span><span class="sxs-lookup"><span data-stu-id="4f584-123">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="4f584-124">Další informace o spolehlivé zasílání zpráv najdete v tématu https://go.microsoft.com/fwlink/?LinkId=231830</span><span class="sxs-lookup"><span data-stu-id="4f584-124">For more information about reliable messaging see https://go.microsoft.com/fwlink/?LinkId=231830</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="4f584-125">Zasílání zpráv obousměrný vícesměrového vysílání</span><span class="sxs-lookup"><span data-stu-id="4f584-125">Two-way Multicast Messaging</span></span>  
 <span data-ttu-id="4f584-126">Zatímco jsou obecně jednosměrné zprávy vícesměrového vysílání, UdpBinding podporuje výměně zpráv žádost odpověď.</span><span class="sxs-lookup"><span data-stu-id="4f584-126">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="4f584-127">Zprávy odesílané pomocí přenosu UDP obsahovat oba From a adresu.</span><span class="sxs-lookup"><span data-stu-id="4f584-127">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="4f584-128">Při použití adresa odesílatele jako nebezpečným způsobem je možné změnit en-route musí věnovat pozornost.</span><span class="sxs-lookup"><span data-stu-id="4f584-128">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="4f584-129">Adresu můžete zkontrolovat pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="4f584-129">The address can be checked using the following code:</span></span>  
  
```  
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
  
 <span data-ttu-id="4f584-130">Tento kód kontroluje první bajt adresa odesílatele, zda obsahuje 0xE0, což znamená, že adresa je adresu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="4f584-130">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="4f584-131">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4f584-131">Security Considerations</span></span>  
 <span data-ttu-id="4f584-132">Při naslouchání zpráv vícesměrového vysílání paketu ICMP přijde na směrovač upozornění, pokud jsou naslouchání na adrese vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="4f584-132">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="4f584-133">Naslouchání pro tyto typy paketů a určení, které adresy vícesměrového vysílání a port naslouchají na může každý v místní podsíti, kteří mají oprávnění.</span><span class="sxs-lookup"><span data-stu-id="4f584-133">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="4f584-134">Nepoužívejte IP adresa odesílatele pro účely zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4f584-134">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="4f584-135">Tyto informace mohou být falešné a může způsobit, že aplikace k odeslání odpovědi na nesprávný počítač.</span><span class="sxs-lookup"><span data-stu-id="4f584-135">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="4f584-136">Jedním ze způsobů pro zmírnění této hrozby je povolit zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="4f584-136">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="4f584-137">Na webu MSDN network úrovně protokolu IPSec (Internet Protocol Security) a/nebo architektury NAP (Network Access Protection) může také použít.</span><span class="sxs-lookup"><span data-stu-id="4f584-137">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
