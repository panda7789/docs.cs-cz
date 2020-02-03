---
title: Směrování – úvod
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 8ce98aab2ed14401fa7c2cbf43eb92a633fa96b0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746463"
---
# <a name="routing-introduction"></a>Směrování – úvod

Směrovací služba poskytuje obecného zprostředkujícího zprostředkovatele SOAP, který dokáže směrovat zprávy na základě obsahu zprávy. Pomocí směrovací služby můžete vytvořit složitou logiku směrování, která vám umožní implementovat scénáře, jako je například agregace služeb, Správa verzí služeb, směrování priorit a směrování vícesměrového vysílání. Směrovací služba také poskytuje zpracování chyb, které umožňuje nastavit seznam koncových bodů zálohy, na které se odesílají zprávy, pokud dojde k selhání při posílání do primárního cílového koncového bodu.

Toto téma je určené pro nové služby Směrování a pokrývá základní konfiguraci a hostování směrovací služby.

## <a name="configuration"></a>Konfigurace

Směrovací služba je implementována jako služba WCF, která zveřejňuje jeden nebo více koncových bodů služby, které přijímají zprávy z klientských aplikací a směrují zprávy do jednoho nebo více cílových koncových bodů. Služba poskytuje <xref:System.ServiceModel.Routing.RoutingBehavior>, který se použije pro koncové body služby vystavené službou. Toto chování se používá ke konfiguraci různých aspektů toho, jak služba funguje. Pro usnadnění konfigurace při použití konfiguračního souboru jsou parametry zadány na **RoutingBehavior**. Ve scénářích založených na kódu by byly tyto parametry zadány jako součást objektu <xref:System.ServiceModel.Routing.RoutingConfiguration>, který lze následně předat do **RoutingBehavior**.

Při spuštění tento problém přidá <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, který se používá k provádění zpracování protokolu SOAP zpráv, do koncových bodů klienta. Tato možnost umožňuje směrovací službě přenášet zprávy do koncových bodů, které vyžadují jinou **třídu MessageVersion** , než je koncový bod, který byla zpráva přijata. **RoutingBehavior** také zaregistruje rozšíření služby, <xref:System.ServiceModel.Routing.RoutingExtension>, což poskytuje bod přístupnosti pro úpravu konfigurace směrovací služby v době běhu.

Třída **Konfigurace RoutingConfiguration** poskytuje konzistentní způsob konfigurace a aktualizace konfigurace směrovací služby.  Obsahuje parametry, které fungují jako nastavení pro směrovací službu a slouží ke konfiguraci **RoutingBehavior** při spuštění služby, nebo je předána do **RoutingExtension** za účelem změny konfigurace směrování v době běhu.

Logika směrování, která se používá k provádění směrování zpráv na základě obsahu, je definována seskupením více <xref:System.ServiceModel.Dispatcher.MessageFilter> objektů dohromady do tabulek filtrů (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objektů). Příchozí zprávy jsou vyhodnocovány proti filtrům zpráv obsaženým v tabulce filtru a pro každý **MessageFilter** , který odpovídá zprávě, předané do cílového koncového bodu. Tabulka filtru, která se má použít ke směrování zpráv, je určena buď pomocí **RoutingBehavior** v konfiguraci, nebo prostřednictvím kódu pomocí objektu **Konfigurace RoutingConfiguration** .

### <a name="defining-endpoints"></a>Definování koncových bodů

I když se může zdát, že byste měli zahájit konfiguraci definováním logiky směrování, kterou použijete, měl by váš první krok být skutečně určující tvar koncových bodů, do kterých budete směrovat zprávy. Směrovací služba používá kontrakty, které definují tvar kanálů používaných k přijímání a posílání zpráv, a proto musí tvar vstupního kanálu odpovídat výstupnímu kanálu.  Pokud například provádíte směrování do koncových bodů, které používají obrazec kanálu požadavek-odpověď, je nutné použít kompatibilní kontrakt na příchozích koncových bodech, například <xref:System.ServiceModel.Routing.IRequestReplyRouter>.

