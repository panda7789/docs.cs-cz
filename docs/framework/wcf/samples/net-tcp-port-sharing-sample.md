---
title: Ukázka služby Net.TCP Port Sharing
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: 8c2819bbf92310ad13067d1e07463717dbffafb9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334910"
---
# <a name="nettcp-port-sharing-sample"></a><span data-ttu-id="722b7-102">Ukázka služby Net.TCP Port Sharing</span><span class="sxs-lookup"><span data-stu-id="722b7-102">Net.TCP Port Sharing Sample</span></span>
<span data-ttu-id="722b7-103">16bitové číslo, volá se, port, protokol TCP/IP používá k rozlišení připojení k více síťových aplikací, které běží na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="722b7-103">The TCP/IP protocol uses a 16-bit number, called a port, to differentiate connections to multiple network applications running on the same machine.</span></span> <span data-ttu-id="722b7-104">Pokud aplikace naslouchá na portu, veškerý provoz TCP pro tento port přejde k dané aplikaci.</span><span class="sxs-lookup"><span data-stu-id="722b7-104">If an application is listening on a port, then all TCP traffic for that port goes to that application.</span></span> <span data-ttu-id="722b7-105">Jiné aplikace nemůže naslouchat na portu ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="722b7-105">Other applications cannot listen on that port at the same time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="722b7-106">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="722b7-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="722b7-107">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="722b7-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="722b7-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="722b7-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="722b7-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="722b7-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 <span data-ttu-id="722b7-110">Mnoho protokolů mají standardní nebo výchozí číslo portu, které používají.</span><span class="sxs-lookup"><span data-stu-id="722b7-110">Many protocols have a standard or default port number that they use.</span></span> <span data-ttu-id="722b7-111">Například protokolu HTTP obvykle využívá TCP port 80.</span><span class="sxs-lookup"><span data-stu-id="722b7-111">For example, the HTTP protocol typically uses TCP port 80.</span></span> <span data-ttu-id="722b7-112">Internetové informační služby (IIS) je sdílet mezi více aplikacemi HTTP port naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="722b7-112">Internet Information Services (IIS) has a listener to share a port between multiple HTTP applications.</span></span> <span data-ttu-id="722b7-113">Služba IIS naslouchá na portu přímo a předává zprávy do příslušné aplikace na základě informací uvnitř datové proudy zpráv.</span><span class="sxs-lookup"><span data-stu-id="722b7-113">IIS listens on the port directly and forwards messages to the appropriate application based on information inside the message stream.</span></span> <span data-ttu-id="722b7-114">To umožňuje používat stejné číslo portu, aniž by bylo konkurovat rezervovat port pro příjem zpráv s více aplikacemi HTTP.</span><span class="sxs-lookup"><span data-stu-id="722b7-114">This allows multiple HTTP applications to use the same port number without having to compete to reserve the port for receiving messages.</span></span>  
  
 <span data-ttu-id="722b7-115">Sdílení portů NetTcp je funkce Windows Communication Foundation (WCF), která podobně umožňuje více síťové aplikace sdílet jeden port.</span><span class="sxs-lookup"><span data-stu-id="722b7-115">NetTcp Port Sharing is a Windows Communication Foundation (WCF)feature that similarly allows multiple network applications to share a single port.</span></span> <span data-ttu-id="722b7-116">Služba sdílení portů NetTcp přijímá připojení pomocí protokol net.tcp a předává zprávy na základě jejich cílové adresy.</span><span class="sxs-lookup"><span data-stu-id="722b7-116">The NetTcp Port Sharing Service accepts connections using the net.tcp protocol and forwards messages based on their destination address.</span></span>  
  
 <span data-ttu-id="722b7-117">Služba sdílení portů NetTcp není standardně povolená.</span><span class="sxs-lookup"><span data-stu-id="722b7-117">The NetTcp Port Sharing Service is not enabled by default.</span></span> <span data-ttu-id="722b7-118">Před spuštěním této ukázky musíte ručně povolit službu.</span><span class="sxs-lookup"><span data-stu-id="722b7-118">Before running this sample, you must manually enable the service.</span></span> <span data-ttu-id="722b7-119">Další informace najdete v tématu [jak: Povolení služby Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="722b7-119">For more information, see [How to: Enable the Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span></span> <span data-ttu-id="722b7-120">Pokud je služba zakázána, je vyvolána výjimka při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="722b7-120">If the service is disabled, an exception is thrown when the server application is started.</span></span>  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 <span data-ttu-id="722b7-121">Port je povoleno sdílení na serveru tak, že nastavíte <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost <xref:System.ServiceModel.NetTcpBinding> vazby nebo <xref:System.ServiceModel.Channels.TcpTransportBindingElement> element vazby.</span><span class="sxs-lookup"><span data-stu-id="722b7-121">Port sharing is enabled on the server by setting the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property of the <xref:System.ServiceModel.NetTcpBinding> binding or the <xref:System.ServiceModel.Channels.TcpTransportBindingElement> binding element.</span></span> <span data-ttu-id="722b7-122">Klient nemá vědět, jak sdílení portů není nakonfigurovaná k použití na serveru.</span><span class="sxs-lookup"><span data-stu-id="722b7-122">The client does not have to know how port sharing has been configured to use it on the server.</span></span>  
  
## <a name="enabling-port-sharing"></a><span data-ttu-id="722b7-123">Povolení sdílení portů</span><span class="sxs-lookup"><span data-stu-id="722b7-123">Enabling Port Sharing</span></span>  
 <span data-ttu-id="722b7-124">Následující kód ukazuje povolení sdílení portu na serveru.</span><span class="sxs-lookup"><span data-stu-id="722b7-124">The following code demonstrates enabling port sharing on the server.</span></span> <span data-ttu-id="722b7-125">Spustí instanci `ICalculator` služby na pevný port se náhodný cesty identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="722b7-125">It starts an instance of the `ICalculator` service on a fixed port with a random URI path.</span></span> <span data-ttu-id="722b7-126">I v případě, že dvě služby můžou sdílet stejný port, jejich celkové adresy koncových bodů i nadále musí být jedinečný tak, aby služba Sdílení portů NetTcp může směrovat zprávy do správné aplikace.</span><span class="sxs-lookup"><span data-stu-id="722b7-126">Even though two services can share the same port, their overall endpoint addresses still must be unique so that the NetTcp Port Sharing Service can route messages to the correct application.</span></span>  

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

 <span data-ttu-id="722b7-127">S povoleno sdílení portu, můžete spustit službu vícekrát bez nutnosti konflikt přes číslo portu.</span><span class="sxs-lookup"><span data-stu-id="722b7-127">With port sharing enabled, you can run the service multiple times without having a conflict over the port number.</span></span> <span data-ttu-id="722b7-128">Pokud změníte kód a zakázat sdílení portů, spouštění dvě kopie výsledků služby v druhé selhání se <xref:System.ServiceModel.AddressAlreadyInUseException>.</span><span class="sxs-lookup"><span data-stu-id="722b7-128">If you change the code to disable port sharing, starting up two copies of the service results in the second failing with an <xref:System.ServiceModel.AddressAlreadyInUseException>.</span></span>  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="722b7-129">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="722b7-129">Running the Sample</span></span>  
 <span data-ttu-id="722b7-130">Testovacího klienta můžete použít ke kontrole, že zprávy jsou správně směrovat do služby Sdílení portu.</span><span class="sxs-lookup"><span data-stu-id="722b7-130">You can use the test client to check that messages are correctly routed to services sharing the port.</span></span>  

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

 <span data-ttu-id="722b7-131">Každá instance služby vytiskne jeho jedinečné číslo a adresu.</span><span class="sxs-lookup"><span data-stu-id="722b7-131">Each instance of the service prints out its unique number and address.</span></span> <span data-ttu-id="722b7-132">Při spuštění service.exe, například může zobrazit následující text.</span><span class="sxs-lookup"><span data-stu-id="722b7-132">For instance, you may see the following text when you run service.exe.</span></span>  
  
```  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="722b7-133">Zadejte číslo, které se tady zobrazí při spuštění client.exe.</span><span class="sxs-lookup"><span data-stu-id="722b7-133">Enter the service number you see here when you run client.exe.</span></span>  
  
```  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="722b7-134">Tato ukázka můžete spustit v konfiguraci mezi počítači změnou vygenerovaný adresy, které klient používá.</span><span class="sxs-lookup"><span data-stu-id="722b7-134">This sample can be run in a cross-machine configuration by changing the generated address that the client uses.</span></span> <span data-ttu-id="722b7-135">V Client.cs změňte řetězec formátu adresa koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="722b7-135">In the Client.cs, change the endpoint address format string to match the new address of your service.</span></span> <span data-ttu-id="722b7-136">Všechny odkazy na "localhost" nahraďte IP adresu počítače serveru.</span><span class="sxs-lookup"><span data-stu-id="722b7-136">Replace any references to "localhost" with the IP address of the server machine.</span></span> <span data-ttu-id="722b7-137">Po provedení této změny je potřeba překompilovat vzorku.</span><span class="sxs-lookup"><span data-stu-id="722b7-137">You must recompile the sample after making this change.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="722b7-138">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="722b7-138">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="722b7-139">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="722b7-139">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="722b7-140">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="722b7-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="722b7-141">Povolte službu NetTcp Port Sharing podle předchozích pokynů v úvodní části.</span><span class="sxs-lookup"><span data-stu-id="722b7-141">Enable the NetTcp Port Sharing Service as previously described in the introduction section.</span></span>  
  
4. <span data-ttu-id="722b7-142">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="722b7-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="722b7-143">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="722b7-143">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="722b7-144">Konkrétní podrobnosti o spuštěním této ukázky jsou dříve součástí běžící ukázkový oddíl.</span><span class="sxs-lookup"><span data-stu-id="722b7-144">Specific details for running this sample are included previously in the Running the Sample section.</span></span>  
