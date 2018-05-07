---
title: Směrování – úvod
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 3ee7ea8271df47354a0897434bf8f203eaf09a51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="routing-introduction"></a>Směrování – úvod
Poskytuje službu Směrování obecné modulární SOAP zprostředkující umožňující směrování zpráv na základě obsahu zprávy. Se službou směrování můžete vytvořit komplexní směrování logiku, která umožňuje implementovat scénáře, jako je služba agregace, verze služby, s prioritou směrování a směrování vícesměrového vysílání. Směrovací služby obsahuje také chyba zpracování, které umožňuje nastavit seznam zálohování koncových bodů, ke kterému jsou zprávy odesílány, pokud dojde k chybě při odesílání na cílové primární koncový bod.  
  
 Toto téma je určené pro ty novým uživatelům služby Směrování a popisuje základní konfigurace a který je hostitelem služby směrování.  
  
## <a name="configuration"></a>Konfigurace  
 Směrovací služby je implementovaný jako službu WCF, které vystavuje jeden nebo více služby koncových bodů, které přijímají zprávy z klientské aplikace a směrování zpráv na jeden nebo více cílové koncové body. Poskytuje služby <xref:System.ServiceModel.Routing.RoutingBehavior>, který se použije ke koncovým bodům služby, který je zveřejněný prostřednictvím služby. Toto chování slouží ke konfiguraci různé aspekty jak služba funguje. Pro usnadnění konfigurace při použití konfiguračního souboru, parametry jsou zadány na **RoutingBehavior**. Ve scénářích založené na kódu by tyto parametry zadané v rámci <xref:System.ServiceModel.Routing.RoutingConfiguration> objekt, který může být předána do **RoutingBehavior**.  
  
 Při spouštění, přidá toto chování <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, který se používá k provádění SOAP zpracování zpráv, na koncové body klientů. To umožňuje službě směrování přenosu zpráv do koncových bodů, které vyžadují jinou **verze MessageVersion** než zpráva byla přijata přes koncový bod. **RoutingBehavior** také zaregistruje rozšíření služby, <xref:System.ServiceModel.Routing.RoutingExtension>, které poskytuje bod usnadnění pro úpravu konfigurace směrování služby za běhu.  
  
 **RoutingConfiguration** třída poskytuje konzistentní způsob konfigurace a aktualizuje se konfigurace služby směrování.  Obsahuje parametry, které fungují jako nastavení služby Směrování a slouží ke konfiguraci **RoutingBehavior** při spuštění služby, nebo je předán **RoutingExtension** k úpravě směrování konfigurace v době běhu.  
  
 Směrování logikou používanou k provedení na základě obsahu směrování zpráv je definované seskupení více <xref:System.ServiceModel.Dispatcher.MessageFilter> filtrovat objekty společně do tabulky (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objektů). Příchozí zprávy jsou porovnán s filtry zpráv, které jsou obsažené v tabulce filtru a pro každou **MessageFilter** odpovídající zprávu, předají do cílového koncového bodu. Je zadána buď pomocí filtru tabulky, který se má použít pro směrování zpráv **RoutingBehavior** v konfiguraci nebo prostřednictvím kódu pomocí **RoutingConfiguration** objektu.  
  
### <a name="defining-endpoints"></a>Definování koncové body  
 Při může zdát, že začněte konfiguraci definováním logice směrování, které budete používat, prvním krokem by měl být ve skutečnosti k určení tvaru, který bude směrování zpráv do koncových bodů. Směrovací služby používá smluv, které definují obrazec kanály použité pro příjem a odesílání zpráv, a proto obrazec vstupní kanál nástroje se musí shodovat s kanálu výstup.  Například, pokud jsou směrování do koncových bodů, které používají tvar kanálu požadavku a odpovědi, pak musíte použít kontraktu kompatibilní na příchozí koncových bodů, například <xref:System.ServiceModel.Routing.IRequestReplyRouter>.  
  
 To znamená, že pokud cílové koncové body používat kontrakty s více komunikačních schémat (například kombinování jednosměrná a obousměrná operations), nebude možné vytvořit jeden služby koncový bod, který může přijímat a směrování zpráv do všech z nich. Je třeba určit, které koncové body kompatibilní tvarů a definujte jeden nebo více služby koncových bodů, které se použije pro příjem zpráv k odeslání do cílové koncové body.  
  
