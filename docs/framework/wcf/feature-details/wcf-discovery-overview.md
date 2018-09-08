---
title: Přehled zjišťování WCF
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: 24d758502e360a8368be25c506b8648b12a3eb20
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44173071"
---
# <a name="wcf-discovery-overview"></a>Přehled zjišťování WCF
Rozhraní API zjišťování poskytují jednotný programovací model pro dynamické publikace a zjišťování webové služby pomocí protokolu WS-Discovery. Tato rozhraní API umožňují služby sami a klientům nalezení služeb publikovaných na publikovat. Jakmile proběhne zjistitelné služby, služby má možnost odesílat zprávy oznámení také naslouchat a reagovat na požadavky na zjišťování. Zjistitelné služby může odesílat zprávy Hello oznamujeme jejich doručení na síť a zprávy Bye oznamujeme jejich odeslání ze sítě. K vyhledání služby klienty odeslat `Probe` žádost, která obsahuje určitá kritéria, například typ kontraktu služby, klíčová slova a oboru v síti. Přijímat služby `Probe` žádosti a určit, zda kritériím neodpovídají. Pokud služba odpovídá, odpovídá odesláním `ProbeMatch` zprávy zpět do klienta o informace nezbytné pro kontaktování služby. Klienti mohou také odesílat `Resolve` požadavků, které zajistí, aby hledání mohlo dojít ke změně jejich adresa koncového bodu služby. Odpovídající služby reagovat na `Resolve` odesláním žádosti `ResolveMatch` zpráv zpět klientovi.  
  
## <a name="ad-hoc-and-managed-modes"></a>Ad-Hoc a spravované režimy  
 Zjišťování rozhraní API podporuje dva různé režimy: spravované a Ad Hoc. Spravovaný režim je centralizovaná serveru s názvem proxy zjišťování, která uchovává informace o dostupných služeb. Zjišťování proxy je možné naplnit informace o službách v mnoha různými způsoby. Například služby odesílat zprávy o oznámení při spuštění až po zjišťování proxy serveru nebo proxy server může číst data z databáze nebo konfiguračního souboru k určení, jaké služby jsou k dispozici. Jak se vyplní proxy zjišťování je zcela na vývojáře. Klienti používají proxy zjišťování k načtení informací o dostupných služeb. Když klient vyhledává služby se odešle `Probe` zprávy zjišťování proxy serveru a proxy server určuje shodu kterékoli ze služeb ví o služby, bude klient Hledat. Pokud existují odešle proxy zjišťování shody `ProbeMatch` odpověď zpět klientovi. Klient pak může kontaktovat službu přímo pomocí služby informace vrácené z proxy serveru. Klíčovým principem za spravovaný režim je odeslání žádosti o zjištění způsobem jednosměrového vysílání jeden úřadu, za proxy zjišťování. Rozhraní .NET Framework obsahuje klíčových komponent, které umožňují vytvářet vlastní proxy server. Služby a klienti najdou proxy server pomocí několika metod:  
  
-   Proxy server můžou reagovat na ad-hoc zprávy.  
  
-   Proxy server můžete odeslat zprávu oznámení při spuštění.  
  
-   Služby a klienti mohou napsané pro vyhledání určitého dobře známé koncového bodu.  
  
 V režimu Ad Hoc není žádný centrální server. Všechny zprávy zjišťování například oznámení o službách a požadavky na klienta se posílají způsobem vícesměrového vysílání. Rozhraní .NET Framework ve výchozím nastavení obsahuje podporu pro Ad-Hoc zjišťování přes protokol UDP. Například pokud služba je konfigurován pro posílat oznámení Hello z po spuštění, odešle je prostřednictvím dobře známé, vícesměrového vysílání adres pomocí protokolu UDP. Klienti mají aktivně naslouchat těchto oznámeních a odpovídajícím způsobem zpracovat. Když klient odešle `Probe` zprávu pro službu je odeslán přes síť pomocí vícesměrového vysílání protokolu. Každá služba, která bude přijímat žádosti Určuje, zda odpovídá kritériím `Probe` zpráv a odpovídá přímo do klienta se `ProbeMatch` zprávu, pokud služba odpovídá kritérii zadanými v `Probe` zprávy.  
  
## <a name="benefits-of-using-wcf-discovery"></a>Výhody použití zjišťování WCF  
 Protože zjišťování WCF je implementována pomocí protokolu WS-Discovery je interoperabilní s dalšími klienty, službami a proxy servery, které také implementují WS-Discovery. Zjišťování WCF je postavena stávajících rozhraní API WCF, které umožňuje snadno přidat funkce zjišťování na vašich stávajících služeb a klientů. Zjistitelnost služby je možné snadno přidat prostřednictvím nastavení konfigurace aplikace. Zjišťování WCF kromě toho také podporuje pomocí protokolu zjišťování přes jiné přenosy, jako jsou sdílené net, pojmenování překrytí a HTTP. Zjišťování WCF poskytuje podporu pro spravovaný režim operace, kde se používá proxy zjišťování. To může snížit síťový provoz, jako jsou zprávy odesílány přímo do proxy zjišťování místo odesílání zprávy vícesměrového vysílání k celé síti. Zjišťování WCF také umožňuje větší flexibilitu při práci s webovými službami. Můžete například změnit adresu služby bez nutnosti znovu nakonfigurovat klienta nebo službě. Když klient musí přístup ke službě, můžete vydat `Probe` zpráv prostřednictvím `Find` žádosti a očekávají, že služba odpověděla s její aktuální adresu. Zjišťování WCF umožňuje klienta k vyhledání služby na základě různých kritérií, včetně typy kontraktů, elementy vazby, obor názvů, oboru a klíčová slova nebo čísla verzí. Zjišťování WCF umožňuje modulu runtime a návrhu doba zjišťování. Přidání zjišťování tak, aby vaše aplikace slouží k povolení dalších scénářů, jako je odolnost proti chybám a automatické konfigurace.  
  
