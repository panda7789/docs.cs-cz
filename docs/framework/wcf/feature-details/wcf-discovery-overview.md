---
title: Přehled zjišťování WCF
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: 449d54e0dd1948885a7298fb4da46067de3eb9d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184204"
---
# <a name="wcf-discovery-overview"></a>Přehled zjišťování WCF
Rozhraní API zjišťování poskytují jednotný programovací model pro dynamickou publikaci a zjišťování webových služeb pomocí protokolu WS-Discovery. Tato řešení API umožňují službám publikovat sebe a klienty k vyhledání publikovaných služeb. Jakmile je služba zjistitelná, služba má možnost odesílat zprávy oznámení, stejně jako naslouchat a reagovat na požadavky na zjišťování. Zjistitelné služby mohou posílat hello zprávy oznámit jejich příchod u sítě a Bye zprávy oznámit jejich odchod ze sítě. Chcete-li najít službu, klienti odešlou požadavek, `Probe` který obsahuje konkrétní kritéria, jako je typ smlouvy o poskytování služeb, klíčová slova a obor v síti. Služby `Probe` obdrží požadavek a určit, zda odpovídají kritériím. Pokud služba odpovídá, odpoví odesláním `ProbeMatch` zprávy zpět klientovi s informacemi potřebnými ke kontaktování služby. Klienti mohou `Resolve` také odesílat požadavky, které jim umožňují najít služby, které mohly změnit adresu koncového bodu. Odpovídající služby `Resolve` reagují na `ResolveMatch` požadavky odesláním zprávy zpět klientovi.  
  
## <a name="ad-hoc-and-managed-modes"></a>Režimy ad-hoc a spravované režimy  
 Rozhraní Discovery API podporuje dva různé režimy: Spravované a Ad-Hoc. Ve spravovaném režimu je centralizovaný server nazývaný proxy server zjišťování, který udržuje informace o dostupných službách. Proxy server zjišťování může být naplněn informacemi o službách různými způsoby. Služby mohou například odesílat zprávy s oznámením během spuštění do proxy serveru zjišťování nebo proxy server může číst data z databáze nebo konfiguračního souboru, aby zjistil, jaké služby jsou k dispozici. Způsob, jakým je vyplněn proxy zjišťování, je zcela na vývojáři. Klienti používají proxy server zjišťování k načtení informací o dostupných službách. Když klient hledá službu, odešle `Probe` zprávu proxy zjišťování a proxy server určuje, zda některá ze služeb, o kterých ví, odpovídá službě, kterou klient hledá. Pokud existují shody zjišťování `ProbeMatch` proxy odešle odpověď zpět klientovi. Klient pak může kontaktovat službu přímo pomocí informací o službě vrácených z proxy serveru. Klíčovým principem spravovaného režimu je, že požadavky na zjišťování jsou odesílány jednosměrovým způsobem jedné autoritě, proxy serveru zjišťování. Rozhraní .NET Framework obsahuje klíčové součásti, které umožňují vytvořit vlastní proxy server. Klienti a služby mohou najít proxy server pomocí několika metod:  
  
- Proxy server může reagovat na zprávy ad-hoc.  
  
- Proxy server může během spuštění odeslat zprávu s oznámením.  
  
- Klienti a služby mohou být zapsány hledat konkrétní známý koncový bod.  
  
 V režimu Ad-Hoc neexistuje žádný centralizovaný server. Všechny zprávy zjišťování, jako jsou oznámení o službě a požadavky klientů, jsou odesílány způsobem vícesměrového vysílání. Ve výchozím nastavení rozhraní .NET Framework obsahuje podporu pro zjišťování Ad-Hoc přes protokol UDP. Například pokud je služba nakonfigurována tak, aby při spuštění odeslala oznámení Hello, odešle ji prostřednictvím známé adresy vícesměrového vysílání pomocí protokolu UDP. Klienti musí tato oznámení aktivně naslouchat a podle toho je zpracovávat. Když klient odešle `Probe` zprávu pro službu, je odeslán a odeslán po síti pomocí protokolu vícesměrového vysílání. Každá služba, která obdrží požadavek určuje, zda `Probe` odpovídá kritériím ve zprávě `ProbeMatch` a odpoví přímo klientovi se `Probe` zprávou, pokud služba odpovídá kritériím zadaným ve zprávě.  
  
