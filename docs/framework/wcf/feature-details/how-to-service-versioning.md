---
title: 'Postupy: Verze služby'
ms.date: 03/30/2017
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
ms.openlocfilehash: 5ce9e7fc896f1ebc46dd25777fc629532339cbe2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988707"
---
# <a name="how-to-service-versioning"></a>Postupy: Verze služby
Toto téma popisuje základní kroky potřebné k vytvoření konfigurace směrování, která směruje zprávy do různých verzí stejné služby. V tomto příkladu jsou zprávy směrovány do dvou různých verzí služby `roundingCalc` kalkulačky (V1) a `regularCalc` (v2). Obě implementace podporují stejné operace. starší služba `roundingCalc`však Zaokrouhlí všechny výpočty na nejbližší celočíselnou hodnotu před vrácením. Klientská aplikace musí být schopná určit, jestli se má používat `regularCalc` novější služba.  
  
> [!WARNING]
> Aby bylo možné směrovat zprávu na konkrétní verzi služby, musí být směrovací služba schopná určit cíl zprávy na základě obsahu zprávy. V níže uvedené metodě bude klient zadat verzi vložením informací do záhlaví zprávy. Existují metody správy verzí, které nevyžadují, aby klienti předávali další data. Například zpráva může být směrována na nejnovější nebo nejvíce kompatibilní verzi služby nebo směrovač může použít část standardní obálky protokolu SOAP.  
  
 Mezi operace vystavené oběma službami patří:  
  
- Přidejte  
  
- Odečten  
  
- Hodnotou  
  
- Rozdělovací  
  
 Vzhledem k tomu, že obě implementace služby pracují se stejnými operacemi a jsou v podstatě totožné s daty, která vrací, nejsou základní data obsažená ve zprávách odesílaných klientskými aplikacemi dostatečně jedinečná, aby bylo možné určit, jak se má směrovat Request. Například filtry akcí nelze použít, protože výchozí akce pro obě služby jsou stejné.  
  
 Dá se vyřešit několika způsoby, jako je například vystavení konkrétního koncového bodu na směrovači pro každou verzi služby nebo přidání vlastního elementu záhlaví do zprávy, aby označovala verzi služby.  Každý z těchto přístupů vám umožní jedinečně směrovat příchozí zprávy na konkrétní verzi služby, ale využití jedinečného obsahu zprávy je upřednostňovanou metodou, jak rozlišovat mezi požadavky na různé verze služeb.  
  
 V tomto příkladu klientská aplikace do zprávy požadavku přidá vlastní hlavičku ' CalcVer '. Tato hlavička bude obsahovat hodnotu, která označuje verzi služby, na kterou se má zpráva směrovat. Hodnota 1 označuje, že zprávu musí zpracovat služba roundingCalc, zatímco hodnota 2 označuje službu regularCalc. Díky tomu může klientská aplikace přímo řídit, která verze služby zprávu zpracuje.  Vzhledem k tomu, že vlastní hlavička je hodnota obsažená v rámci zprávy, můžete použít jeden koncový bod pro příjem zpráv určených pro obě verze služby. Následující kód lze v klientské aplikaci použít k přidání této vlastní hlavičky do zprávy:  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a>Implementace správy verzí služby  
  
1. Vytvořte základní konfiguraci směrovací služby zadáním koncového bodu služby vystaveného službou. Následující příklad definuje jeden koncový bod služby, který se použije pro příjem zpráv. Také definuje koncové body klienta, které budou použity k odesílání zpráv do `roundingCalc` služeb (V1) `regularCalc` a (v2).  
  
    ```xml  
    <services>  
        <service behaviorConfiguration="routingConfiguration"  
                 name="System.ServiceModel.Routing.RoutingService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost/routingservice/router" />  
            </baseAddresses>  
          </host>  
          <!--Set up the inbound endpoint for the Routing Service-->  
          <endpoint address="calculator"  
                    binding="wsHttpBinding"  
                    name="routerEndpoint"  
                    contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        </service>  
    </services>  
    <client>  
    <!--set up the destination endpoints-->  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="http://localhost:8080/servicemodelsamples/service/"  
                    binding="wsHttpBinding"  
                    contract="*" />  
        </client>  
    ```  
  
2. Definujte filtry používané ke směrování zpráv do cílových koncových bodů.  Pro účely tohoto příkladu je použit filtr XPath k detekci hodnoty vlastní hlavičky "CalcVer" a určení, na kterou verzi se má zpráva směrovat. Filtr XPath se používá také k detekci zpráv, které neobsahují hlavičku "CalcVer". Následující příklad definuje požadované filtry a tabulku oboru názvů.  
  
    ```xml  
    <!-- use the namespace table element to define a prefix for our custom namespace-->  
    <namespaceTable>  
      <add prefix="custom" namespace="http://my.custom.namespace/"/>  
    </namespaceTable>  
    <filters>  
      <!--define the different message filters-->  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 2-->  
      <filter name="XPathFilterRegular" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '2'"/>  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 1-->  
      <filter name="XPathFilterRounding" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '1'"/>  
       <!--define an xpath message filter to look for  
           messages that do not contain the custom header-->  
       <filter name="XPathFilterNoHeader" filterType="XPath"  
               filterData="count(sm:header()/custom:CalcVer)=0"/>  
    </filters  
    ```  
  
    > [!NOTE]
    > Předpona oboru názvů S12 je ve výchozím nastavení definována v tabulce oboru názvů a představuje obor `http://www.w3.org/2003/05/soap-envelope`názvů.
  
