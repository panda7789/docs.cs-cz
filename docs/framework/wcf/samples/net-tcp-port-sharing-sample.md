---
title: Ukázka služby Net.TCP Port Sharing
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: e7a814dcdc027980f70ec90e384f3ec2f74b364d
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714707"
---
# <a name="nettcp-port-sharing-sample"></a><span data-ttu-id="df5dc-102">Ukázka služby Net.TCP Port Sharing</span><span class="sxs-lookup"><span data-stu-id="df5dc-102">Net.TCP Port Sharing Sample</span></span>
<span data-ttu-id="df5dc-103">Protokol TCP/IP používá 16bitové číslo označované jako port pro odlišení připojení k více síťovým aplikacím běžícím ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="df5dc-103">The TCP/IP protocol uses a 16-bit number, called a port, to differentiate connections to multiple network applications running on the same machine.</span></span> <span data-ttu-id="df5dc-104">Pokud aplikace naslouchá na portu, pak všechny přenosy TCP pro daný port přecházejí do této aplikace.</span><span class="sxs-lookup"><span data-stu-id="df5dc-104">If an application is listening on a port, then all TCP traffic for that port goes to that application.</span></span> <span data-ttu-id="df5dc-105">Jiné aplikace nemohou na tomto portu současně naslouchat.</span><span class="sxs-lookup"><span data-stu-id="df5dc-105">Other applications cannot listen on that port at the same time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="df5dc-106">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="df5dc-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="df5dc-107">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="df5dc-107">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="df5dc-108">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="df5dc-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="df5dc-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="df5dc-109">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 <span data-ttu-id="df5dc-110">Mnoho protokolů má standardní nebo výchozí číslo portu, které používají.</span><span class="sxs-lookup"><span data-stu-id="df5dc-110">Many protocols have a standard or default port number that they use.</span></span> <span data-ttu-id="df5dc-111">Například protokol HTTP obvykle používá port TCP 80.</span><span class="sxs-lookup"><span data-stu-id="df5dc-111">For example, the HTTP protocol typically uses TCP port 80.</span></span> <span data-ttu-id="df5dc-112">Internetová informační služba (IIS) má naslouchací proces ke sdílení portu mezi více aplikacemi HTTP.</span><span class="sxs-lookup"><span data-stu-id="df5dc-112">Internet Information Services (IIS) has a listener to share a port between multiple HTTP applications.</span></span> <span data-ttu-id="df5dc-113">Služba IIS naslouchá přímo na portu a přesměruje zprávy do příslušné aplikace na základě informací uvnitř datového proudu zpráv.</span><span class="sxs-lookup"><span data-stu-id="df5dc-113">IIS listens on the port directly and forwards messages to the appropriate application based on information inside the message stream.</span></span> <span data-ttu-id="df5dc-114">To umožňuje více aplikacím HTTP používat stejné číslo portu, aniž by bylo nutné soutěžit o rezervaci portu pro příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="df5dc-114">This allows multiple HTTP applications to use the same port number without having to compete to reserve the port for receiving messages.</span></span>  
  
 <span data-ttu-id="df5dc-115">Sdílení portů NetTcp je funkce Windows Communication Foundation (WCF), která podobně umožňuje více síťovým aplikacím sdílet jeden port.</span><span class="sxs-lookup"><span data-stu-id="df5dc-115">NetTcp Port Sharing is a Windows Communication Foundation (WCF)feature that similarly allows multiple network applications to share a single port.</span></span> <span data-ttu-id="df5dc-116">Služba sdílení portů NetTcp akceptuje připojení pomocí protokolu net. TCP a přepošle zprávy na základě jejich cílové adresy.</span><span class="sxs-lookup"><span data-stu-id="df5dc-116">The NetTcp Port Sharing Service accepts connections using the net.tcp protocol and forwards messages based on their destination address.</span></span>  
  
 <span data-ttu-id="df5dc-117">Služba sdílení portů NetTcp není ve výchozím nastavení povolená.</span><span class="sxs-lookup"><span data-stu-id="df5dc-117">The NetTcp Port Sharing Service is not enabled by default.</span></span> <span data-ttu-id="df5dc-118">Před spuštěním této ukázky musíte ručně povolit službu.</span><span class="sxs-lookup"><span data-stu-id="df5dc-118">Before running this sample, you must manually enable the service.</span></span> <span data-ttu-id="df5dc-119">Další informace najdete v tématu [Postup: povolení služby sdílení portů Net. TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="df5dc-119">For more information, see [How to: Enable the Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span></span> <span data-ttu-id="df5dc-120">Pokud je služba zakázaná, vyvolá se při spuštění serverové aplikace výjimka.</span><span class="sxs-lookup"><span data-stu-id="df5dc-120">If the service is disabled, an exception is thrown when the server application is started.</span></span>  
  
```console
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 <span data-ttu-id="df5dc-121">Sdílení portů je na serveru povoleno nastavením vlastnosti <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> <xref:System.ServiceModel.NetTcpBinding> vazby nebo elementu vazby <xref:System.ServiceModel.Channels.TcpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="df5dc-121">Port sharing is enabled on the server by setting the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property of the <xref:System.ServiceModel.NetTcpBinding> binding or the <xref:System.ServiceModel.Channels.TcpTransportBindingElement> binding element.</span></span> <span data-ttu-id="df5dc-122">Klient nemusí znát způsob, jakým bylo sdílení portů nakonfigurováno pro jeho použití na serveru.</span><span class="sxs-lookup"><span data-stu-id="df5dc-122">The client does not have to know how port sharing has been configured to use it on the server.</span></span>  
  
## <a name="enabling-port-sharing"></a><span data-ttu-id="df5dc-123">Povolení sdílení portů</span><span class="sxs-lookup"><span data-stu-id="df5dc-123">Enabling Port Sharing</span></span>  
 <span data-ttu-id="df5dc-124">Následující kód ukazuje povolení sdílení portů na serveru.</span><span class="sxs-lookup"><span data-stu-id="df5dc-124">The following code demonstrates enabling port sharing on the server.</span></span> <span data-ttu-id="df5dc-125">Spustí instanci služby `ICalculator` na pevném portu s náhodným umístěním URI.</span><span class="sxs-lookup"><span data-stu-id="df5dc-125">It starts an instance of the `ICalculator` service on a fixed port with a random URI path.</span></span> <span data-ttu-id="df5dc-126">I když můžou dva služby sdílet stejný port, musí být jejich celkový koncový bod stále jedinečný, aby služba sdílení portů NetTcp mohla směrovat zprávy do správné aplikace.</span><span class="sxs-lookup"><span data-stu-id="df5dc-126">Even though two services can share the same port, their overall endpoint addresses still must be unique so that the NetTcp Port Sharing Service can route messages to the correct application.</span></span>  

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

 <span data-ttu-id="df5dc-127">Když je povolené sdílení portů, můžete službu spustit několikrát, aniž by došlo ke konfliktu s číslem portu.</span><span class="sxs-lookup"><span data-stu-id="df5dc-127">With port sharing enabled, you can run the service multiple times without having a conflict over the port number.</span></span> <span data-ttu-id="df5dc-128">Pokud změníte kód tak, aby se zakázalo sdílení portů, spuštění dvou kopií služby má za následek selhání s <xref:System.ServiceModel.AddressAlreadyInUseException>.</span><span class="sxs-lookup"><span data-stu-id="df5dc-128">If you change the code to disable port sharing, starting up two copies of the service results in the second failing with an <xref:System.ServiceModel.AddressAlreadyInUseException>.</span></span>  
  
```console  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="df5dc-129">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="df5dc-129">Running the Sample</span></span>  
 <span data-ttu-id="df5dc-130">Testovacího klienta můžete použít ke kontrole, zda jsou zprávy správně směrovány na služby sdílející daný port.</span><span class="sxs-lookup"><span data-stu-id="df5dc-130">You can use the test client to check that messages are correctly routed to services sharing the port.</span></span>  

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

 <span data-ttu-id="df5dc-131">Každá instance služby vytiskne své jedinečné číslo a adresu.</span><span class="sxs-lookup"><span data-stu-id="df5dc-131">Each instance of the service prints out its unique number and address.</span></span> <span data-ttu-id="df5dc-132">Při spuštění souboru Service. exe se například může zobrazit následující text.</span><span class="sxs-lookup"><span data-stu-id="df5dc-132">For instance, you may see the following text when you run service.exe.</span></span>  
  
```console  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="df5dc-133">Zadejte číslo služby, které se zobrazí, když spustíte soubor Client. exe.</span><span class="sxs-lookup"><span data-stu-id="df5dc-133">Enter the service number you see here when you run client.exe.</span></span>  
  
```console  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="df5dc-134">Tuto ukázku můžete spustit v konfiguraci mezi počítači změnou vygenerované adresy, kterou klient používá.</span><span class="sxs-lookup"><span data-stu-id="df5dc-134">This sample can be run in a cross-machine configuration by changing the generated address that the client uses.</span></span> <span data-ttu-id="df5dc-135">V Client.cs změňte řetězec formátu adresy koncového bodu tak, aby odpovídal nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="df5dc-135">In the Client.cs, change the endpoint address format string to match the new address of your service.</span></span> <span data-ttu-id="df5dc-136">Nahraďte všechny odkazy na "localhost" adresou IP počítače serveru.</span><span class="sxs-lookup"><span data-stu-id="df5dc-136">Replace any references to "localhost" with the IP address of the server machine.</span></span> <span data-ttu-id="df5dc-137">Po provedení této změny je nutné ukázku znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="df5dc-137">You must recompile the sample after making this change.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="df5dc-138">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="df5dc-138">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="df5dc-139">Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.</span><span class="sxs-lookup"><span data-stu-id="df5dc-139">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="df5dc-140">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="df5dc-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="df5dc-141">Povolte službu sdílení portů NetTcp, jak je popsáno výše v části Úvod.</span><span class="sxs-lookup"><span data-stu-id="df5dc-141">Enable the NetTcp Port Sharing Service as previously described in the introduction section.</span></span>  
  
4. <span data-ttu-id="df5dc-142">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="df5dc-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="df5dc-143">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="df5dc-143">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="df5dc-144">Konkrétní podrobnosti pro spuštění této ukázky jsou uvedeny dříve v části spuštění ukázkového oddílu.</span><span class="sxs-lookup"><span data-stu-id="df5dc-144">Specific details for running this sample are included previously in the Running the Sample section.</span></span>  
