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
# <a name="discovery-binding-element-sample"></a><span data-ttu-id="6fb21-102">Zjišťování – ukázka prvky vazby</span><span class="sxs-lookup"><span data-stu-id="6fb21-102">Discovery Binding Element Sample</span></span>
<span data-ttu-id="6fb21-103">Tento příklad znázorňuje způsob použití elementu vazby zjišťování klienta ke zjišťování služby.</span><span class="sxs-lookup"><span data-stu-id="6fb21-103">This sample demonstrates how to use the discovery client binding element to discover a service.</span></span> <span data-ttu-id="6fb21-104">Tato funkce umožňuje vývojářům přidat do své existující zásobníku kanálu klienta vytváření velmi výsledkem je intuitivní programovací model kanálem klienta zjišťování.</span><span class="sxs-lookup"><span data-stu-id="6fb21-104">This feature enables developers to add a discovery client channel to their existing client channel stack, making the programming model very intuitive.</span></span> <span data-ttu-id="6fb21-105">Po otevření kanálu přidružené adresu služby je duplicita se vyřešila pomocí zjišťování.</span><span class="sxs-lookup"><span data-stu-id="6fb21-105">When the associated channel is opened, the address of the service is resolved using discovery.</span></span> <span data-ttu-id="6fb21-106">Tento příklad se skládá z následující projekty:</span><span class="sxs-lookup"><span data-stu-id="6fb21-106">This sample consists of the following projects:</span></span>  
  
-   <span data-ttu-id="6fb21-107">**CalculatorService**: zjistitelné služby WCF.</span><span class="sxs-lookup"><span data-stu-id="6fb21-107">**CalculatorService**: A discoverable WCF service.</span></span>  
  
-   <span data-ttu-id="6fb21-108">**CalculatorClient**: A WCF klientská aplikace používající kanálu klienta zjišťování k vyhledání a volat CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="6fb21-108">**CalculatorClient**: A WCF client application that uses the discovery client channel to search for and call the CalculatorService.</span></span>  
  
