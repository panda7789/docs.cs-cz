---
title: Vytváření aplikací všesměrového vysílání pomocí přenosu UDP
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 89ac99ffec614eeebd076f9868568dcf2c7b04fd
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45587321"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>Vytváření aplikací všesměrového vysílání pomocí přenosu UDP
Vícesměrové vysílání aplikace odesílat zprávy malé velký počet příjemců ve stejnou dobu bez nutnosti vytvářet bod pro bod připojení. Zvýraznění takové aplikace je rychlost spolehlivost. Jinými slovy je důležitější zaslat včas dat, než se ujistěte se, že ve skutečnosti přijetí žádné konkrétní zprávu. WCF teď podporuje vytváření aplikací s použitím vícesměrového vysílání <xref:System.ServiceModel.UdpBinding>. Tento přenos je užitečné v situacích, kdy služba potřebuje odeslat malých zpráv na počet klientů najednou. Aplikace akciích je příkladem takové služby.  
  
## <a name="implementing-a-multicast-application"></a>Implementace aplikace pro vícesměrové vysílání  
 K implementaci aplikace vícesměrového vysílání, definování kontraktu služby a pro každý softwarová součást, kterou je potřeba reagovat na zprávy vícesměrového vysílání, implementace kontraktu služby. Například může aplikace akciích definování kontraktu služby:  
  
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
  
 Každá aplikace, který chce dostávat zprávy vícesměrového vysílání musí hostovat službu, která poskytuje toto rozhraní.  Například tady je ukázka kódu, který ukazuje, jak přijmout zprávy vícesměrového vysílání:  
  
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
  
 Aplikace určuje adresu UDP, který bude naslouchat všechny služby. Nový <xref:System.ServiceModel.ServiceHost> se vytvoří a koncový bod služby je přístupné přes <xref:System.ServiceModel.UdpBinding>. <xref:System.ServiceModel.ServiceHost> Potom se otevře a spustí se naslouchání pro příchozí zprávy.  
  
 V takové situaci je klienta, který ve skutečnosti odesílá zprávy vícesměrového vysílání. Každá služba, která naslouchá na správné adrese UDP bude přijímat zprávy vícesměrového vysílání. Tady je příklad z klienta, který odesílá zprávy vícesměrového vysílání:  
  
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
  
 Tento kód vygeneruje základní informace a potom pomocí kontraktu služby IStockTicker odesílat zprávy vícesměrového vysílání volat služby naslouchá na správnou adresu UDP.  
  
### <a name="udp-and-reliable-messaging"></a>Spolehlivé zasílání zpráv a UDP  
 Vazba protokolu UDP nepodporuje spolehlivé zasílání zpráv vzhledem k povaze zjednodušené protokolu UDP. Pokud je potřeba potvrdit, že zprávy jsou přijímány vzdálený koncový bod, používejte přenos, který podporuje spolehlivé zasílání zpráv protokolu HTTP nebo TCP. Další informace o spolehlivé zasílání zpráv najdete v tématu https://go.microsoft.com/fwlink/?LinkId=231830  
  
### <a name="two-way-multicast-messaging"></a>Zasílání zpráv obousměrný vícesměrového vysílání  
 Zatímco jsou obecně jednosměrné zprávy vícesměrového vysílání, UdpBinding podporuje výměně zpráv žádost odpověď. Zprávy odesílané pomocí přenosu UDP obsahovat oba From a adresu. Při použití adresa odesílatele jako nebezpečným způsobem je možné změnit en-route musí věnovat pozornost.  Adresu můžete zkontrolovat pomocí následujícího kódu:  
  
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
  
 Tento kód kontroluje první bajt adresa odesílatele, zda obsahuje 0xE0, což znamená, že adresa je adresu vícesměrového vysílání.  
  
### <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Při naslouchání zpráv vícesměrového vysílání paketu ICMP přijde na směrovač upozornění, pokud jsou naslouchání na adrese vícesměrového vysílání. Naslouchání pro tyto typy paketů a určení, které adresy vícesměrového vysílání a port naslouchají na může každý v místní podsíti, kteří mají oprávnění.  
  
 Nepoužívejte IP adresa odesílatele pro účely zabezpečení. Tyto informace mohou být falešné a může způsobit, že aplikace k odeslání odpovědi na nesprávný počítač. Jedním ze způsobů pro zmírnění této hrozby je povolit zabezpečení na úrovni zprávy. Na webu MSDN network úrovně protokolu IPSec (Internet Protocol Security) a/nebo architektury NAP (Network Access Protection) může také použít.
