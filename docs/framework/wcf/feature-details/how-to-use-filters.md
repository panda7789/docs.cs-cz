---
title: 'Postupy: Používání filtrů'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 6c357f2f410362d56fc931529a9fe731df0a477e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968770"
---
# <a name="how-to-use-filters"></a>Postupy: Používání filtrů
Toto téma popisuje základní kroky potřebné k vytvoření konfigurace směrování, která používá více filtrů. V tomto příkladu jsou zprávy směrovány do dvou implementací služby kalkulačky, regularCalc a roundingCalc. Obě implementace podporují stejné operace. Nicméně jedna služba Zaokrouhlí všechny výpočty na nejbližší celočíselnou hodnotu před vrácením. Klientská aplikace musí být schopná určit, jestli se má použít verze zaokrouhlení služby. Pokud se nevyjádří žádné předvolby služby, vyrovnává se zatížení mezi těmito dvěma službami. Mezi operace vystavené oběma službami patří:  
  
- Přidejte  
  
- Odečten  
  
- Hodnotou  
  
- Rozdělovací  
  
 Vzhledem k tomu, že obě služby implementují stejné operace, nemůžete použít filtr akcí, protože akce zadaná ve zprávě nebude jedinečná. Místo toho je nutné provést další práci, aby bylo zajištěno, že budou zprávy směrovány do příslušných koncových bodů.  
  
### <a name="determine-unique-data"></a>Určení jedinečných dat  
  
1. Vzhledem k tomu, že obě implementace služby pracují se stejnými operacemi a jsou v podstatě totožné s daty, která vrací, nejsou základní data obsažená ve zprávách odesílaných klientskými aplikacemi dostatečně jedinečná, aby bylo možné určit, jak se má směrovat Request. Pokud však klientská aplikace přidá do zprávy jedinečnou hodnotu záhlaví, můžete tuto hodnotu použít k určení způsobu směrování zprávy.  
  
     V tomto příkladu, Pokud klientská aplikace potřebuje zprávu zpracovat kalkulačkou zaokrouhlení, přidá vlastní hlavičku pomocí následujícího kódu:  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Nyní můžete použít filtr XPath ke kontrole zpráv pro tuto hlavičku a směrování zpráv obsahujících hlavičku do služby roundCalc.  
  
2. Směrovací služba navíc zveřejňuje dva koncové body virtuální služby, které se dají použít s filtry koncového bodu, EndpointAddress nebo PrefixEndpointAddress k jedinečnému směrování příchozích zpráv do konkrétní implementace kalkulačky založené na koncovém bodu. do které klientská aplikace požadavek odešle.  
  
### <a name="define-endpoints"></a>Definování koncových bodů  
  
1. Při definování koncových bodů používaných směrovací službou byste nejdřív měli určit tvar kanálu používaného klienty a službami. V tomto scénáři používají cílové služby vzor požadavek-odpověď, takže <xref:System.ServiceModel.Routing.IRequestReplyRouter> se použije. Následující příklad definuje koncové body služby vystavené směrovací službou.  
  
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
  
     V této konfiguraci služba Směrování zveřejňuje tři samostatné koncové body. V závislosti na volbách za běhu odesílá klientská aplikace zprávy na jednu z těchto adres. Zprávy přicházející v jednom z "virtuálních" koncových bodů služby ("zaokrouhlování/Kalkulačka" nebo "Regular/Kalkulačka") se předávají odpovídající implementaci kalkulačky. Pokud klientská aplikace neodešle požadavek do konkrétního koncového bodu, bude zpráva adresována do obecného koncového bodu. Bez ohledu na zvolený koncový bod může klientská aplikace také zahrnout vlastní hlavičku, aby označovala, že by měla být zpráva předána implementaci kalkulačky zaokrouhlení.  
  
2. Následující příklad definuje koncové body klienta (cílové), na které směrovací služba směruje zprávy.  
  
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
  
     Tyto koncové body se používají v tabulce filtru k označení cílového koncového bodu, na který se zpráva pošle, když odpovídá konkrétnímu filtru.  
  
