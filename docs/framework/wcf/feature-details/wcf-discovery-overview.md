---
title: Přehled zjišťování WCF
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: e7fd7ae4103600eb5463114987ca4ccbc2e0a1f2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600189"
---
# <a name="wcf-discovery-overview"></a>Přehled zjišťování WCF
Rozhraní API pro zjišťování poskytují jednotný programovací model pro dynamickou publikaci a zjišťování webových služeb pomocí protokolu WS-Discovery. Tato rozhraní API umožňují službám publikování a klientů, aby našli publikované služby. Jakmile je služba zjistitelná, může služba posílat zprávy oznámení a také naslouchat a reagovat na požadavky na zjišťování. Zjistitelné služby mohou odesílat zprávy Hello, které oznamují jejich doručení v síti a bye zprávy, aby bylo možné oznámení odchodu ze sítě. Aby klienti našli službu, odesílají `Probe` požadavek, který obsahuje určitá kritéria, jako je například typ kontraktu služby, klíčová slova a obor v síti. Služby obdrží `Probe` požadavek a určí, zda odpovídají kritériím. Pokud se služba shoduje, odpoví odesláním `ProbeMatch` zprávy zpátky do klienta s informacemi potřebnými ke kontaktování služby. Klienti můžou také odesílat `Resolve` požadavky, které jim umožňují najít služby, u kterých se mohla změnit adresa koncového bodu. Vyhovující služby reagují na `Resolve` požadavky odesláním `ResolveMatch` zprávy zpátky klientovi.  
  
## <a name="ad-hoc-and-managed-modes"></a>Ad-hoc a spravované režimy  
 Rozhraní API pro zjišťování podporuje dva různé režimy: spravované a ad hoc. V spravovaném režimu se nachází centralizovaný Server označovaný jako proxy zjišťování, který uchovává informace o dostupných službách. Proxy zjišťování lze naplnit různými způsoby pomocí informací o službách. Služba může například odesílat zprávy oznámení během spouštění na proxy zjišťování nebo může proxy číst data z databáze nebo konfiguračního souboru a určit, jaké služby jsou k dispozici. Způsob, jakým je vyplněné zjišťování proxy serveru, je zcela pro vývojáře. Klienti používají proxy zjišťování k načítání informací o dostupných službách. Když klient hledá službu, pošle `Probe` zprávu na proxy zjišťování a proxy určí, jestli kterákoli ze služeb, které ví o shodu se službou, kterou klient hledá. Pokud se shodují, proxy zjišťování odešle `ProbeMatch` odpověď zpět klientovi. Klient pak může službu kontaktovat přímo pomocí informací o službě vrácených z proxy serveru. Klíčovým principem na spravovaném režimu je, že požadavky na zjišťování se odesílají v jednosměrovém vysílání pro jednu autoritu, proxy zjišťování. .NET Framework obsahuje klíčové komponenty, které umožňují vytvořit vlastní proxy server. Klienti a služby můžou proxy najít několika způsoby:  
  
- Proxy může reagovat na zprávy ad-hoc.  
  
- Proxy může během spuštění odeslat zprávu s oznámením.  
  
- Klienty a služby lze zapsat za účelem vyhledání konkrétního známého koncového bodu.  
  
 V režimu ad hoc není žádný centralizovaný Server. Všechny zprávy zjišťování, jako jsou například oznámení o službách a požadavky klientů, jsou odesílány vícesměrovém způsobem. Ve výchozím nastavení .NET Framework obsahuje podporu pro ad hoc zjišťování přes protokol UDP. Pokud je třeba služba nakonfigurovaná tak, aby při spuštění odesílala oznámení Hello, pošle ji přes známou adresu vícesměrového vysílání pomocí protokolu UDP. Klienti musí u těchto oznámení aktivně naslouchat a zpracovávat je odpovídajícím způsobem. Když klient pošle `Probe` zprávu pro službu, která se pošle přes síť pomocí protokolu vícesměrového vysílání. Každá služba, která požadavek obdrží, určuje, zda odpovídá kritériím ve `Probe` zprávě a reaguje přímo na klienta se zprávou, `ProbeMatch` Pokud služba odpovídá kritériím zadaným ve `Probe` zprávě.  
  
## <a name="benefits-of-using-wcf-discovery"></a>Výhody použití zjišťování WCF  
 Vzhledem k tomu, že zjišťování WCF je implementováno pomocí protokolu WS-Discovery, spolupracuje s jinými klienty, službami a proxy servery, které implementují funkci WS-Discovery. Zjišťování WCF je postavené na stávajících rozhraních API WCF, což usnadňuje přidání funkce zjišťování do stávajících služeb a klientů. Zjistitelnost služby se dá snadno přidat prostřednictvím nastavení konfigurace aplikace. Kromě toho zjišťování WCF také podporuje použití protokolu zjišťování přes jiné přenosy, jako je například síť typu peer-to-peer, překryv názvů a HTTP. Zjišťování WCF poskytuje podporu pro spravovaný režim operace, kde se používá proxy zjišťování. To může snížit zatížení sítě, protože se zprávy odesílají přímo na proxy zjišťování namísto odesílání zpráv vícesměrového vysílání do celé sítě. Zjišťování WCF také umožňuje větší flexibilitu při práci s webovými službami. Můžete například změnit adresu služby, aniž byste museli překonfigurovat klienta nebo službu. Když klient nástroje musí k této službě přistupovat, může vydat `Probe` zprávu prostřednictvím `Find` žádosti a očekávat, že služba bude odpovídat její aktuální adrese. Zjišťování WCF umožňuje klientovi vyhledat službu na základě různých kritérií, včetně typů kontraktů, vazeb prvků, oboru názvů, oboru a klíčových slov nebo čísel verzí. Zjišťování WCF umožňuje zjišťování doby běhu a návrhu. Přidání zjišťování do aplikace lze použít k povolení jiných scénářů, jako je odolnost proti chybám a Automatická konfigurace.  
  