To znamená, že pokud vaše cílové koncové body používají smlouvy s více způsoby komunikace (například kombinováním jednosměrných a obousměrných operací), nemůžete vytvořit jeden koncový bod služby, který může přijímat zprávy a směrovat je na všechny. Je nutné určit, které koncové body mají kompatibilní tvary, a definovat jeden nebo více koncových bodů služby, které budou použity pro příjem zpráv, které mají být směrovány do cílových koncových bodů.

> [!NOTE]
> Při práci se smlouvami, které určují více vzorů komunikace (například kombinace jednosměrných a obousměrných operací), je alternativním řešením použití duplexního kontraktu ve směrovací službě, jako je například <xref:System.ServiceModel.Routing.IDuplexSessionRouter>. To však znamená, že vazba musí umožňovat duplexní komunikaci, což nemusí být možné pro všechny scénáře. V případech, kdy to není možné, může být komunikace na více koncových bodech nebo v případě změny aplikace nutná.

Další informace o kontraktech směrování najdete v tématu [kontrakty směrování](routing-contracts.md).

Po definování koncového bodu služby můžete pomocí **RoutingBehavior** přidružit ke koncovému bodu konkrétní **Konfigurace RoutingConfiguration** . Při konfiguraci směrovací služby pomocí konfiguračního souboru **RoutingBehavior** slouží k určení tabulky filtru, která obsahuje logiku směrování používanou ke zpracování zpráv přijatých v tomto koncovém bodě. Pokud konfigurujete směrovací službu programově, můžete zadat tabulku filtru pomocí **Konfigurace RoutingConfiguration**.

Následující příklad definuje koncové body služby a klienta, které služba Směrování používá programově a pomocí konfiguračního souboru.

```xml
<services>
  <!--ROUTING SERVICE -->
  <service behaviorConfiguration="routingData"
            name="System.ServiceModel.Routing.RoutingService">
    <host>
      <baseAddresses>
        <add baseAddress="http://localhost:8000/routingservice/router"/>
      </baseAddresses>
    </host>
    <!-- Define the service endpoints that are receive messages -->
    <endpoint address=""
              binding="wsHttpBinding"
              name="reqReplyEndpoint"
              contract="System.ServiceModel.Routing.IRequestReplyRouter" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="routingData">
      <serviceMetadata httpGetEnabled="True"/>
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->
      <routing filterTableName="routingTable1" />
    </behavior>
  </serviceBehaviors>
</behaviors>
<client>
<!-- Define the client endpoint(s) to route messages to -->
  <endpoint name="CalculatorService"
            address="http://localhost:8000/servicemodelsamples/service"
            binding="wsHttpBinding" contract="*" />
</client>
```

```csharp
//set up some communication defaults
string clientAddress = "http://localhost:8000/servicemodelsamples/service";
string routerAddress = "http://localhost:8000/routingservice/router";
Binding routerBinding = new WSHttpBinding();
Binding clientBinding = new WSHttpBinding();
//add the endpoint the router uses to receive messages
serviceHost.AddServiceEndpoint(
     typeof(IRequestReplyRouter),
     routerBinding,
     routerAddress);
//create the client endpoint the router routes messages to
ContractDescription contract = ContractDescription.GetContract(
     typeof(IRequestReplyRouter));
ServiceEndpoint client = new ServiceEndpoint(
     contract,
     clientBinding,
     new EndpointAddress(clientAddress));
//create a new routing configuration object
RoutingConfiguration rc = new RoutingConfiguration();
….
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
//attach the behavior to the service host
serviceHost.Description.Behaviors.Add(
     new RoutingBehavior(rc));
```

Tento příklad nakonfiguruje směrovací službu tak, aby zveřejnila jediný koncový bod s adresou `http://localhost:8000/routingservice/router`, která se používá k přijímání zpráv, které se mají směrovat. Vzhledem k tomu, že se zprávy směrují do koncových bodů požadavek-odpověď, koncový bod služby používá kontrakt <xref:System.ServiceModel.Routing.IRequestReplyRouter>. Tato konfigurace také definuje jeden koncový bod klienta `http://localhost:8000/servicemodelsample/service`, na který jsou zprávy směrovány. Tabulka filtru (není zobrazená) s názvem "routingTable1" obsahuje logiku směrování používanou ke směrování zpráv a je přidružená k koncovému bodu služby pomocí **RoutingBehavior** (pro konfigurační soubor) nebo **Konfigurace RoutingConfiguration** (pro programovou konfiguraci).

