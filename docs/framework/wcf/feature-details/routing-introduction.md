---
title: Směrování – úvod
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: d0f07d0dd171de428f7d556d84dfda04e35880b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158675"
---
# <a name="routing-introduction"></a>Směrování – úvod
Směrovací služba poskytuje obecný modulární SOAP zprostředkovatel, který je schopen směrování zpráv na základě obsahu zpráv. Ve službě Směrování můžete vytvořit komplexní logiku směrování, která umožňuje implementovat scénáře, jako je služba agregace, Správa verzí služby, priority směrování a směrování vícesměrového vysílání. Směrovací služba taky poskytuje chyba zpracování, který umožňuje nastavení seznamů zálohování koncových bodů, do které se odešlou zprávy, pokud dojde k chybě při odesílání na cílové primární koncový bod.  
  
 Toto téma je určené pro ty novým uživatelům služby Směrování a pokrývá základní konfiguraci a který je hostitelem služby směrování.  
  
## <a name="configuration"></a>Konfigurace  
 Směrovací služba je implementovaná jako služba WCF, který zpřístupňuje jeden nebo více koncových bodů služby, které přijímají zprávy z klientských aplikací a směrování zpráv do cílové koncové body. Poskytuje služby <xref:System.ServiceModel.Routing.RoutingBehavior>, který se použije ke koncovým bodům služby určeného službou. Toto chování slouží ke konfiguraci různých aspektů jak služba funguje. Pro usnadnění konfigurace, pokud je používán konfigurační soubor, parametry jsou určeny na **chování RoutingBehavior**. Ve scénářích založený na kódu, tyto parametry by se zadal jako součást <xref:System.ServiceModel.Routing.RoutingConfiguration> objektu, který je pak možné předat do **chování RoutingBehavior**.  
  
 Při spouštění, přidá toto chování <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, který se používá k provedení protokolu SOAP zpracování zpráv do koncových bodů klienta. To umožňuje službě směrování přenosu zpráv do koncových bodů, které vyžadují jinou **MessageVersion** než byla přijata zpráva přes koncový bod. **Chování RoutingBehavior** také zaregistruje rozšíření služby, <xref:System.ServiceModel.Routing.RoutingExtension>, který představuje bod usnadnění pro úpravu konfigurace služby směrování v době běhu.  
  
 **Konfigurace RoutingConfiguration** třída poskytuje konzistentní způsob konfigurace a aktualizuje se konfigurace služby směrování.  Obsahuje parametry, které fungují jako nastavení služby Směrování a slouží ke konfiguraci **chování RoutingBehavior** při spuštění služby, nebo je předán **třída RoutingExtension** upravit směrování konfigurace v době běhu.  
  
 Směrování logika používá ke směrování na základě obsahu zpráv je definována seskupením několika <xref:System.ServiceModel.Dispatcher.MessageFilter> objekty do filtru tabulky (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objekty). Příchozí zprávy se vyhodnocují před filtry zpráv obsažené v tabulce filtrů a pro každou **MessageFilter** , který odpovídá zprávě, předávají do cílového koncového bodu. Tabulky filtru, který se má použít pro směrování zpráv je určené vlastností buď **chování RoutingBehavior** v konfiguraci nebo prostřednictvím kódu pomocí **konfigurace RoutingConfiguration** objektu.  
  
### <a name="defining-endpoints"></a>Definování koncových bodů  
 Když to může zdát, že byste měli začít konfiguraci tak, že definujete směrování logika, kterou budete používat, prvním krokem by ve skutečnosti k určení tvaru budete směrování zpráv do koncových bodů. Směrovací služba používá smlouvy definující tvar kanály použité pro příjem a odesílání zpráv a proto tvar vstupní kanál musí odpovídat výstupní kanál.  Například pokud jsou směrování do koncových bodů, které používají tvar kanálu požadavek odpověď, pak musíte použít kompatibilní kontrakt na vstupní koncové body, jako <xref:System.ServiceModel.Routing.IRequestReplyRouter>.  
  
 To znamená, že pokud vaše cílové koncové body pomocí smluv s více vzorky komunikace (jako je například míchání jednosměrnou a obousměrnou), nebude možné vytvořit koncový bod jedinou službou, která může přijímat a směrování zpráv do všech z nich. Musíte určit, jaké koncové body kompatibilní obrazce a definovat jeden nebo více koncových bodů služby, které se použijí pro příjem zpráv má být směrována na cílové koncové body.  
  
