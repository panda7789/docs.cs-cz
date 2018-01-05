---
title: "Ukázka služby Net.TCP Port Sharing"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dea3a0f0d69662021c78b0f1d57ad0ba8c11fcb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="nettcp-port-sharing-sample"></a><span data-ttu-id="8ec7b-102">Ukázka služby Net.TCP Port Sharing</span><span class="sxs-lookup"><span data-stu-id="8ec7b-102">Net.TCP Port Sharing Sample</span></span>
<span data-ttu-id="8ec7b-103">Protokol TCP/IP používá 16bitové čísla, který se nazývá port, k odlišení připojení k několika síťových aplikací, které jsou spuštěné na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-103">The TCP/IP protocol uses a 16-bit number, called a port, to differentiate connections to multiple network applications running on the same machine.</span></span> <span data-ttu-id="8ec7b-104">Pokud aplikace naslouchá na portu, pak všechny přenosy TCP pro tento port přejde k dané aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-104">If an application is listening on a port, then all TCP traffic for that port goes to that application.</span></span> <span data-ttu-id="8ec7b-105">Ostatní aplikace nemůže naslouchat na tomto portu ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-105">Other applications cannot listen on that port at the same time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8ec7b-106">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8ec7b-107">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8ec7b-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8ec7b-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8ec7b-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 <span data-ttu-id="8ec7b-110">Mnoho protokolů mají standard nebo výchozí číslo portu, které používají.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-110">Many protocols have a standard or default port number that they use.</span></span> <span data-ttu-id="8ec7b-111">Například protokol HTTP se většinou používá TCP port 80.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-111">For example, the HTTP protocol typically uses TCP port 80.</span></span> <span data-ttu-id="8ec7b-112">Internetové informační služby (IIS) má naslouchací proces sdílení portů mezi více aplikacemi HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-112">Internet Information Services (IIS) has a listener to share a port between multiple HTTP applications.</span></span> <span data-ttu-id="8ec7b-113">Služba IIS naslouchá na portu přímo a přeposílá zprávy na příslušnou aplikaci na základě informací uvnitř datového proudu zpráv.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-113">IIS listens on the port directly and forwards messages to the appropriate application based on information inside the message stream.</span></span> <span data-ttu-id="8ec7b-114">To umožňuje používat stejné číslo portu bez nutnosti pokouší tak, aby vyhradil port pro příjem zprávy více aplikacemi HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-114">This allows multiple HTTP applications to use the same port number without having to compete to reserve the port for receiving messages.</span></span>  
  
 <span data-ttu-id="8ec7b-115">Sdílení portů NetTcp je [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]funkce, která podobně umožňuje více síťových aplikací sdílet jeden port.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-115">NetTcp Port Sharing is a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]feature that similarly allows multiple network applications to share a single port.</span></span> <span data-ttu-id="8ec7b-116">Služba sdílení portů NetTcp přijímá připojení pomocí protokolu net.tcp a přeposílá zprávy na základě jejich cílové adresy.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-116">The NetTcp Port Sharing Service accepts connections using the net.tcp protocol and forwards messages based on their destination address.</span></span>  
  
 <span data-ttu-id="8ec7b-117">Služba sdílení portů NetTcp není povolena ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-117">The NetTcp Port Sharing Service is not enabled by default.</span></span> <span data-ttu-id="8ec7b-118">Před spuštěním této ukázce, je nutné ručně povolit službu.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-118">Before running this sample, you must manually enable the service.</span></span> <span data-ttu-id="8ec7b-119">Další informace najdete v tématu [postupy: povolení služby Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="8ec7b-119">For more information, see [How to: Enable the Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span></span> <span data-ttu-id="8ec7b-120">Pokud je služba zakázána, je vyvolána výjimka při spuštění aplikace serveru.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-120">If the service is disabled, an exception is thrown when the server application is started.</span></span>  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 <span data-ttu-id="8ec7b-121">Sdílení portů je na serveru povoleno nastavením <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost <xref:System.ServiceModel.NetTcpBinding> vazba nebo <xref:System.ServiceModel.Channels.TcpTransportBindingElement> prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-121">Port sharing is enabled on the server by setting the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property of the <xref:System.ServiceModel.NetTcpBinding> binding or the <xref:System.ServiceModel.Channels.TcpTransportBindingElement> binding element.</span></span> <span data-ttu-id="8ec7b-122">Klient nemá vědět, jak sdílení portů byl nakonfigurován pro použití na serveru.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-122">The client does not have to know how port sharing has been configured to use it on the server.</span></span>  
  
## <a name="enabling-port-sharing"></a><span data-ttu-id="8ec7b-123">Povolení sdílení portů</span><span class="sxs-lookup"><span data-stu-id="8ec7b-123">Enabling Port Sharing</span></span>  
 <span data-ttu-id="8ec7b-124">Následující kód ukazuje, povolení sdílení portů na serveru.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-124">The following code demonstrates enabling port sharing on the server.</span></span> <span data-ttu-id="8ec7b-125">Spustí instanci `ICalculator` na pevný port s náhodných cestou URI.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-125">It starts an instance of the `ICalculator` service on a fixed port with a random URI path.</span></span> <span data-ttu-id="8ec7b-126">I když dvě služby můžete sdílet stejný port, jejich celkový adresy koncových bodů stále musí být jedinečný, aby služba Sdílení portů NetTcp může směrovat zprávy správnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-126">Even though two services can share the same port, their overall endpoint addresses still must be unique so that the NetTcp Port Sharing Service can route messages to the correct application.</span></span>  
  
```  
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address =  
   String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```  
  
 <span data-ttu-id="8ec7b-127">S sdílení portů povolené, můžete spustit službu vícekrát bez došlo ke konfliktu u číslo portu.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-127">With port sharing enabled, you can run the service multiple times without having a conflict over the port number.</span></span> <span data-ttu-id="8ec7b-128">Pokud změníte kód zakázat sdílení portů, spuštění dvě kopie výsledků služby v druhé selhání s <xref:System.ServiceModel.AddressAlreadyInUseException>.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-128">If you change the code to disable port sharing, starting up two copies of the service results in the second failing with an <xref:System.ServiceModel.AddressAlreadyInUseException>.</span></span>  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="8ec7b-129">Spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="8ec7b-129">Running the Sample</span></span>  
 <span data-ttu-id="8ec7b-130">Chcete-li zkontrolovat, že zprávy jsou správně směrované na sdílení port služby můžete testovacího klienta.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-130">You can use the test client to check that messages are correctly routed to services sharing the port.</span></span>  
  
```  
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
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
  
 <span data-ttu-id="8ec7b-131">Každá instance služby vytiskne jeho jedinečné číslo a adresu.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-131">Each instance of the service prints out its unique number and address.</span></span> <span data-ttu-id="8ec7b-132">Když spustíte service.exe například může zobrazit následující text.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-132">For instance, you may see the following text when you run service.exe.</span></span>  
  
```  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="8ec7b-133">Zadejte číslo služby, kterou tady vidíte při spuštění client.exe.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-133">Enter the service number you see here when you run client.exe.</span></span>  
  
```  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="8ec7b-134">Tato ukázka se může spouštět ve konfigurací mezi počítači změnou generované adresy, které klient používá.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-134">This sample can be run in a cross-machine configuration by changing the generated address that the client uses.</span></span> <span data-ttu-id="8ec7b-135">V Client.cs změňte řetězec formátu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-135">In the Client.cs, change the endpoint address format string to match the new address of your service.</span></span> <span data-ttu-id="8ec7b-136">Nahradí všechny odkazy na "localhost" IP adresu počítače serveru.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-136">Replace any references to "localhost" with the IP address of the server machine.</span></span> <span data-ttu-id="8ec7b-137">Po provedení této změny je potřeba překompilovat vzorku.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-137">You must recompile the sample after making this change.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8ec7b-138">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="8ec7b-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8ec7b-139">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-139">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="8ec7b-140">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8ec7b-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="8ec7b-141">Povolte službu NetTcp Port Sharing výše popsané v části Úvod.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-141">Enable the NetTcp Port Sharing Service as previously described in the introduction section.</span></span>  
  
4.  <span data-ttu-id="8ec7b-142">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8ec7b-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="8ec7b-143">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8ec7b-143">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="8ec7b-144">Konkrétní podrobnosti ke spuštění této ukázce jsou dříve součástí spuštění ukázkový oddíl.</span><span class="sxs-lookup"><span data-stu-id="8ec7b-144">Specific details for running this sample are included previously in the Running the Sample section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec7b-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ec7b-145">See Also</span></span>