### <a name="routing-logic"></a>Logika směrování

Pro definování logiky směrování, která se používá ke směrování zpráv, je nutné určit, která data obsažená v příchozích zprávách se mají jedinečně zpracovávat. Pokud například všechny cílové koncové body, které chcete směrovat, sdílí stejné akce SOAP, hodnota akce obsažená ve zprávě není dobrý indikátor, na který konkrétní koncový bod má být zpráva směrována. Pokud je nutné zprávy jednoznačně směrovat do jednoho konkrétního koncového bodu, měli byste filtrovat data, která jednoznačně identifikují cílový koncový bod, na který je zpráva směrována.

Směrovací služba poskytuje několik implementací **MessageFilter** , které kontrolují konkrétní hodnoty v rámci zprávy, jako je adresa, akce, název koncového bodu nebo dokonce dotaz XPath. Pokud žádná z těchto implementací nevyhovuje vašim potřebám, můžete vytvořit vlastní **MessageFilter** implementaci. Další informace o filtrech zpráv a porovnání implementací používaných směrovací službou najdete v tématu [filtry zpráv](message-filters.md) a [Výběr filtru](choosing-a-filter.md).

Více filtrů zpráv je uspořádáno společně do tabulek filtrů, které přiřadí jednotlivé **MessageFilter** k cílovému koncovému bodu. V případě potřeby můžete také použít tabulku filtru k určení seznamu záložních koncových bodů, ke kterým se služba Směrování pokusí odeslat zprávu v případě selhání přenosu.

Ve výchozím nastavení jsou všechny filtry zpráv v tabulce filtru vyhodnocovány současně. Můžete však zadat <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A>, který způsobí vyhodnocení filtru zprávy v určitém pořadí. Nejprve se vyhodnotí všechny položky s nejvyšší prioritou a filtry zpráv s nižšími prioritami se nevyhodnotí, pokud se shoda najde na vyšší úrovni priority. Další informace o tabulkách filtru najdete v tématu [filtry zpráv](message-filters.md).

V následujících příkladech je použit <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, který se vyhodnotí jako `true` pro všechny zprávy. Tento **MessageFilter** se přidá do tabulky filtru "routingTable1", která přidružuje **MessageFilter** k koncovému bodu klienta s názvem "CalculatorService". **RoutingBehavior** pak určí, že se má tato tabulka používat ke směrování zpráv zpracovávaných koncovým bodem služby.

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name="routingData">
      <serviceMetadata httpGetEnabled="True"/>
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->
      <routing filterTableName="routingTable1" />
    </behavior>
  </serviceBehaviors>
</behaviors>
<!--ROUTING SECTION -->
<routing>
  <filters>
    <filter name="MatchAllFilter1" filterType="MatchAll" />
  </filters>
  <filterTables>
    <table name="routingTable1">
      <filters>
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />
      </filters>
    </table>
  </filterTables>
</routing>
```

```csharp
//create a new routing configuration object
RoutingConfiguration rc = new RoutingConfiguration();
//create the endpoint list that contains the endpoints to route to
//in this case we have only one
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();
endpointList.Add(client);
//add a MatchAll filter to the Router's filter table
//map it to the endpoint list defined earlier
//when a message matches this filter, it is sent to the endpoint contained in the list
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
```

> [!NOTE]
> Ve výchozím nastavení služba Směrování vyhodnocuje pouze záhlaví zprávy. Chcete-li povoleným filtrům přístup k textu zprávy, je nutné nastavit <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> na `false`.

**Odesílání**

I když řada konfigurací směrovací služby používá výhradní logiku filtru, která směruje zprávy pouze na jeden konkrétní koncový bod, může být nutné směrovat danou zprávu na více cílových koncových bodů. Pro vícesměrové vysílání zprávy na více cílů musí platit následující podmínky:

- Obrazec kanálu nesmí být Request-response (přestože může být jednosměrný nebo duplexní), protože klientská aplikace může v reakci na požadavek přijmout jenom jednu odpověď.

- Při vyhodnocování zprávy musí `true` vracet více filtrů.

Pokud jsou tyto podmínky splněny, zpráva bude směrována do všech koncových bodů všech filtrů, které jsou vyhodnoceny jako `true`. Následující příklad definuje konfiguraci směrování, která má za následek směrování zpráv do obou koncových bodů, pokud je adresa koncového bodu ve zprávě `http://localhost:8000/routingservice/router/rounding`.

