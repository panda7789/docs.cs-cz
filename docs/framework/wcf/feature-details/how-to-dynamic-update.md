---
title: 'Postupy: Dynamická aktualizace'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: 7e2fbd6c179444ef4c6e1df5e5068dbd1c5d29fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773046"
---
# <a name="how-to-dynamic-update"></a><span data-ttu-id="a623d-102">Postupy: Dynamická aktualizace</span><span class="sxs-lookup"><span data-stu-id="a623d-102">How To: Dynamic Update</span></span>
<span data-ttu-id="a623d-103">Toto téma popisuje základní kroky potřebné k vytvoření a dynamicky aktualizovat konfiguraci směrování.</span><span class="sxs-lookup"><span data-stu-id="a623d-103">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="a623d-104">V tomto příkladu počáteční konfigurace směrování se získávají z konfiguračního souboru a všechny zprávy směruje do službu kalkulačky regularCalc; ale to se následně aktualizuje prostřednictvím kódu programu Chcete-li změnit cílový koncový bod služby roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="a623d-104">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a623d-105">Mnoho implementací konfigurace budou plně dynamického a nebude Spolehněte se na výchozí konfiguraci. Existují však některé scénáře, jako je třeba v tomto tématu, kde je žádoucí mají výchozí stav konfigurace, když se služba spustí.</span><span class="sxs-lookup"><span data-stu-id="a623d-105">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a623d-106">Dynamické aktualizace dochází pouze v paměti a není výsledkem úprav konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="a623d-106">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="a623d-107">RegularCalc a roundingCalc podporují stejné operace přidat, odečítání, násobení a dělení; ale roundingCalc Zaokrouhlí všechny výpočty na nejbližší celočíselnou hodnotu před vrácením.</span><span class="sxs-lookup"><span data-stu-id="a623d-107">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="a623d-108">Konfigurační soubor se používá ke konfiguraci služby pro směrování zpráv do služby regularCalc.</span><span class="sxs-lookup"><span data-stu-id="a623d-108">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="a623d-109">Po spuštění služby směrování <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> umožňuje změnit konfiguraci služby pro směrování zpráv služby roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="a623d-109">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="a623d-110">Implementace počáteční konfigurace</span><span class="sxs-lookup"><span data-stu-id="a623d-110">Implement Initial Configuration</span></span>  
  
1. <span data-ttu-id="a623d-111">Vytvoření základní konfigurace služby směrování zadat koncové body služby určeného službou.</span><span class="sxs-lookup"><span data-stu-id="a623d-111">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="a623d-112">Následující příklad definuje jedinou službou koncový bod, který se použije pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="a623d-112">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="a623d-113">Definuje také koncový bod klienta, který se použije pro odesílání zpráv regularCalc.</span><span class="sxs-lookup"><span data-stu-id="a623d-113">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
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
  
2. <span data-ttu-id="a623d-114">Zadejte filtr používá pro směrování zpráv do cílové koncové body.</span><span class="sxs-lookup"><span data-stu-id="a623d-114">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="a623d-115">V tomto příkladu je filtr MatchAll používá pro směrování zpráv do regularCalcEndpoint dříve definovali.</span><span class="sxs-lookup"><span data-stu-id="a623d-115">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="a623d-116">Následující příklad definuje filtr a tabulce filtrů.</span><span class="sxs-lookup"><span data-stu-id="a623d-116">The following example defines the filter and filter table.</span></span>  
  
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
  
3. <span data-ttu-id="a623d-117">Vyhodnocování příchozích zpráv proti filtrů obsažených v tabulce filtrů, je třeba přidružit tabulky filtru koncových bodů služby pomocí směrování chování.</span><span class="sxs-lookup"><span data-stu-id="a623d-117">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="a623d-118">Následující příklad ukazuje přiřazování "filterTable1" ke koncovému bodu služby.</span><span class="sxs-lookup"><span data-stu-id="a623d-118">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
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
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="a623d-119">Implementovat dynamické konfigurace</span><span class="sxs-lookup"><span data-stu-id="a623d-119">Implement Dynamic Configuration</span></span>  
 <span data-ttu-id="a623d-120">Směrovací služba dynamickou konfiguraci lze provést pouze v kódu vytvořením nového <xref:System.ServiceModel.Routing.RoutingConfiguration> a pomocí <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> k nahrazení aktuální konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a623d-120">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="a623d-121">V tomto příkladu je služba Směrování v rámci konzolové aplikace v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="a623d-121">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="a623d-122">Po spuštění aplikace, můžete upravit konfiguraci směrování tak, že zadáte "normální" nebo "zaokrouhlení" v okně konzoly ke konfiguraci cílového koncového bodu, který zprávy jsou směrovány na; Zadaný regularCalc při 'pravidelné', jinak se zadá roundingCalc při "zaokrouhlování".</span><span class="sxs-lookup"><span data-stu-id="a623d-122">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1. <span data-ttu-id="a623d-123">Následující příkazy using musí být přidán za účelem podpory služby směrování.</span><span class="sxs-lookup"><span data-stu-id="a623d-123">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. <span data-ttu-id="a623d-124">Následující kód slouží k hostování na vlastním serveru služby směrování jako konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="a623d-124">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="a623d-125">To Inicializuje službu Směrování pomocí konfigurace popsaná v předchozím kroku, která je obsažena v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a623d-125">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="a623d-126">While smyčka obsahuje kód použít ke změně konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="a623d-126">The while loop contains the code used to change the routing configuration.</span></span>  
  
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
  
3. <span data-ttu-id="a623d-127">Dynamicky aktualizovat konfiguraci směrování, je nutné vytvořit novou konfiguraci směrování.</span><span class="sxs-lookup"><span data-stu-id="a623d-127">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="a623d-128">Všechny koncové body, filtry a filtru tabulky, které jsou požadovány pro novou konfiguraci směrování, to musí obsahovat jak zcela nahradit existující konfiguraci směrování.</span><span class="sxs-lookup"><span data-stu-id="a623d-128">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="a623d-129">Chcete-li použít nové konfigurace směrování, je nutné vyvolat <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> a předejte mu novou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a623d-129">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="a623d-130">Přidejte následující kód do while smyčky dříve definovali povolit službu třeba překonfigurovat na základě uživatelského zadání.</span><span class="sxs-lookup"><span data-stu-id="a623d-130">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
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
    > <span data-ttu-id="a623d-131">Od metodou pro zajištění nová konfigurace RoutingConfiguration obsažené v rozšíření služby třída RoutingExtension, nová konfigurace RoutingConfiguration objekty lze zadat kdekoli v rozšiřitelném modelu WCF, nebo můžete získat odkaz na hostitele ServiceHost nebo ServiceExtensions (jako je například jiné ServiceExtension).</span><span class="sxs-lookup"><span data-stu-id="a623d-131">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span>
  
## <a name="example"></a><span data-ttu-id="a623d-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="a623d-132">Example</span></span>  
 <span data-ttu-id="a623d-133">Tady je úplný seznam všech Konzolová aplikace použitý v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="a623d-133">Following is a complete listing of the console application used in this example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="a623d-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="a623d-134">Example</span></span>  
 <span data-ttu-id="a623d-135">Tady je úplný seznam všech konfiguraci souboru použitého v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="a623d-135">Following is a complete listing of the configuration file used in this example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a623d-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a623d-136">See also</span></span>

- [<span data-ttu-id="a623d-137">Směrovací služby</span><span class="sxs-lookup"><span data-stu-id="a623d-137">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