> [!NOTE]
> Při práci s smluv, které určují víc komunikačních schémat (například kombinaci jednosměrnou a obousměrnou operations), použití duplexního kontraktu na směrování služby, jako je řešení <xref:System.ServiceModel.Routing.IDuplexSessionRouter>. Ale to znamená, že vazba musí být schopné duplexní komunikaci, která nemusí být možné pro všechny scénáře. V situacích, kdy to není možné může být nutné které budou zohledňovat komunikaci do více koncových bodů nebo úpravách aplikace.  
  
 Další informace o kontrakty pro směrování najdete v tématu [kontrakty pro směrování](routing-contracts.md).  
  
 Po definování koncového bodu služby, můžete použít **chování RoutingBehavior** přidružit konkrétní **konfigurace RoutingConfiguration** s koncovým bodem. Při konfiguraci pomocí konfiguračního souboru služby směrování **chování RoutingBehavior** slouží k určení filtru tabulky, která obsahuje logiku směrování používají ke zpracování zpráv přijatých na tomto koncovém bodu. Pokud konfigurujete směrovací služba prostřednictvím kódu programu můžete zadat filtr tabulky pomocí **konfigurace RoutingConfiguration**.  
  
 Následující příklad definuje služeb a klientských koncových bodů, které se používají službou směrování, jak prostřednictvím kódu programu a pomocí konfiguračního souboru.  
  
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
  
 Tento příklad konfiguruje službu směrování k vystavení jednoho koncového bodu s adresou `http://localhost:8000/routingservice/router`, který se používá pro příjem zpráv bude směrovat. Protože zprávy jsou směrovány do koncových bodů požadavek odpověď, koncový bod služby používá <xref:System.ServiceModel.Routing.IRequestReplyRouter> kontraktu. Tato konfigurace taky definuje je koncový bod konkrétního klienta `http://localhost:8000/servicemodelsample/service` zprávy jsou směrovány do. Filtr tabulky (není vidět) s názvem "routingTable1" obsahuje logiku směrování slouží ke směrování zpráv a je přidružen koncový bod služby s použitím **chování RoutingBehavior** (pro konfigurační soubor) nebo  **Konfigurace RoutingConfiguration** (pro programovou konfiguraci).  
  
### <a name="routing-logic"></a>Logiku směrování  
 K definování směrování logikou používanou pro směrování zpráv, musíte určit, co mohou být data obsažená v rámci příchozích zpráv jednoznačně reagovali na ni. Například pokud všechny cílové koncové body, které jsou směrování sdílet stejné akce SOAP hodnotu akce obsažené v něm není jasně ukazuje na jaké konkrétní koncového bodu zprávy by měl směrovat na. Pokud jeden konkrétní koncový bod musí jednoznačně směrovat zprávy, by měl filtrovat data, která jednoznačně identifikuje cílového koncového bodu, který se zpráva směruje do.  
  
 Směrovací služba nabízí několik **MessageFilter** implementace, které zkontrolovat konkrétní hodnoty ve zprávě, jako je například adresa, akce, název koncového bodu nebo dokonce dotaz XPath. Pokud žádná z těchto implementací nevyhovuje vašim potřebám, můžete vytvořit vlastní **MessageFilter** implementace. Další informace o filtrech zpráv a porovnání implementace používá služba Směrování najdete v tématu [filtry zpráv](message-filters.md) a [výběr filtru](choosing-a-filter.md).  
  
 Několik filtrů zpráv jsou uspořádané do filtru tabulky, které každou **MessageFilter** s koncovým bodem v cílové. Volitelně můžete filtru tabulky lze také zadat seznam koncových bodů zálohování, které směrovací služba se pokusí odeslat zprávu, která se v případě selhání přenosu.  
  
 Ve výchozím nastavení se všechny filtry zpráv v tabulce filtrů vyhodnocují současně; Můžete však zadat <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> , který způsobí, že filtry zpráv, který se má vyhodnotit v určitém pořadí. Všechny položky s nejvyšší prioritou jsou vyhodnoceny jako první a filtry zpráv nižší priority nebudou vyhodnoceny, pokud se najde shoda na vyšší úrovni priority. Další informace o filtru tabulky, najdete v části [filtry zpráv](message-filters.md).  
  
 Následující příklady používají <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, který se hodnotí jako `true` pro všechny zprávy. To **MessageFilter** se přidá do tabulky "routingTable1" filtr, který přidruží **MessageFilter** s koncovým bodem klienta s názvem "CalculatorService". **Chování RoutingBehavior** pak určuje, že tato tabulka má být použito pro směrování zpráv zpracovaných v koncovém bodě služby.  
  
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
>  Ve výchozím nastavení vyhodnotí směrovací služba pouze záhlaví zprávy. Pokud chcete povolit filtry pro přístup k textu zprávy, je nutné nastavit <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> k `false`.  
  
 **Vícesměrové vysílání**  
  
 Zatímco mnoho konfigurací směrovací služba použít exkluzivní filtr logiku, která provádí směrování zpráv do jediného určitého koncového bodu, budete muset směrování danou zprávu do více cílové koncové body. K vícesměrovému vysílání zpráv do více cílů musí být splněné následující podmínky:  
  
