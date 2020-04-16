---
title: 'Postupy: Používání filtrů'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 34ea961b0ef5db51efcae0b86f2c06171d6d756c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464105"
---
# <a name="how-to-use-filters"></a>Postupy: Používání filtrů
Toto téma popisuje základní kroky potřebné k vytvoření konfigurace směrování, která používá více filtrů. V tomto příkladu zprávy jsou směrovány na dvě implementace kalkulačky služby, regularCalc a zaokrouhleníCalc. Obě implementace podporují stejné operace; jedna služba však zaokrouhluje všechny výpočty na nejbližší celočíselnou hodnotu před vrácením. Klientská aplikace musí být schopna určit, zda má být používána verze zaokrouhlení služby. Pokud není vyjádřena žádná předvolba služby, je zpráva vyrovnána zatížením mezi dvěma službami. Operace vystavené oběma službami jsou:  
  
- Přidat  
  
- Odčítání  
  
- Násobení  
  
- Dělení  
  
 Vzhledem k tomu, že obě služby implementují stejné operace, nelze použít filtr Akce, protože akce zadaná ve zprávě nebude jedinečná. Místo toho je nutné provést další práci, aby zajistily, že zprávy jsou směrovány do příslušných koncových bodů.  
  
### <a name="determine-unique-data"></a>Určení jedinečných dat  
  
1. Vzhledem k tomu, že obě implementace služby zpracovávají stejné operace a jsou v podstatě identické než data, která vracejí, základní data obsažená ve zprávách odeslaných z klientských aplikací nejsou dostatečně jedinečná, aby vám umožnila určit, jak směrovat požadavek. Ale pokud klientská aplikace přidá jedinečnou hodnotu záhlaví zprávy, pak můžete tuto hodnotu použít k určení, jak by měla být zpráva směrována.  
  
     V tomto příkladu pokud klientská aplikace potřebuje zprávu, která má být zpracována kalkulačkou zaokrouhlení, přidá vlastní záhlaví pomocí následujícího kódu:  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Nyní můžete použít filtr XPath ke kontrole zpráv pro toto záhlaví a směrovat zprávy obsahující záhlaví do služby roundCalc.  
  
2. Navíc služba Směrování zpřístupňuje dva koncové body virtuální služby, které lze použít s filtry EndpointName, EndpointAddress nebo PrefixEndpointAddress k jedinečnému směrování příchozích zpráv do konkrétní implementace kalkulačky na základě koncového bodu, do kterého klientská aplikace odešle požadavek.  
  
### <a name="define-endpoints"></a>Definování koncových bodů  
  
1. Při definování koncových bodů používaných službou Směrování byste měli nejprve určit tvar kanálu používaného klienty a službami. V tomto scénáři obě cílové služby používají <xref:System.ServiceModel.Routing.IRequestReplyRouter> vzor požadavek odpověď, takže se používá. Následující příklad definuje koncové body služby vystavené službou Směrování.  
  
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
  
     S touto konfigurací služba Směrování zpřístupňuje tři samostatné koncové body. V závislosti na volbách za běhu klientská aplikace odesílá zprávy na jednu z těchto adres. Zprávy přicházející do jednoho z koncových bodů "virtuální" služby ("zaokrouhlení/kalkulačka" nebo "regular/calculator") jsou předány odpovídající implementaci kalkulačky. Pokud klientská aplikace neodesílá požadavek do určitého koncového bodu, zpráva je určena obecnému koncovému bodu. Bez ohledu na zvolený koncový bod může klientská aplikace také zahrnout vlastní záhlaví označující, že zpráva by měla být předána implementaci kalkulačky zaokrouhlení.  
  
2. Následující příklad definuje koncové body klienta (cíle), ke kterým služba směrování směruje zprávy.  
  
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
  
     Tyto koncové body se používají v tabulce filtrů k označení cílového koncového bodu, do který je zpráva odeslána, když odpovídá určitému filtru.  
  
### <a name="define-filters"></a>Definovat filtry  
  