## <a name="service-publication"></a>Publikace služby  
 Aby bylo možné službu zjistitelnou, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> musí být přidána do hostitele služby a musí být přidán koncový bod zjišťování, aby bylo možné určit, kam se mají zprávy zjišťování naslouchat. Následující příklad kódu ukazuje, jak lze upravit službu v místním prostředí, aby ji bylo možné zjistit.  
  
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
  
 Aby <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> bylo možné službu zjistit, musí být instance přidána do popisu služby. <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>Instance musí být přidána do hostitele služby, aby mohla službě sdělit, kde má naslouchat požadavky na zjišťování. V tomto příkladu <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> je přidána služba (která je odvozena z <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> ) k určení toho, že služba má naslouchat požadavkům na zjišťování přes přenos vícesměrového vysílání UDP. <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>Používá se pro zjišťování ad-hoc, protože všechny zprávy jsou odesílány vícesměrového vysílání.  
  
## <a name="announcement"></a>Ohlášen  
 Ve výchozím nastavení publikace služby neodesílá zprávy s oznámením. Služba musí být nakonfigurovaná tak, aby odesílala zprávy s oznámením. To poskytuje větší flexibilitu zapisovače služeb, protože může informovat službu nezávisle na naslouchání zpráv zjišťování. Oznámení služby je také možné použít jako mechanismus pro registraci služeb s proxy zjišťování nebo jinými registry služby. Následující kód ukazuje, jak nakonfigurovat službu pro posílání zpráv oznámení přes vazbu UDP.  
  
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
 Klientská aplikace může použít <xref:System.ServiceModel.Discovery.DiscoveryClient> třídu k vyhledání služeb. Vývojář vytvoří instanci <xref:System.ServiceModel.Discovery.DiscoveryClient> třídy, která přechází do koncového bodu zjišťování, který určuje, kam se mají posílat `Probe` `Resolve` zprávy. Klient pak volá <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> , který určuje vyhledávací kritéria v rámci <xref:System.ServiceModel.Discovery.FindCriteria> instance. Pokud se najde vyhovující služby, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> vrátí kolekci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> . Následující kód ukazuje, jak zavolat `Find` metodu a pak se připojit ke zjištěné službě.  
  
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
 Pokud používáte zabezpečení na úrovni zpráv, je nutné zadat hodnotu <xref:System.ServiceModel.EndpointIdentity> v koncovém bodu zjišťování služby a použít <xref:System.ServiceModel.EndpointIdentity> u koncového bodu zjišťování klienta. Další informace o zabezpečení na úrovni zpráv najdete v tématu [zabezpečení zpráv](message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Služby pro zjišťování a hostování webů  
 Aby služby WCF bylo možné zjistit, musí být spuštěny. Služby WCF hostované v rámci služby IIS nebo se nedají spustit, dokud služba IIS/neobdrží pro službu vazbu na zprávu, takže se ve výchozím nastavení nedá zjistit.  Existují dvě možnosti, jak zpřístupnit webové služby, které jsou zjistitelné:  
  
1. Použití funkce automatického spuštění Windows serveru AppFabric  
  
2. Pro komunikaci jménem služby použít proxy zjišťování  
  
 Windows Server AppFabric má funkci automatického spuštění, která umožní spuštění služby před přijetím jakýchkoli zpráv. V této automatické sadě se dá nakonfigurovat hostovaná služba IIS/s, aby byla zjistitelná. Další informace o funkci automatického spuštění najdete v tématu [funkce automatického spuštění Windows serveru AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677260(v=azure.10)). Společně s zapnutím funkce automatického spuštění musíte službu nakonfigurovat pro zjišťování. Další informace naleznete v tématu [How to: programing](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)autoforming on a Client[Configure Discovery in a Configuration v konfiguračním souboru](configuring-discovery-in-a-configuration-file.md).  
  
 Proxy zjišťování lze použít ke komunikaci jménem služby WCF, pokud služba není spuštěna. Proxy server může naslouchat testům nebo překládat zprávy a reagovat na klienta. Klient pak může odesílat zprávy přímo službě. Když klient pošle zprávu službě, že se vytvoří její instance, aby reagovala na zprávu. Další informace o implementaci proxy zjišťování najdete v tématu [implementace proxy zjišťování](implementing-a-discovery-proxy.md).  
  
> [!NOTE]
> Aby zjišťování WCF fungovalo správně, musí mít všechny síťové karty (síťový adaptér) jenom 1 IP adresu.
