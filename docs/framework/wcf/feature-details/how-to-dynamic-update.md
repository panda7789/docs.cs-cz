---
title: 'Postupy: Dynamická aktualizace'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: aaeb4d9d42c289cf34a6aee9212fc2d74b8f8c01
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184965"
---
# <a name="how-to-dynamic-update"></a><span data-ttu-id="18f34-102">Postupy: Dynamická aktualizace</span><span class="sxs-lookup"><span data-stu-id="18f34-102">How To: Dynamic Update</span></span>
<span data-ttu-id="18f34-103">Toto téma popisuje základní kroky potřebné k vytvoření a dynamické aktualizaci konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="18f34-103">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="18f34-104">V tomto příkladu počáteční konfigurace směrování je získána z konfiguračního souboru a směruje všechny zprávy do služby calc kalkulačky; však je následně aktualizován programově za účelem změny cílového koncového bodu zaokrouhleníCalc služby.</span><span class="sxs-lookup"><span data-stu-id="18f34-104">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18f34-105">V mnoha implementacích bude konfigurace plně dynamická a nebude spoléhat na výchozí konfiguraci. však existují některé scénáře, například v tomto tématu, kde je žádoucí mít výchozí stav konfigurace při spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="18f34-105">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18f34-106">Dynamické aktualizace se vyskytují pouze v paměti a nevedou k úpravě konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="18f34-106">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="18f34-107">RegularCalc a zaokrouhleníCalc podporují stejné operace sčítání, odečítání, násobení a dělení; zaokrouhleníCal však zaokrouhlí všechny výpočty na nejbližší celočíselnou hodnotu před vrácením.</span><span class="sxs-lookup"><span data-stu-id="18f34-107">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="18f34-108">Konfigurační soubor se používá ke konfiguraci služby směrovat všechny zprávy do služby regularCalc.</span><span class="sxs-lookup"><span data-stu-id="18f34-108">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="18f34-109">Po spuštění <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> služby směrování se používá k překonfigurování služby pro směrování zpráv do služby zaokrouhleníCalc.</span><span class="sxs-lookup"><span data-stu-id="18f34-109">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="18f34-110">Implementovat počáteční konfiguraci</span><span class="sxs-lookup"><span data-stu-id="18f34-110">Implement Initial Configuration</span></span>  
  
1. <span data-ttu-id="18f34-111">Vytvořte základní konfiguraci služby Směrování zadáním koncových bodů služby vystavených službou.</span><span class="sxs-lookup"><span data-stu-id="18f34-111">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="18f34-112">Následující příklad definuje jeden koncový bod služby, který bude použit pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="18f34-112">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="18f34-113">Také definuje koncový bod klienta, který bude použit k odesílání zpráv regularCalc.</span><span class="sxs-lookup"><span data-stu-id="18f34-113">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
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
    <!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    ```  
  
2. <span data-ttu-id="18f34-114">Definujte filtr používaný k směrování zpráv do cílových koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="18f34-114">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="18f34-115">V tomto příkladu MatchAll filtr se používá ke směrování všech zpráv na pravidelnéCalcEndpoint definované dříve.</span><span class="sxs-lookup"><span data-stu-id="18f34-115">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="18f34-116">Následující příklad definuje tabulku filtru a filtru.</span><span class="sxs-lookup"><span data-stu-id="18f34-116">The following example defines the filter and filter table.</span></span>  
  
    ```xml  
    <filters>  
      <!--define the message filter-->  
      <filter name="MatchAllFilter" filterType="MatchAll"/>  
    </filters>  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filter to the message filter table-->  
          <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
3. <span data-ttu-id="18f34-117">Chcete-li vyhodnotit příchozí zprávy proti filtrům obsaženým v tabulce filtrů, je nutné přidružit tabulku filtrů ke koncovým bodům služby pomocí chování směrování.</span><span class="sxs-lookup"><span data-stu-id="18f34-117">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="18f34-118">Následující příklad ukazuje přidruženou "filterTable1" s koncovým bodem služby.</span><span class="sxs-lookup"><span data-stu-id="18f34-118">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
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
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="18f34-119">Implementace dynamické konfigurace</span><span class="sxs-lookup"><span data-stu-id="18f34-119">Implement Dynamic Configuration</span></span>  
 <span data-ttu-id="18f34-120">Dynamickou konfiguraci služby Směrování lze provést pouze <xref:System.ServiceModel.Routing.RoutingConfiguration> v <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> kódu vytvořením nového a nahrazením aktuální konfigurace.</span><span class="sxs-lookup"><span data-stu-id="18f34-120">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="18f34-121">V tomto příkladu je služba směrování hostována samostatně v rámci konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="18f34-121">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="18f34-122">Po spuštění aplikace můžete upravit konfiguraci směrování zadáním "regular" nebo 'rounding' v okně konzoly a nakonfigurovat cílový koncový bod, do kterého jsou zprávy směrovány; regularCalc při zadání "regular", jinak zaokrouhlováníCalc při zadání "zaokrouhlení".</span><span class="sxs-lookup"><span data-stu-id="18f34-122">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1. <span data-ttu-id="18f34-123">Pro podporu služby směrování je nutné přidat následující příkazy using.</span><span class="sxs-lookup"><span data-stu-id="18f34-123">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. <span data-ttu-id="18f34-124">Následující kód se používá k samohostování služby Směrování jako konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="18f34-124">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="18f34-125">Tím se inicializuje služba směrování pomocí konfigurace popsané v předchozím kroku, která je obsažena v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="18f34-125">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="18f34-126">Smyčka while obsahuje kód použitý ke změně konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="18f34-126">The while loop contains the code used to change the routing configuration.</span></span>  
  
    ```csharp  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost =  
            new ServiceHost(typeof(RoutingService)))  
        {  
            // Open the ServiceHost to create listeners
            // and start listening for messages.  
            Console.WriteLine("The Routing Service configured, opening....");  
            serviceHost.Open();  
            Console.WriteLine("The Routing Service is now running.");  
             Console.WriteLine("Type 'quit' to terminate router.");  
             Console.WriteLine("<ENTER> to change routing configuration.");  
             while (Console.ReadLine() != "quit")  
             {  
            ....  
            }  
        }  
    }  
    ```  
  
