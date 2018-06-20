---
title: NetNamedPipeBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
ms.openlocfilehash: d07350dc8b999dfeb47dc1f61049d90a3faf874b
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207287"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="193e5-102">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="193e5-102">NetNamedPipeBinding</span></span>
<span data-ttu-id="193e5-103">Tento příklad ukazuje `netNamedPipeBinding` vazby, která poskytuje komunikaci mezi procesy ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="193e5-103">This sample demonstrates the `netNamedPipeBinding` binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="193e5-104">Pojmenované kanály nefungují mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="193e5-104">Named pipes do not work across machines.</span></span> <span data-ttu-id="193e5-105">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) kalkulačky služby.</span><span class="sxs-lookup"><span data-stu-id="193e5-105">This sample is based on The [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) calculator service.</span></span>  
  
 <span data-ttu-id="193e5-106">V této ukázce služba se hostuje sama.</span><span class="sxs-lookup"><span data-stu-id="193e5-106">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="193e5-107">Klient a služba jsou konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="193e5-107">Both the client and the service are console applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="193e5-108">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="193e5-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="193e5-109">Vazba je zadána v konfiguračních souborech pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="193e5-109">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="193e5-110">Typ vazby je zadán v `binding` atribut [ \<endpoint >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element, jak je znázorněno v následující ukázka konfigurace:</span><span class="sxs-lookup"><span data-stu-id="193e5-110">The binding type is specified in the `binding` attribute of the [\<endpoint>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element as shown in the following sample configuration:</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="193e5-111">Předchozí příklad ukazuje postup konfigurace koncového bodu pomocí `netNamedPipeBinding` vazba s výchozím nastavením.</span><span class="sxs-lookup"><span data-stu-id="193e5-111">The previous sample shows how to configure an endpoint to use the `netNamedPipeBinding` binding with the default settings.</span></span> <span data-ttu-id="193e5-112">Pokud chcete nakonfigurovat `netNamedPipeBinding` vazby a změnit některé jeho nastavení, je nutné definovat Konfigurace vazeb.</span><span class="sxs-lookup"><span data-stu-id="193e5-112">If you want to configure the `netNamedPipeBinding` binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="193e5-113">Koncový bod musí odkazovat Konfigurace vazeb podle názvu s `bindingConfiguration` atribut.</span><span class="sxs-lookup"><span data-stu-id="193e5-113">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="193e5-114">V této ukázce je s názvem Konfigurace vazeb `Binding1` a má následující definice:</span><span class="sxs-lookup"><span data-stu-id="193e5-114">In this sample, the binding configuration is named `Binding1` and has the following definition:</span></span>  
  
```xml  
<bindings>  
  <!--   
        Following is the expanded configuration section for a NetNamedPipeBinding.  
        Each property is configured with the default value.  
     -->  
  <netNamedPipeBinding>  
    <binding name="Binding1"   
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"   
             receiveTimeout="00:10:00"   
             sendTimeout="00:01:00"  
             transactionFlow="false"   
             transferMode="Buffered"   
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"   
             maxBufferPoolSize="524288"  
             maxBufferSize="65536"   
             maxConnections="10"   
             maxReceivedMessageSize="65536">  
      <security mode="Transport">  
        <transport protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netNamedPipeBinding>  
</bindings>  
```  
  
 <span data-ttu-id="193e5-115">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="193e5-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="193e5-116">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="193e5-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="193e5-117">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="193e5-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="193e5-118">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="193e5-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="193e5-119">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="193e5-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="193e5-120">Spustit ukázku v konfiguraci jednoho počítače, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="193e5-120">To run the sample in a single machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="193e5-121">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="193e5-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="193e5-122">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="193e5-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="193e5-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="193e5-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="193e5-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="193e5-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
  
## <a name="see-also"></a><span data-ttu-id="193e5-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="193e5-125">See Also</span></span>
