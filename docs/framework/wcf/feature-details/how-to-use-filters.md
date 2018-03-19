---
title: "Postupy: Použití filtrů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
caps.latest.revision: 
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 94d45537ca3edd5f31f1ed31898857f002312a0b
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-use-filters"></a>Postupy: Použití filtrů
Toto téma popisuje základní kroky potřebné pro vytvoření konfigurace směrování, která používá více filtrů. V tomto příkladu jsou dva implementace služby kalkulačky, regularCalc a roundingCalc směrovány zprávy. Obě implementace podporují stejné operace; ale jedna služba zaokrouhlí na nejbližší celé číslo všech výpočtů před vrácením. Klientská aplikace musí být schopen označuje, zda chcete použít zaokrouhlení verzi služby; Pokud žádné služby přání zpráva je mezi těmito dvěma službami skupinu s vyrovnáváním zatížení. Operace vystavené obě služby jsou:  
  
-   Přidejte  
  
-   Odečtena  
  
-   Násobení  
  
-   Dělení  
  
 Protože obě služby implementovat stejné operace, nemůžete použít filtr akce, protože akci určenou ve zprávě nesmí být jedinečný. Místo toho je potřeba udělat další kroky k zajištění, že zprávy jsou směrované na jednotlivé koncové body.  
  
### <a name="determine-unique-data"></a>Určit jedinečné dat  
  
1.  Protože oba implementace služby zpracování stejné operace a jsou v podstatě stejné než data, která se vracejí, základní data obsažená v zpráv odeslaných z klientské aplikace není dostatečně jedinečný, a umožní vám určit, jak směrovat požadavek. Ale pokud klientská aplikace přidá hodnotu jedinečné záhlaví zprávy, potom můžete tuto hodnotu určit, jak by měl směrovat zprávy.  
  
     Například pokud klientská aplikace potřebuje zprávu, která se má zpracovat modulem zaokrouhlení kalkulačky, přidá vlastní hlavičku s použitím následující kód:  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Teď můžete použít filtr XPath kontrola zpráv pro tuto hlavičku a směrování zpráv obsahující hlavičku ke službě roundCalc.  
  
2.  Kromě toho směrovací služby zpřístupní dva koncové body virtuální služby, které lze použít s EndpointName, EndpointAddress, nebo filtruje PrefixEndpointAddress jednoznačně směrovat příchozí zprávy pro konkrétní kalkulačky implementaci založené na koncový bod do které klientská aplikace odešle požadavek.  
  
### <a name="define-endpoints"></a>Zadejte koncové body  
  
1.  Při definování koncových bodů použitých službou směrování, nejdřív byste měli zjistit obrazec kanál používaný klienty a služby. V tomto scénáři používají cílové služby požadavku a odpovědi vzor, proto <xref:System.ServiceModel.Routing.IRequestReplyRouter> se používá. V následujícím příkladu definuje koncové body služby, který je zveřejněný prostřednictvím služby směrování.  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     Pomocí této konfigurace služby směrování zpřístupní tři samostatné koncové body. V závislosti na rozhodnutích při spuštění klientské aplikace odešle zprávy do jedné z těchto adres. Pro implementaci odpovídající kalkulačky jsou předávány zpráv přicházejících na jednom z koncových bodů služby "virtuální" ("zaokrouhlení/calculator" nebo "regular/calculator"). Pokud klientská aplikace neodešle žádost o konkrétní koncový bod, je určena zpráva obecné koncový bod. Bez ohledu na koncový bod vybrali může klientská aplikace také vybrat možnost zahrnutí vlastní hlavičky k označení, že mají předávat zprávy zaokrouhlení kalkulačky implementace.  
  
2.  V následujícím příkladu definuje koncové body klienta (cíl), které směrovací služby směrování zpráv do.  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     Tyto koncové body jsou v tabulce filtru slouží k určení cílového koncového bodu, který je zpráva odeslána na při odpovídá konkrétní filtr.  
  