## <a name="benefits-of-using-wcf-discovery"></a>Výhody použití zjišťování WCF  
 Vzhledem k tomu, že wcf discovery je implementována pomocí protokolu WS-Discovery je interoperabilní s ostatními klienty, službami a proxy servery, které implementují WS-Discovery také. WCF Discovery je postavenna existující wcf api, což usnadňuje přidání funkce zjišťování do stávajících služeb a klientů. Zjistitelnost služby lze snadno přidat prostřednictvím nastavení konfigurace aplikace. Kromě toho WCF Discovery také podporuje použití protokolu zjišťování přes jiné přenosy, jako je peer net, pojmenování překrytí a HTTP. WCF Discovery poskytuje podporu pro spravovaný režim operace, kde se používá proxy server zjišťování. To může snížit zatížení sítě, protože zprávy jsou odesílány přímo do proxy serveru zjišťování namísto odesílání zpráv vícesměrového vysílání do celé sítě. WCF Discovery také umožňuje větší flexibilitu při práci s webovými službami. Můžete například změnit adresu služby bez nutnosti překonfigurovat klienta nebo službu. Když klient musí přistupovat ke `Probe` službě, `Find` může vydat zprávu prostřednictvím požadavku a očekávat, že služba odpoví svou aktuální adresou. WCF Discovery umožňuje klientovi vyhledat službu na základě různých kritérií, včetně typů smluv, elementů vazby, oboru názvů, oboru a klíčových slov nebo čísel verzí verzí. WCF Discovery umožňuje zjišťování času běhu a návrhu. Přidání zjišťování do aplikace lze použít k povolení dalších scénářů, jako je odolnost proti chybám a automatická konfigurace.  
  
## <a name="service-publication"></a>Publikace služby  
 Chcete-li službu zjistitelné, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> musí být přidán do hostitele služby a koncový bod zjišťování musí být přidán určit, kde se má naslouchat pro zprávy zjišťování. Následující příklad kódu ukazuje, jak lze změnit samoobslužnou službu tak, aby byla zjistitelná.  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
 Instance <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> musí být přidána do popisu služby, aby byla služba zjistitelná. Instance <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> musí být přidána do hostitele služby, aby služba řekla, kde má naslouchat požadavkům na zjišťování. V tomto příkladu je přidán <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>(který je odvozen z) určit, že služba by měla naslouchat požadavky na zjišťování přes přenos vícesměrového vysílání UDP. Používá <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> se pro zjišťování ad-hoc, protože všechny zprávy jsou odesílány způsobem vícesměrového vysílání.  
  
