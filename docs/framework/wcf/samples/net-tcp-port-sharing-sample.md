---
title: Ukázka služby Net.TCP Port Sharing
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: ac90a50c6fe06a643881da2889fdea308404508e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144289"
---
# <a name="nettcp-port-sharing-sample"></a><span data-ttu-id="03ba3-102">Ukázka služby Net.TCP Port Sharing</span><span class="sxs-lookup"><span data-stu-id="03ba3-102">Net.TCP Port Sharing Sample</span></span>
<span data-ttu-id="03ba3-103">Protokol TCP/IP používá 16bitové číslo nazývané port k rozlišení připojení k více síťovým aplikacím spuštěným ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="03ba3-103">The TCP/IP protocol uses a 16-bit number, called a port, to differentiate connections to multiple network applications running on the same machine.</span></span> <span data-ttu-id="03ba3-104">Pokud aplikace naslouchá na portu, přejde do ní veškerý přenos TCP pro tento port.</span><span class="sxs-lookup"><span data-stu-id="03ba3-104">If an application is listening on a port, then all TCP traffic for that port goes to that application.</span></span> <span data-ttu-id="03ba3-105">Jiné aplikace nemohou poslouchat na tomto portu současně.</span><span class="sxs-lookup"><span data-stu-id="03ba3-105">Other applications cannot listen on that port at the same time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="03ba3-106">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="03ba3-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="03ba3-107">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="03ba3-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="03ba3-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="03ba3-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="03ba3-109">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="03ba3-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 <span data-ttu-id="03ba3-110">Mnoho protokolů má standardní nebo výchozí číslo portu, které používají.</span><span class="sxs-lookup"><span data-stu-id="03ba3-110">Many protocols have a standard or default port number that they use.</span></span> <span data-ttu-id="03ba3-111">Protokol HTTP například obvykle používá port TCP 80.</span><span class="sxs-lookup"><span data-stu-id="03ba3-111">For example, the HTTP protocol typically uses TCP port 80.</span></span> <span data-ttu-id="03ba3-112">Internetová informační služba (IIS) má naslouchací proces pro sdílení portu mezi více aplikacemi HTTP.</span><span class="sxs-lookup"><span data-stu-id="03ba3-112">Internet Information Services (IIS) has a listener to share a port between multiple HTTP applications.</span></span> <span data-ttu-id="03ba3-113">Služba IIS naslouchá přímo na portu a předává zprávy příslušné aplikaci na základě informací uvnitř datového proudu zpráv.</span><span class="sxs-lookup"><span data-stu-id="03ba3-113">IIS listens on the port directly and forwards messages to the appropriate application based on information inside the message stream.</span></span> <span data-ttu-id="03ba3-114">To umožňuje více aplikací http používat stejné číslo portu bez nutnosti soutěžit rezervovat port pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="03ba3-114">This allows multiple HTTP applications to use the same port number without having to compete to reserve the port for receiving messages.</span></span>  
  
 <span data-ttu-id="03ba3-115">NetTcp Port Sharing je funkce WCF (Windows Communication Foundation), která podobně umožňuje více síťovým aplikacím sdílet jeden port.</span><span class="sxs-lookup"><span data-stu-id="03ba3-115">NetTcp Port Sharing is a Windows Communication Foundation (WCF)feature that similarly allows multiple network applications to share a single port.</span></span> <span data-ttu-id="03ba3-116">Služba NetTcp Port Sharing Service přijímá připojení pomocí protokolu net.tcp a předává zprávy na základě cílové adresy.</span><span class="sxs-lookup"><span data-stu-id="03ba3-116">The NetTcp Port Sharing Service accepts connections using the net.tcp protocol and forwards messages based on their destination address.</span></span>  
  
 <span data-ttu-id="03ba3-117">Služba sdílení portů NetTcp není ve výchozím nastavení povolena.</span><span class="sxs-lookup"><span data-stu-id="03ba3-117">The NetTcp Port Sharing Service is not enabled by default.</span></span> <span data-ttu-id="03ba3-118">Před spuštěním této ukázky je nutné službu povolit ručně.</span><span class="sxs-lookup"><span data-stu-id="03ba3-118">Before running this sample, you must manually enable the service.</span></span> <span data-ttu-id="03ba3-119">Další informace naleznete v [tématu How to: Enable the Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="03ba3-119">For more information, see [How to: Enable the Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span></span> <span data-ttu-id="03ba3-120">Pokud je služba zakázána, je při spuštění serverové aplikace vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="03ba3-120">If the service is disabled, an exception is thrown when the server application is started.</span></span>  
  
```console
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 <span data-ttu-id="03ba3-121">Sdílení portů je povoleno na <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> serveru <xref:System.ServiceModel.NetTcpBinding> nastavením <xref:System.ServiceModel.Channels.TcpTransportBindingElement> vlastnosti vazby nebo prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="03ba3-121">Port sharing is enabled on the server by setting the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property of the <xref:System.ServiceModel.NetTcpBinding> binding or the <xref:System.ServiceModel.Channels.TcpTransportBindingElement> binding element.</span></span> <span data-ttu-id="03ba3-122">Klient nemusí vědět, jak bylo sdílení portů nakonfigurováno pro jeho použití na serveru.</span><span class="sxs-lookup"><span data-stu-id="03ba3-122">The client does not have to know how port sharing has been configured to use it on the server.</span></span>  
  
## <a name="enabling-port-sharing"></a><span data-ttu-id="03ba3-123">Povolení sdílení portů</span><span class="sxs-lookup"><span data-stu-id="03ba3-123">Enabling Port Sharing</span></span>  
 <span data-ttu-id="03ba3-124">Následující kód ukazuje povolení sdílení portů na serveru.</span><span class="sxs-lookup"><span data-stu-id="03ba3-124">The following code demonstrates enabling port sharing on the server.</span></span> <span data-ttu-id="03ba3-125">Spustí instanci `ICalculator` služby na pevném portu s náhodnou cestou IDENTIFIKÁTORURI.</span><span class="sxs-lookup"><span data-stu-id="03ba3-125">It starts an instance of the `ICalculator` service on a fixed port with a random URI path.</span></span> <span data-ttu-id="03ba3-126">Přestože dvě služby mohou sdílet stejný port, jejich celkové adresy koncového bodu musí být stále jedinečné, aby služba sdílení portů NetTcp mohla směrovat zprávy do správné aplikace.</span><span class="sxs-lookup"><span data-stu-id="03ba3-126">Even though two services can share the same port, their overall endpoint addresses still must be unique so that the NetTcp Port Sharing Service can route messages to the correct application.</span></span>  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address = $"net.tcp://localhost:9000/calculator/{salt}";
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 <span data-ttu-id="03ba3-127">Pokud je povoleno sdílení portů, můžete službu spustit vícekrát, aniž byste měli konflikt nad číslem portu.</span><span class="sxs-lookup"><span data-stu-id="03ba3-127">With port sharing enabled, you can run the service multiple times without having a conflict over the port number.</span></span> <span data-ttu-id="03ba3-128">Pokud změníte kód zakázat sdílení portů, spuštění dvou kopií služby <xref:System.ServiceModel.AddressAlreadyInUseException>má za následek druhé selhání s .</span><span class="sxs-lookup"><span data-stu-id="03ba3-128">If you change the code to disable port sharing, starting up two copies of the service results in the second failing with an <xref:System.ServiceModel.AddressAlreadyInUseException>.</span></span>  
  
```console  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="03ba3-129">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="03ba3-129">Running the Sample</span></span>  
 <span data-ttu-id="03ba3-130">Testovací ho klienta můžete použít ke kontrole, zda jsou zprávy správně směrovány do služeb sdílejících port.</span><span class="sxs-lookup"><span data-stu-id="03ba3-130">You can use the test client to check that messages are correctly routed to services sharing the port.</span></span>  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = $"net.tcp://localhost:9000/calculator/{salt}";
      ChannelFactory<ICalculator> factory = new ChannelFactory<ICalculator>(new NetTcpBinding());  
      ICalculator proxy = factory.CreateChannel(new EndpointAddress(address));  
  
      // Call the Add service operation.  
      double value1 = 100.00D;  
      double value2 = 15.99D;  
      double result = proxy.Add(value1, value2);  
      Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Subtract service operation.  
      value1 = 145.00D;  
      value2 = 76.54D;  
      result = proxy.Subtract(value1, value2);  
      Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Multiply service operation.  
      value1 = 9.00D;  
      value2 = 81.25D;  
      result = proxy.Multiply(value1, value2);  
      Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Divide service operation.  
      value1 = 22.00D;  
      value2 = 7.00D;  
      result = proxy.Divide(value1, value2);  
      Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
      Console.WriteLine();  
      Console.WriteLine("Press <ENTER> to terminate client.");  
      Console.ReadLine();  
  
      factory.Close();  
   }  
}  
```

 <span data-ttu-id="03ba3-131">Každá instance služby vytiskne své jedinečné číslo a adresu.</span><span class="sxs-lookup"><span data-stu-id="03ba3-131">Each instance of the service prints out its unique number and address.</span></span> <span data-ttu-id="03ba3-132">Například se může zobrazit následující text při spuštění service.exe.</span><span class="sxs-lookup"><span data-stu-id="03ba3-132">For instance, you may see the following text when you run service.exe.</span></span>  
  
```console  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="03ba3-133">Zadejte číslo služby, které se zde zobrazí při spuštění souboru client.exe.</span><span class="sxs-lookup"><span data-stu-id="03ba3-133">Enter the service number you see here when you run client.exe.</span></span>  
  
