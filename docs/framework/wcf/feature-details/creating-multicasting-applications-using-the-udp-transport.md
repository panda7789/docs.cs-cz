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
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>Vytváření aplikací všesměrového vysílání pomocí přenosu UDP
Aplikace vícesměrového vysílání odesílají malé zprávy velkému počtu příjemců současně, aniž by bylo nutné navázat připojení Point-to-Point. Důrazem na takové aplikace je rychlost nad spolehlivostí. Jinými slovy je důležitější odesílat včasná data, než aby bylo zajištěno, že konkrétní zpráva je skutečně přijata. WCF teď podporuje psaní aplikací využívajících vícesměrové vysílání pomocí <xref:System.ServiceModel.UdpBinding> . Tento přenos je užitečný ve scénářích, kdy služba potřebuje posílat malé zprávy na několik klientů současně. Taková služba je příkladem takové služby.  
  
## <a name="implementing-a-multicast-application"></a>Implementace aplikace vícesměrového vysílání  
 K implementaci aplikace vícesměrového vysílání definujte kontrakt služby a pro každou součást softwaru, která potřebuje reagovat na zprávy vícesměrového vysílání, implementujte kontrakt služby. Například burzovní aplikace pro vyměřování může definovat kontrakt služby:  
  
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
  
 Každá aplikace, která chce přijímat zprávy vícesměrového vysílání, musí hostovat službu, která toto rozhraní zpřístupňuje.  Například zde je příklad kódu, který ukazuje, jak přijímat zprávy vícesměrového vysílání:  
  
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
  
 Aplikace určuje adresu UDP, na které budou všechny služby naslouchat. Vytvoří se nový, který bude <xref:System.ServiceModel.ServiceHost> vystavený koncový bod služby pomocí <xref:System.ServiceModel.UdpBinding> . <xref:System.ServiceModel.ServiceHost>Pak se otevře a začne naslouchat příchozím zprávám.  
  
 V tomto typu scénáře se jedná o klienta, který ve skutečnosti odesílá zprávy vícesměrového vysílání. Každá služba, která naslouchá na správné adrese UDP, bude dostávat zprávy vícesměrového vysílání. Tady je příklad klienta, který odesílá zprávy vícesměrového vysílání:  
  
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
  
 Tento kód vygeneruje skladové informace a pak pomocí kontraktu služby IStockTicker odesílá zprávy vícesměrového vysílání pro volání služeb, které naslouchá na správné adrese UDP.  
  
### <a name="udp-and-reliable-messaging"></a>UDP a spolehlivé zasílání zpráv  
  Vazba UDP nepodporuje spolehlivé zasílání zpráv z důvodu odlehčené povahy protokolu UDP. Pokud potřebujete potvrdit, že zprávy jsou přijímány vzdáleným koncovým bodem, použijte přenos, který podporuje spolehlivé zasílání zpráv jako HTTP nebo TCP. Další informace o spolehlivém zasílání zpráv najdete v tématu <https://go.microsoft.com/fwlink/?LinkId=231830> .  
  
### <a name="two-way-multicast-messaging"></a>Obousměrné zasílání zpráv vícesměrového vysílání  
 I když zprávy vícesměrového vysílání jsou všeobecně jednosměrné, UdpBinding podporuje výměnu zpráv žádostí a odpovědí. Zprávy odeslané pomocí přenosu UDP obsahují adresy od i do. Při použití adresy z se musí dbát na to, že by se mohla vést ke škodlivým změnám v cestě en-route.  Adresu lze zkontrolovat pomocí následujícího kódu:  
  
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
  
 Tento kód zkontroluje první bajt adresy z, aby bylo možné zjistit, zda obsahuje 0xE0, což znamená, že se jedná o adresu s vícenásobným přetypováním.  
  
### <a name="security-considerations"></a>Aspekty zabezpečení  
 Při naslouchání zpráv vícesměrového vysílání se paketu protokolu ICMP pošle do směrovače s oznámením, že nasloucháte na adrese vícesměrového vysílání. Kdokoli v místní podsíti, který má oprávnění, by mohl naslouchat těmto typům paketů a určit, na které adrese vícesměrového vysílání a portu nasloucháte.  
  
 Pro jakékoli účely zabezpečení nepoužívejte IP adresu odesílatele. Tyto informace můžou být falešné a můžou způsobit, že aplikace pošle odpovědi na nesprávný počítač. Jedním ze způsobů, jak tuto hrozbu zmírnit, je povolit zabezpečení na úrovni zpráv. Na úrovni sítě je možné použít také protokol IPSec (Internet Protocol Security) a/nebo NAP (Network Access Protection).
