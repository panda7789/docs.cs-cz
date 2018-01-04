---
title: "Postupy: Dynamická aktualizace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
caps.latest.revision: "4"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 748286b4f6fa22b23423ff5c176c76d11fbe742d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-dynamic-update"></a><span data-ttu-id="4d31d-102">Postupy: Dynamická aktualizace</span><span class="sxs-lookup"><span data-stu-id="4d31d-102">How To: Dynamic Update</span></span>
<span data-ttu-id="4d31d-103">Toto téma popisuje základní kroky potřebné k vytvoření a dynamicky aktualizovat konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="4d31d-103">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="4d31d-104">V tomto příkladu počáteční konfigurace směrování se získávají z konfiguračního souboru a směrovat všechny zprávy na službu kalkulačky regularCalc; Nicméně je následně aktualizován prostřednictvím kódu programu Chcete-li změnit do cílového koncového bodu služby roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="4d31d-104">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d31d-105">V mnoha implementacích konfigurace, bude plně dynamické a nebude spoléhají na výchozí konfiguraci; Existují však některé scénáře, jako je třeba v tomto tématu, kde je žádoucí, aby výchozí stav konfigurace při spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="4d31d-105">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d31d-106">Dynamické aktualizace dojít pouze v paměti a výsledkem není úpravu konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="4d31d-106">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="4d31d-107">RegularCalc a roundingCalc podporují stejné operace přidat, odečíst, násobení a dělení; ale roundingCalc zaokrouhlí na nejbližší celé číslo všech výpočtů před vrácením.</span><span class="sxs-lookup"><span data-stu-id="4d31d-107">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="4d31d-108">Konfigurační soubor se používá ke konfiguraci služby směrovat všechny zprávy ve službě regularCalc.</span><span class="sxs-lookup"><span data-stu-id="4d31d-108">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="4d31d-109">Po spuštění služby směrování <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> se používá k znovu nakonfigurovat službu pro směrování zpráv do služby roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="4d31d-109">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="4d31d-110">Implementace počáteční konfigurace</span><span class="sxs-lookup"><span data-stu-id="4d31d-110">Implement Initial Configuration</span></span>  
  
1.  <span data-ttu-id="4d31d-111">Vytvořte základní konfigurace služby směrování zadáním koncové body služby, který je zveřejněný prostřednictvím služby.</span><span class="sxs-lookup"><span data-stu-id="4d31d-111">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="4d31d-112">V následujícím příkladu definuje koncového bodu jedné služby, který se použije pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="4d31d-112">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="4d31d-113">Definuje také klienta koncový bod, který se použije k odesílání zpráv do regularCalc.</span><span class="sxs-lookup"><span data-stu-id="4d31d-113">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
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
  
2.  <span data-ttu-id="4d31d-114">Zadejte filtr slouží ke směrování zpráv do cílového koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="4d31d-114">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="4d31d-115">V tomto příkladu MatchAll filtr umožňuje směrovat všechny zprávy regularCalcEndpoint definována dříve.</span><span class="sxs-lookup"><span data-stu-id="4d31d-115">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="4d31d-116">V následujícím příkladu definuje filtr a tabulku filtru.</span><span class="sxs-lookup"><span data-stu-id="4d31d-116">The following example defines the filter and filter table.</span></span>  
  
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
  