-   Tvar kanálu nesmí být požadavek odpověď (i když mohou být jednosměrné nebo obousměrné,) vzhledem k tomu, že pouze jednu odpověď lze přijímat pomocí klientské aplikace v odpovědi na požadavek.  
  
-   Několik filtrů musí vracet `true` při vyhodnocování zprávy.  
  
 Pokud jste splnili tyto podmínky se zpráva směruje na všechny koncové body všech filtrů, která se vyhodnotí `true`. Následující příklad definuje konfiguraci směrování, jejímž výsledkem zprávy směruje se oba koncové body v případě, že je adresa koncového bodu ve zprávě `http://localhost:8000/routingservice/router/rounding`.  
  
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
 Pro podporu směrování zpráv mezi rozdílných protokolů **chování RoutingBehavior** ve výchozím nastavení přidá <xref:System.ServiceModel.Routing.SoapProcessingBehavior> do všech koncových bodů klienta, které zprávy jsou směrovány na. Toto chování automaticky vytvoří nový **MessageVersion** před směrováním zprávy na koncový bod, jakož i vytváření kompatibilní **MessageVersion** pro jakýkoliv dokument odpověď před vrácením do žádost o klientská aplikace.  
  
 Kroky k vytvoření nového **MessageVersion** odchozí zprávy jsou následující:  
  
 **Zpracování žádosti**  
  
-   Získejte **MessageVersion** výstupní vazbu/kanálu.  
  
-   Získejte čtečka textu pro původní zprávy.  
  
-   Vytvořte novou zprávu o stejnou akci, čtečky textu a nový **MessageVersion**.  
  
-   Pokud <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, zkopírujte do, z FaultTo a záhlaví RelatesTo nové zprávy.  
  
-   Zkopírujte všechny vlastnosti zprávy do nové zprávy.  
  
-   Store původní zprávy s požadavkem pro použití při zpracování odpovědi.  
  
-   Vrátí novou zprávu požadavku.  
  
 **Zpracování odpovědi**  
  
-   Získejte **MessageVersion** původní zprávy s požadavkem.  
  
-   Získání čtečky textu zprávy přijaté odpovědi.  
  
-   Vytvoření nové zprávy odpovědi se stejnou akci, čtečky textu a **MessageVersion** původní zprávy s požadavkem.  
  
-   Pokud <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, zkopírujte do, z FaultTo a záhlaví RelatesTo nové zprávy.  
  
-   Zkopírujte vlastnosti zprávy do nové zprávy.  
  
-   Vrátí nové zprávy odpovědi.  
  
 Ve výchozím nastavení **SoapProcessingBehavior** se automaticky přidá do koncových bodů klienta podle <xref:System.ServiceModel.Routing.RoutingBehavior> při spuštění služby; však můžete řídit, zda zpracování SOAP se přidá do všech koncových bodů klienta pomocí <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> vlastnost. Můžete také přidat chování přímo do určitého koncového bodu a povolit nebo zakázat toto chování na úrovni koncového bodu, pokud přesněji řídit zpracování SOAP se vyžaduje.  
  
