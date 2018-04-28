---
title: Přehled zjišťování WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7b44a1587c704b0995821c7126f0264695861558
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="wcf-discovery-overview"></a>Přehled zjišťování WCF
Zjišťování rozhraní API poskytuje jednotný programovací model pro dynamické publikace a zjišťování webové služby pomocí protokolu WS-Discovery. Tato rozhraní API umožňují služby k publikování sami a klienti najít publikované služby. Jakmile služba je k zjistitelný, služba má možnost zasílání oznámení a také naslouchat a reagovat na požadavky na zjišťování. Zjistitelný služby může odesílat zprávy Hello oznamujeme jejich přijetí v síti a zprávy Bye oznamujeme jejich přesun ze sítě. Pokud chcete vyhledat služby, klienti odesílají `Probe` požadavek, který obsahuje určitá kritéria, například typ kontraktu služby, klíčová slova a oboru v síti. Přijímat služby `Probe` žádosti a určit, zda se shodují se kritéria. Pokud služba odpovídá, odpoví odesláním `ProbeMatch` zprávy zpět do klienta se informace potřebné k kontaktovat službu. Klienty můžete také odeslat `Resolve` požadavků, které mohly najít služby, které mohl změnit jejich adresa koncového bodu. Odpovídající služby reagovat na `Resolve` požadavky odesláním `ResolveMatch` zprávy zpět do klienta.  
  
## <a name="ad-hoc-and-managed-modes"></a>Ad Hoc a spravované režimy  
 Zjišťování rozhraní API podporuje dvou různých režimech: spravované a Ad-Hoc. V režimu spravované je centralizovaný server volá zjišťování proxy server, který uchovává informace o dostupných služeb. Zjišťování proxy možné naplnit informace o službách v mnoha různými způsoby. Například služby mohou zasílat zprávy oznámení během spuštění až zjišťování proxy server nebo proxy server může číst data z databáze nebo konfigurační soubor k určení, které služby jsou dostupné. Jak se naplní zjišťování proxy je zcela až vývojář. Klienti používají zjišťování proxy k načtení informací o dostupných služeb. Když klient vyhledá službu se zasílá `Probe` zprávu zjišťování proxy a proxy určuje, zda se shodují služeb ví o služby je hledání klienta. Pokud existují odpovídá zasílá proxy zjišťování `ProbeMatch` odpověď zpět klientovi. Klient může poté kontaktovat službu přímo pomocí vrácené z proxy serveru služby informace. Klíčovým principem za spravovaný režim je, že jsou v režimu jednosměrového vysílání jeden autoritě zjišťování proxy odeslání požadavků zjišťování. Rozhraní .NET Framework obsahuje klíčové komponenty, které vám umožňují vytvářet vlastní proxy server. Služby a klienti mohou vyhledat proxy server pomocí několik metod:  
  
-   Proxy server může reagovat na ad hoc zprávy.  
  
-   Proxy server můžete odeslat zprávu oznámení během spuštění.  
  
-   Služby a klienti je možné zapsat do vyhledejte konkrétní dobře známé koncový bod.  
  
 V režimu Ad Hoc není žádný centrální server. Všechny zprávy zjišťování například oznámení týkající se služeb a požadavky klientů jsou odesílány způsobem vícesměrového vysílání. Ve výchozím nastavení rozhraní .NET Framework obsahuje podporu pro zjišťování Ad-Hoc přes protokol UDP. Například pokud služba je nakonfigurovaný k odeslání oznámení Hello na spouštění, odešle se přes adresu dobře známé a vícesměrového vysílání pomocí protokolu UDP. Klienti mají aktivně naslouchat těchto oznámení a jejich zpracování odpovídajícím způsobem. Když klient odešle `Probe` zpráva pro službu odesláním přes síť pomocí protokolu vícesměrového vysílání. Každá služba, která obdrží požadavek určuje, zda je odpovídá kritérií `Probe` zprávy a odpovídá přímo na klienta se `ProbeMatch` zpráv, pokud služba odpovídá kritérii zadanými v `Probe` zprávy.  
  
## <a name="benefits-of-using-wcf-discovery"></a>Výhody použití zjišťování WCF  
 Protože zjišťování WCF je implementovaná pomocí protokolu WS-Discovery je umožňuje vzájemnou spolupráci s jinými klienty, služby a proxy servery, které implementují WS-Discovery také. Zjišťování WCF je založena na stávajících WCF rozhraní API, který umožňuje snadno přidat další funkce zjišťování vaší existující služeb a klientů. Možnosti rozpoznání služby lze snadno přidat prostřednictvím nastavení konfigurace aplikace. Kromě toho zjišťování WCF podporuje také pomocí protokolu zjišťování přes ostatní přenosy, například sdílené sítě, pojmenování překrytí a HTTP. Zjišťování WCF poskytuje podporu pro spravovaný režim operace, kde se používá zjišťování proxy. To může snížit síťový provoz, jako jsou zprávy odesílány přímo do zjišťování proxy místo odesílání zpráv vícesměrového vysílání k celé síti. Zjišťování WCF taky umožňuje větší flexibilitu při práci s webovými službami. Například můžete změnit adresu služby bez nutnosti znovu nakonfigurovat klienta nebo službu. Když klient musí přístup ke službě mohla vystavovat `Probe` zprávy prostřednictvím `Find` žádosti a očekávají, že služba odpovědět s aktuální adresy. Zjišťování WCF umožňuje klienta pro vyhledávání na základě různých kritérií, například typy kontraktů, prvky vazby, obor názvů, oboru a klíčová slova nebo čísla verzí služby. Zjišťování WCF umožňuje modulu runtime a návrhu dobu zjišťování. Přidání zjišťování tak, aby vaše aplikace umožňuje povolit další scénáře, jako je odolnost proti chybám a automatické konfigurace.  
  
