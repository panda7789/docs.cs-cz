---
title: 'Postupy: Dynamická aktualizace'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: 597a4f8776398769307214090a8b463981bc0d46
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2018
ms.locfileid: "48848137"
---
# <a name="how-to-dynamic-update"></a>Postupy: Dynamická aktualizace
Toto téma popisuje základní kroky potřebné k vytvoření a dynamicky aktualizovat konfiguraci směrování. V tomto příkladu počáteční konfigurace směrování se získávají z konfiguračního souboru a všechny zprávy směruje do službu kalkulačky regularCalc; ale to se následně aktualizuje prostřednictvím kódu programu Chcete-li změnit cílový koncový bod služby roundingCalc.  
  
> [!NOTE]
>  Mnoho implementací konfigurace budou plně dynamického a nebude Spolehněte se na výchozí konfiguraci. Existují však některé scénáře, jako je třeba v tomto tématu, kde je žádoucí mají výchozí stav konfigurace, když se služba spustí.  
  
> [!NOTE]
>  Dynamické aktualizace dochází pouze v paměti a není výsledkem úprav konfiguračních souborů.  
  
 RegularCalc a roundingCalc podporují stejné operace přidat, odečítání, násobení a dělení; ale roundingCalc Zaokrouhlí všechny výpočty na nejbližší celočíselnou hodnotu před vrácením. Konfigurační soubor se používá ke konfiguraci služby pro směrování zpráv do služby regularCalc. Po spuštění služby směrování <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> umožňuje změnit konfiguraci služby pro směrování zpráv služby roundingCalc.  
  
### <a name="implement-initial-configuration"></a>Implementace počáteční konfigurace  
  
1.  Vytvoření základní konfigurace služby směrování zadat koncové body služby určeného službou. Následující příklad definuje jedinou službou koncový bod, který se použije pro příjem zpráv. Definuje také koncový bod klienta, který se použije pro odesílání zpráv regularCalc.  
  
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
  
2.  Zadejte filtr používá pro směrování zpráv do cílové koncové body. V tomto příkladu je filtr MatchAll používá pro směrování zpráv do regularCalcEndpoint dříve definovali. Následující příklad definuje filtr a tabulce filtrů.  
  
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
  
3.  Vyhodnocování příchozích zpráv proti filtrů obsažených v tabulce filtrů, je třeba přidružit tabulky filtru koncových bodů služby pomocí směrování chování. Následující příklad ukazuje přiřazování "filterTable1" ke koncovému bodu služby.  
  
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
  
## <a name="implement-dynamic-configuration"></a>Implementovat dynamické konfigurace  
 Směrovací služba dynamickou konfiguraci lze provést pouze v kódu vytvořením nového <xref:System.ServiceModel.Routing.RoutingConfiguration> a pomocí <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> k nahrazení aktuální konfiguraci.  V tomto příkladu je služba Směrování v rámci konzolové aplikace v místním prostředí. Po spuštění aplikace, můžete upravit konfiguraci směrování tak, že zadáte "normální" nebo "zaokrouhlení" v okně konzoly ke konfiguraci cílového koncového bodu, který zprávy jsou směrovány na; Zadaný regularCalc při 'pravidelné', jinak se zadá roundingCalc při "zaokrouhlování".  
  
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
  
2.  Následující kód slouží k hostování na vlastním serveru služby směrování jako konzolové aplikace. To Inicializuje službu Směrování pomocí konfigurace popsaná v předchozím kroku, která je obsažena v konfiguračním souboru aplikace. While smyčka obsahuje kód použít ke změně konfigurace směrování.  
  
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
  
3.  Dynamicky aktualizovat konfiguraci směrování, je nutné vytvořit novou konfiguraci směrování. Všechny koncové body, filtry a filtru tabulky, které jsou požadovány pro novou konfiguraci směrování, to musí obsahovat jak zcela nahradit existující konfiguraci směrování. Chcete-li použít nové konfigurace směrování, je nutné vyvolat <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> a předejte mu novou konfiguraci.  
  
     Přidejte následující kód do while smyčky dříve definovali povolit službu třeba překonfigurovat na základě uživatelského zadání.  
  
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
    > Od metodou pro zajištění nová konfigurace RoutingConfiguration obsažené v rozšíření služby třída RoutingExtension, nová konfigurace RoutingConfiguration objekty lze zadat kdekoli v rozšiřitelném modelu WCF, nebo můžete získat odkaz na hostitele ServiceHost nebo ServiceExtensions (jako je například jiné ServiceExtension).
  
## <a name="example"></a>Příklad  
 Tady je úplný seznam všech Konzolová aplikace použitý v tomto příkladu.  
  
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
 Tady je úplný seznam všech konfiguraci souboru použitého v tomto příkladu.  
  
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
