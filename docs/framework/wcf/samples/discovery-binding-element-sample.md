---
title: Zjišťování – ukázka prvky vazby
ms.date: 03/30/2017
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
ms.openlocfilehash: d906d9a389c50095f2af5d52e3874c3e43199e68
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45514035"
---
# <a name="discovery-binding-element-sample"></a>Zjišťování – ukázka prvky vazby
Tento příklad znázorňuje způsob použití elementu vazby zjišťování klienta ke zjišťování služby. Tato funkce umožňuje vývojářům přidat do své existující zásobníku kanálu klienta vytváření velmi výsledkem je intuitivní programovací model kanálem klienta zjišťování. Po otevření kanálu přidružené adresu služby je duplicita se vyřešila pomocí zjišťování. Tento příklad se skládá z následující projekty:  
  
-   **CalculatorService**: zjistitelné služby WCF.  
  
-   **CalculatorClient**: A WCF klientská aplikace používající kanálu klienta zjišťování k vyhledání a volat CalculatorService.  
  
-   **DynamicCalculatorClient**: A WCF klientská aplikace, který používá k hledání a volat CalculatorService dynamické koncový bod.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a>CalculatorService  
 Tento projekt obsahuje jednoduchou kalkulačku služba, která implementuje `ICalculatorService` kontraktu.  
  
 Následující soubor App.config se používá k přidání `<serviceDiscovery>` chování v chování služby, stejně jako koncový bod zjišťování.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">  
        <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />  
      </service>  
    </services>  
    <behaviors>  
      <!--Enable discovery through configuration.-->  
      <serviceBehaviors>  
        <behavior name="CalculatorBehavior">  
          <serviceDiscovery>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 Díky službě a její koncové body zjistitelné. CalculatorService je služba v místním prostředí, která přidá jeden koncový bod pomocí vazby NetTcpBinding. Také přidá `EndpointDiscoveryBehavior` ke koncovému bodu a určuje obor, jak je znázorněno v následujícím kódu.  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a>CalculatorClient  
 Tento projekt obsahuje implementace klienta, která odesílá zprávy CalculatorService. Používá tento program `CreateCustomBindingWithDiscoveryElement()` metodu pro vytvoření vlastní vazby, která používá kanálu klienta zjišťování.  
  
```  
static CustomBinding CreateCustomBindingWithDiscoveryElement()  
 {  
      DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
            // Provide the search criteria and the endpoint over which the probe is sent  
            discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
            discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
            CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
            // Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
            // An exception is thrown if this binding element is not at the top  
            customBinding.Elements.Insert(0, discoveryBindingElement);  
  
            return customBinding; }  
```  
  
 Po <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> je vytvořena instance, vývojář určuje kritéria pro vyhledávání pro službu. V takovém případě je kritérium hledání zjišťování `ICalculatorService` typu. Kromě toho určuje vývojář <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> který vrátí hodnotu <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> , která určuje, kde hledat pro služby. <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Vrátí nový <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance. Další informace najdete v tématu [použití vlastní vazby s kanálem klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).  
  
```  
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
    // to the DiscoveryClientBindingElement. The Discovery ClientChannel   
    // uses this endpoint to send Probe message.  
    public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
    {  
        public override DiscoveryEndpoint GetDiscoveryEndpoint()  
        {  
            return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
        }  
    }  
```  
  
 V tomto případě klient používá port UDP vícesměrového vysílání mechanismus definované pomocí protokolu zjišťování k vyhledání služby v místní podsíti. Zbývající část metody vytvoří vlastní vazby a vloží elementu vazby zjišťování v horní části zásobníku.  
  
> [!NOTE]
>  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Musí být umístěn v horní části zásobníku vazby. Žádné <xref:System.ServiceModel.Channels.BindingElement> nad <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Ujistěte se, že objekt pro vytváření kanálů nebo kanál vytvoří nepoužívá `EndpointAddress` nebo `Via` vlastnosti, protože skutečná adresa se nachází pouze v kanálu klienta zjišťování.  
  
 Dále `CalculatorClient` dá vytvořit instance předáním této vlastní vazby, jakož i adresu koncového bodu.  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 Při použití kanálu klienta zjišťování, zadaná adresa konstantní koncový bod dříve je předáno. Za běhu, nyní kanálu klienta zjišťování vyhledá službu zadané pomocí kritérií hledání a se k němu připojuje. Pro službu a klienta k navázání připojení musí mít také stejný základní zásobníku vazby.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Sestavte řešení.  
  
3.  Spouštějte aplikace služby a každá klient aplikace.  
  
4.  Podívejte se, že byl klient nemůže najít službu bez znalosti jeho adresu.  
  
## <a name="see-also"></a>Viz také
