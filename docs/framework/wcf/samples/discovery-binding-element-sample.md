---
title: Zjišťování – ukázka prvky vazby
ms.date: 03/30/2017
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
ms.openlocfilehash: 853f5cebfd745b3413d605dcfbf0e395e103b4f1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805665"
---
# <a name="discovery-binding-element-sample"></a>Zjišťování – ukázka prvky vazby
Tento příklad znázorňuje způsob použití prvku vazby klienta zjišťování pro zjišťování služby. Tato funkce umožňuje vývojářům přidat kanálem klienta zjišťování do své existující zásobníku kanálu klienta provedení programovací model velmi intuitivní. Po otevření přiřazený kanál adresu služby, se vyřeší, pomocí zjišťování. Tato ukázka se skládá z následujících projektech:  
  
-   **CalculatorService**: zjistitelný služby WCF.  
  
-   **CalculatorClient**: A WCF klientské aplikace, která používá k hledání a volání CalculatorService kanálem klienta zjišťování.  
  
-   **DynamicCalculatorClient**: A WCF klientské aplikace, která používá k hledání a volání CalculatorService dynamické koncový bod.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a>CalculatorService  
 Tento projekt obsahuje jednoduché kalkulačky služba, která implementuje `ICalculatorService` kontrakt.  
  
 Následující soubor App.config se používá k přidání `<serviceDiscovery>` chování v chování služby a také koncový bod zjišťování.  
  
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
  
 Díky tomu je služba a její koncové body zjistitelný. CalculatorService je služba s vlastním hostováním přidá jeden koncový bod pomocí NetTcpBinding vazby. Dojde také `EndpointDiscoveryBehavior` ke koncovému bodu a určuje obor, jak je znázorněno v následujícím kódu.  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a>CalculatorClient  
 Tento projekt obsahuje implementace klienta, který odesílá zprávy CalculatorService. Tento program používá `CreateCustomBindingWithDiscoveryElement()` metodu pro vytvoření vlastní vazby, který používá kanálem klienta zjišťování.  
  
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
  
 Po <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> je vytvořena instance, vývojář určuje kritéria pro hledání pro službu. V takovém případě je kritérium hledání zjišťování `ICalculatorService` typu. Kromě toho určuje vývojář <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> která vrací <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> který určuje, kde má být vyhledán služeb. <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Vrátí novou <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance. Další informace najdete v tématu [použití vlastní vazby s kanálem klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).  
  
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
  
 V tomto případě klient používá port UDP vícesměrového vysílání mechanismus definované protokol Discovery k vyhledání služeb v místní podsíti. Zbývající část metoda vytvoří vlastní vazby a vloží prvku vazby zjišťování v horní části zásobníku.  
  
> [!NOTE]
>  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Musí být umístěny v horní části zásobníku vazby. Všechny <xref:System.ServiceModel.Channels.BindingElement> na <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> musíte zajistit, aby že kanálu nebo kanálu vytvoří nepoužívá `EndpointAddress` nebo `Via` vlastnosti, protože skutečná adresa nachází pouze v kanálem klienta zjišťování.  
  
 Dále `CalculatorClient` může být vytvořena instance předáním ve tento vlastní vazby a také adresu koncového bodu.  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 Při použití kanálem klienta zjišťování, zadaná adresa koncového bodu konstantní dříve je předána. V době běhu teď kanálem klienta zjišťování vyhledá službu určeného kritéria hledání a se k němu připojuje. Pro tuto službu a klienta, který má být navázáno připojení musí mít také stejnou základní vazby zásobníku.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Sestavte řešení.  
  
3.  Spusťte aplikaci služby a každý z klienta aplikace.  
  
4.  Sledujte, aby bylo možné najít službu, aniž by věděly, jeho adresu klienta.  
  
## <a name="see-also"></a>Viz také