```xml
<!--ROUTING SECTION -->
<routing>
  <filters>
    <filter name="MatchAllFilter1" filterType="MatchAll" />
    <filter name="RoundingFilter1" filterType="EndpointAddress"
            filterData="http://localhost:8000/routingservice/router/rounding" />
  </filters>
  <filterTables>
    <table name="routingTable1">
      <filters>
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />
        <add filterName="RoundingFilter1" endpointName="RoundingCalcService" />
      </filters>
    </table>
  </filterTables>
</routing>
```

```csharp
rc.FilterTable.Add(new MatchAllMessageFilter(), calculatorEndpointList);
rc.FilterTable.Add(new EndpointAddressMessageFilter(new EndpointAddress(
    "http://localhost:8000/routingservice/router/rounding")),
    roundingCalcEndpointList);
```

### <a name="soap-processing"></a>Zpracování SOAP

Aby bylo možné podporovat směrování zpráv mezi odlišnými protokoly, **RoutingBehavior** ve výchozím nastavení přidá <xref:System.ServiceModel.Routing.SoapProcessingBehavior> do všech koncových bodů klienta, na které jsou zprávy směrovány. Toto chování automaticky vytvoří novou **třídu MessageVersion** před směrováním zprávy do koncového bodu, stejně jako vytvoření kompatibilního souboru **MessageVersion** pro libovolný dokument odpovědi před jeho vrácením do žádající klientské aplikace.

Kroky pro vytvoření nové sady **MessageVersion** pro odchozí zprávy jsou následující:

**Zpracování žádosti**

- Získejte **třídu MessageVersion** odchozí vazby nebo kanálu.

- Získá čtečku textu pro původní zprávu.

- Vytvoří novou zprávu se stejnou akcí, čtečkou textu a novou **verzí MessageVersion**.

- Pokud <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>! = **Addressing. None**, zkopírujte do nové zprávy záhlaví do, z, FaultTo a RelatesTo.

- Kopírovat všechny vlastnosti zprávy do nové zprávy.

- Uloží původní zprávu požadavku, která se má použít při zpracování odpovědi.

- Vrátí novou zprávu požadavku.

**Zpracování odpovědí**

- Získejte **třídu MessageVersion** původní zprávy s požadavkem.

- Získejte čtečku textu pro přijatou zprávu odpovědi.

- Vytvoří novou zprávu odpovědi se stejnou akcí, čtečkou textu a **verzí** původní zprávy požadavku.

- Pokud <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>! = **Addressing. None**, zkopírujte do nové zprávy záhlaví do, z, FaultTo a RelatesTo.

- Zkopírujte vlastnosti zprávy do nové zprávy.

- Vrátí novou zprávu odpovědi.

Ve výchozím nastavení je **SoapProcessingBehavior** automaticky přidán do koncových bodů klienta <xref:System.ServiceModel.Routing.RoutingBehavior> při spuštění služby; Můžete však určit, zda bude zpracování protokolu SOAP přidáno do všech koncových bodů klienta pomocí vlastnosti <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A>. Můžete také přidat chování přímo do konkrétního koncového bodu a povolit nebo zakázat toto chování na úrovni koncového bodu, pokud je potřeba podrobnější řízení zpracování protokolu SOAP.

> [!NOTE]
> Je-li zpracování protokolu SOAP zakázáno pro koncový bod, který vyžaduje jinou třídu MessageVersion než původní zpráva požadavku, je nutné zadat vlastní mechanismus pro provedení všech úprav protokolu SOAP, které jsou požadovány před odesláním zprávy do cílový koncový bod.