```console  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="03ba3-134">Tuto ukázku lze spustit v konfiguraci mezi počítači změnou generované adresy, kterou klient používá.</span><span class="sxs-lookup"><span data-stu-id="03ba3-134">This sample can be run in a cross-machine configuration by changing the generated address that the client uses.</span></span> <span data-ttu-id="03ba3-135">V Client.cs změňte formátovací řetězec adresy koncového bodu tak, aby odpovídal nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="03ba3-135">In the Client.cs, change the endpoint address format string to match the new address of your service.</span></span> <span data-ttu-id="03ba3-136">Nahraďte všechny odkazy na "localhost" IP adresou serverového počítače.</span><span class="sxs-lookup"><span data-stu-id="03ba3-136">Replace any references to "localhost" with the IP address of the server machine.</span></span> <span data-ttu-id="03ba3-137">Po provedení této změny je nutné znovu zkompilovat ukázku.</span><span class="sxs-lookup"><span data-stu-id="03ba3-137">You must recompile the sample after making this change.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="03ba3-138">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="03ba3-138">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="03ba3-139">Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="03ba3-139">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="03ba3-140">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="03ba3-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="03ba3-141">Povolte službu sdílení portů NetTcp, jak je popsáno dříve v úvodní části.</span><span class="sxs-lookup"><span data-stu-id="03ba3-141">Enable the NetTcp Port Sharing Service as previously described in the introduction section.</span></span>  
  
4. <span data-ttu-id="03ba3-142">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="03ba3-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="03ba3-143">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="03ba3-143">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="03ba3-144">Konkrétní podrobnosti pro spuštění této ukázky jsou zahrnuty dříve v spuštění ukázkové části.</span><span class="sxs-lookup"><span data-stu-id="03ba3-144">Specific details for running this sample are included previously in the Running the Sample section.</span></span>  