## <a name="service-publication"></a>Služba publikace  
 Zjistitelnost služby <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> musí být přidán pro hostitele služby a zjišťování musí být přidaný koncový bod, kde chcete přijímat zprávy zjišťování. Následující příklad kódu ukazuje, jak lze upravit služba s vlastním hostováním zjistitelnost.  
  
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
  
 A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance musí být přidán k popisu služby pro službu zjistitelné. A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance musí být přidaný do hostitele služby říct službu, kde k naslouchání požadavkům zjišťování. V tomto příkladu <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (který je odvozen z <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) se přidá k určení, že služba má naslouchat žádostem zjišťování přes protokol UDP. přenos vícesměrového vysílání. <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Se používá pro zjištění Ad-Hoc, všechny zprávy jsou odesílány způsobem vícesměrového vysílání.  
  
## <a name="announcement"></a>Oznámení  
 Ve výchozím nastavení služba publikace neodešle se zprávy oznámení. Služba musí být nakonfigurována k odeslání zprávy oznámení. To poskytuje větší flexibilita pro služby zapisovače vzhledem k tomu, že může informovat službu odděleně od naslouchání pro zjišťování zprávy. Oznámení služby mohou sloužit také jako mechanismus pro registraci služby zjišťování proxy nebo jiné služby registrech. Následující kód ukazuje, jak nakonfigurovat službu pro odeslání zpráv oznámení vazbu UDP.  
  
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
 Klientská aplikace můžete použít <xref:System.ServiceModel.Discovery.DiscoveryClient> třída k vyhledání služeb. Vývojář vytvoří instanci <xref:System.ServiceModel.Discovery.DiscoveryClient> třídu, která předá koncový bod zjišťování, která určuje, kam má posílat `Probe` nebo `Resolve` zprávy. Klient pak zavolá <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> , určuje kritéria vyhledávání v rámci <xref:System.ServiceModel.Discovery.FindCriteria> instance. Pokud se najdou odpovídající služby, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> vrátí kolekci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Následující kód ukazuje způsob volání `Find` metoda a připojte se k zjištěnou službu.  
  
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
  
## <a name="discovery-and-message-level-security"></a>Zjišťování a úrovně zabezpečení zpráv  
 Při použití zabezpečení na úrovni zprávy je nutné zadat <xref:System.ServiceModel.EndpointIdentity> na koncový bod zjišťování služby a odpovídající <xref:System.ServiceModel.EndpointIdentity> na koncový bod zjišťování klienta. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] úroveň zabezpečení zpráv najdete v tématu [zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Zjišťování a webové hostovaných služeb  
 V pořadí pro služby WCF zjistitelné musí být spuštěn. Služby WCF hostované v rámci služby IIS nebo WAS se nespustí, dokud služba IIS / byl přijme zprávu o vázaný službu, takže nemohou být zjistitelný ve výchozím nastavení.  Existují dvě možnosti pro provádění zjistitelný hostované webové služby:  
  
1.  Použít funkci systému Windows Server AppFabric automatického – spuštění  
  
2.  Použít proxy server zjišťování komunikovat jménem služby  
  
 Windows Server AppFabric má o funkci automatického spuštění, která vám umožní službu spustit před příjmem všechny zprávy. Pomocí automatického spuštění nastavit službu IIS nebo WAS hostované službu lze nakonfigurovat zjistitelné. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Viz funkce automatického spuštění, [Windows Server AppFabric automatického – spuštění funkce](http://go.microsoft.com/fwlink/?LinkId=205545). Společně s zapnout funkci automatického spuštění, musíte nakonfigurovat službu pro zjišťování. Další informace najdete v tématu [postupy: programové přidání možnosti rozpoznání do klienta a služby WCF](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[konfigurace zjišťování v konfiguračním souboru](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).  
  
 Zjišťování proxy umožňuje komunikovat jménem služby WCF, pokud služba není spuštěna. Proxy server může sledovat u testu paměti nebo vyřešit zprávy a reagovat na klientovi. Klient pak může odesílat zprávy přímo ke službě. Když klient odešle zprávu do služby bude vytvořena instance reagovat na zprávu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] implementace proxy zjišťování najdete [implementace Proxy zjišťování](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).  
  
> [!NOTE]
>  Zjišťování WCF fungovat správně musí mít všechny síťové adaptéry (řadiče síťového rozhraní) pouze 1 IP adresu.