> [!NOTE]
>  Pokud zpracování SOAP je zakázaná pro koncový bod, který vyžaduje jinou třídu MessageVersion než původní zprávy s požadavkem, je nutné zadat vlastní mechanismus pro provedení změny protokolu SOAP, které jsou nutné před odesláním zprávy cílový koncový bod.  
  
 V následujících příkladech **soapProcessingEnabled** vlastnost se používá při prevenci **SoapProcessingBehavior** z automaticky přidán do všech koncových bodů klientů.  
  
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
  
### <a name="dynamic-configuration"></a>Dynamickou konfiguraci  
 Při přidání dalších klientských koncových bodů, nebo třeba upravit filtry, které se používají ke směrování zpráv, potřebujete způsob, jak aktualizovat konfiguraci dynamicky za běhu, aby se zabránilo přerušení služby aktuálně příjem zpráv pomocí koncových bodů Služba směrování. Úprava konfiguračního souboru nebo kód hostitelskou aplikaci nestačí vždy, protože některé z metod vyžaduje provedení recyklace aplikace, což by mohlo dojít k potenciální ztrátě všechny zprávy momentálně v provozu a má větší potenciál pro výpadku, zatímco Čekání na službu restartovat.  
  
 Upravit lze pouze **konfigurace RoutingConfiguration** prostřednictvím kódu programu. Zatímco služba může počáteční konfiguraci pomocí konfiguračního souboru, můžete upravovat konfiguraci za běhu pouze tak, že vytváří nový **RoutingConfigution** a předejte ji jako parametr, který se <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> – metoda vystavené <xref:System.ServiceModel.Routing.RoutingExtension> služby rozšíření. Všechny zprávy aktuálně při přenosu i nadále možné směrovat pomocí předchozí konfigurace, při zprávy přijaté po volání **ApplyConfiguration** používat nové nakonfigurování. Následující příklad ukazuje vytvoření instance služby Směrování a následně úpravou konfigurace.  
  
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
>  Při aktualizaci služby směrování tímto způsobem je pouze možné předat novou konfiguraci. Není možné změnit pouze vybrané prvky aktuální konfigurace nebo přidání nových položek do aktuální konfigurace. musíte vytvořit a předat novou konfiguraci, která nahradí stávající.  
  
> [!NOTE]
>  Otevřít pomocí předchozí konfiguraci relace pokračovat pomocí předchozí konfigurace. Nová konfigurace se používá pouze pomocí nové relace.  
  
## <a name="error-handling"></a>Zpracování chyb  
 Pokud existuje <xref:System.ServiceModel.CommunicationException> dochází při pokusu o odeslání zprávy, zkuste místo pro zpracování chyb. Tyto výjimky obvykle signalizují, že došlo k potížím při pokusu o komunikaci s koncovým bodem definované klienta, například <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, nebo <xref:System.ServiceModel.CommunicationObjectFaultedException>. Zpracování – kód chyby: také zachytit a pokus opakujte při odesílání <xref:System.TimeoutException> dojde, což je další běžné výjimku, která není odvozena od **communicationexception –**.  
  
 Při jedné z předchozí výjimky, směrovací služba převezme služby při selhání do seznamu zálohy koncových bodů. Pokud všechny koncové body zálohování neúspěšné a zobrazí se selháním komunikace nebo pokud koncový bod vrací výjimku, která indikuje selhání v rámci cílové služby, směrovací služba vrátí chybu do klientské aplikace.  
  
> [!NOTE]
>  Funkce zpracování chyb shromažďuje a zpracovává výjimky, ke kterým dochází při pokusu o odeslání zprávy a při pokusu o zavření kanálu. Kód pro zpracování chyb není určena pro zjišťování nebo zpracování výjimek vytvořených koncových bodů aplikace, který komunikuje s; <xref:System.ServiceModel.FaultException> vyvolané služby se zobrazí na směrování služby jako **FaultMessage** a je počet plynoucích zpět do klienta.  
>   
>  Pokud dojde k chybě, když se pokusí služba směrování přenosu zprávy, se může zobrazit <xref:System.ServiceModel.FaultException> na straně klienta, spíše než <xref:System.ServiceModel.EndpointNotFoundException> získali byste normálně chybí směrovací službou. Směrovací služba může proto maskovat výjimky a poskytovat úplnou transparentnost není-li prozkoumat vnořené výjimky.  
  
