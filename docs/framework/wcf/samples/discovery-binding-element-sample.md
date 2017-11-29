---
title: "Zjišťování – ukázka prvky vazby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 821f629a7f39869975af19c793fe26188a40d7d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="discovery-binding-element-sample"></a><span data-ttu-id="40636-102">Zjišťování – ukázka prvky vazby</span><span class="sxs-lookup"><span data-stu-id="40636-102">Discovery Binding Element Sample</span></span>
<span data-ttu-id="40636-103">Tento příklad znázorňuje způsob použití prvku vazby klienta zjišťování pro zjišťování služby.</span><span class="sxs-lookup"><span data-stu-id="40636-103">This sample demonstrates how to use the discovery client binding element to discover a service.</span></span> <span data-ttu-id="40636-104">Tato funkce umožňuje vývojářům přidat kanálem klienta zjišťování do své existující zásobníku kanálu klienta provedení programovací model velmi intuitivní.</span><span class="sxs-lookup"><span data-stu-id="40636-104">This feature enables developers to add a discovery client channel to their existing client channel stack, making the programming model very intuitive.</span></span> <span data-ttu-id="40636-105">Po otevření přiřazený kanál adresu služby, se vyřeší, pomocí zjišťování.</span><span class="sxs-lookup"><span data-stu-id="40636-105">When the associated channel is opened, the address of the service is resolved using discovery.</span></span> <span data-ttu-id="40636-106">Tato ukázka se skládá z následujících projektech:</span><span class="sxs-lookup"><span data-stu-id="40636-106">This sample consists of the following projects:</span></span>  
  
