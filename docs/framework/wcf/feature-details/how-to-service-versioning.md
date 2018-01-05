---
title: "Postupy: Verze služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
caps.latest.revision: "6"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4da80d264b05f9c7a1461a7298e521623a97f31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-service-versioning"></a><span data-ttu-id="b9e22-102">Postupy: Verze služby</span><span class="sxs-lookup"><span data-stu-id="b9e22-102">How To: Service Versioning</span></span>
<span data-ttu-id="b9e22-103">Toto téma popisuje základní kroky potřebné pro vytvoření konfigurace směrování, který směruje zprávy pro různé verze nástroje stejnou službu.</span><span class="sxs-lookup"><span data-stu-id="b9e22-103">This topic outlines the basic steps required to create a routing configuration that routes messages to different versions of the same service.</span></span> <span data-ttu-id="b9e22-104">V tomto příkladu jsou směrovány zprávy dvě různé verze služby kalkulačky, `roundingCalc` (v1) a `regularCalc` (v2).</span><span class="sxs-lookup"><span data-stu-id="b9e22-104">In this example, messages are routed to two different versions of a calculator service, `roundingCalc` (v1) and `regularCalc` (v2).</span></span> <span data-ttu-id="b9e22-105">Obě implementace podporují stejné operace; ale službu starší `roundingCalc`, zaokrouhlí na nejbližší celé číslo všech výpočtů před vrácením.</span><span class="sxs-lookup"><span data-stu-id="b9e22-105">Both implementations support the same operations; however the older service, `roundingCalc`, rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="b9e22-106">Klientská aplikace musí být schopen označuje, zda chcete použít novější `regularCalc` služby.</span><span class="sxs-lookup"><span data-stu-id="b9e22-106">A client application must be able to indicate whether to use the newer `regularCalc` service.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b9e22-107">Aby bylo možné směrovat zprávy na verzi konkrétní službu, službu směrování musí být schopní určit, na základě obsahu zprávy cíl zprávy.</span><span class="sxs-lookup"><span data-stu-id="b9e22-107">In order to route a message to a specific service version, the Routing Service must be able to determine the message destination based on the message content.</span></span> <span data-ttu-id="b9e22-108">V metodě ukázáno níže bude klient určit verzi vložením informace do záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="b9e22-108">In the method demonstrated below, the client will specify the version by inserting information into a message header.</span></span> <span data-ttu-id="b9e22-109">Existují metody verze služby, které nechcete, aby klienti předat další data.</span><span class="sxs-lookup"><span data-stu-id="b9e22-109">There are methods of service versioning that do not require clients to pass additional data.</span></span> <span data-ttu-id="b9e22-110">Například zpráva může směrovat na nejnovější nebo nejvíce kompatibilní verzi služby nebo směrovači použít součástí standardní obálku protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b9e22-110">For example, a message could be routed to the most recent or most compatible version of a service or the router could use a part of the standard SOAP envelope.</span></span>  
  
 <span data-ttu-id="b9e22-111">Operace vystavené obě služby jsou:</span><span class="sxs-lookup"><span data-stu-id="b9e22-111">The operations exposed by both services are:</span></span>  
  
-   <span data-ttu-id="b9e22-112">Přidejte</span><span class="sxs-lookup"><span data-stu-id="b9e22-112">Add</span></span>  
  
-   <span data-ttu-id="b9e22-113">Odečtena</span><span class="sxs-lookup"><span data-stu-id="b9e22-113">Subtract</span></span>  
  
-   <span data-ttu-id="b9e22-114">Násobení</span><span class="sxs-lookup"><span data-stu-id="b9e22-114">Multiply</span></span>  
  
