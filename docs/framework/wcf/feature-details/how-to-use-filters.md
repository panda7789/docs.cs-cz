---
title: 'Postupy: Používání filtrů'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 5d3ed4a1d64edee274e60f5bf156b4294902df8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972858"
---
# <a name="how-to-use-filters"></a>Postupy: Používání filtrů
Toto téma popisuje základní kroky potřebné k vytvoření konfigurace směrování, která používá více filtrů. V tomto příkladu jsou směrovány dvě implementace službu kalkulačky, regularCalc a roundingCalc zprávy. Obou implementacích podporují stejné operace; jedna služba ale Zaokrouhlí všechny výpočty na nejbližší celočíselnou hodnotu před vrácením. Klientská aplikace musí být schopen určit, jestli se má použít zaokrouhlení verze služby; Pokud je vyjádřená žádná předvolba služby zpráva je mezi těmito dvěma službami s vyrovnáváním zatížení. Operace vystavené obě služby jsou:  
  
- Přidejte  
  
- Odečíst  
  
- Násobení  
  
- Dělení  
  
 Vzhledem k tomu, že obě služby implementovat stejné operace, nemůžete použít filtr akce, protože akce určená ve zprávě nesmí být jedinečný. Místo toho je nutné provést další práce k zajištění, že zprávy jsou směrovány na jednotlivé koncové body.  
  
### <a name="determine-unique-data"></a>Určení jedinečných dat  
  
1. Protože obou implementacích služby zpracování stejné operace a jsou v podstatě totožné než data, která vrátí, základní data obsažená ve zprávách odesílaných z klientských aplikací není dostatečně jedinečných, aby bylo možné určit, jak se směrují požadavek. Ale pokud klientská aplikace přidá hodnotu záhlaví ke zprávě, pak můžete použít tuto hodnotu k určení, jak se mají směrovat zprávy.  
  
     Například pokud klientská aplikace potřebuje zpráva, která má být zpracována zaokrouhlení kalkulačky, přidá vlastní hlavičku s použitím následujícího kódu:  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Teď můžete použít filtr XPath ke kontrole zpráv pro toto záhlaví a směrovat zprávy obsahující hlavičku do roundCalc služby.  
  
2. Kromě toho služba Směrování poskytuje dva koncové body služby virtuální, které lze použít s Název_koncového_bodu EndpointAddress, nebo filtruje PrefixEndpointAddress jednoznačně směrovat příchozí zprávy pro konkrétní Kalkulačka implementaci založené na koncový bod do které klientská aplikace odešle požadavek.  
  
### <a name="define-endpoints"></a>Definujte koncové body  
  
1. Při definování koncových bodů použitých službou směrování, byste měli určit tvar kanálu používat klientů a služeb. V tomto scénáři cílové služby použít model požadavek odpověď, proto <xref:System.ServiceModel.Routing.IRequestReplyRouter> se používá. Následující příklad definuje koncové body služby, vystavený službou směrování.  
  
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
  
     S touto konfigurací směrovací služba poskytuje tři samostatné koncové body. V závislosti na možnosti běhu klientská aplikace odešle zprávy do jedné z těchto adres. Zprávy odeslané na jednom z koncových bodů služby "virtuální" ("zaokrouhlení/Kalkulačka" nebo "normální/Kalkulačka") se předávají do odpovídající implementace kalkulačky. Pokud klientská aplikace nebude odeslat žádost o konkrétní koncový bod, zpráva zaslána obecné koncový bod. Bez ohledu na zvolené koncový bod klientská aplikace si také obsahovat vlastní hlavičky k označení, že mají zprávy předávat zaokrouhlení implementace kalkulačku.  
  
2. Následující příklad definuje, které směrovací služba provádí směrování zpráv do koncových bodů klienta (cíl).  
  
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
  
     Tyto koncové body jsou v tabulce filtrů slouží k označení cílový koncový bod, který je zpráva odeslána případě, že odpovídá konkrétní filtr.  
  
