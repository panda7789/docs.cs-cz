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
ms.openlocfilehash: 3dde7dc8b051c4238203173bd009a8f71dd9c6c3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>Vytváření aplikací všesměrového vysílání pomocí přenosu UDP
Malé zprávy na velký počet příjemců vícesměrového vysílání aplikace posílat ve stejnou dobu, aniž by bylo nutné vytvořit bod nebo bod připojení. Důraz takové aplikace je rychlost nad spolehlivost. Jinými slovy je důležité k odeslání včas dat, než se ujistěte se, že je ve skutečnosti přijatá žádné konkrétní zpráva. WCF teď podporuje zápis vícesměrového vysílání aplikací pomocí <xref:System.ServiceModel.UdpBinding>. Tento přenos je užitečný ve scénářích, kde se služba potřebuje k odeslání zprávy malý počet klientů současně. Běžícími aplikace je příkladem těchto služeb.  
  
## <a name="implementing-a-multicast-application"></a>Implementace vícesměrového vysílání aplikace  
 Chcete-li implementovat vícesměrového vysílání aplikace, definování kontraktu služby a pro každou součást softwaru, který potřebuje reagovat na zprávy vícesměrového vysílání, implementujte kontrakt služby. Například může aplikace běžícími definování kontraktu služby:  
  
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
  
 Všech aplikací, které chce dostávat zprávy vícesměrového vysílání, musí hostitel služby, která zveřejňuje toto rozhraní.  Například zde je ukázka kódu, která ukazuje, jak přijmout zprávy vícesměrového vysílání:  
  
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
  
 Aplikace určuje adresu UDP, který bude naslouchat všechny služby. Nový <xref:System.ServiceModel.ServiceHost> je vytvořena a koncový bod služby je vystaven pomocí <xref:System.ServiceModel.UdpBinding>. <xref:System.ServiceModel.ServiceHost> Je pak otevřít a začne naslouchat pro příchozí zprávy.  
  
 V takové situaci je klienta, která ve skutečnosti odesílá zprávy vícesměrového vysílání. Každá služba, která naslouchá na správnou adresu UDP obdrží zprávy vícesměrového vysílání. Tady je příklad klienta, který odesílá zprávy vícesměrového vysílání:  
  
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
  
 Tento kód generuje uložené informace a pak použije kontrakt služby IStockTicker k odeslání zprávy vícesměrového vysílání volat služby naslouchá na správnou adresu UDP.  
  
### <a name="udp-and-reliable-messaging"></a>Spolehlivé zasílání zpráv a UDP  
 Vazba UDP nepodporuje spolehlivé zasílání zpráv z důvodu lightweight povaha protokol UDP. Pokud je nutné potvrdit, že vzdálený koncový bod přijímá zprávy, použijte přenos, který podporuje spolehlivé zasílání zpráv protokolu HTTP nebo TCP. Další informace o spolehlivé zasílání zpráv najdete v části http://go.microsoft.com/fwlink/?LinkId=231830  
  
### <a name="two-way-multicast-messaging"></a>Zasílání zpráv obousměrný vícesměrového vysílání  
 Zprávy vícesměrového vysílání jsou obecně jednosměrné, podporuje UdpBinding exchange zprávu požadavku/odpovědi. Zprávy odeslané pomocí přenosu UDP obsahovat obě From a adresu. Musí dát pozor při pomocí adresa odesílatele, může to být neoprávněnému změně en trasy.  Adresu můžete zkontrolovat pomocí následujícího kódu:  
  
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
  
 Tento kód kontroluje první bajt adresa odesílatele chcete zobrazit, pokud obsahuje 0xE0, která znamená, že adresa je adresu vícesměrového vysílání.  
  
### <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Pokud naslouchá pro zprávy vícesměrového vysílání paketu ICMP se odesílají do směrovače, upozornění, pokud jsou naslouchá na adrese vícesměrového vysílání. Každý, kdo v místní podsíti, který má oprávnění může naslouchat pro tyto typy paketů a určení, které adresy vícesměrového vysílání a portu jsou naslouchá na.  
  
 Nepoužívejte k jakýmkoli jiným účelům zabezpečení IP adresu odesílatele. Tyto informace mohou být falešné a může způsobit, že aplikace k odeslání odpovědi na nesprávný počítač. Jedním ze způsobů pro zmírnění této hrozby je umožnit úrovně zabezpečení zpráv. V síti úroveň protokolu IPSec (Internet Protocol Security) nebo architekturu NAP (Network Access Protection) může také použít.