-   <span data-ttu-id="b9e22-115">Dělení</span><span class="sxs-lookup"><span data-stu-id="b9e22-115">Divide</span></span>  
  
 <span data-ttu-id="b9e22-116">Protože oba implementace služby zpracování stejné operace a jsou v podstatě stejné než data, která se vracejí, základní data obsažená v zpráv odeslaných z klientské aplikace není dostatečně jedinečný, a umožní vám určit, jak směrovat požadavek.</span><span class="sxs-lookup"><span data-stu-id="b9e22-116">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="b9e22-117">Filtry akcí například nelze použít, protože výchozí akce pro obě služby jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="b9e22-117">For example, Action filters cannot be used because the default actions for both services are the same.</span></span>  
  
 <span data-ttu-id="b9e22-118">To může být vyřešené v několika způsoby, například vystavení konkrétní koncový bod na směrovači pro každou verzi služby nebo přidáváte vlastní hlavičky element do zprávy, která označuje verzi aktualizace service.</span><span class="sxs-lookup"><span data-stu-id="b9e22-118">This can be resolved in several ways, such as exposing a specific endpoint on the router for each version of the service or adding a custom header element to the message to indicate service version.</span></span>  <span data-ttu-id="b9e22-119">Každý z těchto přístupů umožňuje jednoznačně směrovat příchozí zprávy na konkrétní verzi služby, ale využívá obsah jedinečný zprávy je preferovanou metodu rozdíl mezi požadavky pro různé verze aktualizace service.</span><span class="sxs-lookup"><span data-stu-id="b9e22-119">Each of these approaches allows you to uniquely route incoming messages to a specific version of the service, but utilizing unique message content is the preferred method of differentiating between requests for different service versions.</span></span>  
  
 <span data-ttu-id="b9e22-120">V tomto příkladu klientská aplikace přidá vlastní hlavičku 'CalcVer' zprávu požadavku.</span><span class="sxs-lookup"><span data-stu-id="b9e22-120">In this example, the client application adds the ‘CalcVer’ custom header to the request message.</span></span> <span data-ttu-id="b9e22-121">Tuto hlavičku bude obsahovat hodnotu, která určuje verzi služby, který zpráva by měl směrovat na.</span><span class="sxs-lookup"><span data-stu-id="b9e22-121">This header will contain a value that indicates the version of the service that the message should be routed to.</span></span> <span data-ttu-id="b9e22-122">Hodnota 1, který značí, že musí být zpráva zpracována službou roundingCalc, zatímco hodnotu (2) označuje službu regularCalc.</span><span class="sxs-lookup"><span data-stu-id="b9e22-122">A value of ‘1’ indicates that the message must be processed by the roundingCalc service, while a value of ‘2’ indicates the regularCalc service.</span></span> <span data-ttu-id="b9e22-123">To umožňuje aplikaci klienta přímo řídit, kterou verzi služby zpracuje zprávu.</span><span class="sxs-lookup"><span data-stu-id="b9e22-123">This allows the client application to directly control which version of the service will process the message.</span></span>  <span data-ttu-id="b9e22-124">Vzhledem k tomu, že vlastní hlavička je hodnota obsažená v rámci zprávy, můžete použít jeden koncový bod pro příjem zprávy určené pro obě verze služby.</span><span class="sxs-lookup"><span data-stu-id="b9e22-124">Since the custom header is a value contained within the message, you can use one endpoint to receive messages destined for both versions of the service.</span></span> <span data-ttu-id="b9e22-125">Následující kód slouží v aplikaci klienta k do zprávy přidat tento vlastní hlavičky:</span><span class="sxs-lookup"><span data-stu-id="b9e22-125">The following code can be used in the client application to add this custom header to the message:</span></span>  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a><span data-ttu-id="b9e22-126">Implementace služby správy verzí</span><span class="sxs-lookup"><span data-stu-id="b9e22-126">Implement Service Versioning</span></span>  
  
1.  <span data-ttu-id="b9e22-127">Vytvořte základní konfigurace směrování služby zadáním koncový bod služby, který je zveřejněný prostřednictvím služby.</span><span class="sxs-lookup"><span data-stu-id="b9e22-127">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="b9e22-128">V následujícím příkladu definuje koncového bodu jedné služby, který se použije pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="b9e22-128">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="b9e22-129">Definuje také koncové body klientů, které budou použity k odeslání zprávy `roundingCalc` (v1) a `regularCalc` služby (v2).</span><span class="sxs-lookup"><span data-stu-id="b9e22-129">It also defines the client endpoints which will be used to send messages to the `roundingCalc` (v1) and the `regularCalc` (v2) services.</span></span>  
  
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
  