1. Chcete-li směrovat zprávy založené na vlastní záhlaví "ZaokrouhlováníCalculator", které klientská aplikace přidá do zprávy, definujte filtr, který používá dotaz XPath ke kontrole přítomnosti této hlavičky. Vzhledem k tomu, že tato hlavička je definována pomocí vlastního oboru názvů, přidejte také položku oboru názvů, která definuje vlastní předponu oboru názvů "vlastní", která se používá v dotazu XPath. Následující příklad definuje potřebný oddíl směrování, tabulku oboru názvů a filtr XPath.  
  
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
  
     Tento **MessageFilter** hledá zaokrouhleníCalculator záhlaví ve zprávě, která obsahuje hodnotu "zaokrouhlení". Tato hlavička je nastavena klientem označující, že zpráva by měla být směrována do zaokrouhleníCalc služby.  
  
    > [!NOTE]
    > Předpona oboru názvů s12 je ve výchozím nastavení definována `http://www.w3.org/2003/05/soap-envelope`v tabulce oboru názvů a představuje obor názvů .
  
2. Musíte také definovat filtry, které hledají zprávy přijaté na dva virtuální koncové body. První virtuální koncový bod je koncový bod "regular/calculator". Klient může odesílat požadavky na tento koncový bod označující, že zpráva by měla být směrována do služby regularCalc. Následující konfigurace definuje filtr, který <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> používá k určení, pokud zpráva dorazila prostřednictvím koncového bodu s názvem zadaným v filterData.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     Pokud je zpráva přijata koncovým bodem služby s názvem "calculatorEndpoint", tento filtr vyhodnotí `true`.  
  
3. Dále definujte filtr, který hledá zprávy odeslané na adresu roundingEndpoint. Klient může odesílat požadavky do tohoto koncového bodu označující, že zpráva by měla být směrována do zaokrouhleníCalc služby. Následující konfigurace definuje filtr, který <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> používá k určení, pokud zpráva dorazila na koncový bod "zaokrouhlení/kalkulačka".  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     Pokud je zpráva přijata na adresu, která `http://localhost/routingservice/router/rounding/` začíná, pak tento filtr vyhodnotí na **true**. Vzhledem k tomu, že `http://localhost/routingservice/router` základní adresa používaná touto konfigurací je a adresa zadaná pro zaokrouhleníEndpoint je "zaokrouhlení/kalkulačka", úplná adresa používaná ke komunikaci s tímto koncovým bodem je `http://localhost/routingservice/router/rounding/calculator`, která odpovídá tomuto filtru.  
  
    > [!NOTE]
    > Filtr PrefixEndpointAddress nevyhodnocuje název hostitele při provádění shody, protože jeden hostitel může být odkazován pomocí různých názvů hostitelů, které mohou být všechny platné způsoby odkazování na hostitele z klientské aplikace. Například všechny následující mohou odkazovat na stejného hostitele:  
    >
    > - localhost  
    > - 127.0.0.1  
    > - `www.contoso.com`  
    > - ContosoWeb01  
  
4. Konečný filtr musí podporovat směrování zpráv, které dorazí na obecný koncový bod bez vlastní hlavičky. V tomto scénáři by zprávy by měly střídat mezi regularCalc a zaokrouhleníCalc služby. Chcete-li podporovat směrování "kruhového dotazování" těchto zpráv, použijte vlastní filtr, který umožňuje, aby se jedna instance filtru shodovala pro každou zpracovávanou zprávu.  Následující definuje dvě instance RoundRobinMessageFilter, které jsou seskupeny dohromady označující, že by měly střídat mezi sebou.  
  
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
  
     Za běhu tento typ filtru se střídá mezi všemi definovanými instancemi filtru tohoto typu, které jsou konfigurovány jako stejná skupina, do jedné kolekce. To způsobí, že zprávy zpracované tímto `true` vlastním `RoundRobinFilter1` `RoundRobinFilter2`filtrem se budou střídat mezi návratem pro a .  
  
### <a name="define-filter-tables"></a>Definovat tabulky filtrů  
  