### <a name="define-filters"></a>Zadejte filtry  
  
1.  Chcete-li směrovat zprávy založené na vlastní hlavičky "RoundingCalculator", který klientská aplikace přidá ke zprávě, definujte filtr, který používá dotaz XPath Pokud chcete zkontrolovat přítomnost tuto hlavičku. Vzhledem k tomu, že tuto hlavičku se definuje pomocí vlastní obor názvů, také přidáte obor názvů položku, která definuje vlastní obor názvů předponu "vlastní", který se používá v dotazu XPath. V následujícím příkladu definuje nezbytné směrování části, obor názvů tabulku a filtr XPath.  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"   
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     To **MessageFilter** hledá RoundingCalculator záhlaví zprávy, která obsahuje hodnotu "zaokrouhlení". Tuto hlavičku je nastavená klientem indikující, že zpráva by měla směrované na službu roundingCalc.  
  
    > [!NOTE]
    >  Předpona oboru názvů s12 je definována ve výchozím nastavení v tabulce obor názvů a představuje obor názvů "http://www.w3.org/2003/05/soap-envelope".  
  
2.  Je třeba definovat filtry, které vypadají zprávy přijaté na dva virtuální koncové body. První virtuální koncový bod je koncový bod "regular/calculator". Klient může odesílat požadavky na tento koncový bod k označení, že zpráva by měla směrované na službu regularCalc. Definuje filtr, který používá následující konfigurace <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> k určení, pokud zpráva dorazila po uplynutí přes koncový bod s názvem zadaným v fulltextových dat filtru.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     Pokud je koncový bod služby s názvem "calculatorEndpoint" přijme zprávu, tento filtr se vyhodnocuje `true`.  
  
3.  V dalším kroku definujte filtr, který hledá zprávy odeslané na adresu roundingEndpoint. Klient může odesílat požadavky na tento koncový bod k označení, že zpráva by měla směrované na službu roundingCalc. Definuje filtr, který používá následující konfigurace <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> k určení, pokud zpráva dorazila po uplynutí na koncovém bodu "zaokrouhlení/calculator".  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     Pokud je přijata zpráva na adresu, která začíná "http://localhost/routingservice/router/rounding/", pak tento filtr se vyhodnocuje **true**. Vzhledem k tomu je základní adresa použitá v této konfiguraci je "http://localhost/routingservice/router" a "zaokrouhlení/calculator" je zadaná adresa roundingEndpoint, úplná adresa použitá pro komunikaci se tento koncový bod je "http://localhost/ routingservice/směrovače nebo zaokrouhlení/calculator", který by odpovídal tento filtr.  
  
    > [!NOTE]
    >  Filtr PrefixEndpointAddress nevyhodnocuje název hostitele, při provádění shodu, protože je jeden hostitel lze odkazovat pomocí různých názvů hostitelů, které může všechny být platné způsoby odkazů na hostiteli z klientské aplikace. Všechny tyto například mohou odkazovat na stejného hostitele:  
    >   
    >  -   localhost  
    > -   127.0.0.1  
    > -   www.contoso.com  
    > -   ContosoWeb01  
  
4.  Poslední filtr musí podporovat směrování zpráv, které přicházejí na obecné koncového bodu bez vlastní hlavičky. V tomto scénáři by měl mezi službami regularCalc a roundingCalc alternativní zprávy. Pro podporu "kruhové dotazování" směrování tyto zprávy, použijte vlastní filtr, který umožňuje jednu instanci filtru tak, aby odpovídaly pro každou zprávu zpracovat.  Následující definuje dvě instance RoundRobinMessageFilter, které jsou seskupeny dohromady indikující, že by měl alternativní mezi sebou.  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     Za běhu tento typ filtru střídá definovaný filtr instance tohoto typu, které jsou nakonfigurované jako stejnou skupinu do jedné kolekce. To způsobí, že zpráv zpracovaných správcem tento vlastní filtr na alternativní mezi vrácení `true` RoundRobinFilter1 a RoundRobinFilter2.  
  
