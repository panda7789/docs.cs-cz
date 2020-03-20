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
# <a name="how-to-dynamic-update"></a>Postupy: Dynamická aktualizace
Toto téma popisuje základní kroky potřebné k vytvoření a dynamické aktualizaci konfigurace směrování. V tomto příkladu počáteční konfigurace směrování je získána z konfiguračního souboru a směruje všechny zprávy do služby calc kalkulačky; však je následně aktualizován programově za účelem změny cílového koncového bodu zaokrouhleníCalc služby.  
  
> [!NOTE]
> V mnoha implementacích bude konfigurace plně dynamická a nebude spoléhat na výchozí konfiguraci. však existují některé scénáře, například v tomto tématu, kde je žádoucí mít výchozí stav konfigurace při spuštění služby.  
  
> [!NOTE]
> Dynamické aktualizace se vyskytují pouze v paměti a nevedou k úpravě konfiguračních souborů.  
  
 RegularCalc a zaokrouhleníCalc podporují stejné operace sčítání, odečítání, násobení a dělení; zaokrouhleníCal však zaokrouhlí všechny výpočty na nejbližší celočíselnou hodnotu před vrácením. Konfigurační soubor se používá ke konfiguraci služby směrovat všechny zprávy do služby regularCalc. Po spuštění <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> služby směrování se používá k překonfigurování služby pro směrování zpráv do služby zaokrouhleníCalc.  
  
### <a name="implement-initial-configuration"></a>Implementovat počáteční konfiguraci  
  
1. Vytvořte základní konfiguraci služby Směrování zadáním koncových bodů služby vystavených službou. Následující příklad definuje jeden koncový bod služby, který bude použit pro příjem zpráv. Také definuje koncový bod klienta, který bude použit k odesílání zpráv regularCalc.  
  
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
  
2. Definujte filtr používaný k směrování zpráv do cílových koncových bodů. V tomto příkladu MatchAll filtr se používá ke směrování všech zpráv na pravidelnéCalcEndpoint definované dříve. Následující příklad definuje tabulku filtru a filtru.  
  
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
  
3. Chcete-li vyhodnotit příchozí zprávy proti filtrům obsaženým v tabulce filtrů, je nutné přidružit tabulku filtrů ke koncovým bodům služby pomocí chování směrování. Následující příklad ukazuje přidruženou "filterTable1" s koncovým bodem služby.  
  
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
 Dynamickou konfiguraci služby Směrování lze provést pouze <xref:System.ServiceModel.Routing.RoutingConfiguration> v <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> kódu vytvořením nového a nahrazením aktuální konfigurace.  V tomto příkladu je služba směrování hostována samostatně v rámci konzolové aplikace. Po spuštění aplikace můžete upravit konfiguraci směrování zadáním "regular" nebo 'rounding' v okně konzoly a nakonfigurovat cílový koncový bod, do kterého jsou zprávy směrovány; regularCalc při zadání "regular", jinak zaokrouhlováníCalc při zadání "zaokrouhlení".  
  
1. Pro podporu služby směrování je nutné přidat následující příkazy using.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. Následující kód se používá k samohostování služby Směrování jako konzolové aplikace. Tím se inicializuje služba směrování pomocí konfigurace popsané v předchozím kroku, která je obsažena v konfiguračním souboru aplikace. Smyčka while obsahuje kód použitý ke změně konfigurace směrování.  
  
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
  
3. Chcete-li dynamicky aktualizovat konfiguraci směrování, je nutné vytvořit novou konfiguraci směrování. To musí obsahovat všechny koncové body, filtry a tabulky filtrů, které jsou požadovány pro novou konfiguraci směrování, protože zcela nahradí stávající konfiguraci směrování. Chcete-li použít novou konfiguraci směrování, musíte vyvolat <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> a předat novou konfiguraci.  
  
     Přidejte následující kód do smyčky while definované dříve, aby bylo možné službu překonfigurovat na základě vstupu uživatele.  
  
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
    > Vzhledem k tomu, že metoda pro poskytování nové routingconfiguration je obsažena v rozšíření služby RoutingExtension, nové objekty RoutingConfiguration mohou být poskytnuty kdekoli v modelu rozšiřitelnosti WCF, který má nebo může získat odkaz na ServiceHost nebo ServiceExtensions (například v jiném ServiceExtension).
  
## <a name="example"></a>Příklad  

Následuje úplný seznam konzolové aplikace použité v tomto příkladu:
  
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
  
## <a name="example"></a>Příklad  

Následuje úplný seznam konfiguračního souboru použitého v tomto příkladu:
  
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

- [Směrovací služby](../samples/routing-services.md)