## <a name="announcement"></a>Oznámení  
 Ve výchozím nastavení neodesílá publikace služby zprávy s oznámením. Služba musí být nakonfigurována tak, aby odesílala zprávy s oznámením. To poskytuje další flexibilitu pro autory služby, protože mohou oznámit službu odděleně od naslouchání pro zprávy zjišťování. Oznámení služby lze také použít jako mechanismus pro registraci služeb s proxy serverem zjišťování nebo jinými registry služeb. Následující kód ukazuje, jak nakonfigurovat službu pro odesílání zpráv oznámení prostřednictvím vazby UDP.  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(discoveryBehavior);

    // Send announcements on UDP multicast transport
    discoveryBehavior.AnnouncementEndpoints.Add(
      new UdpAnnouncementEndpoint());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.Description.Endpoints.Add(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
## <a name="service-discovery"></a>Zjišťování služeb  
 Klientská aplikace můžete <xref:System.ServiceModel.Discovery.DiscoveryClient> použít třídu k vyhledání služeb. Vývojář vytvoří instanci <xref:System.ServiceModel.Discovery.DiscoveryClient> třídy, která prochází v koncovém `Probe` bodu `Resolve` zjišťování, který určuje, kam se má odesílat nebo zprávy. Klient pak <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> volá, který určuje <xref:System.ServiceModel.Discovery.FindCriteria> kritéria hledání v rámci instance. Pokud jsou nalezeny <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> odpovídající služby, vrátí kolekci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Následující kód ukazuje, jak `Find` volat metodu a potom se připojit k zjištěné služby.  
  
```csharp  
class Client
{
    static EndpointAddress serviceAddress;
  
    static void Main()
    {  
        if (FindService())
        {
            InvokeService();
        }
    }  
  
    // ** DISCOVERY ** //  
    static bool FindService()  
    {  
        Console.WriteLine("\nFinding Calculator Service ..");  
        DiscoveryClient discoveryClient =
            new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
        Collection<EndpointDiscoveryMetadata> calculatorServices =
            (Collection<EndpointDiscoveryMetadata>)discoveryClient.Find(new FindCriteria(typeof(ICalculator))).Endpoints;  
  
        discoveryClient.Close();  
  
        if (calculatorServices.Count == 0)  
        {  
            Console.WriteLine("\nNo services are found.");  
            return false;  
        }  
        else  
        {  
            serviceAddress = calculatorServices[0].Address;  
            return true;  
        }  
    }  
  
    static void InvokeService()  
    {  
        Console.WriteLine("\nInvoking Calculator Service at {0}\n", serviceAddress);  
  
        // Create a client  
        CalculatorClient client = new CalculatorClient();  
        client.Endpoint.Address = serviceAddress;  
        client.Add(10,3);  
    }
}  
```  
  
## <a name="discovery-and-message-level-security"></a>Zjišťování a zabezpečení na úrovni zpráv  
 Při použití zabezpečení na úrovni zprávy <xref:System.ServiceModel.EndpointIdentity> je nutné zadat koncový <xref:System.ServiceModel.EndpointIdentity> bod zjišťování služby a odpovídající koncový bod zjišťování klienta. Další informace o zabezpečení na úrovni zpráv naleznete v [tématu Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Zjišťování a hostované webové služby  
 Aby služby WCF byly zjistitelné, musí být spuštěny. Služby WCF hostované ve službě IIS nebo WAS nelze spustit, dokud služba IIS/WAS neobdrží zprávu vázanou na službu, takže je nelze ve výchozím nastavení zjistit.  Existují dvě možnosti, jak zjistit služby hostované na webu:  
  
1. Použití funkce automatického spuštění windows server appfabric  
  
2. Ke komunikaci jménem služby použijte proxy server zjišťování.  
  
 Windows Server AppFabric má funkci automatického spuštění, která umožní spuštění služby před přijetím zpráv. Pomocí této sady automatického spuštění lze službu hostovanou službu IIS/WAS nakonfigurovat tak, aby byla zjistitelná. Další informace o funkci automatického spuštění naleznete v [tématu Funkce automatického spuštění systému Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677260(v=azure.10)). Spolu se zapnutím funkce automatického spuštění je nutné nakonfigurovat službu pro zjišťování. Další informace naleznete v [tématu How to: Programmatically Add Discoverability to a WCF Service and Client](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Configuring Discovery in a Configuration File](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).  
  
 Proxy zjišťování lze použít ke komunikaci jménem služby WCF, pokud služba není spuštěna. Proxy server může naslouchat sondy nebo vyřešit zprávy a reagovat na klienta. Klient pak může odesílat zprávy přímo do služby. Když klient odešle zprávu do služby bude vytvořena instance reagovat na zprávu. Další informace o implementaci proxy serveru zjišťování naleznete [v tématu Implementace proxy serveru zjišťování](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).  
  
> [!NOTE]
> Aby zjišťování WCF fungovalo správně, všechny síťové karty (řadič síťového rozhraní) by měly mít pouze 1 adresu IP.