V následujících příkladech slouží vlastnost **soapProcessingEnabled** k tomu, aby se zabránilo automatickému přidání **SoapProcessingBehavior** do všech koncových bodů klienta.

```xml
<behaviors>
  <!--default routing service behavior definition-->
  <serviceBehaviors>
    <behavior name="routingConfiguration">
      <routing filterTableName="filterTable1" soapProcessingEnabled="false"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

```csharp
//create the default RoutingConfiguration
RoutingConfiguration rc = new RoutingConfiguration();
rc.SoapProcessingEnabled = false;
```

### <a name="dynamic-configuration"></a>Dynamická konfigurace

Když přidáte další koncové body klienta nebo potřebujete upravit filtry, které se používají ke směrování zpráv, musíte mít způsob, jak dynamicky aktualizovat konfiguraci v době běhu, aby se zabránilo přerušení služby pro koncové body, které aktuálně přijímají zprávy. Směrovací služba. Změna konfiguračního souboru nebo kódu hostitelské aplikace není vždy dostatečná, protože kterákoli z metod vyžaduje recyklace aplikace, což by vedlo k potenciální ztrátě všech zpráv, které jsou právě přenášeny, a potenciální výpadek při čeká se na restartování služby.

**Konfigurace RoutingConfiguration** můžete změnit jenom programově. I když můžete službu zpočátku konfigurovat pomocí konfiguračního souboru, můžete změnit jenom konfiguraci za běhu, a to tak, že vytvoříte novou **Konfigurace RoutingConfiguration** a předáte ji jako parametr metodě <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> vystavené rozšířením služby <xref:System.ServiceModel.Routing.RoutingExtension>. Všechny zprávy, které jsou aktuálně ve přenosu, se budou směrovat pomocí předchozí konfigurace, zatímco zprávy přijaté po volání **ApplyConfiguration** používají novou konfiguraci. Následující příklad ukazuje vytvoření instance směrovací služby a následné úpravě konfigurace.

```csharp
RoutingConfiguration routingConfig = new RoutingConfiguration();
routingConfig.RouteOnHeadersOnly = true;
routingConfig.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
RoutingBehavior routing = new RoutingBehavior(routingConfig);
routerHost.Description.Behaviors.Add(routing);
routerHost.Open();
// Construct a new RoutingConfiguration
RoutingConfiguration rc2 = new RoutingConfiguration();
ServiceEndpoint clientEndpoint = new ServiceEndpoint();
ServiceEndpoint clientEndpoint2 = new ServiceEndpoint();
// Add filters to the FilterTable in the new configuration
rc2.FilterTable.add(new MatchAllMessageFilter(),
       new List<ServiceEndpoint>() { clientEndpoint });
rc2.FilterTable.add(new MatchAllMessageFilter(),
       new List<ServiceEndpoint>() { clientEndpoint2 });