## <a name="service-publication"></a>Služba publikace  
 Zjistitelnost služby <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> musí být přidané do hostitele služby a zjišťování. musí být koncový bod přidán do zadejte, kam chcete přijímat zprávy zjišťování. Následující příklad kódu ukazuje, jak služba v místním prostředí můžete upravit tak, aby zjistitelnost.  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",  
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

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
  
 A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance musí být přidané do popisu služby pro službu zjistitelné. A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance musí být přidané do tohoto hostitele služby službu zjistit, kde k naslouchání požadavkům zjišťování. V tomto příkladu <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (který je odvozen z <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) se přidá k určení, že služba naslouchat požadavkům pro požadavky na zjišťování přes port UDP přenos vícesměrového vysílání. <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Se používá pro zjištění Ad-Hoc, protože jsou všechny zprávy odeslané způsobem vícesměrového vysílání.  
  
## <a name="announcement"></a>Oznámení  
 Ve výchozím nastavení služba publikace neodešle zprávy oznámení. Služba musí nakonfigurována na odeslání zprávy oznámení. To poskytuje větší flexibilitu pro zápis služby vzhledem k tomu, že jsou oznámení služby odděleně od naslouchání pro vyhledávání zpráv. Oznámení služby také slouží jako mechanismus pro registraci služby pomocí proxy zjišťování nebo jiné služby registrů. Následující kód ukazuje, jak nakonfigurovat službu pro odeslání zpráv oznámení UDP vazby.  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

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
  
## <a name="service-discovery"></a>Zjišťování služby  
 Klientská aplikace můžete použít <xref:System.ServiceModel.Discovery.DiscoveryClient> třídy k nalezení služeb. Vytvoří instanci Vývojář <xref:System.ServiceModel.Discovery.DiscoveryClient> třídu, která se předá do koncového bodu zjišťování, která určuje, kam má odesílat `Probe` nebo `Resolve` zprávy. Klient pak zavolá <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> , který určuje kritéria vyhledávání v rámci <xref:System.ServiceModel.Discovery.FindCriteria> instance. Pokud se najdou odpovídající služby, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> vrátí kolekci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Následující kód ukazuje, jak volat `Find` metoda a připojte se k zjištěnou službu.  
  
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
 Při použití zabezpečení na úrovni zpráv je potřeba zadat <xref:System.ServiceModel.EndpointIdentity> na koncový bod zjišťování služby a odpovídající <xref:System.ServiceModel.EndpointIdentity> na koncový bod zjišťování klienta. Další informace o zabezpečení na úrovni zpráv, najdete v části [zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Zjišťování a Web hostovaných služeb  
 V pořadí pro služby WCF zjistitelné musí být spuštěn. Služby WCF hostované v IIS nebo WAS se nespustí, dokud služba IIS / WAS přijme zprávu mez pro služby, proto nemohou být zjistitelné ve výchozím nastavení.  Existují dvě možnosti pro vytváření služeb hostovaných webových zjistitelné:  
  
1.  Použít funkci systému Windows Server AppFabric automatické spuštění  
  
2.  Komunikovat jménem službě pomocí proxy zjišťování  
  
 Windows Server AppFabric obsahuje funkci automatického spuštění, které vám umožní službu spustit před přijetím všechny zprávy. Automatické spouštění nastavení IIS / WAS hostované služby je nakonfigurovat zjistitelné. Další informace o najdete v tématu automatického spuštění funkce [funkce systému Windows Server AppFabric automatického spuštění](https://go.microsoft.com/fwlink/?LinkId=205545). Spolu s povolením funkce Automatické spouštění, musíte nakonfigurovat službu pro zjišťování. Další informace najdete v tématu [postupy: programové přidání zjistitelnosti do klienta a služby WCF](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[konfigurace zjišťování v konfiguračním souboru](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).  
  
 Zjišťování proxy serveru umožňuje komunikovat jménem služby WCF, když služba není spuštěná. Proxy server může sledovat testu nebo vyřešit zprávy a reagovat na klientovi. Klient pak může odesílat zprávy přímo ke službě. Když klient odešle zprávu do služby bude vytvořena instance reagovat na zprávu. Další informace o implementace zjišťování proxy serveru najdete v [implementace Proxy zjišťování](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).  
  
> [!NOTE]
>  Zjišťování WCF fungovala správně měli všech síťových rozhraních (řadiče síťového rozhraní) mít jenom 1 IP adresu.