### <a name="tracing-exceptions"></a>Sledování výjimek  
 Při odesílání zprávy na koncový bod v seznamu se nezdaří, směrovací služba trasování Výsledná data výjimky a připojí podrobnosti o výjimce jako do zprávy vlastnost s názvem **výjimky**. To zachová data výjimky a umožňuje programový přístup uživatelů prostřednictvím zprávy inspector.  Výjimka data se ukládají na zprávu ve slovníku, který mapuje název koncového bodu na podrobnosti o výjimce došlo při pokusu o odeslání zprávy.  
  
### <a name="backup-endpoints"></a>Zálohování koncových bodů  
 Každá položka filtru v tabulce filtrů můžete volitelně zadat seznamu zálohy koncových bodů, které se používají v případě selhání přenosu, při odesílání na primární koncový bod. Pokud dojde k takové chybě, směrovací služba se pokusí zaslání zprávy na první položku v seznamu zálohy koncových bodů. Pokud tento pokus o odeslání také zaznamená selhání přenosu, zkusí se další koncový bod v seznamu záloh. Směrovací služba pokračuje v odesílání zprávy pro každý koncový bod v seznamu, dokud úspěšně doručení zprávy, všechny koncové body, vrátí hodnotu Neúspěch přenosu nebo selhání než přenos je vrácený koncový bod.  
  
 Následující příklady konfigurovat směrovací služba použít záložní seznam.  
  
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
  
### <a name="supported-error-patterns"></a>Vzory podporované chyb  
 Následující tabulka popisuje vzory, které jsou kompatibilní s použitím seznamů záložního koncového bodu, spolu s poznámky popisující podrobnosti o zpracování chyb pro určité vzory.  
  
|Vzor|Relace|Transakce|Kontextu přijetí|Nepodporuje zálohování seznamu|Poznámky|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|Jednosměrný||||Ano|Pokusí se znovu odeslat zprávu na záložního koncového bodu. Pokud se tato zpráva vícesměrového vysílání, pouze zprávu na selhání kanálu je přesunout do jeho cílovou složku zálohy.|  
|Jednosměrný||✓||Ne|Vyvolá se výjimka a transakce je vrácena zpět.|  
|Jednosměrný|||✓|Ano|Pokusí se znovu odeslat zprávu na záložního koncového bodu. Po zprávy se úspěšně přijatá, dokončení všech zobrazí kontexty. Pokud zpráva není úspěšně přijme libovolný koncový bod, nejsou dokončeny kontext přijetí.<br /><br /> Když se tato zpráva vícesměrového vysílání, kontext přijetí se dokončí, pouze pokud zpráva se úspěšně přijme aspoň jeden koncový bod (primárních nebo záložních). Pokud žádný z koncových bodů v některém z vícesměrového vysílání cesty úspěšně zobrazí zpráva, kontext přijetí nedokončí.|  
|Jednosměrný||✓|✓|Ano|Přerušit předchozí transakce, vytvořte novou transakci a znovu odeslat všechny zprávy. Cíl zálohy se přenáší zprávy, které došlo k chybě.<br /><br /> Po vytvoření transakce ve kterém veškeré přenosy dat úspěšné dokončení kontexty přijetí a potvrzení transakce.|  
|Jednosměrný|✓|||Ano|Pokusí se znovu odeslat zprávu na záložního koncového bodu. V případě vícesměrového vysílání se znovu pouze zprávy v relaci došlo k chybě nebo relaci zavřete jehož relaci se nepovedlo odeslat do cíle zálohování.|  
|Jednosměrný|✓|✓||Ne|Vyvolá se výjimka a transakce je vrácena zpět.|  
|Jednosměrný|✓||✓|Ano|Pokusí se znovu odeslat zprávu na záložního koncového bodu. Po všechny zprávy odešle dokončena bez chyb, relace indikuje žádné další zprávy a služba Směrování úspěšně zavře všechny odchozí relace kanálů, obdrží všechny kontexty jsou dokončeny, a kanálů příchozích relací je uzavřen.|  
|Jednosměrný|✓|✓|✓|Ano|Zrušit aktuální transakci a vytvořte novou. Znovu odešlete všechny předchozí zprávy v relaci. Poté, co byl vytvořen transakce které všechny zprávy se úspěšně odeslaly a relace indikuje, že se žádné další zprávy, všechny odchozí relace kanály zavřená, zobrazí všechny kontexty jsou dokončeny s transakcí, je kanálů příchozích relací zavření, a je transakce potvrzena.<br /><br /> Když probíhá relace vícesměrového vysílání zpráv, u kterých nedošlo k chybě se zopakuje pro stejný cíl jako před a zpráv, ke které došlo k chybě odesílají do cíle zálohování.|  
|Obousměrný||||Ano|Poslat cílovou složku zálohy.  Po kanál vrátí zprávu odpovědi, vrátí odpověď klientovi původní.|  
|Obousměrný|✓|||Ano|Odeslání všech zpráv na kanál pro cílovou složku zálohy.  Po kanál vrátí zprávu odpovědi, vrátí odpověď klientovi původní.|  
|Obousměrný||✓||Ne|Vyvolá se výjimka a transakce je vrácena zpět.|  
|Obousměrný|✓|✓||Ne|Vyvolá se výjimka a transakce je vrácena zpět.|  
|Duplex||||Ne|Duplexní komunikaci mimo relace se aktuálně nepodporuje.|  
|Duplex|✓|||Ano|Poslat cílovou složku zálohy.|  
  