rc2.RouteOnHeadersOnly = false;
// Apply the new configuration to the Routing Service hosted in
routerHost.routerHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc2);
```

> [!NOTE]
> Při aktualizaci směrovací služby tímto způsobem je možné předat pouze novou konfiguraci. Není možné upravovat pouze vybrané prvky aktuální konfigurace nebo připojit nové položky k aktuální konfiguraci; musíte vytvořit a předat novou konfiguraci, která nahradí stávající.

> [!NOTE]
> Všechny relace otevřené pomocí předchozí konfigurace pokračují v předchozí konfiguraci. Nová konfigurace je používána pouze novými relacemi.

## <a name="error-handling"></a>Zpracování chyb

Pokud při pokusu o odeslání zprávy dojde k nějaké <xref:System.ServiceModel.CommunicationException>, probíhá zpracování chyb. Tyto výjimky obvykle označují, že došlo k potížím při pokusu o komunikaci s definovaným koncovým bodem klienta, například <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>nebo <xref:System.ServiceModel.CommunicationObjectFaultedException>. Zpracování chyb – kód bude také zachytit a pokusit se o opakované odeslání, když dojde k <xref:System.TimeoutException>, což je další běžná výjimka, která není odvozena od **CommunicationException**.

Pokud dojde k jedné z předchozích výjimek, směrovací služba převezme seznam koncových bodů zálohy. Pokud se všechny koncové body zálohování nezdaří s chybou komunikace, nebo pokud koncový bod vrátí výjimku, která označuje chybu v cílové službě, služba Směrování vrátí chybu klientské aplikaci.

> [!NOTE]
> Funkce zpracování chyb zachytí a zpracovává výjimky, ke kterým dochází při pokusu o odeslání zprávy a při pokusu o zavření kanálu. Kód pro zpracování chyb není určen k detekci nebo zpracování výjimek vytvořených koncovými body aplikace, se kterými komunikuje. <xref:System.ServiceModel.FaultException>, který vyvolala služba, se ve směrovací službě zobrazí jako **FaultMessage** a přesměruje se na klienta.
>
> Pokud dojde k chybě, když se směrovací služba pokusí o předání zprávy, můžete získat <xref:System.ServiceModel.FaultException> na straně klienta, a ne <xref:System.ServiceModel.EndpointNotFoundException>, který byste normálně získali při absenci služby směrování. Směrovací služba může proto maskovat výjimky a neposkytuje úplnou transparentnost, Pokud neprojdete vnořené výjimky.

### <a name="tracing-exceptions"></a>Trasování výjimek

Při odeslání zprávy do koncového bodu v seznamu se služba Směrování vysleduje výsledná data výjimky a připojí podrobnosti o výjimce jako vlastnost zprávy s názvem **výjimky**. Tím se zachová data výjimky a umožní uživatelům programový přístup prostřednictvím kontroly zpráv.  Data výjimky jsou uložena na jednu zprávu ve slovníku, který mapuje název koncového bodu na podrobnosti výjimky zjištěné při pokusu o odeslání zprávy.

### <a name="backup-endpoints"></a>Koncové body zálohování

Každá položka filtru v tabulce filtru může volitelně určovat seznam koncových bodů zálohy, které se používají v případě selhání přenosu při odesílání do primárního koncového bodu. Pokud dojde k selhání, služba Směrování se pokusí zprávu přenést do první položky v seznamu koncových bodů zálohy. Pokud se tento pokus o odeslání narazí i na selhání přenosu, pokusí se další koncový bod v seznamu zálohování. Směrovací služba pokračuje v posílání zpráv do každého koncového bodu v seznamu, dokud se zpráva úspěšně nepřijme, všechny koncové body vrátí selhání přenosu, nebo koncový bod vrátí selhání bez přenosu.

Následující příklady nakonfigurují směrovací službu tak, aby používala seznam zálohování.

```xml
<routing>
  <filters>
    <!-- Create a MatchAll filter that catches all messages -->
    <filter name="MatchAllFilter1" filterType="MatchAll" />
  </filters>
  <filterTables>
    <!-- Set up the Routing Service's Message Filter Table -->
    <filterTable name="filterTable1">
        <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->
        <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
        <!-- Listed in the backupEndpointList -->
        <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
    </filterTable>
  </filterTables>
  <!-- Create the backup endpoint list -->
  <backupLists>
    <!-- Add an endpoint list that contains the backup destinations -->
    <backupList name="backupEndpointList">
      <add endpointName="realDestination" />
      <add endpointName="backupDestination" />
    </backupList>
  </backupLists>
