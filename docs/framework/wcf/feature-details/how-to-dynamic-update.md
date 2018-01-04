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
# <a name="how-to-dynamic-update"></a>Postupy: Dynamická aktualizace
Toto téma popisuje základní kroky potřebné k vytvoření a dynamicky aktualizovat konfigurace směrování. V tomto příkladu počáteční konfigurace směrování se získávají z konfiguračního souboru a směrovat všechny zprávy na službu kalkulačky regularCalc; Nicméně je následně aktualizován prostřednictvím kódu programu Chcete-li změnit do cílového koncového bodu služby roundingCalc.  
  
> [!NOTE]
>  V mnoha implementacích konfigurace, bude plně dynamické a nebude spoléhají na výchozí konfiguraci; Existují však některé scénáře, jako je třeba v tomto tématu, kde je žádoucí, aby výchozí stav konfigurace při spuštění služby.  
  
> [!NOTE]
>  Dynamické aktualizace dojít pouze v paměti a výsledkem není úpravu konfiguračních souborů.  
  
 RegularCalc a roundingCalc podporují stejné operace přidat, odečíst, násobení a dělení; ale roundingCalc zaokrouhlí na nejbližší celé číslo všech výpočtů před vrácením. Konfigurační soubor se používá ke konfiguraci služby směrovat všechny zprávy ve službě regularCalc. Po spuštění služby směrování <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> se používá k znovu nakonfigurovat službu pro směrování zpráv do služby roundingCalc.  
  
### <a name="implement-initial-configuration"></a>Implementace počáteční konfigurace  
  
1.  Vytvořte základní konfigurace služby směrování zadáním koncové body služby, který je zveřejněný prostřednictvím služby. V následujícím příkladu definuje koncového bodu jedné služby, který se použije pro příjem zpráv. Definuje také klienta koncový bod, který se použije k odesílání zpráv do regularCalc.  
  
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
  
2.  Zadejte filtr slouží ke směrování zpráv do cílového koncových bodů. V tomto příkladu MatchAll filtr umožňuje směrovat všechny zprávy regularCalcEndpoint definována dříve. V následujícím příkladu definuje filtr a tabulku filtru.  
  
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
  
3.  Pokud chcete vyhodnotit příchozí zprávy před filtry, které jsou obsaženy v tabulce filtru, musíte přidružit tabulku filtru koncové body služby pomocí směrování chování. Následující příklad ukazuje přiřadit "filterTable1" ke koncovému bodu služby.  
  
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
  
## <a name="implement-dynamic-configuration"></a>Implementace dynamické konfigurace  
 Dynamické konfigurace služby směrování lze provést pouze v kódu tak, že vytvoříte novou <xref:System.ServiceModel.Routing.RoutingConfiguration> a pomocí <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> nahradit aktuální konfiguraci.  V tomto příkladu se hostuje sama v rámci aplikace konzoly služby směrování. Po spuštění aplikace, můžete upravit konfigurace směrování zadáním 'pravidelné' nebo 'zaokrouhlení, v okně konzoly Konfigurace cílového koncového bodu, který zprávy jsou směrovány do; regularCalc při 'pravidelné' se zadá, jinak se zadá roundingCalc při 'zaokrouhlení'.  
  
1.  Následující příkazy using musí být přidán za účelem podpory služby směrování.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2.  Následující kód slouží k hostování na vlastním směrovací služby jako konzolové aplikace. To inicializuje směrovací služby pomocí konfigurace popsané v předchozím kroku, který je obsažený v konfiguračním souboru aplikace. Chvíli smyčky obsahuje kód použít ke změně konfigurace směrování.  
  
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
  
3.  Pokud chcete dynamicky aktualizovat konfigurace směrování, musí být vytvořeny nové konfigurace směrování. Tato položka musí obsahovat všechny koncové body, filtrů a filtru tabulky, které jsou požadovány pro nové konfigurace směrování jako úplně nahradí existující konfigurace směrování. Chcete-li použít nové konfigurace směrování, je nutné vyvolat <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> a předejte novou konfiguraci.  
  
     Přidejte následující kód chvíli smyčky dříve definované lze umožnit službě třeba změnit konfiguraci na základě vstup uživatele.  
  
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
    >  Od metodou pro zajištění nové RoutingConfiguration se nachází v rozšíření služby RoutingExtension, nové RoutingConfiguration objekty lze zadat libovolné místo ve model rozšiřitelnosti WCF, který má nebo můžete získat odkaz na hostitele ServiceHost nebo ServiceExtensions (například v jiné ServiceExtension). Příklad dynamicky aktualizuje RoutingConfiguration tímto způsobem, naleznete v části [dynamická Rekonfigurace](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md).  
  
## <a name="example"></a>Příklad  
 Toto je úplný seznam všech konzolové aplikace použité v tomto příkladu.  
  
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
  
## <a name="example"></a>Příklad  
 Toto je úplný seznam všech konfiguraci souboru použitého v tomto příkladu.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Směrovací služby](../../../../docs/framework/wcf/samples/routing-services.md)