### <a name="define-filter-tables"></a>Definujte filtr tabulek  
  
1.  Přidružit filtry s koncovými body konkrétního klienta, je nutné umístit v tabulce filtru. Tento příklad scénář také používá nastavení priority filtr, který je volitelné nastavení, která umožňuje určit pořadí, ve kterém jsou zpracovány filtry. Pokud žádná priorita filtru není zadán, jsou všechny filtry vyhodnotí současně.  
  
    > [!NOTE]
    >  Při zadávání prioritu filtr umožňuje vám umožňují řídit pořadí filtry, které se zpracovávají, může nepříznivě ovlivnit výkon služby směrování. Pokud je to možné, vytvořte logiku filtru tak, aby použití filtru priority se nevyžaduje.  
  
     Následující tabulku filtru definuje a přidá "Třída XPathFilter" definovaného dříve do tabulky s prioritou 2. Tato položka také určuje, že pokud třída "XPathFilter" odpovídá zprávu, zpráva směrované na "roundingCalcEndpoint"  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          <filterTables>  
    </routing>  
    ```  
  
     Při zadání priority filtru, filtry nejvyšší prioritou, se vyhodnocují jako první. Pokud jeden nebo více filtrů na úrovni s konkrétní prioritou shodují, se vyhodnotí žádné filtry na nižších úrovních priority. Pro tento scénář 2 je nejvyšší prioritou zadaný a toto je jediná položka filtru na této úrovni.  
  
2.  Chcete-li zkontrolovat, pokud je na koncový bod konkrétní přijata zpráva zkontrolováním název koncového bodu nebo předpona adresy byly definovány položky filtru. Následující položky přidat obě tyto položky filtru do filtru tabulky a přidružit cílové koncové body, které zprávy budou směrované na. Tyto filtry jsou nastavena priorita 1 k označení, že by měly být pouze spuštěny Pokud předchozí filtr XPath neodpovídá zprávy.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Vzhledem k tomu, že tyto filtry filtru prioritu 1, se bude vyhodnocena pouze pokud filtr úrovní priority 2 neodpovídá zprávy. Navíc vzhledem k tomu, že oba filtry mají stejnou úrovní priority se vyhodnotí současně. Protože oba filtry se vzájemně vylučují, je možné pouze jeden z nich tak, aby odpovídaly zprávu.  
  
3.  Pokud zpráva neodpovídá žádnému z předchozí filtrů, zpráva byla přijata prostřednictvím koncového bodu obecná služba a neobsahuje žádné informace hlavičky, která určuje, kam směruje. Tyto zprávy jsou ke zpracování pomocí vlastního filtru, který zatížení je vyrovnává mezi službami dvě kalkulačky. Následující příklad ukazuje, jak přidat filtr položky do tabulce filtru. Každý filtr je spojen s jednou ze dvou cílové koncové body.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Protože tyto položky zadat prioritou 0, se bude vyhodnocena pouze pokud žádný filtr vyšší prioritu odpovídá zprávě. Navíc vzhledem k tomu, jak jsou se stejnou prioritou, jsou vyhodnocovány současně.  
  
     Jak je uvedeno nahoře, vlastní filtr používá tyto definice filtru vyhodnotí pouze jednu nebo jiné jako `true` pro každý přijatá zpráva. Protože pouze dva filtry jsou definovány pomocí stejné nastavení zadané skupiny tento filtr, efekt je, že střídá odesílání regularCalcEndpoint a RoundingCalcEndpoint směrovací služby.  
  
4.  Abyste mohli vyhodnotit zprávy před filtry, musí být tabulku filtru nejprve přidružený koncové body služby, které se použijí pro příjem zpráv.  Následující příklad ukazuje, jak přidružit do směrovací tabulky koncové body služby pomocí směrování chování:  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a>Příklad  
 Níže je úplný seznam všech konfiguračního souboru.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Směrovací služby](../../../../docs/framework/wcf/samples/routing-services.md)