</routing>
```

```csharp
//create the endpoint list that contains the service endpoints we want to route to
List<ServiceEndpoint> backupList = new List<ServiceEndpoint>();
//add the endpoints in the order that the Routing Service should contact them
//first add the endpoint that we know is down
//clearly, normally you wouldn't know that this endpoint was down by default
backupList.Add(fakeDestination);
//then add the real Destination endpoint
//the Routing Service attempts to send to this endpoint only if it
//encounters a TimeOutException or CommunicationException when sending
//to the previous endpoint in the list.
backupList.Add(realDestination);
//add the backupDestination endpoint
//the Routing Service attempts to send to this endpoint only if it
//encounters a TimeOutException or CommunicationsException when sending
//to the previous endpoints in the list
backupList.Add(backupDestination);
//create the default RoutingConfiguration option
RoutingConfiguration rc = new RoutingConfiguration();
//add a MatchAll filter to the Routing Configuration's filter table
//map it to the list of endpoints defined above
//when a message matches this filter, it is sent to the endpoints in the list in order
//if an endpoint is down or does not respond (which the first endpoint won't
//since the client does not exist), the Routing Service automatically moves the message
//to the next endpoint in the list and try again.
rc.FilterTable.Add(new MatchAllMessageFilter(), backupList);
```

### <a name="supported-error-patterns"></a>Podporované vzorce chyb

Následující tabulka popisuje vzory, které jsou kompatibilní s používáním seznamů záložních koncových bodů, spolu s poznámkami popisujícími podrobnosti zpracování chyb pro konkrétní vzory.

|Vzor|Relace|Transakce|Kontext příjmu|Seznam zálohování je podporovaný.|Poznámky:|
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|
|Jednosměrný||||Ano|Pokusí se znovu odeslat zprávu na koncový bod zálohy. Pokud je tato zpráva vícesměrové vysílání, do svého cílového umístění zálohy se přesune jenom zpráva v neúspěšném kanálu.|
|Jednosměrný||✔️||Ne|Je vyvolána výjimka a transakce je vrácena zpět.|
|Jednosměrný|||✔️|Ano|Pokusí se znovu odeslat zprávu na koncový bod zálohy. Po úspěšném přijetí zprávy dokončete všechny kontexty příjmu. Pokud není zpráva úspěšně přijata žádným koncovým bodem, neprovádějte kontext Receive.<br /><br /> Při vícesměrovém vysílání této zprávy je kontext příjmu dokončen pouze v případě, že zpráva byla úspěšně přijata alespoň jedním koncovým bodem (primárním nebo záložním). Pokud žádný z koncových bodů v žádné ze všech cest vícesměrového vysílání úspěšně neobdrží zprávu, neprovádějte kontext Receive.|
|Jednosměrný||✔️|✔️|Ano|Přerušit předchozí transakci, vytvořit novou transakci a znovu odeslat všechny zprávy. Zprávy, u kterých došlo k chybě, se přenáší do cílového umístění zálohy.<br /><br /> Po vytvoření transakce, ve které jsou všechny přenosy úspěšné, dokončete kontext příjmu a potvrďte transakci.|
|Jednosměrný|✔️|||Ano|Pokusí se znovu odeslat zprávu na koncový bod zálohy. Ve scénáři vícesměrového vysílání se v rámci zálohování znovu přemístí pouze zprávy v relaci, u kterých došlo k chybě, nebo v relaci, jejichž zavření relace se nezdařilo.|
|Jednosměrný|✔️|✔️||Ne|Je vyvolána výjimka a transakce je vrácena zpět.|
|Jednosměrný|✔️||✔️|Ano|Pokusí se znovu odeslat zprávu na koncový bod zálohy. Jakmile se všechna zpráva pošle bez chyby, relace indikuje žádné další zprávy a směrovací služba úspěšně zavřela všechny kanály odchozích relací, všechny kontexty příjmu jsou dokončeny a kanál příchozí relace je uzavřený.|
|Jednosměrný|✔️|✔️|✔️|Ano|Přeruší aktuální transakci a vytvoří novou. Znovu odešle všechny předchozí zprávy v relaci. Po vytvoření transakce, ve které byly všechny zprávy úspěšně odeslány a relace indikuje žádné další zprávy, jsou všechny kanály odchozích relací uzavřeny, jsou všechny kontexty příjmu dokončeny s transakcí, kanál příchozí relace je uzavřeno a transakce je potvrzena.<br /><br /> Když jsou relace vícesměrové vysílání, zprávy, u kterých došlo k chybě, se odešlou do stejného cílového umístění jako předtím a zprávy, které se objevily, se odesílají do cílů zálohování.|
|Obousměrný postup||||Ano|Odeslat do cílového umístění zálohy.  Až kanál vrátí zprávu odpovědi, vrátí odpověď původnímu klientovi.|
|Obousměrný postup|✔️|||Ano|Odeslat všechny zprávy na kanálu do cílového umístění zálohy.  Až kanál vrátí zprávu odpovědi, vrátí odpověď původnímu klientovi.|
|Obousměrný postup||✔️||Ne|Je vyvolána výjimka a transakce je vrácena zpět.|
|Obousměrný postup|✔️|✔️||Ne|Je vyvolána výjimka a transakce je vrácena zpět.|
|Duplex||||Ne|Komunikace bez relací není v současné době podporovaná.|
|Duplex|✔️|||Ano|Odeslat do cílového umístění zálohy.|

## <a name="hosting"></a>Hostování

Vzhledem k tomu, že je služba Směrování implementována jako služba WCF, musí být buď v rámci aplikace, nebo hostovaná službou IIS, nebo WAS. Doporučuje se, aby směrovací služba byla hostována buď ve službě IIS, WAS, nebo v aplikaci služby systému Windows, která umožňuje využívat funkce automatické správy spuštění a životního cyklu, které jsou k dispozici v těchto hostitelských prostředích.

Následující příklad znázorňuje hostování směrovací služby v aplikaci.

```csharp
using (ServiceHost serviceHost =
                new ServiceHost(typeof(RoutingService)))