## <a name="hosting"></a>Hostování  
 Protože směrovací služba je implementovaná jako služba WCF, se musí být buď v rámci aplikace v místním prostředí nebo hostované službou IIS nebo WAS. Doporučuje se, že směrovací služba hostitelem služby IIS, WAS nebo aplikace služby Windows využít k automatickému spuštění a životního cyklu správy funkce dostupné v těchto prostředích.  
  
 Následující příklad ukazuje, který je hostitelem služby směrování v aplikaci.  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 K hostování služby směrování v rámci služby IIS nebo WAS, musíte vytvořit soubor služby (.svc) nebo použít aktivaci prostřednictvím konfigurace služby. Při použití souboru služby, je nutné zadat <xref:System.ServiceModel.Routing.RoutingService> pomocí parametru služby. Následující příklad obsahuje ukázkový soubor služby, který slouží k hostování služby směrování pomocí služby IIS nebo WAS.  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a>Služba Směrování a zosobnění  
 Směrovací služba WCF je možné s zosobnění pro odesílání a příjem zpráv. Použít obvyklé omezení Windows zosobnění. Pokud byste potřebovali nastavení účtu služby nebo oprávnění k použití zosobnění při zápisu vlastní služby, pak budete muset provést tyto stejné kroky pro použití zosobnění se směrovací službou. Další informace najdete v tématu [delegace a zosobnění](delegation-and-impersonation-with-wcf.md).  
  
 Zosobnění se směrovací službou vyžaduje použití zosobnění technologie ASP.NET v režimu kompatibility ASP.NET nebo používání přihlašovacích údajů Windows, které jsou nakonfigurované k povolení zosobnění. Další informace o režim kompatibility ASP.NET najdete v tématu [služby WCF a ASP.NET](wcf-services-and-aspnet.md).  
  
> [!WARNING]
>  Směrovací služba WCF nepodporuje zosobnění se základním ověřováním.  
  
 Použití zosobnění technologie ASP.NET se směrovací službou, povolte režim kompatibility ASP.NET ve službě hostitelské prostředí. Směrovací služba již byla označena jako umožňuje režim kompatibility ASP.NET a zosobnění se automaticky povolí. Zosobnění je podporované pouze použití integrace ASP.NET se směrovací službou.  
  
 Použití zosobnění přihlašovacích údajů Windows se směrovací službou musíte nakonfigurovat přihlašovací údaje a služby. Objekt přihlašovacích údajů klienta (<xref:System.ServiceModel.Security.WindowsClientCredential>, přístupné z <xref:System.ServiceModel.ChannelFactory>) definuje <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnost, která musí být nastaven tak, aby povolovala zosobnění. Nakonec ve službě je nutné nakonfigurovat <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> chování nastavení `ImpersonateCallerForAllOperations` k `true`. Směrovací služba používá tento příznak se rozhodnout, jestli se má vytvořit klienty pro předávání zpráv s zosobnění povoleno.  
  
## <a name="see-also"></a>Viz také:

- [Filtry zpráv](message-filters.md)
- [Kontrakty pro směrování](routing-contracts.md)
- [Výběr filtru](choosing-a-filter.md)
