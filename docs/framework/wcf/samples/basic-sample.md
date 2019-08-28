---
title: Základní ukázka
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 07015c61ccab303d0fe38e65077d984ff40ce357
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045710"
---
# <a name="basic-sample"></a><span data-ttu-id="1b3a8-102">Základní ukázka</span><span class="sxs-lookup"><span data-stu-id="1b3a8-102">Basic Sample</span></span>

<span data-ttu-id="1b3a8-103">V této ukázce se dozvíte, jak nastavit službu jako zjistitelnou a jak hledat a volat zjistitelnou službu.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-103">This sample shows how to make a service discoverable and how to search for and call a discoverable service.</span></span> <span data-ttu-id="1b3a8-104">Tato ukázka se skládá ze dvou projektů: služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-104">This sample is composed of two projects: service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="1b3a8-105">Tato ukázka implementuje zjišťování v kódu.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-105">This sample implements discovery in code.</span></span>  <span data-ttu-id="1b3a8-106">Ukázku, která implementuje zjišťování v konfiguraci, najdete v tématu [Configuration](../../../../docs/framework/wcf/samples/configuration-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1b3a8-106">For a sample that implements discovery in configuration, see [Configuration](../../../../docs/framework/wcf/samples/configuration-sample.md).</span></span>

## <a name="service"></a><span data-ttu-id="1b3a8-107">Služba</span><span class="sxs-lookup"><span data-stu-id="1b3a8-107">Service</span></span>

<span data-ttu-id="1b3a8-108">Toto je jednoduchá implementace služby Kalkulačka.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-108">This is a simple calculator service implementation.</span></span> <span data-ttu-id="1b3a8-109">Kód související se zjišťováním lze nalézt v `Main` <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> umístění, kde je přidán do hostitele služby a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> je přidán, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-109">The discovery related code can be found in `Main` where a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is added to the service host and a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is added as shown in the following code.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new
      WSHttpBinding(), String.Empty);

    // Make the service discoverable over UDP multicast
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    serviceHost.Open();
    // ...
}
```

## <a name="client"></a><span data-ttu-id="1b3a8-110">Klient</span><span class="sxs-lookup"><span data-stu-id="1b3a8-110">Client</span></span>

<span data-ttu-id="1b3a8-111">Klient nástroje používá <xref:System.ServiceModel.Discovery.DynamicEndpoint> k vyhledání služby.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-111">The client uses a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to locate the service.</span></span> <span data-ttu-id="1b3a8-112"><xref:System.ServiceModel.Discovery.DynamicEndpoint>Standardní koncový bod při otevření klienta vyřeší koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-112">The <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a standard endpoint, resolves the endpoint of the service when the client is opened.</span></span> <span data-ttu-id="1b3a8-113">V takovém případě <xref:System.ServiceModel.Discovery.DynamicEndpoint> vyhledá službu na základě kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-113">In this case, the <xref:System.ServiceModel.Discovery.DynamicEndpoint> looks for the service based on the service contract.</span></span> <span data-ttu-id="1b3a8-114"><xref:System.ServiceModel.Discovery.DynamicEndpoint> Provádí hledání<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-114">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> conducts the search over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> by default.</span></span> <span data-ttu-id="1b3a8-115">Jakmile nalezne koncový bod služby, klient se k této službě připojí přes určenou vazbu.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-115">Once it locates a service endpoint, the client connects to that service over the specified binding.</span></span>

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

<span data-ttu-id="1b3a8-116">Klient definuje metodu s názvem `InvokeCalculatorService` , která <xref:System.ServiceModel.Discovery.DiscoveryClient> používá třídu pro hledání služeb.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-116">The client defines a method called `InvokeCalculatorService` that uses the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to search for services.</span></span> <span data-ttu-id="1b3a8-117">Dědí z <xref:System.ServiceModel.Description.ServiceEndpoint>, takže`InvokeCalculatorService` může být předán metodě. <xref:System.ServiceModel.Discovery.DynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="1b3a8-117">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> inherits from <xref:System.ServiceModel.Description.ServiceEndpoint>, so it can be passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="1b3a8-118">Příklad následně používá <xref:System.ServiceModel.Discovery.DynamicEndpoint> k vytvoření `CalculatorServiceClient` instance a volání různých operací služby kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-118">The example then uses the <xref:System.ServiceModel.Discovery.DynamicEndpoint> to create an instance of `CalculatorServiceClient` and calls the various operations of the calculator service.</span></span>

```csharp
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)
{
   // Create a client
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);

   Console.WriteLine("Invoking CalculatorService");
   Console.WriteLine();

   double value1 = 100.00D;
   double value2 = 15.99D;

   // Call the Add service operation.
   double result = client.Add(value1, value2);
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

   // Call the Subtract service operation.
   result = client.Subtract(value1, value2);
   Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

   // Call the Multiply service operation.
   result = client.Multiply(value1, value2);
   Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

   // Call the Divide service operation.
   result = client.Divide(value1, value2);
   Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
   Console.WriteLine();

   //Closing the client gracefully closes the connection and cleans up resources
   client.Close();
}
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="1b3a8-119">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="1b3a8-119">To use this sample</span></span>

1. <span data-ttu-id="1b3a8-120">Tato ukázka používá koncové body HTTP a ke spuštění této ukázky musí být přidány správné seznamy ACL adres URL.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-120">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="1b3a8-121">Další informace najdete v tématu [Konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353).</span><span class="sxs-lookup"><span data-stu-id="1b3a8-121">For more information, see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="1b3a8-122">Spuštění následujícího příkazu u zvýšeného oprávnění by mělo přidat příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="1b3a8-123">Pokud příkaz nefunguje tak, jak je, je vhodné nahradit doménu a uživatelské jméno pro následující argumenty.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="1b3a8-124">Pomocí sady Visual Studio 2012 otevřete základní. sln a sestavte ukázku.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-124">Using Visual Studio 2012, open the Basic.sln and build the sample.</span></span>

3. <span data-ttu-id="1b3a8-125">Spusťte aplikaci Service. exe.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-125">Run the service.exe application.</span></span>

4. <span data-ttu-id="1b3a8-126">Po spuštění služby spusťte soubor Client. exe.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-126">After the service has started, run the client.exe.</span></span>

5. <span data-ttu-id="1b3a8-127">Pozor, aby klient mohl najít službu bez znalosti její adresy.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-127">Observe that the client was able to find the service without knowing its address.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b3a8-128">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1b3a8-129">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-129">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="1b3a8-130">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1b3a8-131">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1b3a8-131">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`