1. Chcete-li přidružit filtry ke konkrétním koncovým bodům klienta, musíte je umístit do tabulky filtrů. Tento ukázkový scénář také používá nastavení priority filtru, což je volitelné nastavení, které umožňuje označit pořadí, ve kterém jsou filtry zpracovány. Pokud není zadána žádná priorita filtru, jsou všechny filtry vyhodnocovány současně.  
  
    > [!NOTE]
    > Při určení priority filtru umožňuje řídit pořadí, ve kterém jsou filtry zpracovávány, může nepříznivě ovlivnit výkon služby Směrování. Pokud je to možné, vytvořte logiku filtru tak, aby nebylo vyžadováno použití priorit filtru.  
  
     Následující definuje tabulku filtrů a přidá "XPathFilter" definované dříve do tabulky s prioritou 2. Tato položka také určuje, `XPathFilter` že pokud se zpráva shoduje, `roundingCalcEndpoint`bude zpráva směrována do .  
  
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
          </filterTables>  
    </routing>  
    ```  
  
     Při zadávání priority filtru jsou nejprve vyhodnoceny filtry s nejvyšší prioritou. Pokud se jeden nebo více filtrů na určité úrovni priority shodují, nebudou vyhodnoceny žádné filtry na nižších úrovních priority. V tomto scénáři 2 je nejvyšší priorita zadaná a toto je jediná položka filtru na této úrovni.  
  
2. Položky filtru byly definovány ke kontrole, zda je zpráva přijata na konkrétní koncový bod kontrolou názvu koncového bodu nebo předpony adresy. Následující položky přidají obě tyto položky filtru do tabulky filtrů a přidruží je k cílovým koncovým bodům, ke kterým bude zpráva směrována. Tyto filtry jsou nastaveny na prioritu 1 označující, že by měly být spuštěny pouze v případě, že předchozí filtr XPath neodpovídá zprávě.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Vzhledem k tomu, že tyto filtry mají prioritu filtru 1, budou vyhodnoceny pouze v případě, že filtr na úrovni priority 2 neodpovídá zprávě. Protože oba filtry mají stejnou úroveň priority, budou vyhodnoceny současně. Vzhledem k tomu, že se oba filtry vzájemně vylučují, je možné, aby zprávu shodovaly pouze jeden nebo druhý filtr.  
  
3. Pokud zpráva neodpovídá žádné z předchozích filtrů, byla zpráva přijata prostřednictvím obecného koncového bodu služby a neobsahovala žádné informace záhlaví, které by naznačovalo, kam ji směrovat. Tyto zprávy mají být zpracovány vlastní filtr, který vyrovnává zatížení mezi dvěma kalkulačky služby. Následující příklad ukazuje, jak přidat položky filtru do tabulky filtrů; každý filtr je přidružen k jednomu ze dvou cílových koncových bodů.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Vzhledem k tomu, že tyto položky určují prioritu 0, budou vyhodnoceny pouze v případě, že zprávu neodpovídá žádnému filtru s vyšší prioritou. Také, protože oba mají stejnou prioritu, jsou hodnoceny současně.  
  
     Jak již bylo zmíněno dříve, vlastní filtr používaný těmito definicemi filtrů vyhodnocuje pouze jednu nebo druhou jako `true` pro každou přijatou zprávu. Vzhledem k tomu, že pouze dva filtry jsou definovány pomocí tohoto filtru, se stejným nastavením zadané skupiny, efekt je, že služba směrování střídá mezi odesílání do regularCalcEndpoint a ZaokrouhleníCalcEndpoint.  
  
4. Chcete-li vyhodnotit zprávy proti filtrům, musí být tabulka filtrů nejprve přidružena k koncovým bodům služby, které budou použity k příjmu zpráv.  Následující příklad ukazuje, jak přidružit směrovací tabulku k koncovým bodům služby pomocí chování směrování:  
  
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
 Následuje úplný seznam konfiguračního souboru.  
  
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

- [Směrovací služby](../../../../docs/framework/wcf/samples/routing-services.md)