### <a name="define-filters"></a>Definování filtrů  
  
1. Chcete-li směrovat zprávy založené na vlastní hlavičky "RoundingCalculator", který klientská aplikace přidá do zprávy, definujte filtr, který se použije dotaz XPath ke kontrole přítomnosti této hlavičky. Protože tato hlavička se definuje pomocí vlastního oboru názvů, přidejte také zadání oboru názvů, který definuje předponu vlastního oboru názvů "vlastní", který se používá v dotazu XPath. Následující příklad definuje oddíl nezbytné směrování, obor názvů tabulku a filtr XPath.  
  
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
  
     To **MessageFilter** hledá RoundingCalculator záhlaví ve zprávě, která obsahuje hodnotu "zaokrouhlení". Tato hlavička nastavená klientem k označení, že se mají směrovat zprávy do služby roundingCalc.  
  
    > [!NOTE]
    > Předpona oboru názvů S12 na úrovni Standard je definované ve výchozím nastavení v tabulce obor názvů a představuje obor názvů `http://www.w3.org/2003/05/soap-envelope`.
  
2. Musíte také definovat filtry, které vyhledávají zprávy přijaté na dva virtuální koncové body. První virtuální koncový bod je koncový bod "normální/Kalkulačka". K tomuto koncovému bodu k označení, že se mají směrovat zprávy do služby regularCalc může klient odeslat požadavky. Definuje filtr, který používá následující konfiguraci <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> k určení, pokud byla zpráva doručena prostřednictvím koncového bodu s názvem zadaným v fulltextových dat filtru.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     Pokud zprávu neobdrží koncový bod služby s názvem "calculatorEndpoint", tento filtr se vyhodnotí jako `true`.  
  
3. Dále definujte filtr, který hledá zprávy odeslané na adresu roundingEndpoint. K tomuto koncovému bodu k označení, že se mají směrovat zprávy do služby roundingCalc může klient odeslat požadavky. Definuje filtr, který používá následující konfiguraci <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> k určení, pokud byly přijaty zprávy v koncovém bodě "zaokrouhlení/Kalkulačka".  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     Pokud je přijata zpráva na adresu, která začíná `http://localhost/routingservice/router/rounding/` pak vyhodnotí jako tento filtr **true**. Protože je základní adresu použitou touto konfigurací `http://localhost/routingservice/router` a je úplná adresa slouží ke komunikaci s tímto koncovým bodem adresa zadaná pro roundingEndpoint je "zaokrouhlení/Kalkulačka" `http://localhost/routingservice/router/rounding/calculator`, který odpovídá tomuto filtru.  
  
    > [!NOTE]
    >  Filtr PrefixEndpointAddress nevyhodnocuje název hostitele při provádění shodu, protože je jeden hostitel lze odkazovat pomocí různých názvů hostitelů, které mohou všechny být platné způsoby odkazující na hostitele z klientské aplikace. Všechny tyto například může odkazovat na stejného hostitele:  
    >   
    > - localhost  
    > - 127.0.0.1  
    > - `www.contoso.com`  
    > - ContosoWeb01  
  
4. Konečné filtr musí podporovat směrování zpráv, které přicházejí na obecné koncový bod bez vlastní hlavičce. V tomto scénáři by měl alternativní zpráv mezi službami regularCalc a roundingCalc. Pro podporu "kruhové dotazování" směrování tyto zprávy, použijte vlastní filtr, který umožňuje jedna instance filtru tak, aby odpovídaly pro každou zprávu zpracovat.  Následující informace definují dvě instance RoundRobinMessageFilter, které jsou seskupeny k označení, že by měl alternativní mezi sebou.  
  
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
  
     Za běhu tento typ filtru střídá všechny definovaný filtr instance tohoto typu, které jsou nakonfigurované jako stejnou skupinu do jedné kolekce. To způsobí, že zprávy zpracované tento vlastní filtr do alternativní mezi vrácení `true` pro `RoundRobinFilter1` a `RoundRobinFilter2`.  
  