-   <span data-ttu-id="6fb21-109">**DynamicCalculatorClient**: A WCF klientská aplikace, který používá k hledání a volat CalculatorService dynamické koncový bod.</span><span class="sxs-lookup"><span data-stu-id="6fb21-109">**DynamicCalculatorClient**: A WCF client application that uses a dynamic endpoint to search for and call the CalculatorService.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6fb21-110">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="6fb21-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6fb21-111">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6fb21-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6fb21-112">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="6fb21-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6fb21-113">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6fb21-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a><span data-ttu-id="6fb21-114">CalculatorService</span><span class="sxs-lookup"><span data-stu-id="6fb21-114">CalculatorService</span></span>  
 <span data-ttu-id="6fb21-115">Tento projekt obsahuje jednoduchou kalkulačku služba, která implementuje `ICalculatorService` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="6fb21-115">This project contains a simple calculator service that implements the `ICalculatorService` contract.</span></span>  
  
 <span data-ttu-id="6fb21-116">Následující soubor App.config se používá k přidání `<serviceDiscovery>` chování v chování služby, stejně jako koncový bod zjišťování.</span><span class="sxs-lookup"><span data-stu-id="6fb21-116">The following App.config file is used to add a `<serviceDiscovery>` behavior in the service behaviors as well as the discovery endpoint.</span></span>  
  
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
  
 <span data-ttu-id="6fb21-117">Díky službě a její koncové body zjistitelné.</span><span class="sxs-lookup"><span data-stu-id="6fb21-117">This makes the service and its endpoints discoverable.</span></span> <span data-ttu-id="6fb21-118">CalculatorService je služba v místním prostředí, která přidá jeden koncový bod pomocí vazby NetTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="6fb21-118">The CalculatorService is a self-hosted service that adds one endpoint using the NetTcpBinding binding.</span></span> <span data-ttu-id="6fb21-119">Také přidá `EndpointDiscoveryBehavior` ke koncovému bodu a určuje obor, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6fb21-119">It also adds an `EndpointDiscoveryBehavior` to the endpoint and specifies a scope as shown in the following code.</span></span>  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a><span data-ttu-id="6fb21-120">CalculatorClient</span><span class="sxs-lookup"><span data-stu-id="6fb21-120">CalculatorClient</span></span>  
 <span data-ttu-id="6fb21-121">Tento projekt obsahuje implementace klienta, která odesílá zprávy CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="6fb21-121">This project contains a client implementation that sends messages to the CalculatorService.</span></span> <span data-ttu-id="6fb21-122">Používá tento program `CreateCustomBindingWithDiscoveryElement()` metodu pro vytvoření vlastní vazby, která používá kanálu klienta zjišťování.</span><span class="sxs-lookup"><span data-stu-id="6fb21-122">This program uses the `CreateCustomBindingWithDiscoveryElement()` method to create a custom binding that uses the Discovery Client Channel.</span></span>  
  
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
  
 <span data-ttu-id="6fb21-123">Po <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> je vytvořena instance, vývojář určuje kritéria pro vyhledávání pro službu.</span><span class="sxs-lookup"><span data-stu-id="6fb21-123">After the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is instantiated, the developer specifies the criteria to use when searching for a service.</span></span> <span data-ttu-id="6fb21-124">V takovém případě je kritérium hledání zjišťování `ICalculatorService` typu.</span><span class="sxs-lookup"><span data-stu-id="6fb21-124">In this case, the discovery find criterion is the `ICalculatorService` type.</span></span> <span data-ttu-id="6fb21-125">Kromě toho určuje vývojář <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> který vrátí hodnotu <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> , která určuje, kde hledat pro služby.</span><span class="sxs-lookup"><span data-stu-id="6fb21-125">Additionally, the developer specifies a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> which returns a <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> that specifies where to look for the services.</span></span> <span data-ttu-id="6fb21-126"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Vrátí nový <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.</span><span class="sxs-lookup"><span data-stu-id="6fb21-126">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> returns a new <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.</span></span> <span data-ttu-id="6fb21-127">Další informace najdete v tématu [použití vlastní vazby s kanálem klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="6fb21-127">For more information, see [Using a Custom Binding with the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span></span>  
  
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
  
 <span data-ttu-id="6fb21-128">V tomto případě klient používá port UDP vícesměrového vysílání mechanismus definované pomocí protokolu zjišťování k vyhledání služby v místní podsíti.</span><span class="sxs-lookup"><span data-stu-id="6fb21-128">In this case, the client uses the UDP multicast mechanism defined by the Discovery protocol to search for services on the local subnet.</span></span> <span data-ttu-id="6fb21-129">Zbývající část metody vytvoří vlastní vazby a vloží elementu vazby zjišťování v horní části zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6fb21-129">The remainder of the method creates a custom binding and inserts the Discovery binding element at the top of the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fb21-130"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Musí být umístěn v horní části zásobníku vazby.</span><span class="sxs-lookup"><span data-stu-id="6fb21-130">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must be placed on the top of the binding stack.</span></span> <span data-ttu-id="6fb21-131">Žádné <xref:System.ServiceModel.Channels.BindingElement> nad <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Ujistěte se, že objekt pro vytváření kanálů nebo kanál vytvoří nepoužívá `EndpointAddress` nebo `Via` vlastnosti, protože skutečná adresa se nachází pouze v kanálu klienta zjišťování.</span><span class="sxs-lookup"><span data-stu-id="6fb21-131">Any <xref:System.ServiceModel.Channels.BindingElement> on top of <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must make sure that the channel factory or channel it creates does not use the `EndpointAddress` or `Via` properties, because the actual address is found only at the Discovery client channel.</span></span>  
  
 <span data-ttu-id="6fb21-132">Dále `CalculatorClient` dá vytvořit instance předáním této vlastní vazby, jakož i adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="6fb21-132">Next, the `CalculatorClient` can be instantiated by passing in this custom binding as well as an endpoint address.</span></span>  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 <span data-ttu-id="6fb21-133">Při použití kanálu klienta zjišťování, zadaná adresa konstantní koncový bod dříve je předáno.</span><span class="sxs-lookup"><span data-stu-id="6fb21-133">When using the Discovery Client Channel, the constant endpoint address specified previously is passed in.</span></span> <span data-ttu-id="6fb21-134">Za běhu, nyní kanálu klienta zjišťování vyhledá službu zadané pomocí kritérií hledání a se k němu připojuje.</span><span class="sxs-lookup"><span data-stu-id="6fb21-134">Now at runtime, the Discovery Client Channel finds the service specified by the find criteria and connects to it.</span></span> <span data-ttu-id="6fb21-135">Pro službu a klienta k navázání připojení musí mít také stejný základní zásobníku vazby.</span><span class="sxs-lookup"><span data-stu-id="6fb21-135">For the service and the client to establish a connection, they must also have the same underlying binding stack.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6fb21-136">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="6fb21-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="6fb21-137">Otevřete řešení v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6fb21-137">Open the solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="6fb21-138">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="6fb21-138">Build the solution.</span></span>  
  
3.  <span data-ttu-id="6fb21-139">Spouštějte aplikace služby a každá klient aplikace.</span><span class="sxs-lookup"><span data-stu-id="6fb21-139">Run the service application and each of the client applications.</span></span>  
  
4.  <span data-ttu-id="6fb21-140">Podívejte se, že byl klient nemůže najít službu bez znalosti jeho adresu.</span><span class="sxs-lookup"><span data-stu-id="6fb21-140">Observe that the client was able to find the service without knowing its address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb21-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fb21-141">See Also</span></span>