### <a name="define-filters"></a>Definovat filtry  
  
1. Chcete-li směrovat zprávy založené na vlastní hlavičce "RoundingCalculator", kterou klientská aplikace přidá do zprávy, definujte filtr, který používá dotaz XPath ke kontrole přítomnosti této hlavičky. Vzhledem k tomu, že je tato hlavička definována pomocí vlastního oboru názvů, přidejte také položku oboru názvů definující vlastní předponu oboru názvů "Custom", která se používá v dotazu XPath. Následující příklad definuje nezbytný oddíl směrování, tabulku oboru názvů a filtr XPath.  
  
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
  
     Tento **MessageFilter** vyhledá hlavičku RoundingCalculator ve zprávě, která obsahuje hodnotu "zaokrouhlení". Tato hlavička je nastavena klientem, aby označovala, že by měla být zpráva směrována do služby roundingCalc.  
  
    > [!NOTE]
    > Předpona oboru názvů S12 je ve výchozím nastavení definována v tabulce oboru názvů a představuje obor `http://www.w3.org/2003/05/soap-envelope`názvů.
  
2. Musíte také definovat filtry, které hledají zprávy přijaté ve dvou virtuálních koncových bodech. Prvním virtuálním koncovým bodem je koncový bod Regular/kalkulačky. Klient může odesílat požadavky na tento koncový bod, aby označoval, že by se měla směrovat zpráva do služby regularCalc. Následující konfigurace definuje filtr, který používá <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> k určení, zda byla zpráva doručena prostřednictvím koncového bodu s názvem zadaným v fulltextových.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     Pokud koncový bod služby s názvem "calculatorEndpoint" obdrží zprávu, tento filtr se `true`vyhodnotí jako.  
  
3. Dále Definujte filtr, který vyhledává zprávy odeslané na adresu roundingEndpoint. Klient může odesílat požadavky na tento koncový bod, aby označoval, že by se měla směrovat zpráva do služby roundingCalc. Následující konfigurace definuje filtr, který používá <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> k určení, zda byla zpráva doručena do koncového bodu zaokrouhlení/kalkulačky.  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     Pokud je zpráva přijata na adrese, která začíná `http://localhost/routingservice/router/rounding/` na, tento filtr se vyhodnotí jako **true**. Vzhledem k tomu, že základní adresa používaná touto `http://localhost/routingservice/router` konfigurací je a adresa zadaná pro roundingEndpoint je "zaokrouhlování/Kalkulačka", úplná adresa použitá ke komunikaci s tímto koncovým `http://localhost/routingservice/router/rounding/calculator`bodem je, což odpovídá tomuto filtru.  
  
    > [!NOTE]
    > Filtr PrefixEndpointAddress nevyhodnotí název hostitele při shodě, protože jeden hostitel může být odkazován pomocí různých názvů hostitelů, které mohou být platnými způsoby odkazu na hostitele z klientské aplikace. Například všechny následující mohou odkazovat na stejného hostitele:  
    >   
    > - místního  
    > - 127.0.0.1  
    > - `www.contoso.com`  
    > - ContosoWeb01  
  
4. Konečný filtr musí podporovat směrování zpráv, které přicházejí do obecného koncového bodu bez vlastní hlavičky. V tomto scénáři by se zprávy měly střídat mezi službami regularCalc a roundingCalc. Aby bylo možné podporovat "kruhové dotazování" těchto zpráv, použijte vlastní filtr, který umožňuje, aby jedna instance filtru odpovídala každé zpracovávané zprávě.  Níže jsou definovány dvě instance RoundRobinMessageFilter, které jsou seskupeny tak, aby označovaly, že by měly být mezi sebou vzájemně jiné.  
  
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
  
     Za běhu tento typ filtru střídavě mezi všemi definovanými instancemi filtru tohoto typu, které jsou nakonfigurované jako stejné skupiny, do jedné kolekce. To způsobí, že se zprávy zpracovávané tímto vlastním filtrem `true` střídají `RoundRobinFilter1` mezi `RoundRobinFilter2`vrácením pro a.  
  