3. <span data-ttu-id="18f34-127">Chcete-li dynamicky aktualizovat konfiguraci směrování, je nutné vytvořit novou konfiguraci směrování.</span><span class="sxs-lookup"><span data-stu-id="18f34-127">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="18f34-128">To musí obsahovat všechny koncové body, filtry a tabulky filtrů, které jsou požadovány pro novou konfiguraci směrování, protože zcela nahradí stávající konfiguraci směrování.</span><span class="sxs-lookup"><span data-stu-id="18f34-128">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="18f34-129">Chcete-li použít novou konfiguraci směrování, musíte vyvolat <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> a předat novou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="18f34-129">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="18f34-130">Přidejte následující kód do smyčky while definované dříve, aby bylo možné službu překonfigurovat na základě vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="18f34-130">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
    ```csharp  
    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
    string destEndpoint = Console.ReadLine();  
    // Create a new RoutingConfiguration  
    RoutingConfiguration rc = new RoutingConfiguration();  
    // Determine the endpoint to configure for  
    switch (destEndpoint)  
    {  
        case "regular":  
            // Define the destination endpoint  
            ServiceEndpoint regularCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        case "rounding":  
            // Define the destination endpoint  
            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        default:  
            Console.WriteLine("Incorrect value entered, no change.");  
            break;  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="18f34-131">Vzhledem k tomu, že metoda pro poskytování nové routingconfiguration je obsažena v rozšíření služby RoutingExtension, nové objekty RoutingConfiguration mohou být poskytnuty kdekoli v modelu rozšiřitelnosti WCF, který má nebo může získat odkaz na ServiceHost nebo ServiceExtensions (například v jiném ServiceExtension).</span><span class="sxs-lookup"><span data-stu-id="18f34-131">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span>
  
## <a name="example"></a><span data-ttu-id="18f34-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="18f34-132">Example</span></span>  

<span data-ttu-id="18f34-133">Následuje úplný seznam konzolové aplikace použité v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="18f34-133">The following is a complete listing of the console application used in this example:</span></span>
  
```csharp
//-----------------------------------------------------------------  
//  Copyright (c) Microsoft Corporation.  All Rights Reserved.  
//-----------------------------------------------------------------  
  
using System;  
using System.Collections.Generic;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.ServiceModel.Description;  
using System.ServiceModel.Dispatcher;  
using System.ServiceModel.Routing;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    public class Router  
    {  
        // Host the service within this EXE console application.  
        public static void Main()  
        {
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
            {  
                // Open the ServiceHost to create listeners
                // and start listening for messages.  
                Console.WriteLine("The Routing Service configured, opening....");  
                serviceHost.Open();  
                Console.WriteLine("The Routing Service is now running.");  
                Console.WriteLine("Type 'quit' to terminate router.");  
                Console.WriteLine("<ENTER> to change routing configuration.");  
                while (Console.ReadLine() != "quit")  
                {  
                    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
                    string destEndpoint = Console.ReadLine();  
                    // Create a new RoutingConfiguration  
                    RoutingConfiguration rc = new RoutingConfiguration();  
                    // Determine the endpoint to configure for  
                    switch (destEndpoint)  
                    {  
                        case "regular":  
                            // Define the destination endpoint  
                            ServiceEndpoint regularCalc = new ServiceEndpoint(  
                            ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                            new NetTcpBinding(),  
                            new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        case "rounding":  
                            // Define the destination endpoint  
                            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
                                ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                                new NetTcpBinding(),  
                                new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        default:  
                            Console.WriteLine("Incorrect value entered, no change.");  
                            break;  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="18f34-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="18f34-134">Example</span></span>  

<span data-ttu-id="18f34-135">Následuje úplný seznam konfiguračního souboru použitého v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="18f34-135">The following is a complete listing of the configuration file used in this example:</span></span>
  
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
<!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
  
      <filters>  
        <!--define the message filter-->  
        <filter name="MatchAllFilter" filterType="MatchAll"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filter to the message filter table-->  
            <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="18f34-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="18f34-136">See also</span></span>

- [<span data-ttu-id="18f34-137">Směrovací služby</span><span class="sxs-lookup"><span data-stu-id="18f34-137">Routing Services</span></span>](../samples/routing-services.md)