> [!NOTE]
>  Při práci s smluv, které určují víc komunikačních schémat (například směs jednosměrná a obousměrná operations), použití duplexního kontraktu na směrování služby, jako je alternativní řešení <xref:System.ServiceModel.Routing.IDuplexSessionRouter>. Ale to znamená, že vazba musí být schopný duplexní komunikace, která nemusí být možné pro všechny scénáře. Ve scénářích, kde to není možné může být nutné řešení komunikace do víc koncových bodů nebo úprava aplikace.  
  
 Další informace o směrování kontrakty najdete v tématu [kontrakty pro směrování](../../../../docs/framework/wcf/feature-details/routing-contracts.md).  
  
 Až koncový bod služby je nadefinované, můžete použít **RoutingBehavior** přidružit konkrétní **RoutingConfiguration** ke koncovému bodu. Při konfiguraci služby směrování pomocí konfiguračního souboru **RoutingBehavior** slouží k určení filtru tabulky, která obsahuje směrování logiku používá ke zpracování zprávy přijaté na tento koncový bod. Pokud konfigurujete směrovací služby prostřednictvím kódu programu můžete zadat tabulku filtru pomocí **RoutingConfiguration**.  
  
 V následujícím příkladu definuje klienta a služby koncové body, které používají směrovací služby prostřednictvím kódu programu i pomocí konfiguračního souboru.  
  
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
  
 Tento příklad konfiguruje službu Směrování a vystavit jeden koncový bod s adresou "http://localhost:8000/routingservice/router", který se používá pro příjem zpráv k odeslání. Protože zprávy jsou směrovány do koncových bodů požadavku a odpovědi, koncový bod služby používá <xref:System.ServiceModel.Routing.IRequestReplyRouter> kontrakt. Tato konfigurace také definuje koncový bod jednoho klienta "http://localhost:8000/servicemodelsample/service", jsou směrovány zprávy. Tabulka filtru (není vidět) s názvem "routingTable1" obsahuje směrování logikou používanou pro směrování zpráv a je přidružen koncový bod služby pomocí **RoutingBehavior** (pro konfigurační soubor) nebo  **RoutingConfiguration** (pro Programová konfigurace).  
  
