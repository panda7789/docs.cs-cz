---
title: NetNamedPipeBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
ms.openlocfilehash: b8a852345572e172d7c5400dca535bb8c098ec4f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584191"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="3a795-102">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="3a795-102">NetNamedPipeBinding</span></span>
<span data-ttu-id="3a795-103">Tato ukázka demonstruje `netNamedPipeBinding` vazbu, která poskytuje komunikaci mezi procesy ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="3a795-103">This sample demonstrates the `netNamedPipeBinding` binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="3a795-104">Pojmenované kanály nefungují napříč počítači.</span><span class="sxs-lookup"><span data-stu-id="3a795-104">Named pipes do not work across machines.</span></span> <span data-ttu-id="3a795-105">Tato ukázka je založená na službě [Začínáme](getting-started-sample.md) Kalkulačka.</span><span class="sxs-lookup"><span data-stu-id="3a795-105">This sample is based on The [Getting Started](getting-started-sample.md) calculator service.</span></span>  
  
 <span data-ttu-id="3a795-106">V této ukázce je služba hostovaná v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="3a795-106">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="3a795-107">Klient i služba jsou konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="3a795-107">Both the client and the service are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a795-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3a795-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3a795-109">Vazba je určena v konfiguračních souborech pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="3a795-109">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="3a795-110">Typ vazby je určen v `binding` atributu [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) [ \<endpoint> \<client> ](../../configure-apps/file-schema/wcf/endpoint-of-client.md) prvku nebo, jak je znázorněno v následující ukázkové konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="3a795-110">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) or [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element, as shown in the following sample configuration:</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="3a795-111">Předchozí příklad ukazuje, jak nakonfigurovat koncový bod pro použití `netNamedPipeBinding` vazby s výchozím nastavením.</span><span class="sxs-lookup"><span data-stu-id="3a795-111">The previous sample shows how to configure an endpoint to use the `netNamedPipeBinding` binding with the default settings.</span></span> <span data-ttu-id="3a795-112">Pokud chcete nakonfigurovat `netNamedPipeBinding` vazbu a změnit některá její nastavení, musíte definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="3a795-112">If you want to configure the `netNamedPipeBinding` binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="3a795-113">Koncový bod musí odkazovat na konfiguraci vazby podle názvu s `bindingConfiguration` atributem.</span><span class="sxs-lookup"><span data-stu-id="3a795-113">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="3a795-114">V této ukázce má konfigurace vazby název `Binding1` a má následující definici:</span><span class="sxs-lookup"><span data-stu-id="3a795-114">In this sample, the binding configuration is named `Binding1` and has the following definition:</span></span>  
  
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
  
 <span data-ttu-id="3a795-115">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="3a795-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3a795-116">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="3a795-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3a795-117">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="3a795-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3a795-118">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a795-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3a795-119">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a795-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3a795-120">Chcete-li spustit ukázku v jedné konfiguraci počítače, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a795-120">To run the sample in a single machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3a795-121">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="3a795-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3a795-122">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="3a795-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3a795-123">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="3a795-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3a795-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3a795-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