3. Definujte tabulku filtru, která přidruží jednotlivé filtry ke koncovému bodu klienta. Pokud zpráva obsahuje hlavičku "CalcVer" s hodnotou 1, bude odeslána službě regularCalc. Pokud hlavička obsahuje hodnotu 2, bude odeslána do služby roundingCalc. Pokud není k dispozici hlavička, zpráva bude směrována do regularCalc.  
  
     Následující definice tabulky filtru a přidává filtry definované dříve.  
  
    ```xml  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <!--look for the custom header = 1, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
          <!--look for the custom header = 2, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
          <!--look for the absence of the custom header, and if  
              it is not present, assume the v1 endpoint-->  
          <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
4. Chcete-li vyhodnotit příchozí zprávy proti filtrům obsaženým v tabulce filtru, je nutné přidružit tabulku filtru k koncovým bodům služby pomocí chování směrování. Následující příklad ukazuje přidružení `filterTable1` k koncovým bodům služby:  
  
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
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
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
                address="http://localhost:8080/servicemodelsamples/service/"  
                binding="wsHttpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 2-->  
        <filter name="XPathFilterRegular" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '2'"/>  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 1-->  
        <filter name="XPathFilterRounding" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '1'"/>  
        <!--define an xpath message filter to look for  
            messages that do not contain the custom header-->  
        <filter name="XPathFilterNoHeader" filterType="XPath"  
                filterData="count(sm:header()/custom:CalcVer)=0"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filters to the message filter table-->  
            <!--look for the custom header = 1, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
            <!--look for the custom header = 2, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
            <!--look for the absence of the custom header, and if  
                it is not present, assume the v1 endpoint-->  
            <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="example"></a>Příklad  
 Následuje úplný seznam klientských aplikací.  
  
```csharp  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    //The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
    //Client implementation code.  
    class Client  
    {  
        static void Main()  
        {  
            //Print out the welcome text  
            Console.WriteLine("This sample routes the Calculator Sample through the new WCF RoutingService");  
            Console.WriteLine("Wait for all the services to indicate that they've started, then press");  
            Console.WriteLine("<ENTER> to start the client.");  
  
            while (Console.ReadLine() != "quit")  
            {  
                //Offer the Address configuration for the client  
                Console.WriteLine("");  
                Console.WriteLine("Welcome to the Calculator Client!");  
  
                EndpointAddress epa;  
                //set the default address as the general router endpoint  
                epa = new EndpointAddress("http://localhost/routingservice/router/calculator");  
  
                //set up the CalculatorClient with the EndpointAddress, the WSHttpBinding, and the ICalculator contract  
                //We use the WSHttpBinding so that the outgoing has a message envelope, which we'll manipulate in a minute  
                CalculatorClient client = new CalculatorClient(new WSHttpBinding(), epa);  
                //client.Endpoint.Contract = ContractDescription.GetContract(typeof(ICalculator));  
  
                //Ask the customer if they want to add a custom header to the outgoing message.  
                //The Router will look for this header, and if so ignore the endpoint the message was  
                //received on, and instead direct the message to the RoundingCalcService.  
                Console.WriteLine("");  
                Console.WriteLine("Which calculator service should be used?");  
                Console.WriteLine("Enter 1 for the rounding calculator, 2 for the regular calculator.");  
                Console.WriteLine("[1] or [2]?");  
  
                string header = Console.ReadLine();  
  
                //get the current operationContextScope from the client's inner channel  
                using (OperationContextScope ocs = new OperationContextScope((client.InnerChannel)))  
                {  
                    //get the outgoing message headers element (collection) from the context  
                    MessageHeaders messageHeadersElement = OperationContext.Current.OutgoingMessageHeaders;  
  
                    //if they wanted to create the header, go ahead and add it to the outgoing message  
                    if (header != null && (header=="1" || header=="2"))  
                    {  
                        //create a new header "RoundingCalculator", no specific namespace, and set the value to   
                        //the value of header.  
                        //the Routing Service will look for this header in order to determine if the message  
                        //should be routed to the RoundingCalculator  
                        messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", header));  
                    }  
                    else //incorrect choice, no header added  
                    {  
                        Console.WriteLine("Incorrect value entered, not adding a header");  
                    }  
  
                        //call the client operations  
                        CallClient(client);  
                }  
  
                //close the client to clean it up  
                client.Close();  
                Console.WriteLine();  
                Console.WriteLine("Press <ENTER> to run the client again or type 'quit' to quit.");  
            }  
        }  
  
        private static void CallClient(CalculatorClient client)  
        {  
            Console.WriteLine("");  
            Console.WriteLine("Sending!");  
            // Call the Add service operation.  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            value1 = 145.00D;  
            value2 = 76.54D;  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            value1 = 9.00D;  
            value2 = 81.25D;  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            value1 = 22.00D;  
            value2 = 7.00D;  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Směrovací služby](../../../../docs/framework/wcf/samples/routing-services.md)