2.  <span data-ttu-id="b9e22-130">Zadejte filtry slouží ke směrování zpráv do cílového koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="b9e22-130">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="b9e22-131">V tomto příkladu filtr XPath slouží ke zjištění hodnotu vlastní hlavičky "CalcVer" určení verze zprávy by měl směrovat na.</span><span class="sxs-lookup"><span data-stu-id="b9e22-131">For this example, the XPath filter is used to detect the value of the "CalcVer" custom header to determine which version the message should be routed to.</span></span> <span data-ttu-id="b9e22-132">Filtr XPath se také používá ke zjišťování zpráv, které neobsahují hlavičku "CalcVer".</span><span class="sxs-lookup"><span data-stu-id="b9e22-132">An XPath filter is also used to detect messages that do not contain the "CalcVer" header.</span></span> <span data-ttu-id="b9e22-133">V následujícím příkladu definuje požadované filtry a obor názvů tabulky.</span><span class="sxs-lookup"><span data-stu-id="b9e22-133">The following example defines the required filters and namespace table.</span></span>  
  
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
    >  <span data-ttu-id="b9e22-134">Předpona oboru názvů s12 je definována ve výchozím nastavení v tabulce obor názvů a představuje obor názvů "http://www.w3.org/2003/05/soap-envelope".</span><span class="sxs-lookup"><span data-stu-id="b9e22-134">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace "http://www.w3.org/2003/05/soap-envelope".</span></span>  
  
3.  <span data-ttu-id="b9e22-135">Definujte tabulku filtru, který přidruží každý filtr koncový bod klienta.</span><span class="sxs-lookup"><span data-stu-id="b9e22-135">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="b9e22-136">Pokud zpráva obsahuje hlavičku "CalcVer" s hodnotou 1, odešle se ke službě regularCalc.</span><span class="sxs-lookup"><span data-stu-id="b9e22-136">If the message contains the "CalcVer" header with a value of 1, it will be sent to the regularCalc service.</span></span> <span data-ttu-id="b9e22-137">Pokud hlavička obsahuje hodnotu 2, odešle se ke službě roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="b9e22-137">If the header contains a value of 2, it will be sent to the roundingCalc service.</span></span> <span data-ttu-id="b9e22-138">Pokud je k dispozici žádné záhlaví, zprávy budou směrované na regularCalc.</span><span class="sxs-lookup"><span data-stu-id="b9e22-138">If no header is present, the message will be routed to the regularCalc.</span></span>  
  
     <span data-ttu-id="b9e22-139">Následující tabulku filtru definuje a přidá filtry definované dříve.</span><span class="sxs-lookup"><span data-stu-id="b9e22-139">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
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
  
4.  <span data-ttu-id="b9e22-140">Pokud chcete vyhodnotit příchozí zprávy před filtry, které jsou obsaženy v tabulce filtru, musíte přidružit tabulku filtru koncové body služby pomocí směrování chování.</span><span class="sxs-lookup"><span data-stu-id="b9e22-140">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="b9e22-141">Následující příklad ukazuje přiřadit "filterTable1" s koncovými body služby:</span><span class="sxs-lookup"><span data-stu-id="b9e22-141">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b9e22-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9e22-142">Example</span></span>  
 <span data-ttu-id="b9e22-143">Níže je úplný seznam všech konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b9e22-143">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b9e22-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9e22-144">Example</span></span>  
 <span data-ttu-id="b9e22-145">Níže je úplný seznam všech klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="b9e22-145">The following is a complete listing of the client application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b9e22-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9e22-146">See Also</span></span>  
 [<span data-ttu-id="b9e22-147">Směrovací služby</span><span class="sxs-lookup"><span data-stu-id="b9e22-147">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