-   <span data-ttu-id="40636-107">**CalculatorService**: zjistitelný [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="40636-107">**CalculatorService**: A discoverable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
-   <span data-ttu-id="40636-108">**CalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientské aplikace, která se používá k hledání a volání CalculatorService kanálem klienta zjišťování.</span><span class="sxs-lookup"><span data-stu-id="40636-108">**CalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery client channel to search for and call the CalculatorService.</span></span>  
  
-   <span data-ttu-id="40636-109">**DynamicCalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientské aplikace, která používá k hledání a volání CalculatorService dynamické koncový bod.</span><span class="sxs-lookup"><span data-stu-id="40636-109">**DynamicCalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses a dynamic endpoint to search for and call the CalculatorService.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="40636-110">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="40636-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="40636-111">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="40636-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="40636-112">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="40636-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="40636-113">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="40636-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a><span data-ttu-id="40636-114">CalculatorService</span><span class="sxs-lookup"><span data-stu-id="40636-114">CalculatorService</span></span>  
 <span data-ttu-id="40636-115">Tento projekt obsahuje jednoduché kalkulačky služba, která implementuje `ICalculatorService` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="40636-115">This project contains a simple calculator service that implements the `ICalculatorService` contract.</span></span>  
  
 <span data-ttu-id="40636-116">Následující soubor App.config se používá k přidání `<serviceDiscovery>` chování v chování služby a také koncový bod zjišťování.</span><span class="sxs-lookup"><span data-stu-id="40636-116">The following App.config file is used to add a `<serviceDiscovery>` behavior in the service behaviors as well as the discovery endpoint.</span></span>  
  
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
  
 <span data-ttu-id="40636-117">Díky tomu je služba a její koncové body zjistitelný.</span><span class="sxs-lookup"><span data-stu-id="40636-117">This makes the service and its endpoints discoverable.</span></span> <span data-ttu-id="40636-118">CalculatorService je služba s vlastním hostováním přidá jeden koncový bod pomocí NetTcpBinding vazby.</span><span class="sxs-lookup"><span data-stu-id="40636-118">The CalculatorService is a self-hosted service that adds one endpoint using the NetTcpBinding binding.</span></span> <span data-ttu-id="40636-119">Dojde také `EndpointDiscoveryBehavior` ke koncovému bodu a určuje obor, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="40636-119">It also adds an `EndpointDiscoveryBehavior` to the endpoint and specifies a scope as shown in the following code.</span></span>  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a><span data-ttu-id="40636-120">CalculatorClient</span><span class="sxs-lookup"><span data-stu-id="40636-120">CalculatorClient</span></span>  
 <span data-ttu-id="40636-121">Tento projekt obsahuje implementace klienta, který odesílá zprávy CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="40636-121">This project contains a client implementation that sends messages to the CalculatorService.</span></span> <span data-ttu-id="40636-122">Tento program používá `CreateCustomBindingWithDiscoveryElement()` metodu pro vytvoření vlastní vazby, který používá kanálem klienta zjišťování.</span><span class="sxs-lookup"><span data-stu-id="40636-122">This program uses the `CreateCustomBindingWithDiscoveryElement()` method to create a custom binding that uses the Discovery Client Channel.</span></span>  
  
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
  
 <span data-ttu-id="40636-123">Po <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> je vytvořena instance, vývojář určuje kritéria pro hledání pro službu.</span><span class="sxs-lookup"><span data-stu-id="40636-123">After the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is instantiated, the developer specifies the criteria to use when searching for a service.</span></span> <span data-ttu-id="40636-124">V takovém případě je kritérium hledání zjišťování `ICalculatorService` typu.</span><span class="sxs-lookup"><span data-stu-id="40636-124">In this case, the discovery find criterion is the `ICalculatorService` type.</span></span> <span data-ttu-id="40636-125">Kromě toho určuje vývojář <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> která vrací <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> který určuje, kde má být vyhledán služeb.</span><span class="sxs-lookup"><span data-stu-id="40636-125">Additionally, the developer specifies a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> which returns a <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> that specifies where to look for the services.</span></span> <span data-ttu-id="40636-126"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> Vrátí novou <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.</span><span class="sxs-lookup"><span data-stu-id="40636-126">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> returns a new <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="40636-127">[Použití vlastní vazby s kanálem klienta zjišťování](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span><span class="sxs-lookup"><span data-stu-id="40636-127"> [Using a Custom Binding with the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span></span>  
  
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
  
 <span data-ttu-id="40636-128">V tomto případě klient používá port UDP vícesměrového vysílání mechanismus definované protokol Discovery k vyhledání služeb v místní podsíti.</span><span class="sxs-lookup"><span data-stu-id="40636-128">In this case, the client uses the UDP multicast mechanism defined by the Discovery protocol to search for services on the local subnet.</span></span> <span data-ttu-id="40636-129">Zbývající část metoda vytvoří vlastní vazby a vloží prvku vazby zjišťování v horní části zásobníku.</span><span class="sxs-lookup"><span data-stu-id="40636-129">The remainder of the method creates a custom binding and inserts the Discovery binding element at the top of the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40636-130"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Musí být umístěny v horní části zásobníku vazby.</span><span class="sxs-lookup"><span data-stu-id="40636-130">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must be placed on the top of the binding stack.</span></span> <span data-ttu-id="40636-131">Všechny <xref:System.ServiceModel.Channels.BindingElement> na <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> musíte zajistit, aby že kanálu nebo kanálu vytvoří nepoužívá `EndpointAddress` nebo `Via` vlastnosti, protože skutečná adresa nachází pouze v kanálem klienta zjišťování.</span><span class="sxs-lookup"><span data-stu-id="40636-131">Any <xref:System.ServiceModel.Channels.BindingElement> on top of <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must make sure that the channel factory or channel it creates does not use the `EndpointAddress` or `Via` properties, because the actual address is found only at the Discovery client channel.</span></span>  
  
 <span data-ttu-id="40636-132">Dále `CalculatorClient` může být vytvořena instance předáním ve tento vlastní vazby a také adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="40636-132">Next, the `CalculatorClient` can be instantiated by passing in this custom binding as well as an endpoint address.</span></span>  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 <span data-ttu-id="40636-133">Při použití kanálem klienta zjišťování, zadaná adresa koncového bodu konstantní dříve je předána.</span><span class="sxs-lookup"><span data-stu-id="40636-133">When using the Discovery Client Channel, the constant endpoint address specified previously is passed in.</span></span> <span data-ttu-id="40636-134">V době běhu teď kanálem klienta zjišťování vyhledá službu určeného kritéria hledání a se k němu připojuje.</span><span class="sxs-lookup"><span data-stu-id="40636-134">Now at runtime, the Discovery Client Channel finds the service specified by the find criteria and connects to it.</span></span> <span data-ttu-id="40636-135">Pro tuto službu a klienta, který má být navázáno připojení musí mít také stejnou základní vazby zásobníku.</span><span class="sxs-lookup"><span data-stu-id="40636-135">For the service and the client to establish a connection, they must also have the same underlying binding stack.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="40636-136">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="40636-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="40636-137">Otevřete řešení v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40636-137">Open the solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="40636-138">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="40636-138">Build the solution.</span></span>  
  
3.  <span data-ttu-id="40636-139">Spusťte aplikaci služby a každý z klienta aplikace.</span><span class="sxs-lookup"><span data-stu-id="40636-139">Run the service application and each of the client applications.</span></span>  
  
4.  <span data-ttu-id="40636-140">Sledujte, aby bylo možné najít službu, aniž by věděly, jeho adresu klienta.</span><span class="sxs-lookup"><span data-stu-id="40636-140">Observe that the client was able to find the service without knowing its address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40636-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="40636-141">See Also</span></span>
