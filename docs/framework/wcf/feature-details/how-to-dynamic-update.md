---
title: 'Postupy: Dynamická aktualizace'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: 0a103e980d0d1be08f3ae6850c6af64405582c7b
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972079"
---
# <a name="how-to-dynamic-update"></a>Postupy: Dynamická aktualizace
Toto téma popisuje základní kroky potřebné k vytvoření a dynamické aktualizaci konfigurace směrování. V tomto příkladu se konfigurace počátečního směrování získá z konfiguračního souboru a směruje všechny zprávy do služby regularCalc kalkulačky. je ale následně Aktualizováno programově, aby se změnil cílový koncový bod služby roundingCalc.  
  
> [!NOTE]
> V mnoha implementacích bude konfigurace plně dynamická a nebude se spoléhat na výchozí konfiguraci. Existují však některé scénáře, jako je například v tomto tématu, kde je žádoucí mít výchozí stav konfigurace při spuštění služby.  
  
> [!NOTE]
> Dynamické aktualizace se vyskytují pouze v paměti a nevedou k úpravě konfiguračních souborů.  
  
 RegularCalc i roundingCalc podporují stejné operace sčítání, odčítání, násobení a dělení; roundingCalc však Zaokrouhlí všechny výpočty na nejbližší celočíselnou hodnotu před vrácením. Konfigurační soubor se používá ke konfiguraci služby ke směrování všech zpráv do služby regularCalc. Po spuštění směrovací služby se služba znovu nakonfiguruje tak, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> aby směrovala zprávy do služby roundingCalc.  
  
### <a name="implement-initial-configuration"></a>Implementace počáteční konfigurace  
  
1. Vytvořte základní konfiguraci směrovací služby zadáním koncových bodů služby vystavených službou. Následující příklad definuje jeden koncový bod služby, který se použije pro příjem zpráv. Definuje také koncový bod klienta, který bude použit k posílání zpráv do regularCalc.  
  
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
  
2. Definujte filtr, který se použije ke směrování zpráv do cílových koncových bodů. V tomto příkladu se používá filtr MatchAll ke směrování všech zpráv do regularCalcEndpoint, které jste definovali dříve. Následující příklad definuje tabulku filtru a filtru.  
  
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
  
3. Chcete-li vyhodnotit příchozí zprávy proti filtrům obsaženým v tabulce filtru, je nutné přidružit tabulku filtru k koncovým bodům služby pomocí chování směrování. Následující příklad znázorňuje přidružení "filterTable1" ke koncovému bodu služby.  
  
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
  
## <a name="implement-dynamic-configuration"></a>Implementovat dynamickou konfiguraci  
 Dynamickou konfiguraci směrovací služby lze provést pouze v kódu vytvořením nového <xref:System.ServiceModel.Routing.RoutingConfiguration> a použitím <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> k nahrazení aktuální konfigurace.  V tomto příkladu je směrovací služba samoobslužně hostována v rámci konzolové aplikace. Po spuštění aplikace můžete změnit konfiguraci směrování zadáním "normálního" nebo "zaokrouhlení" v okně konzoly ke konfiguraci cílového koncového bodu, na který jsou zprávy směrovány. regularCalc při zadání ' Regular ', jinak roundingCalc při zadání ' zaokrouhlení '.  
  
1. Aby bylo možné podporovat směrovací službu, je nutné přidat následující příkazy using.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. Následující kód slouží k samoobslužnému hostování směrovací služby jako konzolové aplikace. Tím inicializujete směrovací službu pomocí konfigurace popsané v předchozím kroku, který je obsažen v konfiguračním souboru aplikace. Smyčka while obsahuje kód používaný ke změně konfigurace směrování.  
  
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
  
3. Chcete-li dynamicky aktualizovat konfiguraci směrování, je nutné vytvořit novou konfiguraci směrování. Tato akce musí obsahovat všechny koncové body, filtry a tabulky filtru, které jsou požadovány pro novou konfiguraci směrování, protože zcela nahradí stávající konfiguraci směrování. Aby bylo možné použít novou konfiguraci směrování, je nutné vyvolat <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> novou konfiguraci a předat ji.  
  
     Do dříve definované smyčky while přidejte následující kód, který umožní překonfigurovat službu na základě vstupu uživatele.  
  
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
    > Vzhledem k tomu, že metoda pro poskytování nového konfigurace RoutingConfiguration je obsažena v rozšíření služby RoutingExtension, mohou být nové objekty konfigurace RoutingConfiguration poskytnuty kdekoli v modelu rozšiřitelnosti WCF, který má nebo může získat odkaz na třídu ServiceHost nebo ServiceExtensions (například v jiném ServiceExtension).
  
## <a name="example"></a>Příklad  
 Následuje úplný seznam konzolové aplikace použité v tomto příkladu.  
  
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
 Následuje úplný seznam konfiguračního souboru použitého v tomto příkladu.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Směrovací služby](../../../../docs/framework/wcf/samples/routing-services.md)
