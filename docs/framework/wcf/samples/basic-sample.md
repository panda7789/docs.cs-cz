---
title: Základní ukázka
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 67c626dfa511251043da81e025aab20578be3016
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502135"
---
# <a name="basic-sample"></a><span data-ttu-id="39ce0-102">Základní ukázka</span><span class="sxs-lookup"><span data-stu-id="39ce0-102">Basic Sample</span></span>
<span data-ttu-id="39ce0-103">Tento příklad ukazuje, jak zjistitelnost služby a jak k hledání a volání zjistitelný služby.</span><span class="sxs-lookup"><span data-stu-id="39ce0-103">This sample shows how to make a service discoverable and how to search for and call a discoverable service.</span></span> <span data-ttu-id="39ce0-104">Tato ukázka se skládá ze dvou projektů: klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="39ce0-104">This sample is composed of two projects: service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39ce0-105">Tato ukázka implementuje zjišťování v kódu.</span><span class="sxs-lookup"><span data-stu-id="39ce0-105">This sample implements discovery in code.</span></span>  <span data-ttu-id="39ce0-106">Příklad, který implementuje zjišťování v konfiguraci, najdete v části [konfigurace](../../../../docs/framework/wcf/samples/configuration-sample.md).</span><span class="sxs-lookup"><span data-stu-id="39ce0-106">For a sample that implements discovery in configuration, see [Configuration](../../../../docs/framework/wcf/samples/configuration-sample.md).</span></span>  
  
## <a name="service"></a><span data-ttu-id="39ce0-107">Služba</span><span class="sxs-lookup"><span data-stu-id="39ce0-107">Service</span></span>  
 <span data-ttu-id="39ce0-108">Toto je jednoduchá kalkulačky implementace služby.</span><span class="sxs-lookup"><span data-stu-id="39ce0-108">This is a simple calculator service implementation.</span></span> <span data-ttu-id="39ce0-109">Zjišťování související kód lze nalézt v `Main` kde <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> se přidá do hostitele služby a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> se přidá, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="39ce0-109">The discovery related code can be found in `Main` where a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is added to the service host and a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is added as shown in the following code.</span></span>  
  
```  
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
  
## <a name="client"></a><span data-ttu-id="39ce0-110">Klient</span><span class="sxs-lookup"><span data-stu-id="39ce0-110">Client</span></span>  
 <span data-ttu-id="39ce0-111">Klient použije <xref:System.ServiceModel.Discovery.DynamicEndpoint> najít službu.</span><span class="sxs-lookup"><span data-stu-id="39ce0-111">The client uses a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to locate the service.</span></span> <span data-ttu-id="39ce0-112"><xref:System.ServiceModel.Discovery.DynamicEndpoint>, Koncový bod standardní řeší koncový bod služby v případě, že klient je otevřen.</span><span class="sxs-lookup"><span data-stu-id="39ce0-112">The <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a standard endpoint, resolves the endpoint of the service when the client is opened.</span></span> <span data-ttu-id="39ce0-113">V takovém případě <xref:System.ServiceModel.Discovery.DynamicEndpoint> hledá služby založené na kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="39ce0-113">In this case, the <xref:System.ServiceModel.Discovery.DynamicEndpoint> looks for the service based on the service contract.</span></span> <span data-ttu-id="39ce0-114"><xref:System.ServiceModel.Discovery.DynamicEndpoint> Provádí hledání přes <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="39ce0-114">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> conducts the search over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> by default.</span></span> <span data-ttu-id="39ce0-115">Jakmile je možné vyhledat koncového bodu služby, klient připojí k této službě přes Zadaná vazba.</span><span class="sxs-lookup"><span data-stu-id="39ce0-115">Once it locates a service endpoint, the client connects to that service over the specified binding.</span></span>  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 <span data-ttu-id="39ce0-116">Definuje metodu s názvem klient `InvokeCalculatorService` používající <xref:System.ServiceModel.Discovery.DiscoveryClient> třídy pro vyhledání služeb.</span><span class="sxs-lookup"><span data-stu-id="39ce0-116">The client defines a method called `InvokeCalculatorService` that uses the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to search for services.</span></span> <span data-ttu-id="39ce0-117"><xref:System.ServiceModel.Discovery.DynamicEndpoint> Dědí z <xref:System.ServiceModel.Description.ServiceEndpoint>, takže může být předán `InvokeCalculatorService` metoda.</span><span class="sxs-lookup"><span data-stu-id="39ce0-117">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> inherits from <xref:System.ServiceModel.Description.ServiceEndpoint>, so it can be passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="39ce0-118">V příkladu se pak použije <xref:System.ServiceModel.Discovery.DynamicEndpoint> k vytvoření instance `CalculatorServiceClient` a volá různých operací službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="39ce0-118">The example then uses the <xref:System.ServiceModel.Discovery.DynamicEndpoint> to create an instance of `CalculatorServiceClient` and calls the various operations of the calculator service.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="39ce0-119">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="39ce0-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="39ce0-120">Tato ukázka používá koncových bodů protokolu HTTP a pokud chcete tuto ukázku spustit, musí být přidán správné seznamy ACL adresy URL.</span><span class="sxs-lookup"><span data-stu-id="39ce0-120">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="39ce0-121">Další informace najdete v tématu [konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).</span><span class="sxs-lookup"><span data-stu-id="39ce0-121">For more information, see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="39ce0-122">Spuštěním následujícího příkazu na zvýšená oprávnění měli přidat příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="39ce0-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="39ce0-123">Můžete nahradit domény a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, protože je.</span><span class="sxs-lookup"><span data-stu-id="39ce0-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="39ce0-124">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete Basic.sln a sestavit ukázku.</span><span class="sxs-lookup"><span data-stu-id="39ce0-124">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Basic.sln and build the sample.</span></span>  
  
3.  <span data-ttu-id="39ce0-125">Spusťte aplikaci service.exe.</span><span class="sxs-lookup"><span data-stu-id="39ce0-125">Run the service.exe application.</span></span>  
  
4.  <span data-ttu-id="39ce0-126">Po spuštění služby, spusťte client.exe.</span><span class="sxs-lookup"><span data-stu-id="39ce0-126">After the service has started, run the client.exe.</span></span>  
  
5.  <span data-ttu-id="39ce0-127">Sledujte, aby bylo možné najít službu, aniž by věděly, jeho adresu klienta.</span><span class="sxs-lookup"><span data-stu-id="39ce0-127">Observe that the client was able to find the service without knowing its address.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="39ce0-128">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="39ce0-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="39ce0-129">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="39ce0-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="39ce0-130">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="39ce0-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="39ce0-131">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="39ce0-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
  
## <a name="see-also"></a><span data-ttu-id="39ce0-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="39ce0-132">See Also</span></span>
