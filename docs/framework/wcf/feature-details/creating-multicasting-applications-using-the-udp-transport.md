---
title: "Vytváření aplikací všesměrového vysílání pomocí přenosu UDP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57c30c8b6b381be931789f3f64cbd26943bb2b34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="bb282-102">Vytváření aplikací všesměrového vysílání pomocí přenosu UDP</span><span class="sxs-lookup"><span data-stu-id="bb282-102">Creating Multicasting Applications using the UDP Transport</span></span>
<span data-ttu-id="bb282-103">Malé zprávy na velký počet příjemců vícesměrového vysílání aplikace posílat ve stejnou dobu, aniž by bylo nutné vytvořit bod nebo bod připojení.</span><span class="sxs-lookup"><span data-stu-id="bb282-103">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="bb282-104">Důraz takové aplikace je rychlost nad spolehlivost.</span><span class="sxs-lookup"><span data-stu-id="bb282-104">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="bb282-105">Jinými slovy je důležité k odeslání včas dat, než se ujistěte se, že je ve skutečnosti přijatá žádné konkrétní zpráva.</span><span class="sxs-lookup"><span data-stu-id="bb282-105">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="bb282-106">WCF teď podporuje zápis vícesměrového vysílání aplikací pomocí <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="bb282-106">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="bb282-107">Tento přenos je užitečný ve scénářích, kde se služba potřebuje k odeslání zprávy malý počet klientů současně.</span><span class="sxs-lookup"><span data-stu-id="bb282-107">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="bb282-108">Běžícími aplikace je příkladem těchto služeb.</span><span class="sxs-lookup"><span data-stu-id="bb282-108">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="bb282-109">Implementace vícesměrového vysílání aplikace</span><span class="sxs-lookup"><span data-stu-id="bb282-109">Implementing a Multicast Application</span></span>  
 <span data-ttu-id="bb282-110">Chcete-li implementovat vícesměrového vysílání aplikace, definování kontraktu služby a pro každou součást softwaru, který potřebuje reagovat na zprávy vícesměrového vysílání, implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="bb282-110">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="bb282-111">Například může aplikace běžícími definování kontraktu služby:</span><span class="sxs-lookup"><span data-stu-id="bb282-111">For example, a stock ticker application might define a service contract:</span></span>  
  
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
  
 <span data-ttu-id="bb282-112">Všech aplikací, které chce dostávat zprávy vícesměrového vysílání, musí hostitel služby, která zveřejňuje toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bb282-112">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="bb282-113">Například zde je ukázka kódu, která ukazuje, jak přijmout zprávy vícesměrového vysílání:</span><span class="sxs-lookup"><span data-stu-id="bb282-113">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="bb282-114">Aplikace určuje adresu UDP, který bude naslouchat všechny služby.</span><span class="sxs-lookup"><span data-stu-id="bb282-114">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="bb282-115">Nový <xref:System.ServiceModel.ServiceHost> je vytvořena a koncový bod služby je vystaven pomocí <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="bb282-115">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="bb282-116"><xref:System.ServiceModel.ServiceHost> Je pak otevřít a začne naslouchat pro příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="bb282-116">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="bb282-117">V takové situaci je klienta, která ve skutečnosti odesílá zprávy vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="bb282-117">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="bb282-118">Každá služba, která naslouchá na správnou adresu UDP obdrží zprávy vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="bb282-118">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="bb282-119">Tady je příklad klienta, který odesílá zprávy vícesměrového vysílání:</span><span class="sxs-lookup"><span data-stu-id="bb282-119">Here is an example of a client that sends out multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="bb282-120">Tento kód generuje uložené informace a pak použije kontrakt služby IStockTicker k odeslání zprávy vícesměrového vysílání volat služby naslouchá na správnou adresu UDP.</span><span class="sxs-lookup"><span data-stu-id="bb282-120">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="bb282-121">Spolehlivé zasílání zpráv a UDP</span><span class="sxs-lookup"><span data-stu-id="bb282-121">UDP and Reliable Messaging</span></span>  
 <span data-ttu-id="bb282-122">Vazba UDP nepodporuje spolehlivé zasílání zpráv z důvodu lightweight povaha protokol UDP.</span><span class="sxs-lookup"><span data-stu-id="bb282-122">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="bb282-123">Pokud je nutné potvrdit, že vzdálený koncový bod přijímá zprávy, použijte přenos, který podporuje spolehlivé zasílání zpráv protokolu HTTP nebo TCP.</span><span class="sxs-lookup"><span data-stu-id="bb282-123">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="bb282-124">Další informace o spolehlivé zasílání zpráv najdete v části http://go.microsoft.com/fwlink/?LinkId=231830</span><span class="sxs-lookup"><span data-stu-id="bb282-124">For more information about reliable messaging see http://go.microsoft.com/fwlink/?LinkId=231830</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="bb282-125">Zasílání zpráv obousměrný vícesměrového vysílání</span><span class="sxs-lookup"><span data-stu-id="bb282-125">Two-way Multicast Messaging</span></span>  
 <span data-ttu-id="bb282-126">Zprávy vícesměrového vysílání jsou obecně jednosměrné, podporuje UdpBinding exchange zprávu požadavku/odpovědi.</span><span class="sxs-lookup"><span data-stu-id="bb282-126">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="bb282-127">Zprávy odeslané pomocí přenosu UDP obsahovat obě From a adresu.</span><span class="sxs-lookup"><span data-stu-id="bb282-127">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="bb282-128">Musí dát pozor při pomocí adresa odesílatele, může to být neoprávněnému změně en trasy.</span><span class="sxs-lookup"><span data-stu-id="bb282-128">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="bb282-129">Adresu můžete zkontrolovat pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="bb282-129">The address can be checked using the following code:</span></span>  
  
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
  
 <span data-ttu-id="bb282-130">Tento kód kontroluje první bajt adresa odesílatele chcete zobrazit, pokud obsahuje 0xE0, která znamená, že adresa je adresu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="bb282-130">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="bb282-131">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bb282-131">Security Considerations</span></span>  
 <span data-ttu-id="bb282-132">Pokud naslouchá pro zprávy vícesměrového vysílání paketu ICMP se odesílají do směrovače, upozornění, pokud jsou naslouchá na adrese vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="bb282-132">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="bb282-133">Každý, kdo v místní podsíti, který má oprávnění může naslouchat pro tyto typy paketů a určení, které adresy vícesměrového vysílání a portu jsou naslouchá na.</span><span class="sxs-lookup"><span data-stu-id="bb282-133">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="bb282-134">Nepoužívejte k jakýmkoli jiným účelům zabezpečení IP adresu odesílatele.</span><span class="sxs-lookup"><span data-stu-id="bb282-134">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="bb282-135">Tyto informace mohou být falešné a může způsobit, že aplikace k odeslání odpovědi na nesprávný počítač.</span><span class="sxs-lookup"><span data-stu-id="bb282-135">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="bb282-136">Jedním ze způsobů pro zmírnění této hrozby je umožnit úrovně zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="bb282-136">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="bb282-137">V síti úroveň protokolu IPSec (Internet Protocol Security) nebo architekturu NAP (Network Access Protection) může také použít.</span><span class="sxs-lookup"><span data-stu-id="bb282-137">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