```

Chcete-li hostovat směrovací službu ve službě IIS nebo WAS, je nutné buď vytvořit soubor služby (. svc), nebo použít aktivaci služby na základě konfigurace. Při použití souboru služby je nutné zadat <xref:System.ServiceModel.Routing.RoutingService> pomocí parametru služby. Následující příklad obsahuje ukázkový soubor služby, který se dá použít k hostování směrovací služby se službou IIS nebo WAS.

```aspx-csharp
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,
     PublicKeyToken=31bf3856ad364e35" %>
```

## <a name="routing-service-and-impersonation"></a>Služba Směrování a zosobnění

Směrovací službu WCF lze použít s zosobněním pro posílání i přijímání zpráv. Platí všechna obvyklá omezení Windows pro zosobnění. Pokud jste museli nastavit oprávnění služby nebo účtu pro použití zosobnění při psaní vlastní služby, budete muset provést stejný postup, abyste mohli použít zosobnění u směrovací služby. Další informace najdete v tématu [delegování a zosobnění](delegation-and-impersonation-with-wcf.md).

Zosobnění pomocí směrovací služby vyžaduje buď použití zosobnění ASP.NET v režimu kompatibility ASP.NET, nebo použití přihlašovacích údajů systému Windows, které byly nakonfigurovány tak, aby umožňovaly zosobnění. Další informace o režimu kompatibility ASP.NET najdete v tématu [služby WCF a ASP.NET](wcf-services-and-aspnet.md).

> [!WARNING]
> Směrovací služba WCF nepodporuje zosobnění s využitím základního ověřování.

Pokud chcete používat zosobnění ASP.NET se službou směrování, povolte v hostitelském prostředí služby režim kompatibility ASP.NET. Směrovací služba již byla označena jako povolení režimu kompatibility ASP.NET a zosobnění bude automaticky povoleno. Zosobnění je jediné podporované použití integrace ASP.NET se směrovací službou.

Pokud chcete používat zosobnění přihlašovacích údajů systému Windows se službou směrování, je nutné nakonfigurovat pověření i službu. Objekt přihlašovacích údajů klienta (<xref:System.ServiceModel.Security.WindowsClientCredential>přístupný z <xref:System.ServiceModel.ChannelFactory>) definuje vlastnost <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>, která musí být nastavena tak, aby povolovala zosobnění. Nakonec ve službě potřebujete nakonfigurovat chování <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> pro nastavení `ImpersonateCallerForAllOperations` na `true`. Směrovací služba používá tento příznak k rozhodnutí, jestli se mají vytvořit klienti pro předávání zpráv s povoleným zosobněním.

## <a name="see-also"></a>Viz také

- [Filtry zpráv](message-filters.md)
- [Kontrakty pro směrování](routing-contracts.md)
- [Výběr filtru](choosing-a-filter.md)