3.  <span data-ttu-id="4d31d-117">Pokud chcete vyhodnotit příchozí zprávy před filtry, které jsou obsaženy v tabulce filtru, musíte přidružit tabulku filtru koncové body služby pomocí směrování chování.</span><span class="sxs-lookup"><span data-stu-id="4d31d-117">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="4d31d-118">Následující příklad ukazuje přiřadit "filterTable1" ke koncovému bodu služby.</span><span class="sxs-lookup"><span data-stu-id="4d31d-118">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
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
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="4d31d-119">Implementace dynamické konfigurace</span><span class="sxs-lookup"><span data-stu-id="4d31d-119">Implement Dynamic Configuration</span></span>  
 <span data-ttu-id="4d31d-120">Dynamické konfigurace služby směrování lze provést pouze v kódu tak, že vytvoříte novou <xref:System.ServiceModel.Routing.RoutingConfiguration> a pomocí <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> nahradit aktuální konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4d31d-120">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="4d31d-121">V tomto příkladu se hostuje sama v rámci aplikace konzoly služby směrování.</span><span class="sxs-lookup"><span data-stu-id="4d31d-121">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="4d31d-122">Po spuštění aplikace, můžete upravit konfigurace směrování zadáním 'pravidelné' nebo 'zaokrouhlení, v okně konzoly Konfigurace cílového koncového bodu, který zprávy jsou směrovány do; regularCalc při 'pravidelné' se zadá, jinak se zadá roundingCalc při 'zaokrouhlení'.</span><span class="sxs-lookup"><span data-stu-id="4d31d-122">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1.  <span data-ttu-id="4d31d-123">Následující příkazy using musí být přidán za účelem podpory služby směrování.</span><span class="sxs-lookup"><span data-stu-id="4d31d-123">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2.  <span data-ttu-id="4d31d-124">Následující kód slouží k hostování na vlastním směrovací služby jako konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d31d-124">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="4d31d-125">To inicializuje směrovací služby pomocí konfigurace popsané v předchozím kroku, který je obsažený v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d31d-125">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="4d31d-126">Chvíli smyčky obsahuje kód použít ke změně konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="4d31d-126">The while loop contains the code used to change the routing configuration.</span></span>  
  
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
  
3.  <span data-ttu-id="4d31d-127">Pokud chcete dynamicky aktualizovat konfigurace směrování, musí být vytvořeny nové konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="4d31d-127">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="4d31d-128">Tato položka musí obsahovat všechny koncové body, filtrů a filtru tabulky, které jsou požadovány pro nové konfigurace směrování jako úplně nahradí existující konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="4d31d-128">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="4d31d-129">Chcete-li použít nové konfigurace směrování, je nutné vyvolat <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> a předejte novou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4d31d-129">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="4d31d-130">Přidejte následující kód chvíli smyčky dříve definované lze umožnit službě třeba změnit konfiguraci na základě vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="4d31d-130">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
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
    >  <span data-ttu-id="4d31d-131">Od metodou pro zajištění nové RoutingConfiguration se nachází v rozšíření služby RoutingExtension, nové RoutingConfiguration objekty lze zadat libovolné místo ve model rozšiřitelnosti WCF, který má nebo můžete získat odkaz na hostitele ServiceHost nebo ServiceExtensions (například v jiné ServiceExtension).</span><span class="sxs-lookup"><span data-stu-id="4d31d-131">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span> <span data-ttu-id="4d31d-132">Příklad dynamicky aktualizuje RoutingConfiguration tímto způsobem, naleznete v části [dynamická Rekonfigurace](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md).</span><span class="sxs-lookup"><span data-stu-id="4d31d-132">For an example of dynamically updating the RoutingConfiguration in this manner, see [Dynamic Reconfiguration](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d31d-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d31d-133">Example</span></span>  
 <span data-ttu-id="4d31d-134">Toto je úplný seznam všech konzolové aplikace použité v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="4d31d-134">Following is a complete listing of the console application used in this example.</span></span>  
  
```  
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
  
## <a name="example"></a><span data-ttu-id="4d31d-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d31d-135">Example</span></span>  
 <span data-ttu-id="4d31d-136">Toto je úplný seznam všech konfiguraci souboru použitého v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="4d31d-136">Following is a complete listing of the configuration file used in this example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4d31d-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d31d-137">See Also</span></span>  
 [<span data-ttu-id="4d31d-138">Směrovací služby</span><span class="sxs-lookup"><span data-stu-id="4d31d-138">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