### <a name="routing-logic"></a>Směrování logiky  
 K definování směrování logikou používanou pro směrování zpráv, je třeba určit, jaké data obsažená v příchozí zprávy můžou jednoznačně reagovali na ni. Například pokud všechny cílové koncové body, které jsou směrování sdílet stejné akce SOAP, hodnota akce obsažené v zpráva není vhodný indikátor které konkrétní koncového bodu zpráva by měl směrovat na. Pokud pro jeden konkrétní koncový bod musí jednoznačně směrování zpráv, by měl filtrovat na datech, která jednoznačně identifikuje cílového koncového bodu, který je zpráva směrována na.  
  
 Směrovací služby nabízí několik **MessageFilter** implementací, které prohlédnout konkrétní hodnoty ve zprávě, jako je například adresu, akce, název koncového bodu nebo i dotaz XPath. Pokud žádná z těchto implementace podle svých potřeb můžete vytvořit vlastní **MessageFilter** implementace. Další informace o filtry zpráv a porovnání implementace používá služba Směrování najdete v tématu [filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md) a [výběr filtru](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md).  
  
 Více filtrů zpráv jsou uspořádané do filtru tabulky, které jednotlivé přiřadit **MessageFilter** s cílový koncový bod. Volitelně filtru tabulky lze také určit seznam koncových bodů zálohování, které směrovací služby se pokusí odeslat zprávu, která se v případě selhání přenosu.  
  
 Ve výchozím nastavení všechny filtry zpráv v tabulce filtru se vyhodnocují současně; Můžete však zadat <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> , která způsobí filtry zpráv, který se má vyhodnotit v určitém pořadí. Všechny položky s nejvyšší prioritou se vyhodnocují jako první a filtry zpráv nižší priority nebudou vyhodnoceny, pokud je nalezena shoda s vyšší úrovní priority. Další informace o filtru tabulky najdete v tématu [filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
 Následující příklady používají <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, který se vyhodnocuje `true` pro všechny zprávy. To **MessageFilter** se přidá do tabulky "routingTable1" filtr, který přidruží **MessageFilter** s koncovým bodem klienta s názvem "CalculatorService". **RoutingBehavior** pak určuje, že tato tabulka musí používat ke směrování zpráv zpracovaných v koncovém bodě služby.  
  
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
>  Ve výchozím nastavení vyhodnotí směrovací služby pouze záhlaví zprávy. Chcete-li povolit filtry pro přístup k textu zprávy, musíte nastavit <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> k `false`.  
  
 **Vícesměrové vysílání**  
  
 Při mnoho konfigurace směrování služby používat výhradní filtru logiky, která směrování zpráv do pouze jeden konkrétní koncový bod, můžete směrovat danou zprávou více cílové koncové body. Pro vícesměrové vysílání zprávu pro více cílů musí být splněné následující podmínky:  
  
-   Tvar kanálu nesmí být požadavku a odpovědi (ale nemusí být jednosměrná nebo duplexní,) protože pouze jednu odpověď lze přijímat pomocí klienta aplikace v odpovědi na požadavek.  
  
-   Více filtrů musí vracet `true` při vyhodnocování zprávy.  
  
 Pokud jsou tyto podmínky splněny, zpráva se směruje na všechny koncové body všechny filtry, která se vyhodnotí jako `true`. V následujícím příkladu definuje konfigurace směrování, jejímž výsledkem zprávy směrovány do obou koncových bodů, pokud je adresa koncového bodu ve zprávě http://localhost:8000/routingservice/router/rounding.  
  
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
  
### <a name="soap-processing"></a>Zpracování protokolu SOAP  
 Pro podporu směrování zpráv mezi odlišné protokoly **RoutingBehavior** ve výchozím nastavení přidá <xref:System.ServiceModel.Routing.SoapProcessingBehavior> pro všechny koncové klienta, které jsou směrovány zprávy. Toto chování automaticky vytvoří nový **verze MessageVersion** před směrování zprávy do koncového bodu, jakož i vytváření kompatibilní **verze MessageVersion** pro každý dokument odpovědi, před jeho vrácením aplikace vznášející požadavek klienta.  
  
 Kroky potřebné k vytvoření nové **verze MessageVersion** odchozí zprávy jsou následující:  
  
 **Zpracování žádosti**  
  
-   Získat **verze MessageVersion** odchozí vazba nebo kanálu.  
  
-   Získáte čtečka textu pro původní zprávy.  
  
-   Vytvořte novou zprávu o stejnou akci, čtečky textu a novou **verze MessageVersion**.  
  
-   Pokud <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, zkopírujte na, z FaultTo a související s záhlaví novou zprávu.  
  
-   Zkopírujte všechny vlastnosti zprávy do nové zprávy.  
  
-   Uložte na původní zprávu požadavku pro použití při zpracování odpovědi.  
  
-   Vrátí novou zprávu požadavku.  
  
 **Zpracování odpovědi**  
  
-   Získat **verze MessageVersion** původní zprávy požadavku.  
  
-   Získání čtečky textu zprávy přijaté odpovědi.  
  
-   Vytvoření nové zprávy odpovědi stejné akce čtečky textu a **verze MessageVersion** původní zprávy požadavku.  
  
-   Pokud <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, zkopírujte na, z FaultTo a související s záhlaví novou zprávu.  
  
-   Vlastnosti zprávy zkopírujte do nové zprávy.  
  
-   Vrátí nové zprávy odpovědi.  
  
 Ve výchozím nastavení **SoapProcessingBehavior** se automaticky přidá do koncových bodů klienta podle <xref:System.ServiceModel.Routing.RoutingBehavior> při spuštění služby; však můžete řídit, jestli je zpracování SOAP přidané do všechny koncové body klienta pomocí <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> vlastnost. Můžete také přidat přímo na konkrétní chování a povolit nebo zakázat toto chování na úrovni koncového bodu, pokud je potřeba podrobnější řízení zpracování protokolu SOAP.  
  
> [!NOTE]
>  Pokud SOAP zpracování je zakázán pro koncový bod, který vyžaduje jinou třídu MessageVersion než původní zprávu požadavku, je nutné zadat vlastní mechanismus pro všechny změny protokolu SOAP, které jsou nutné před odesláním zprávy do cílový koncový bod.  
  
 V následujících příkladech **soapProcessingEnabled** vlastnost se používá při prevenci **SoapProcessingBehavior** automaticky přidat všechny koncové body klienta.  
  
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
  
### <a name="dynamic-configuration"></a>Dynamické konfigurace  
 Je-li přidat koncové body další klienta, nebo změňte filtry, které se používají ke směrování zpráv, musí být způsob, jak aktualizovat konfiguraci dynamicky za běhu, aby se zabránilo přerušení služby aktuálně přijímání zpráv pomocí koncových bodů Služba směrování. Úprava konfigurační soubor nebo kód hostitelskou aplikaci nestačí vždy, protože buď metoda vyžaduje provedení recyklace aplikace, což by vedlo k potenciální ztrátě všechny zprávy právě přenosu a možné výpadek při Čeká se na službu restartovat.  
  
 Upravit lze pouze **RoutingConfiguration** prostřednictvím kódu programu. Nejdřív nakonfigurovat službu pomocí konfiguračního souboru, můžete upravit pouze konfiguraci v době běhu vytvořením nové **RoutingConfigution** a předejte ji jako parametr, který se <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> – metoda vystavené <xref:System.ServiceModel.Routing.RoutingExtension> služby rozšíření. Všechny zprávy právě přenosu nadále ho směrovat pomocí předchozí konfiguraci při zprávy přijaté po volání **ApplyConfiguration** použít novou konfiguraci. Následující příklad ukazuje vytvoření instance služby Směrování a následně změna konfigurace.  
  
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
>  Při aktualizaci služby směrování tímto způsobem je jenom možné předat novou konfiguraci. Není možné změnit pouze vyberte prvky aktuální konfigurace nebo přidání nových položek pro aktuální konfiguraci; musíte vytvořit a předat novou konfiguraci, který nahrazuje stávající.  
  
> [!NOTE]
>  Všechny relace otevřené pomocí předchozí konfiguraci pokračovat pomocí předchozí konfiguraci. Nová konfigurace se používá pouze pomocí nové relace.  
  
## <a name="error-handling"></a>Zpracování chyb  
 Pokud existuje <xref:System.ServiceModel.CommunicationException> je došlo při pokusu o odeslání zprávy, proveďte místní zpracování chyb. Tyto výjimky typicky značí, že došlo k potížím při pokusu o komunikaci s koncového bodu definovaného klienta, například <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, nebo <xref:System.ServiceModel.CommunicationObjectFaultedException>. Zpracování – kód chyby se také catch a pokus opakovat při odesílání <xref:System.TimeoutException> dojde, což je další běžné výjimku, který není odvozen od **communicationexception –**.  
  
 Když dojde k některé z předchozích výjimek, směrovací služby převezme na seznam zálohování koncové body. Pokud všechny koncové body zálohování nezdaří s chybou komunikace, nebo pokud koncový bod vrací výjimku, která indikuje selhání v rámci cílové služby, směrovací služby vrátí chybu do klientské aplikace.  
  
> [!NOTE]
>  Zpracování chyb funkce zaznamená a zpracovává výjimky, které ke kterým dochází při pokusu o odeslání zprávy a při pokusu o zavření kanálu. Kód pro ošetření chyb není určena pro zjišťování nebo zpracování výjimek vytvořených koncových bodů aplikace, které je komunikaci s; <xref:System.ServiceModel.FaultException> vyvolané služby se zobrazuje na směrování služby jako **FaultMessage** a je plynoucích zpět do klienta.  
>   
>  Pokud dojde k chybě při směrování služba se pokusí předávání zprávu, může dojít <xref:System.ServiceModel.FaultException> na straně klienta, ne <xref:System.ServiceModel.EndpointNotFoundException> by za normálních okolností získat chybí službu směrování. Směrovací služba může proto maskování výjimky a neposkytuje plnou průhlednost, není-li prověřit vnořené výjimky.  
  
### <a name="tracing-exceptions"></a>Trasování výjimky  
 Při odesílání zprávy do koncového bodu v seznamu se nezdaří, směrovací služby trasování Výsledná data výjimky a připojí podrobnosti o výjimce jako vlastnost zprávu s názvem **výjimky**. To zachovává data výjimky a umožňuje programový přístup uživatelů prostřednictvím inspector zprávy.  Výjimka data se ukládají na zprávu ve slovník, který mapuje název koncového bodu na podrobnosti o výjimce došlo při pokusu o odeslání zprávy do něj.  
  
### <a name="backup-endpoints"></a>Zálohování koncové body  
 Každý záznam filtru v tabulce filtru můžete volitelně zadat seznam zálohování koncových bodů, které se používají v případě selhání přenosu při odesílání na primární koncový bod. Pokud dojde k takové selhání, pokusí se službu směrování přenosu zprávy první položce v seznamu zálohování koncový bod. Pokud tento pokus o odeslání taky zaznamená selhání přenosu, zkusí se další koncového bodu v záložním seznamu. Směrovací služby pokračuje v odesílání zprávy na každý koncový bod v seznamu, dokud zpráva se úspěšně přijme, všechny koncové body vrátí chybu přenosu nebo jiný přenos selhání je vrácen rutinou koncový bod.  
  
 V následujících příkladech konfiguruje službu směrování na používání zálohování seznamu.  
  
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
  
### <a name="supported-error-patterns"></a>Vzory podporované chyby  
 Následující tabulka popisuje vzorů, které jsou kompatibilní s použitím seznamů zálohování koncový bod, společně s poznámky popisující podrobnosti o zpracování chyb pro určité vzory.  
  
|Vzor|Relace|Transakce|Přijímat kontextu|Zálohování seznamu podporována|Poznámky|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|Jednosměrný||||Ano|Pokusí se znovu odeslat zprávu na koncový bod zálohování. Pokud je tato zpráva vícesměrového vysílání, pouze zprávu na selhání kanálu je přesunout do cíle zálohování.|  
|Jednosměrný||![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")||Ne|Je vyvolána výjimka, a transakce je vrácena zpět.|  
|Jednosměrný|||![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")|Ano|Pokusí se znovu odeslat zprávu na koncový bod zálohování. Po zpráva se úspěšně přijatá, dokončení všech zobrazí kontexty. Pokud zpráva není úspěšně přijme žádný koncový bod, neprovádějte kontext receive.<br /><br /> Když se tato zpráva vícesměrového vysílání, kontext receive je vyplněno pouze pokud zpráva se úspěšně přijme aspoň jeden koncový bod (primární nebo zálohování). Pokud žádná z koncových bodů ve všech vícesměrového vysílání cestách úspěšně zobrazí zpráva, neprovádějte kontext receive.|  
|Jednosměrný||![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")|![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")|Ano|Abort předchozí transakce, vytvořte novou transakci a znovu odeslat všechny zprávy. Zprávy, které došlo k chybě, se přenáší do cílového umístění zálohy.<br /><br /> Po vytvoření transakce ve které všechny přenosy úspěšné dokončete kontexty příjmu a potvrzení transakce.|  
|Jednosměrný|![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")|||Ano|Pokusí se znovu odeslat zprávu na koncový bod zálohování. V případě vícesměrového vysílání jsou pouze zprávy, že došlo k chybě v relaci nebo relaci zavřete jehož relace se nezdařilo nutno do cíle zálohování.|  
|Jednosměrný|![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")|![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")||Ne|Je vyvolána výjimka, a transakce je vrácena zpět.|  
|Jednosměrný|![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")||![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")|Ano|Pokusí se znovu odeslat zprávu na koncový bod zálohování. Po všechny zprávy odesílá dokončení bez chyby, relace určuje žádné další zprávy a směrovací služby úspěšně zavře všechny odchozí relace linek, všechny obdrží kontexty jsou dokončeny, a kanál příchozí relace je uzavřený.|  
|Jednosměrný|![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")|![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")|![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")|Ano|Přerušit aktuální transakci a vytvořte novou. Odešlete ji znova všechny předchozí zprávy v relaci. Po transakce vytvořila ve kterém mají byl úspěšně odeslán všechny zprávy relace určuje, že žádné další zprávy, všechny kanály odchozí relace zavřou, přijímat všechny kontexty se dokončila s transakcí, kanál příchozí relace je zavřená, a že je transakce potvrzena.<br /><br /> Pokud bude relací vícesměrového vysílání, které jsou ke stejnému cíli jako před nutno zprávy, které měl žádná chyba a zprávy, které došlo k chybě odešlou do cíle zálohování.|  
|Obousměrné||||Ano|Odeslat do cílového umístění zálohy.  Po kanál, který vrátí zprávu odpovědi, vrátí odpověď na původní klienta.|  
|Obousměrné|![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")|||Ano|Odešlete všechny zprávy na kanálu cíl zálohy.  Po kanál, který vrátí zprávu odpovědi, vrátí odpověď na původní klienta.|  
|Obousměrné||![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")||Ne|Je vyvolána výjimka, a transakce je vrácena zpět.|  
|Obousměrné|![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")|![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")||Ne|Je vyvolána výjimka, a transakce je vrácena zpět.|  
|Duplex||||Ne|Duplexní komunikace non relace se aktuálně nepodporuje.|  
|Duplex|![Značky zaškrtnutí](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "zaškrtnutí")|||Ano|Odeslat do cílového umístění zálohy.|  
  
## <a name="hosting"></a>Hostování  
 Protože směrovací služby je implementovaná jako služby WCF, musí to být buď samoobslužně hostované v rámci aplikace nebo hostované služby IIS nebo WAS. Doporučuje se, že směrovací služby hostované ve služby IIS, WAS nebo aplikace služby systému Windows využívat výhod automatické spuštění a životního cyklu správy funkce dostupné v těchto hostitelská prostředí.  
  
 Následující příklad ukazuje, který je hostitelem služby směrování v aplikaci.  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 K hostování služby směrování v rámci služby IIS nebo WAS, musíte vytvořit soubor služby (SVC) nebo použít aktivaci prostřednictvím konfigurace služby. Při použití souboru služby, je nutné zadat <xref:System.ServiceModel.Routing.RoutingService> pomocí parametru služby. Následující příklad obsahuje ukázkový soubor služby, které je možné k hostování služby IIS nebo WAS směrování.  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a>Služba Směrování a zosobnění  
 Směrovací služby WCF můžete použít s zosobnění pro odesílání a přijímání zpráv. Použít všechny obvyklé omezení Windows zosobnění. Pokud by musel nastavení účtu služby nebo oprávnění k použití zosobnění při zápisu vlastní služby, pak budete muset provést tyto stejné kroky při použití zosobnění se směrovací službou. Další informace najdete v tématu [delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Zosobnění se směrovací službou vyžaduje použití zosobnění technologie ASP.NET v režimu kompatibility ASP.NET nebo použití pověření systému Windows, které byly nakonfigurovány k povolení zosobnění. Další informace o režim kompatibility ASP.NET najdete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
> [!WARNING]
>  Směrovací služby WCF nepodporuje zosobnění se základním ověřováním.  
  
 Chcete-li použít zosobnění technologie ASP.NET se službou směrování, povolte režim kompatibility ASP.NET ve službě hostování prostředí. Směrovací služba již byl označen jako což režim kompatibility ASP.NET a zosobnění budou automaticky povolené. Zosobnění je používat jenom podporované ASP.NET integrace se službou směrování.  
  
 Použití zosobnění pro pověření systému Windows se směrovací službou musíte nakonfigurovat přihlašovací údaje a služby. Objekt pověření klienta (<xref:System.ServiceModel.Security.WindowsClientCredential>, přístupný z <xref:System.ServiceModel.ChannelFactory>) definuje <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnost, která musí být nastavena tak, aby povolovala zosobnění. Nakonec služby je nutné nakonfigurovat <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> chování nastavit `ImpersonateCallerForAllOperations` k `true`. Směrovací služba používá tento příznak se rozhodnout, jestli se mají vytvořit klienty pro předávání zpráv s zosobnění povoleno.  
  
## <a name="see-also"></a>Viz také  
 [Filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [Kontrakty pro směrování](../../../../docs/framework/wcf/feature-details/routing-contracts.md)  
 [Výběr filtru](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md)