### <a name="define-filter-tables"></a>Definice tabulek filtru  
  
1. Chcete-li přidružit filtry ke konkrétním koncovým bodům klienta, je nutné je umístit do tabulky filtru. Tento ukázkový scénář také používá nastavení priority filtru, což je volitelné nastavení, které umožňuje určit pořadí, ve kterém jsou filtry zpracovávány. Pokud není zadána žádná priorita filtru, všechny filtry budou vyhodnocovány současně.  
  
    > [!NOTE]
    > Když zadáte prioritu filtru, můžete řídit pořadí, ve kterém se filtry zpracovávají, což může negativně ovlivnit výkon směrovací služby. Pokud je to možné, sestavte logiku filtru tak, aby se použití priorit filtru nevyžadovalo.  
  
     Následující definice tabulky filtru a přidá "Třída XPathFilter" definované dříve v tabulce s prioritou 2. Tato položka také určuje, že pokud `XPathFilter` zpráva odpovídá, bude zpráva směrována `roundingCalcEndpoint`do.  
  
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
  
     Při zadávání priority filtru jsou nejprve vyhodnocovány filtry s nejvyšší prioritou. Pokud jeden nebo více filtrů na určité úrovni priority odpovídá, nebudou vyhodnoceny žádné filtry na úrovních s nižší prioritou. V tomto scénáři je 2 zadaná nejvyšší priorita a jedná se o jedinou položku filtru na této úrovni.  
  
2. Byly definovány položky filtru, aby bylo možné zjistit, zda je zpráva přijata v určitém koncovém bodu, a to kontrolou názvu koncového bodu nebo předpony adresy. Následující záznamy tyto položky filtru přidejte do tabulky filtru a přidružte je k cílovým koncovým bodům, na které bude zpráva směrována. U těchto filtrů je nastavena priorita 1, což označuje, že by měly být spuštěny pouze v případě, že předchozí filtr XPath neodpovídá zprávě.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Vzhledem k tomu, že tyto filtry mají prioritu filtru 1, budou vyhodnoceny pouze v případě, že filtr s úrovní priority 2 neodpovídá zprávě. Vzhledem k tomu, že oba filtry mají stejnou úroveň priority, budou vyhodnocovány současně. Vzhledem k tomu, že oba filtry se vzájemně vylučují, je možné, že pouze jedna nebo druhá bude odpovídat zprávě.  
  
3. Pokud se zpráva neshoduje s žádným z předchozích filtrů, pak byla zpráva přijata prostřednictvím obecného koncového bodu služby a neobsahuje žádné informace v hlavičce, které určují, kam se má směrovat. Tyto zprávy mají být zpracovány vlastním filtrem, který vyrovnává jejich zatížení mezi dvěma službami kalkulačky. Následující příklad ukazuje, jak přidat položky filtru do tabulky filtru; Každý filtr je přidružen k jednomu ze dvou cílových koncových bodů.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Vzhledem k tomu, že tyto položky určují prioritu 0, budou vyhodnoceny pouze v případě, že se zpráva neshoduje s žádným filtrem s vyšší prioritou. Kromě toho, vzhledem k tomu, že oba mají stejnou prioritu, jsou vyhodnocovány současně.  
  
     Jak již bylo zmíněno dříve, vlastní filtr používaný těmito definicemi filtru vyhodnocuje pouze jeden nebo druhý `true` jako pro každou přijatou zprávu. Vzhledem k tomu, že jsou pomocí tohoto filtru definované jenom dva filtry se stejným nastavením skupiny, použije se tento efekt jako služba Směrování mezi odesláním do regularCalcEndpoint a RoundingCalcEndpoint.  
  
4. Aby bylo možné vyhodnotit zprávy proti filtrům, musí být nejprve přidružena k koncovým bodům služby, které budou použity pro příjem zpráv.  Následující příklad ukazuje, jak přidružit směrovací tabulku k koncovým bodům služby pomocí chování směrování:  
  
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
  
## <a name="see-also"></a>Viz také:

- [Směrovací služby](../../../../docs/framework/wcf/samples/routing-services.md)
