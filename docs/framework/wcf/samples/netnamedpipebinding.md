---
title: NetNamedPipeBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
ms.openlocfilehash: 5904a5b61c0cc472c40eb2b4967815d5e6add195
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714661"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="4d84e-102">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="4d84e-102">NetNamedPipeBinding</span></span>
<span data-ttu-id="4d84e-103">Tato ukázka demonstruje `netNamedPipeBinding` vazby, která poskytuje komunikaci mezi procesy ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="4d84e-103">This sample demonstrates the `netNamedPipeBinding` binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="4d84e-104">Pojmenované kanály nefungují napříč počítači.</span><span class="sxs-lookup"><span data-stu-id="4d84e-104">Named pipes do not work across machines.</span></span> <span data-ttu-id="4d84e-105">Tato ukázka je založená na službě [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) Kalkulačka.</span><span class="sxs-lookup"><span data-stu-id="4d84e-105">This sample is based on The [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) calculator service.</span></span>  
  
 <span data-ttu-id="4d84e-106">V této ukázce je služba hostovaná v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="4d84e-106">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="4d84e-107">Klient i služba jsou konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d84e-107">Both the client and the service are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d84e-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4d84e-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4d84e-109">Vazba je určena v konfiguračních souborech pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="4d84e-109">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="4d84e-110">Typ vazby je určen v atributu `binding` [\<koncového bodu >](../../configure-apps/file-schema/wcf/endpoint-element.md) nebo [\<koncového bodu >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) \<elementu klienta >, jak je znázorněno v následující ukázkové konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="4d84e-110">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) or [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element, as shown in the following sample configuration:</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="4d84e-111">Předchozí příklad ukazuje, jak nakonfigurovat koncový bod pro použití vazby `netNamedPipeBinding` s výchozími nastaveními.</span><span class="sxs-lookup"><span data-stu-id="4d84e-111">The previous sample shows how to configure an endpoint to use the `netNamedPipeBinding` binding with the default settings.</span></span> <span data-ttu-id="4d84e-112">Pokud chcete nakonfigurovat vazbu `netNamedPipeBinding` a změnit některá její nastavení, musíte definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="4d84e-112">If you want to configure the `netNamedPipeBinding` binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="4d84e-113">Koncový bod musí odkazovat na konfiguraci vazby podle názvu s atributem `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="4d84e-113">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="4d84e-114">V této ukázce je konfigurace vazby pojmenována `Binding1` a má následující definici:</span><span class="sxs-lookup"><span data-stu-id="4d84e-114">In this sample, the binding configuration is named `Binding1` and has the following definition:</span></span>  
  
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
  
 <span data-ttu-id="4d84e-115">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="4d84e-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4d84e-116">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="4d84e-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4d84e-117">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4d84e-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4d84e-118">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d84e-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4d84e-119">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d84e-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4d84e-120">Chcete-li spustit ukázku v jedné konfiguraci počítače, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d84e-120">To run the sample in a single machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4d84e-121">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="4d84e-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4d84e-122">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="4d84e-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="4d84e-123">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="4d84e-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d84e-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4d84e-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
