---
title: Vytváření aplikací všesměrového vysílání pomocí přenosu UDP
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 6825aaafe87ae362fd9266f7c7a82a36d054a69f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185245"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>Vytváření aplikací všesměrového vysílání pomocí přenosu UDP
Aplikace vícesměrového vysílání odesílají malé zprávy velkému počtu příjemců současně bez nutnosti navazovat připojení z bodu do bodu. Důraz těchto aplikací je rychlost nad spolehlivostí. Jinými slovy je důležitější odesílat včasná data než zajistit, aby byla skutečně přijata jakákoli konkrétní zpráva. WCF nyní podporuje zápis vícesměrového vysílání aplikací pomocí <xref:System.ServiceModel.UdpBinding>. Tento přenos je užitečné ve scénářích, kde služba potřebuje odeslat malé zprávy na počet klientů současně. Příkladem takové služby je burzovní aplikace.  
  
## <a name="implementing-a-multicast-application"></a>Implementace aplikace vícesměrového vysílání  
 Chcete-li implementovat aplikaci vícesměrového vysílání, definujte servisní smlouvu a pro každou softwarovou součást, která potřebuje reagovat na zprávy vícesměrového vysílání, implementujte servisní smlouvu. Například burzovní aplikace může definovat servisní smlouvu:  
  
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
  
 Každá aplikace, která chce přijímat zprávy vícesměrového vysílání, musí být hostitelem služby, která zpřístupňuje toto rozhraní.  Zde je například ukázka kódu, která ukazuje, jak přijímat zprávy vícesměrového vysílání:  
  
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
  
 Aplikace určuje adresu UDP, na které budou poslouchat všechny služby. Vytvoří <xref:System.ServiceModel.ServiceHost> se nový a koncový bod služby <xref:System.ServiceModel.UdpBinding>je vystaven pomocí . Poté <xref:System.ServiceModel.ServiceHost> se otevře a začne naslouchat příchozím zprávám.  
  
 V tomto typu scénáře je klient, který skutečně odesílá zprávy vícesměrového vysílání. Každá služba, která naslouchá na správné adrese UDP, obdrží zprávy vícesměrového vysílání. Zde je příklad klienta, který odesílá zprávy vícesměrového vysílání:  
  
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
  
 Tento kód generuje informace o akciích a potom používá servisní smlouvu IStockTicker k odesílání zpráv vícesměrového vysílání pro volání služeb naslouchání na správné adrese UDP.  
  
### <a name="udp-and-reliable-messaging"></a>UDP a spolehlivé zasílání zpráv  
 Vazba UDP nepodporuje spolehlivé zasílání zpráv z důvodu zjednodušené povahy protokolu UDP. Pokud potřebujete potvrdit, že zprávy jsou přijímány vzdálený koncový bod, použijte přenos, který podporuje spolehlivé zasílání zpráv, jako je HTTP nebo TCP. Další informace o spolehlivých zprávách naleznete v tématuhttps://go.microsoft.com/fwlink/?LinkId=231830  
  
### <a name="two-way-multicast-messaging"></a>Obousměrné zasílání zpráv vícesměrového vysílání  
 Zatímco zprávy vícesměrového vysílání jsou obecně jednosměrné, UdpBinding podporuje výměnu žádostí a odpovědí. Zprávy odeslané pomocí přenosu UDP obsahují adresu Od i Do. Při použití adresy Od je třeba dbát na to, aby mohla být na cestě změněna.  Adresu lze zkontrolovat pomocí následujícího kódu:  
  
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
  
 Tento kód zkontroluje první bajt adresy Od a zjistí, zda obsahuje 0xE0, což znamená, že adresa je vícesměrová adresa.  
  
### <a name="security-considerations"></a>Aspekty zabezpečení  
 Při naslouchání zprávám vícesměrového vysílání je směrovači odeslán paket ICMP s upozorněním, že nasloucháte na adrese vícesměrového vysílání. Kdokoli v místní podsíti, který má oprávnění, může naslouchat těmto typům paketů a určit, na které adrese a portu vícesměrového vysílání nasloucháte.  
  
 Nepoužívejte IP adresu odesílatele pro žádné bezpečnostní účely. Tyto informace mohou být zfalšovány a mohou způsobit, že aplikace odešle odpovědi nesprávnému počítači. Jedním ze způsobů, jak zmírnit tuto hrozbu, je povolit zabezpečení na úrovni zprávy. Na úrovni sítě lze použít také protokol IPSec (Internet Protocol Security) a/nebo NAP (Ochrana přístupu k síti).