### <a name="define-filter-tables"></a>Definujte filtr tabulky  
  
1. Filtry přidružit s koncovými body konkrétního klienta, je nutné je umístit v tabulce filtrů. Tento ukázkový scénář také používá nastavení priority filtr, což je volitelné nastavení, která umožňuje určit pořadí, ve kterém jsou zpracovány filtry. Pokud není zadána žádná priorita filtru, všechny filtry jsou vyhodnocovány současně.  
  
    > [!NOTE]
    >  Při zadávání prioritu filtr umožňuje řídit pořadí, ve které filtry se zpracovávají, může nepříznivě ovlivnit výkon služby směrování. Pokud je to možné, vytvořte filtr logiky tak, aby se nevyžaduje použití filtru priority.  
  
     Následující tabulka filtr definuje a přidá "Třída XPathFilter" definovali dříve do tabulky s prioritou 2. Tato položka také určuje, že pokud `XPathFilter` odpovídá zprávu, zpráva se budou směrovat do `roundingCalcEndpoint`.  
  
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
  
     Při určování priority filtr, filtry nejvyšší prioritou, je vyhodnocen jako první. Pokud jeden nebo více filtrů na úrovni s konkrétní prioritou shodují, se vyhodnotí na nižších úrovních priority se žádné filtry. V tomto scénáři 2 je nejvyšší pořadí podle priority a jde o jediný záznam filtr na této úrovni.  
  
2. Chcete-li zkontrolovat, pokud je přijata zpráva na určitý koncový bod zkontrolováním název koncového bodu nebo předpona adresy byly definovány položky filtru. Následující položky přidat obě tyto položky filtru tabulky filtru a přidružit je k cílové koncové body, které zprávy se budou směrovat do. Tyto filtry nastavené s prioritou 1 označuje, že jejich by měl spustí jenom v případě předchozího filtr XPath neodpovídá zprávu.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Vzhledem k tomu, že tyto filtry filtr priority 1, že bude vyhodnocena pouze pokud filtr na úrovni priority 2 neodpovídá zprávu. Navíc vzhledem k tomu, že oba filtry mají stejnou prioritu, se vyhodnotí současně. Protože oba filtry se vzájemně vylučují, je možné pouze jeden z nich tak, aby odpovídaly zprávu.  
  
3. Pokud zpráva neodpovídá žádnému z předchozí filtrů, zpráva byla přijata prostřednictvím koncového bodu obecná služba a neobsahuje žádné informace hlavičky, která označuje, kde ho směrovat. Tyto zprávy jsou zpracovávat vlastní filtr vyrovnává které zatížení mezi dvěma Kalkulačka služby. Následující příklad ukazuje, jak přidat filtr položky do tabulce filtru. Každý filtr je přidružený nejméně k jednomu ze dvou cílové koncové body.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Protože tyto položky určit prioritu 0, že bude vyhodnocena pouze pokud žádný filtr s vyšší prioritou odpovídá zprávu. Také protože obě mají stejnou prioritu, jsou vyhodnocovány současně.  
  
     Jak už bylo zmíněno dříve, vlastní filtr používá tyto definice filtru vyhodnotí pouze jednu nebo jiných jako `true` u každé zprávy přijaté. Protože pouze dva filtry jsou definovány pomocí tohoto filtru, stejné nastavení zadané skupiny, efekt je, že směrovací služba střídá odesílání regularCalcEndpoint a RoundingCalcEndpoint.  
  
4. K vyhodnocení zpráv filtry, musí být filtr tabulky nejprve přidružené koncové body služby, které se použijí pro příjem zpráv.  Následující příklad ukazuje, jak přidružit směrovací tabulce koncových bodů služby pomocí směrování chování:  
  
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
 Tady je úplný seznam všech konfiguračního souboru.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Směrovací služby](../../../../docs/framework/wcf/samples/routing-services.md)
